Aliases Junky
=======

debian/ubuntu aliases of my own


I put all those here with different purposes in mind:
- ease the exchange with my linux wonderful world co-explorators (Grüßen Nitneuk & Stefen)
- get eventual tips, feedbacks and improvements suggestions
- get my hand on bash, git & github (see 'Help for Git & Github' hereafter)


How To
==========

Easy version
-----------------------
- find the aliases that fit your need in the text files (sorted by thematic)
- open the file ~/.bash_aliases for edition and paste the alias (create one if none)
- save
- reload the aliases with the command . ~/.bashrc (reload aliases globally: ~/.bash_aliases is just for your session)

Junky version (generate the ~/.bash_aliases file from multiple text files)
-------------------------
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
[#Alias management][Alias management]---------------------


[#Apps and processes][Apps and processes]---------------------


[#APT-GET-DOOMSDAY-MACHINE][APT-GET-DOOMSDAY-MACHINE]---------------------


[#Bittorrent Sync][Bittorrent Sync]---------------------


[#Clipboard][Clipboard]---------------------


[#Directories navigation][Directories navigation]---------------------


[#Git][Git]---------------------


[#Other utilities][Other utilities]---------------------


[#PulseAudio][PulseAudio]---------------------


[#Screens][Screens]---------------------


[#Shell][Shell]---------------------


[#Simple server][Simple server]---------------------


[#Smartphone sync tools][Smartphone sync tools]---------------------


[#System][System]---------------------


[#VirtualMachine][VirtualMachine]---------------------


[#Web utilities][Web utilities]---------------------




Alias management
===============================

#aliases to edit aliases

# with gedit
alias edit-alias="gedit ~/.bash_aliases"
alias edal="gedit ~/.bash_aliases file"

# with sublime-text 3
alias edals="subl ~/.bash_aliases"
alias edalsub="subl ~/.bash_aliases"

# with vim
alias edalv="vim ~/.bash_aliases"
alias edav="vim ~/.bash_aliases"

#NEEDS TO RELOAD ALIAS BY COMMAND reload-alias OR . ~/.bashrc for the change to be taken in account
alias reload-alias=". ~/.bashrc"
alias real=". ~/.bashrc"
alias sureal="genal && real"
alias megreal="genal && real && genalreadme"

#have a look to the existing aliases
alias catal="cat ~/.bash_aliases"
alias catag="cat ~/.bash_aliases | grep"

#add a new alias <alias name, command> to the perso file (not directly shared on github, cf genalreadme())
function addl(){
  sed -i "\$a alias $1='$2'" $aldir/src/perso; 
  echo "edit alias done"
}

#Lets generate aliases from the different text sources!
function genal(){
  echo -e 'Starting to generate aliases\e[0m'
  excluding=$exclude_from_aliases_piped
  cd $aldir/src/;
  for filename in !($excluding); do
    echo -e "\n\n\n#$filename\n#===============================\n"
    cat "$filename"
  done > ~/.bash_aliases;
  echo -e '\e[0;32mbash_aliases re-generated\e[0m'
}

#now let's prepare the README for Github to include a basic description and then directly the aliases while excluding personal aliases and setting of local directories trough variables $loc and $aldir (alias directories).
#I also keep my encryption aliases offline as I wouldn't like to spread stuff that are probably bad practices
function genalreadme(){
  excluding=$exclude_from_github_piped
  cd $aldir/src/;
  echo -e 'Generatign the Table of Content in Github Markdown'
  for filename in !($excluding); do
    echo -e "\n[#$filename][$filename]---------------------\n"
  done > ToC;
  echo -e 'Generatign the aliases'
  for filename in !($excluding); do
    echo -e "\n\n\n$filename\n===============================\n"
    cat "$filename"
  done > cat_src;
  cat 'readme' 'ToC' 'cat_src' > $aldir/README.md
  echo -e '\e[0;32mREADME.md re-generated!!\e[0m'
}

function genalgitignore(){
  excluding=$exclude_from_github
  for filename in $excluding; do
    echo src/$filename
  done > $aldir/.gitignore
}


Apps and processes
===============================

#kill processes
alias killchrome="killall chromium-browse" #kill chrome processes
alias killfire="killall firefox" #kill firefox processes
alias killfox="killall firefox" #idem
alias killthunder='killall thunderbird'
alias killbox='killall rhythmbox' #if you got a better music player btw....

#app shortkey
alias gk="gksudo gedit" #edit a text file as root
alias txt="gedit" 
alias g="gedit"
alias s="subl"
alias ff="firefox"
alias n="nautilus"


APT-GET-DOOMSDAY-MACHINE
===============================

# Those are my favorite ones :D
alias agi="sudo apt-get install -y"
alias agud="sudo apt-get update -y"
alias agug="sudo apt-get upgrade -y"
#####DOOOMSDAY MACHINE#####
alias agu="echo UPDATE && sudo apt-get update -y && echo UPGRADE && sudo apt-get upgrade -y && echo AUTOREMOVE && sudo apt-get autoremove"
#####DOOOMSDAY MACHINE#####
alias agar="sudo apt-get autoremove"
alias agadd="echo sudo add-apt-repository && sudo add-apt-repository"


Bittorrent Sync
===============================

alias btsyncconfig="sudo dpkg-reconfigure btsync"
alias btsync="sudo /etc/init.d/btsync start && echo btsync start && firefox http://localhost:4444/gui/"
alias btstop="sudo /etc/init.d/btsync stop && echo btsync stop"


#VOLE cf project at http://vole.cc
alias newvole="cd ~/Vole/users/ && mkdir" #create file for a new user
#alias vole="sudo /etc/init.d/btsync start && echo btsync start && . $loc/vole/Makefile && echo Makefile && firefox http://localhost:6789/"
alias vole="sudo /etc/init.d/btsync start && echo btsync start &&
            echo http://localhost:6789/ &&
            cd $loc/vole/ &&
            export GOPATH=`pwd` &&
            export PATH=$PATH:$GOPATH/bin &&
            make &&
            echo volego"
#never perfectly worked, needed to reload the aliases for a reason I couldn't identify so far


Clipboard
===============================


alias xclipp='xclip -sel clip <' 
#copy the content of the file in argument but less nice than the following I found later on the web.


# source: http://madebynathan.com/2011/10/04/a-nicer-way-to-use-xclip/
# A shortcut function that simplifies usage of xclip.
# - Accepts input from either stdin (pipe), or params.
# ------------------------------------------------
cb() {
  local _scs_col="\e[0;32m"; local _wrn_col='\e[1;31m'; local _trn_col='\e[0;33m'
  # Check that xclip is installed.
  if ! type xclip > /dev/null 2>&1; then
    echo -e "$_wrn_col""You must have the 'xclip' program installed.\e[0m"
  # Check user is not root (root doesn't have access to user xorg server)
  elif [[ "$USER" == "root" ]]; then
    echo -e "$_wrn_col""Must be regular user (not root) to copy a file to the clipboard.\e[0m"
  else
    # If no tty, data should be available on stdin
    if ! [[ "$( tty )" == /dev/* ]]; then
      input="$(< /dev/stdin)"
    # Else, fetch input from params
    else
      input="$*"
    fi
    if [ -z "$input" ]; then  # If no input, print usage message.
      echo "Copies a string to the clipboard."
      echo "Usage: cb <string>"
      echo "       echo <string> | cb"
    else
      # Copy input to clipboard
      echo -n "$input" | xclip -selection c
      # Truncate text for status
      if [ ${#input} -gt 80 ]; then input="$(echo $input | cut -c1-80)$_trn_col...\e[0m"; fi
      # Print status.
      echo -e "$_scs_col""Copied to clipboard:\e[0m $input"
    fi
  fi
}
# Aliases / functions leveraging the cb() function
# ------------------------------------------------
# Copy contents of a file
function cbf() { cat "$1" | cb; }  
# Copy SSH public key
alias cbssh="cbf ~/.ssh/id_rsa.pub"  
# Copy current working directory
alias cbwd="pwd | cb"  
# Copy most recent command in bash history
alias cbhs="cat $HISTFILE | tail -n 1 | cb"

#*******************
#I added an artisanal help command Max-made help
alias cbhelp="echo -e '*****\ncbf = Copy contents of a file \ncbssh = Copy SSH public key \ncbhs = Copy most recent command in bash history \n*****'"


Directories navigation
===============================

#CD
alias cdp="cd ../"
alias cdpp="cd ../ && cd ../"
#cd ~ = cd

#LS UTILITIES
alias lss="ls --size -h"
alias lssa="ls --size -ha"
alias lsss="ls --size -h -S"
alias lsssa="ls --size -ha -S"


#create a folder and 'cd' in it
function mkcd() {
  mkdir -p "$1" && cd "$1";
}
#source: https://github.com/RepublicOfCoders/Aliases/blob/master/alias.txt


#I love to use aliases to reach a given directory.
#Far to much private information here but just to let you get the idea
alias aliases="cd $aldir && ls"

alias scripts='cd $loc/scripts && ls'
alias scriptcd='scripts'

alias youtube="cd ~/DL/youtube/ && ls"
alias youtuben="nautilus ~/DL/youtube/"

alias mp3="cd ~/DL/mp3/ && ls"
alias mp3n="nautilus ~/DL/mp3/"

alias dl="cd ~/DL/ && ls"
alias dln="nautilus ~/DL/"

alias bidouille="cd ~/Bidouille/ && ls"
alias bidouillen="nautilus ~/Bidouille/"

alias school="cd ~/DL/Courses/CodeSchool/JS/ && ls"
alias coffeescript="cd ~/DL/Courses/CodeSchool/JS/4\ -\ CoffeeScript/ && ls"
alias backbone="cd ~/DL/Courses/CodeSchool/JS/3\ -\ Backbone.js/ && ls"
alias nodeschool="cd ~/DL/Courses/CodeSchool/JS/5\ -\ Node.js/ && ls"
alias schooln="nautilus ~/DL/Courses/CodeSchool/JS/"

alias htc="cd ~/HTCsync/ && ls"
alias images="cd ~/Images/ && ls"
alias htcimg="cd ~/Images/HTC_Cam/ && ls"
alias voyages='cd ~/HTCsync/Voyages/ && ls'


Git
===============================

alias gpom="git push origin master"


Other utilities
===============================

#EOG: open an image
alias img="echo eog for Eye of GNOME && eog"

#PING
alias pig="echo Trying to ping google.fr && ping google.fr"

#HOWTO: files where I note my own howto historic
alias howg="cat $loc/HOWTO/* | grep -H"
alias howto="nautilus $loc/HOWTO"


#Extraction
extract () {
    if [ -f $1 ] ; then
      case $1 in
        *.tar.bz2) tar xjf $1 ;;
        *.tar.gz) tar xzf $1 ;;
        *.bz2) bunzip2 $1 ;;
        *.rar) unrar e $1 ;;
        *.gz) gunzip $1 ;;
        *.tar) tar xf $1 ;;
        *.tbz2) tar xjf $1 ;;
        *.tgz) tar xzf $1 ;;
        *.zip) unzip $1 ;;
        *.Z) uncompress $1 ;;
        *.7z) 7z x $1 ;;
        *) echo "'$1' cannot be extracted via extract()" ;;
         esac
     else
         echo "'$1' is not a valid file"
     fi
}
#source: https://github.com/RepublicOfCoders/Aliases/blob/master/alias.txt


PulseAudio
===============================

#I got issues with PulseAudio while I try to use an USB sound card: PulseAudio gets lost between the possible outputs
#I use to do the change manually with Pavucontrol, which is just a GUI for pacmd
#but nothing worth command aliases \o/

#Pavucontrol-killer from the command line

#Visualizing the stats of sinks and apps output
alias pavu="echo pacmd list-sinks \| grep index && pacmd list-sinks | grep index && echo pactl list short sink-inputs
&& pactl list short sink-inputs && echo [Help] pactl move-sink-input [ID] [sink] ALIAS ms [ID] [sink]"

#changing the output sink for a given app
alias ms="pactl move-sink-input"
# [Help] pactl move-sink-input [ID] [sink] ALIAS ms [ID] [sink]
#source: http://unix.stackexchange.com/questions/65246/change-pulseaudio-input-output-from-shell


#Changing the master sink (that is, the one your sound keys controls)
#The sink IDs tend to change so I just try to change and ask for a sink list to adapt
alias sw0="pacmd set-default-sink 0 && pacmd list-sinks | grep index"
alias sw1="pacmd set-default-sink 1 && pacmd list-sinks | grep index"
alias sw2="pacmd set-default-sink 2 && pacmd list-sinks | grep index"
alias sw3="pacmd set-default-sink 3 && pacmd list-sinks | grep index"
alias sw4="pacmd set-default-sink 4 && pacmd list-sinks | grep index"
alias sw5="pacmd set-default-sink 5 && pacmd list-sinks | grep index"


Screens
===============================

#PCSCR
alias pc="xrandr --output LVDS --mode 1280x800 --pos 0x0 --rotate normal --output CRT1 --off --output DFP1 --off"
alias tv="xrandr --output LVDS --off --output CRT1 --mode 1360x768 --pos 0x0 --rotate normal --output DFP1 --off"
alias pctv="xrandr --output LVDS --mode 1280x800 --pos 0x0 --rotate normal --output CRT1 --mode 1360x768 --pos 0x0 --rotate normal --output DFP1 --off"


alias red="redshift -l 45.702073:3.955733" #turn the screen more red depending of the hour of the day (avoiding eye fatigue)


Shell
===============================

alias hig="history | grep" #look for the argument in the shell history (an other one of my favorite)
alias c="clear" #clear the screen
alias cc='c && cd'


Simple server
===============================

#one line simple server
alias locbid="cd ~/Projet/ && python -m SimpleHTTPServer"


#stuffs to push updates to appengine, very handy for Udacity courses
alias locgin="cd ~/Projet/ && google_appengine/dev_appserver.py udacity/maxlathunchained/"
alias upgin="cd ~/Projet/ && google_appengine/appcfg.py update udacity/maxlathunchained/"

alias locgintest="cd ~/Projet/ && google_appengine/dev_appserver.py --port=9999 nk1nk3/ "
alias upgintest="cd ~/Projet/ && google_appengine/appcfg.py update nk1nk3/ "

alias locginyou="cd ~/Projet/ && google_appengine/dev_appserver.py --port=9090 youtify/ "
alias upginyou="cd ~/Projet/ && google_appengine/appcfg.py update youtify/ "

alias locginbook="cd ~/Projet/ && google_appengine/dev_appserver.py --port=7777 booksurfing/ "
alias upginbook="cd ~/Projet/ && google_appengine/appcfg.py update booksurfing/ "

alias locginblog="cd ~/Projet/ && google_appengine/dev_appserver.py --port=7778 booksurfing/cs253-blog/ "

alias cmdgin="gedit $loc/cmdgin" #OUVRIR MEMO COMMAND APPENGINE


Smartphone sync tools
===============================

#Synchronization utilities between my smartphone (/media/SD/) and my computer

alias htcphotosync="rsync -h --progress --stats -r -t --modify-window=1 -l -D --update /media/SD/DCIM/Camera/ ~/Images/HTC_Cam/"
#backup the photos on my computer

alias htcfilesync="rsync -h --progress --delete --stats -r -t --modify-window=1 -l -D --update /home/maxlath/HTCsync/ /media/SD/HTCSync/"
#transfer the file on my computer to my smartphone (containing Music, Travel documents, Videos  subfolders and stuffs)

alias htcsync="echo STARTING HTCPHOTOSYNC && htcphotosync && echo STARTING HTCFILESYNC && htcfilesync"
#lauch both does previous sync and tell proudly about it



System
===============================

alias shn="sudo shutdown -h now" #turn off the PC now & quickly (requires password so a bit tedious though)
alias srn="sudo shutdown -r now" #reboot PC now (same pb with pw and can't turn off acpi on my buggy machine)
alias sleep="sudo pm-suspend --quirk-s3-bios" #http://manpages.ubuntu.com/manpages/hardy/man8/pm-action.8.html

#GRUB
alias edgrub="gk /etc/default/grub"
alias edgrubs="sudo s /etc/default/grub"
alias regrub="sudo update-grub"

#NETHOGS (per process bandwidth meter)
alias netwlan="sudo nethogs wlan0"
alias netusb="sudo nethogs usb0"
alias neteth="sudo nethogs eth0"

#PING
alias pig="echo Trying to ping google.fr && ping google.fr"

#PATH MANAGEMENT
alias path="gk ~/.profile"
alias repath=". ~/.profile"


VirtualMachine
===============================

#start an existant virtual machine called wind7
alias vmw7="virtualbox --startvm wind7"
alias win7="vmw7"
alias w7="vmw7"

alias killvm="killall VirtualBox" #kill vm
alias killbox="killall VirtualBox" #idem


Web utilities
===============================

#Open your brother's console to start to mess around!

#prepare your clipboard to inject jquery. The script is a copy from http://blog.reybango.com/2010/09/02/how-to-easily-inject-jquery-into-any-web-page/
alias loadjquery="xclipp $loc/scripts/jqueryinject.js && echo -e '\e[0;32mjQuery loaded in Clipboard:\e[0m ready for Console'"
alias jquery="loadjquery"

#I created a little text file 'editweb.js' to stock my pre-tailored jquery command
alias edweb="g $loc/scripts/editweb.js"
alias edwebs="s $loc/scripts/editweb.js"
alias loadbodyfonthelvetica="grep 'helvetica' $loc/scripts/editweb.js | cb"
alias helvetica="loadbodyfonthelvetica"
alias loadbodyfontverdana="grep 'verdana' $loc/scripts/editweb.js | cb"
alias verdana="loadbodyfontverdana"

# command examples
# jQuery('body, div, p, blockquote, li, pre').css({'font-family': 'verdana', 'font-weight': ''});
# jQuery('body, div, p, blockquote, li, pre').css({'font-family': 'helvetica', 'font-weight': ''});

