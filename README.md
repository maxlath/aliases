Aliases Junky
=======

debian/ubuntu aliases of my own


I put all those here with different purposes in mind:
- ease the exchange with my linux wonderful world co-explorators (Grüßen Nitneuk & Stefen)
- get eventual tips, feedbacks and improvements suggestions
- get my hand on bash, git & github (see 'Help for Git & Github' hereafter)


How To
-------

*Easy version
- find the aliases that fit your need in the text files (sorted by thematic)
- open the file ~/.bash_aliases for edition and paste the alias (create one if none)
- save
- reload the aliases with the command . ~/.bashrc (reload aliases globally: ~/.bash_aliases is just for your session)

*Junky version (generate the ~/.bash_aliases file from multiple text files)
- create a folder dedicated to your aliases
- create there a text file 'loc-dir' to define the path you will use as variable
	-> set 'aldir' (for alias-directory) to the path of the alias folder you just created: aldir=~/MyAliases
	(make sure you don't use a '/' at the end)
- you will generate your '~/.bash_aliases' file with the 'genal' function (cf AliasManagement)
	-> make sure to also set a 'exclude_from_aliases' variable: mine look like exclude_from_aliases="readme|cat_src|old"
		(I exclude the source of this readme, an intermediary result of the genal function and my old aliases I don't use but don't want to erase yet)
- first generation requires to launch the command directly in the shell, it can look as this (mind to edit the 'exclude_from_aliases' variable depending of the file you already created that are ):
	```aldir=`pwd`
	exclude_from_aliases=""
	cd $aldir/src/;
	echo -e '\n\e[0;32 Starting to generate aliases'
  	for filename in !($exclude_from_aliases); do
    	echo -e "\n\n\n#$filename\n#===============================\n"
    	cat "$filename"
  	done > ~/.bash_aliases;
  	echo -e '\n\e[0;32 bash_aliases re-generated'
	}```
- As for the Easy version, you need to reload the aliases with the command . ~/.bashrc (reload aliases globally: ~/.bash_aliases is just for your session)
	

Manipulate Aliases
-------
see 'Alias management'
functionalities includes:
- edit the aliases file ('edal')
- generate the aliases file ('genal')
- reload aliases ('real')
- add an alias to aliases from command line ('addal')
- search in existing aliases ('catag')

Installation required
-------
- Some commands require to install packages (nethogs, xrandr...): time to fire your 'agi'!

Help for bash syntax
------
http://www.tldp.org/LDP/abs/html/refcards.html

Help for Git & Github
------
If some want to use this repo for pedagogic purpose too, you are very welcome!
Here is a great tutorial http://rogerdudler.github.io/git-guide/


Table of Contents
=================
[#!(readme][!(readme]---------------------


[#loc_dir][loc_dir]---------------------


[#perso][perso]---------------------


[#cat_src][cat_src]---------------------


[#old][old]---------------------


[#encryption][encryption]---------------------


[#ToC)][ToC)]---------------------




!(readme
===============================




loc_dir
===============================




perso
===============================

# Bittorrent Sync
alias stefan="cd ~/Sync/Stefan && ls"

#THUNDER
alias thunderclean="cd ~/.thunderbird/q9j6ogps.default && rm localstore.rdf"
alias thunderlog="firefox ~/.thunderbird/q9j6ogps.default/Mail/mail.gandi.net/filterlog.html"
alias thunderlogs="firefox ~/.thunderbird/q9j6ogps.default/Mail/mail.gandi.net/filterlog.html"

#RECETTES
alias cookie="cat ~/Documents/Recettes/COOOOOKIE | cowsay"

##########################TO SORT################################


#AJOUT PAR COMMAND ADDLIAS NON TRIE


# function cs(){
#   cd $1;
#   ls;
# }



cat_src
===============================




old
===============================

#TORRENT
alias utorrent="firefox http://localhost:1111/gui/ && utserver -settingspath /opt/utorrent-server-v3_0/"

#BABEL
alias startbabel="sudo service network-manager stop && cd $loc/babel && sudo ./wifi-autoconf.sh wlan0"
alias stopnetman="sudo service network-manager stop"
alias startnetman="sudo service network-manager start"

#BONDING
alias bondon="$loc/alscripts/bond.sh"
alias bondoff="$loc/alscripts/bondoff.sh"


#WATCH
alias watch="bash $loc/alscripts/watch.sh"


encryption
===============================

#KEYS
alias dogpg="gpg --yes -q --no-secmem-warning --encrypt-files -r nk@maxlath.eu"
alias ungpg="gpg --yes -q --no-secmem-warning --decrypt-files  -r nk@maxlath.eu blop.gpg"

alias addkey="cd ~/Documents/.key && ./addkey.sh"
alias grepkey="cd ~/Documents/.key && ./grepkey.sh"


ToC)
===============================

