<<<<<<< HEAD
Linux CLI cheat sheet

# GPG

## Import Key
gpg --import [file]

## Encrypt
gpg --encrypt --recipient [recipient] --recipient wgelpi@redhat.com [file]

## Decrypt
gpg --decrypt [file]

# Key locations

/bashrc
/etc/yum.repos.d
epel.repo
epel-testing.repo ##Required (as of 21-May-2020) for Terminator
	##Key command to enable just single packages to flow through epel-testing
	includepkgs=terminator

# Key packages/repos

## Terminator
https://terminator-gtk3.readthedocs.io/en/latest/

# Setting up Terminal Servers in /bashrc

## Access ./bashrc
`vim ~/.bashrc`
`source ~/.bashrc`

## User specific aliases and functions
function funcRDP() {
    xfreerdp +compression /bpp:32 /w:1440 /h:900 /u:wgelpi /d:win /cert-ignore +clipboard /drive:wgelpi,/home/wgelpi /v:$1
}

function funcRDPfull() {
    xfreerdp +compression /bpp:32 /f /u:wgelpi@win /cert-ignore +clipboard /drive:wgelpi,/home/wgelpi /v:$1
}

## ./bashrc function to push updates to GitHub

# git commit function
```
#git commit function 
function gitPush(){
	git status
    git add -A
    git commit -m "${1}"
    git push origin master
    git status
}

alias gitpush="gitPush"

function testParms(){
        echo ${1}
        echo ${2}
}

alias testparm="testParms"
```

## tableau VM - Login to Tableau terminal services
alias tableauvm="funcRDP bitblprod.win.redhat.com"
alias tableauvmfull="funcRDPfull bitblprod.win.redhat.com"

## Remove duplicates from your audit logs
export HISTCONTROL=erasedups

# Key URLs

## Markdown Guide
https://www.markdownguide.org/getting-started/

## Bash-Scripting Guide
https://tldp.org/LDP/abs/html/

## PyCharm
https://www.jetbrains.com/help/pycharm/installation-guide.html#

## Find/Search for files
https://fedoramagazine.org/commandline-quick-tips-locate-file/

## Extracting tar files
https://www.interserver.net/tips/kb/extract-tar-gz-files-using-linux-command-line/

## Dive Into Python 3
https://diveintopython3.problemsolving.io/

## Postman install
https://learning.postman.com/docs/postman/launching-postman/installation-and-updates/#installing-postman-on-linux

## Create a pull request in GitHub
https://opensource.com/article/19/7/create-pull-request-github

# Simple bash script example
```
#!/bin/bash
# Generate a ldif file programatically for bulk ldap updates and custom alias creation
# 

ldapDNgroup="$1"
		  # make sure file exist and readable
if [ ! -f $FILE ]; then
		echo "$FILE : does not exists"
		exit 1
elif [ ! -r $FILE ]; then
		echo "$FILE: can not read"
		exit 2
fi

funEchoConfig () {

groupID=$1
description=$2
ownerID=$3
noteS=$4

echo "dn: cn=${groupID},ou=adhoc,ou=managedGroups,dc=redhat,dc=com"
echo "owner: uid=${ownerID},ou=users,dc=redhat,dc=com"
echo "owner: uid=abhidas,ou=users,dc=redhat,dc=com"
echo "owner: uid=skamired,ou=users,dc=redhat,dc=com"
echo "rhatRoverGroupName: ${groupID}"
echo "description: ${description}"
echo "rhatGroupNotes: ${noteS}"
echo "cn: ${groupID}"
echo "objectClass: rhatRoverGroup"
echo "objectClass: groupOfUniqueNames"
echo "objectClass: top"
echo ""
}

OLDIFS=${IFS}
IFS=,

while read group desc owner notes ; do	

    #echo $group
    #echo $desc
    #echo $owner
    #echo $notes
    funEchoConfig "${group}" "${desc}" "${owner}" "${notes}"

done < "$ldapDNgroup"

IFS=${OLDIFS}
```

# Gitlab

## Adding content to Gitlab via CLI
https://docs.gitlab.com/ee/gitlab-basics/start-using-git.html

# GitHub

## Merging content to GitHub
```
git clone https://github.com/chanduakkin/test_repo.git
cd test_repo/
ls -ltr
vim README.md 
git status
git add -A
git status
git commit -m "updated README.md"
git push origin master
```
=======
>>>>>>> 79492cf83a00ee78620f0c111e5f1b333aa89358