# MyGitRepos

## By Teemu Koskinen

H7: My miniproject will be about Salt state that will install Git, SSH and Micro on the computer if necessary. It will also generate SSH public key automatically and clone my three Github repos to be ready on that computer when I want to edit those three repos. This state is meant to be working on both Windows and Linux distributions. This state is mainly for my own use but if someone has multiple Github repos that you want to edit on the new computer then my state might help you too. 

## ALL Linux Homework

[H7](https://github.com/Teemu21/Linux-HomeWork/blob/main/H7.md)

## UPDATE:

This project will only work on Windows if you have Linux on Windows. You can install Linux on Windows by following this [guide](https://itsfoss.com/install-bash-on-windows/).

# State:

This project is now COMPLETE which means that this project works on both Linux and Windows distributions.
 
# Project 

Follow the project flow in this [document](https://github.com/Teemu21/MyGitRepos/blob/main/Project.md).

# Instructions for using this Salt state:

1. Download files from release called "Complete" on your Salt master.
2. Make new directory under your own /srv/salt/ directory and copy the files to that directory.
3. Run Salt state with this command: "sudo salt "*" state.apply yourdir" and you should see similar result like below as a result.
4. Run commands named: sshkey and repos.
Additional instructions:

* If you have Windows machine and you have followed FOSS's instructions to install Linux on Windows know that when you run bash sshkey on Windows it will create SSH keys on your WSL machine but not on your actual Windows machine. After running sshkey on Windows you will have to manually run command "ssh-keygen" on your actual Windows machine so that you can use pull/push in Git.
* If your Salt Master isn't in actual publick IP address then you have to do like instruction above says about Windows. If your Salt Master has public IP address then you can use this Salt state on the WSL as well. WSL has it's own virtual network that can't be changed so you can't use it with Salt in the homenetwork.
* On Linux you should be aware that if you run sshkey before repos Git might get confused and give your character length error with first four characters being gene instead of cloning. If this happens delete sshkey command from /usr/local/bin or move it somewhere else.
  	
# Finish Salt State's Results:

	$ sudo salt "*" state.apply repos
	raspberrypi:
	----------
	          ID: programs
	    Function: pkg.installed
	      Result: True
	     Comment: All specified packages are already installed
	     Started: 10:53:22.215967
	    Duration: 245.716 ms
	     Changes:   
	----------
	          ID: choco
	    Function: chocolatey.installed
	        Name: git
	      Result: False
	     Comment: State 'chocolatey.installed' was not found in SLS 'repos'
	              Reason: 'chocolatey' __virtual__ returned False: chocolatey module could not be loaded
	     Changes:   
	----------
	          ID: choco
	    Function: chocolatey.installed
	        Name: micro
	      Result: False
	     Comment: State 'chocolatey.installed' was not found in SLS 'repos'
	              Reason: 'chocolatey' __virtual__ returned False: chocolatey module could not be loaded
	     Changes:   
	----------
	          ID: installmicro
	    Function: cmd.run
	        Name: curl https://getmic.ro | bash
	      Result: True
	     Comment: Command "curl https://getmic.ro | bash" run
	     Started: 10:53:23.816740
	    Duration: 8153.94 ms
	     Changes:   
	              ----------
	              pid:
	                  2198
	              retcode:
	                  0
	              stderr:
	                    % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
	                                                   Dload  Upload   Total   Spent    Left  Speed
	                  
	                    0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
	                    0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
	                    0     0    0     0    0     0      0      0 --:--:--  0:00:01 --:--:--     0
	                    0     0    0     0    0     0      0      0 --:--:--  0:00:02 --:--:--     0
	                  100  9898  100  9898    0     0   3051      0  0:00:03  0:00:03 --:--:--  3051
	                    % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
	                                                   Dload  Upload   Total   Spent    Left  Speed
	                  
	                    0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
	                    0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
	                    0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0
	                  
	                    6 4072k    6  271k    0     0   178k      0  0:00:22  0:00:01  0:00:21  178k
	                   47 4072k   47 1942k    0     0   770k      0  0:00:05  0:00:02  0:00:03 1667k
	                  100 4072k  100 4072k    0     0  1220k      0  0:00:03  0:00:03 --:--:-- 2093k
	              stdout:
	                  Detected platform: linux-arm
	                  Latest Version: 2.0.10
	                  Downloading https://github.com/zyedidia/micro/releases/download/v2.0.10/micro-2.0.10-linux-arm.tar.gz
	                  micro-2.0.10/micro
	                  
	                  
	                   __  __ _                  ___           _        _ _          _ _
	                  |  \/  (_) ___ _ __ ___   |_ _|_ __  ___| |_ __  | | | ___  __| | |
	                  | |\/| | |/ __| '__/ _ \   | || '_ \/ __| __/ _\ | | |/ _ \/ _  | |
	                  | |  | | | (__| | | (_) |  | || | | \__ \ || (_| | | |  __/ (_| |_|
	                  |_|  |_|_|\___|_|  \___/  |___|_| |_|___/\__\__,_|_|_|\___|\__,_(_)
	                  
	                  Micro has been downloaded to the current directory.
	                  You can run it with:
	                  
	                  ./micro
	----------
	          ID: installmicro
	    Function: cmd.run
	        Name: sudo mv micro /usr/local/bin
	      Result: True
	     Comment: Command "sudo mv micro /usr/local/bin" run
	     Started: 10:53:31.972844
	    Duration: 178.877 ms
	     Changes:   
	              ----------
	              pid:
	                  2235
	              retcode:
	                  0
	              stderr:
	              stdout:
	----------
	          ID: /usr/local/bin/repos
	    Function: file.managed
	      Result: True
	     Comment: File /usr/local/bin/repos updated
	     Started: 10:53:32.153936
	    Duration: 245.138 ms
	     Changes:   
	              ----------
	              diff:
	                  New file
	              mode:
	                  0644
	----------
	          ID: /usr/local/bin/sshkey
	    Function: file.managed
	      Result: True
	     Comment: File /usr/local/bin/sshkey updated
	     Started: 10:53:32.400235
	    Duration: 96.36 ms
	     Changes:   
	              ----------
	              diff:
	                  New file
	              mode:
	                  0644
	----------
	          ID: reposfile
	    Function: file.managed
	        Name: /usr/local/bin/repos
	      Result: True
	     Comment: 
	     Started: 10:53:32.497612
	    Duration: 13.859 ms
	     Changes:   
	              ----------
	              mode:
	                  0755
	----------
	          ID: sshfile
	    Function: file.managed
	        Name: /usr/local/bin/sshkey
	      Result: True
	     Comment: 
	     Started: 10:53:32.512464
	    Duration: 11.92 ms
	     Changes:   
	              ----------
	              mode:
	                  0755
	
	Summary for raspberrypi
	------------
	Succeeded: 7 (changed=6)
	Failed:    2
	------------
	Total states run:     9
	Total run time:   8.946 s
	windows:
	----------
	          ID: programs
	    Function: pkg.installed
	      Result: False
	     Comment: The following packages failed to install/update: ssh, git
	     Started: 10:53:20.569061
	    Duration: 298.297 ms
	     Changes:   
	              ----------
	              git:
	                  Unable to locate package git
	              ssh:
	                  Unable to locate package ssh
	----------
	          ID: choco
	    Function: chocolatey.installed
	        Name: git
	      Result: True
	     Comment: git 2.36.0 is already installed
	     Started: 10:53:20.882994
	    Duration: 7658.251 ms
	     Changes:   
	----------
	          ID: choco
	    Function: chocolatey.installed
	        Name: micro
	      Result: True
	     Comment: micro 2.0.10 is already installed
	     Started: 10:53:28.541245
	    Duration: 4832.024 ms
	     Changes:   
	----------
	          ID: installmicro
	    Function: cmd.run
	        Name: curl https://getmic.ro | bash
	      Result: False
	     Comment: Command "curl https://getmic.ro | bash" run
	     Started: 10:53:33.373269
	    Duration: 3561.755 ms
	     Changes:   
	              ----------
	              pid:
	                  16244
	              retcode:
	                  1
	              stderr:
	                    % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
	                                                   Dload  Upload   Total   Spent    Left  Speed
	                  
	                    0     0    0     0    0     0      0      0 --:--:-- --:--:-- --:--:--     0Access is denied.
	                  
	                  
	                  
	                  100  9898  100  9898    0     0  54458      0 --:--:-- --:--:-- --:--:-- 56560
	                  curl: (23) Failure writing output to destination
	              stdout:
	----------
	          ID: installmicro
	    Function: cmd.run
	        Name: sudo mv micro /usr/local/bin
	      Result: False
	     Comment: Command "sudo mv micro /usr/local/bin" run
	     Started: 10:53:36.935024
	    Duration: 31.266 ms
	     Changes:   
	              ----------
	              pid:
	                  29200
	              retcode:
	                  1
	              stderr:
	                  'sudo' is not recognized as an internal or external command,
	                  operable program or batch file.
	              stdout:
	----------
	          ID: C:/repos
	    Function: file.managed
	      Result: True
	     Comment: File C:/repos updated
	     Started: 10:53:36.966290
	    Duration: 254.358 ms
	     Changes:   
	              ----------
	              diff:
	                  New file
	----------
	          ID: C:/sshkey
	    Function: file.managed
	      Result: True
	     Comment: File C:/sshkey updated
	     Started: 10:53:37.220648
	    Duration: 28.15 ms
	     Changes:   
	              ----------
	              diff:
	                  New file
	----------
	          ID: reposfile
	    Function: file.managed
	        Name: /usr/local/bin/repos
	      Result: False
	     Comment: The 'mode' option is not supported on Windows
	     Started: 10:53:37.248798
	    Duration: 0.0 ms
	     Changes:   
	----------
	          ID: sshfile
	    Function: file.managed
	        Name: /usr/local/bin/sshkey
	      Result: False
	     Comment: The 'mode' option is not supported on Windows
	     Started: 10:53:37.248798
	    Duration: 0.0 ms
	     Changes:   
	
	Summary for windows
	------------
	Succeeded: 4 (changed=5)
	Failed:    5
	------------
	Total states run:     9
	Total run time:  16.664 s
	ERROR: Minions returned with non-zero exit code
	
