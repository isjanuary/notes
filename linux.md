how to set proxy of git

	git config --global http.proxy http://yourProxy:yourPort
	git config --global http.proxy http://user:password@proxy:port
	git config --global url."https://".insteadOf git://		(This will change http:// protocol to git://)
	git config file is here: ~/.gitconfig
	npm config file is here: ~/.npmrc



how to set proxy of apt-get
	
	vim /etc/apt/apt.conf
	type this line:		Acquire::http::proxy "http://proxy.chn.fujixerox.com:8000/";
						Acquire::http::proxy "http://yourProxyName:port";






how to install npm
    website: 
            https://github.com/npm/npm
    search: Fancy Install (Unix)
        use curl -L
        config curl proxy if necessary, see:
        http://stackoverflow.com/questions/7559103/how-to-setup-curl-to-permanently-use-a-proxy
    if EACCESS OR fail to mkdir occurred, use sudo curl -L url | sudo sh






how to setup chrome browser

	1.	wget https://dl.google.com/linux/direct/google-chrome-stable_current_i386.deb
		Or	wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb
	2.	sudo dpkg -i google-chrome-stable_current_i386.deb/amd64.deb
	3.	sudo apt-get -f install





useful instructions for vim plugins
	website: https://github.com/VundleVim/Vundle.vim
			 oli.me.uk/2013/06/29/equipping-vim-for-javascript/
			 https://github.com/sirver/ultisnips/
			 https://github.com/honza/vim-snippets/




remove all new lines in one file
	command: tr -d '\n' < yourfile.txt
	ref web: stackoverflow.com/questions/3134791/how-do-i-remove-newlines-from-a-text-file





td-agent info
	website: http://docs.treasuredata.com/articles/td-agent#set-up-td-agent
install td-agent
	start:   curl -L http://toolbelt.treasuredata.com/sh/install-ubuntu-precise-td-agent2.sh -o README 
															(output	curl result to file named "README")
			 follow steps in file "README"
			 sudo curl https://packages.treasuredata.com/GPG-KEY-td-agent -o key 
			 sudo apt-key add key
			 												(output agent key to file "key" and add it to key)
			 sudo echo "deb...." > /etc/apt/...
			 sudo apt-get update
			 sudo apt-get install -y  --force-yes td-agent
	---- finish ----





superagent usage
	webite: https://github.com/visionmedia/superagent				            (official site)
			smalljs.org/ajax/superagent






YouCompleteMe: vim coding auto completion
    website: https://github.com/Valloric/YouCompleteMe                          (official site)
             http://www.alexeyshmalko.com/2014/youcompleteme-ultimate-autocomplete-plugin-for-vim/
             https://github.com/Valloric/YouCompleteMe/issues/28                solution to <VAR>-NOTFOUND







Useful commands:
    1. find . -type f -name 'expr'                                          find files with 'expr' type
    2. find . -type f ! -name 'expr'                                        find files without 'expr' type    
    3. find . -type f -name 'expr' | xargs grep 'str'                       find files with string 'str' in 'expr'
                                                                          type files

    4. find . ! -path "path/to/dir/*"                                       find files excluding dir

    5. grep -r "lib/mail" --exclude-dir="dir"                               find files with string "lib/mail" but
                                                                          excluding dir






share document across windows and linux
    step: FolderA ---> right click ---> Properties ---> Local Network Share tab 
                  ---> tick 'Share this folder'




mongodb:
    install:         http://www.runoob.com/mongodb/mongodb-linux-install.html
    official site:   https://www.mongodb.org/
possible problem: Unable to locate package mongodb-org
    website:   http://stackoverflow.com/questions/28945921/e-unable-to-locate-package-mongodb-org
               https://migueldavid.eu/linux/ubuntu-precise-12-04-unable-to-locate-package-mongodb-org/
               stackoverflow.com/questions/24899849/connection-refused-to-mongodb-errno-111





url for firefox latest version
    websit: https://www.mozilla.org/en-US/firefox/all/




command xrandr error: Failed to get size of gamma for output default
    website:   http://linuxbsdos.com/2014/10/31/solutions-for-low-screen-resolution-in-ubuntu-14-0414-10-and-virtualbox/
               http://crunchbang.org/forums/viewtopic.php?id=33990
               http://ubuntuforums.org/showthread.php?t=2269341
               http://unix.stackexchange.com/questions/176452/how-to-fix-error-xrandr-cannot-find-output-vga1
               https://bugs.launchpad.net/ubuntu/+source/x11-utils/+bug/1078695
               http://ubuntuforums.org/showthread.php?t=2263316





Nvidia X server settings
    website:   https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia
               https://help.ubuntu.com/community/Nvidia
               http://blog.sina.com.cn/s/blog_58c3ebc30100jk7z.html
               http://www.cnblogs.com/moinmoin/archive/2011/03/23/ubuntu-nvidia-widescreen-resolution.html





verify which ports are listening
    nmap cmd:   sudo nmap -sT -O localhost
                install nmap if namp is not available
putty(client for windows) and install ssh service
    putty usage:    http://internal.math.arizona.edu/services/computing/remote-access/shell/putty
                    Host Name:  username@ipAddr
                    Port:       22(in most cases)
                    if 'NETWORK error: connection refused' shows up, perhaps ssh is not installed
                    on remote machine. use namp cmd above to check if ssh is in use
    install ssh:    http://stackoverflow.com/questions/22499443/why-the-sshd-service-is-unrecognized
                    sudo apt-get install openssh-client
                    sudo apt-get install openssh-server
                    sudo /etc/init.d/ssh restart (restart ssh)
   



All icons in ~ directory are shown in Desktop
    reason:     dir ~/Desktop has been removed
    solution:   revert ~/Desktop; vim ~/.config/user-dirs.dirs;
    ref:        http://askubuntu.com/questions/479546/how-do-i-remove-home-folder-that-shows-up-on-desktop
                http://stackoverflow.com/questions/19173955/why-are-the-files-under-root-directory-showed-on-desktop-in-centos-after-i-de



install gitlab client
    [see this](https://about.gitlab.com/downloads/#centos7)  


[makefile](http://blog.csdn.net/haoel/article/details/2886)
