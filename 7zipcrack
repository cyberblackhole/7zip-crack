#!/bin/bash

yellow=`tput setaf 3`
red=`tput setaf 1`
green=`tput setaf 2`
reset=`tput sgr0`
cracked=1

figlet -t 7zipCrack

function ctrlc(){
	echo -e "\n${red}Ctrl-C caught. Quiting!${reset}"
	exit 1
}

trap "ctrlc" 2

if [ $# -ne 2 ]
then
	echo "${red}Usage: $0 7zipfile wordlist $reset";
	exit 1
fi

while read word
do
	echo -ne "\r${yellow}Trying Password: $word $reset"
	7z x -p$word $1 -aoa &>/dev/null
	if [ $? -eq 0 ]; then
		cracked=0
		echo -e "\n\n${green}Password is: $word $reset"
		break
	fi
done < $2

if [ $cracked -eq 1 ]; then
	echo "${red}Couldn't Crack the password!. Try a different Dictonary. ${reset}"
fi
