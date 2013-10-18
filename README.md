Aliases Junky
=======

debian/ubuntu aliases of my own


I put all those here with different purposes in mind:
- ease the exchange with my linux wonderful world co-explorators (Grüßen Nitneuk & Stefen)
- get eventual tips, feedbacks and improvements suggestions
- get my hand on bash, git & github (see 'Help for Git & Github' hereafter)


How To
==========

####Easy version
- find the aliases that fit your need in the text files (sorted by thematic)
- open the file ~/.bash_aliases for edition and paste the alias (create one if none)
- save
- reload the aliases with the command . ~/.bashrc (reload aliases globally: ~/.bash_aliases is just for your session)

####Junky version
 (generate the ~/.bash_aliases file from multiple text files)
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
	
######NB: Problems with Github MarkDown
I could find a way to nicely escape bash commentaries '#' which Github MarkDown turned into hearders, I thus replaced them with backslash (cf genalreadme). Beware not to copy commentaries without changing back from '\' to '#' !

######Manipulate Aliases
see 'Alias management'
functionalities includes:
- edit the aliases file ('edal')
- generate the alias file from different source text file ('genal')
- reload aliases ('real')
- add an alias to aliases from command line ('addal')
- search in existing aliases ('catag')

######Installation required
- Some commands require to install packages (nethogs, xrandr...): time to fire your 'agi'!

######Help for bash syntax
http://www.tldp.org/LDP/abs/html/refcards.html

######Help for Git & Github
If some want to use this repo for pedagogic purpose too, you are very welcome!
Here is a great tutorial http://rogerdudler.github.io/git-guide/


Table of Contents
=================
[Alias management-include](https://github.com/maxlath/aliases/blob/master/src/Alias%20management-include)

[Apps and processes-include](https://github.com/maxlath/aliases/blob/master/src/Apps%20and%20processes-include)

[APT-GET-DOOMSDAY-MACHINE-include](https://github.com/maxlath/aliases/blob/master/src/APT-GET-DOOMSDAY-MACHINE-include)

[Bittorrent Sync-include](https://github.com/maxlath/aliases/blob/master/src/Bittorrent%20Sync-include)

[Clipboard-include](https://github.com/maxlath/aliases/blob/master/src/Clipboard-include)

[Directories navigation-include](https://github.com/maxlath/aliases/blob/master/src/Directories%20navigation-include)

[Git-include](https://github.com/maxlath/aliases/blob/master/src/Git-include)

[Other utilities-include](https://github.com/maxlath/aliases/blob/master/src/Other%20utilities-include)

[PulseAudio-include](https://github.com/maxlath/aliases/blob/master/src/PulseAudio-include)

[Screens-include](https://github.com/maxlath/aliases/blob/master/src/Screens-include)

[Shell-include](https://github.com/maxlath/aliases/blob/master/src/Shell-include)

[Simple server-include](https://github.com/maxlath/aliases/blob/master/src/Simple%20server-include)

[Smartphone sync tools-include](https://github.com/maxlath/aliases/blob/master/src/Smartphone%20sync%20tools-include)

[System-include](https://github.com/maxlath/aliases/blob/master/src/System-include)

[VirtualMachine-include](https://github.com/maxlath/aliases/blob/master/src/VirtualMachine-include)

[Web utilities-include](https://github.com/maxlath/aliases/blob/master/src/Web%20utilities-include)
