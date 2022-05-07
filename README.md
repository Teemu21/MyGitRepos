# MyGitRepos - By Teemu Koskinen
H7: My miniproject will be about Salt state that will install Git, SSH and Micro on the computer if necessary. It will also generate SSH public key automatically and clone my three Github repos to be ready on that computer when I want to edit those three repos. This state is meant to be working on both Windows and Linux distributions. This state is mainly for my own use but if someone has multiple Github repos that you want to edit on the new computer then my state might help you too. 

# State:

This project is currently in ALPHA state.

# Start 7.5.2022:

I will start this project by creating those three repositories I talked about before but I actually has to create just two because one of them already exist. 

The repositories that will be used in this project are Animesongs, Soturikissat and MyGunpla.

![repos](repos.png)

Let's test the main thing in this project that is the cloning multiple git repositories at the same time.

	$ git clone git@github.com:Teemu21/Animesongs.git git@github.com:Teemu21/Soturikissat.git git@github.com:Teemu21/MyGunpla.git
	
Let's test this.

	$ git clone git@github.com:Teemu21/Animesongs.git git@github.com:Teemu21/Soturikissat.git git@github.com:Teemu21/MyGunpla.git
	fatal: Too many arguments.
	
	usage: git clone [<options>] [--] <repo> [<dir>]
	
	    -v, --verbose         be more verbose
	    -q, --quiet           be more quiet
	    --progress            force progress reporting
	    -n, --no-checkout     don't create a checkout
	    --bare                create a bare repository
	    --mirror              create a mirror repository (implies bare)
	    -l, --local           to clone from a local repository
	    --no-hardlinks        don't use local hardlinks, always copy
	    -s, --shared          setup as shared repository
	    --recurse-submodules[=<pathspec>]
	                          initialize submodules in the clone
	    --recursive ...       alias of --recurse-submodules
	    -j, --jobs <n>        number of submodules cloned in parallel
	    --template <template-directory>
	                          directory from which templates will be used
	    --reference <repo>    reference repository
	    --reference-if-able <repo>
	                          reference repository
	    --dissociate          use --reference only while cloning
	    -o, --origin <name>   use <name> instead of 'origin' to track upstream
	    -b, --branch <branch>
	                          checkout <branch> instead of the remote's HEAD
	    -u, --upload-pack <path>
	                          path to git-upload-pack on the remote
	    --depth <depth>       create a shallow clone of that depth
	    --shallow-since <time>
	                          create a shallow clone since a specific time
	    --shallow-exclude <revision>
	                          deepen history of shallow clone, excluding rev
	    --single-branch       clone only one branch, HEAD or --branch
	    --no-tags             don't clone any tags, and make later fetches not to follow them
	    --shallow-submodules  any cloned submodules will be shallow
	    --separate-git-dir <gitdir>
	                          separate git dir from working tree
	    -c, --config <key=value>
	                          set config inside the new repository
	    --server-option <server-specific>
	                          option to transmit
	    -4, --ipv4            use IPv4 addresses only
	    -6, --ipv6            use IPv6 addresses only
	    --filter <args>       object filtering
	    --remote-submodules   any cloned submodules will use their remote-tracking branch
	    --sparse              initialize sparse-checkout file to include only files at root

Seems like that cloning multiple repositories even bt hand isn't as easy as I thought it would be.

After looking info in the internet I found out that you have to use && git clone to clone multiple git repositories in their own directories.

	$ git clone git@github.com:Teemu21/Animesongs.git && git clone git@github.com:Teemu21/Soturikissat.git && git clone git@github.com:Teemu21/MyGunpla.git
	Cloning into 'Animesongs'...
	remote: Enumerating objects: 276, done.
	remote: Counting objects: 100% (119/119), done.
	remote: Compressing objects: 100% (80/80), done.
	remote: Total 276 (delta 78), reused 80 (delta 39), pack-reused 157
	Receiving objects: 100% (276/276), 34.40 KiB | 617.00 KiB/s, done.
	Resolving deltas: 100% (179/179), done.
	Cloning into 'Soturikissat'...
	remote: Enumerating objects: 4, done.
	remote: Counting objects: 100% (4/4), done.
	remote: Compressing objects: 100% (4/4), done.
	remote: Total 4 (delta 0), reused 0 (delta 0), pack-reused 0
	Receiving objects: 100% (4/4), 7.40 KiB | 7.40 MiB/s, done.
	Cloning into 'MyGunpla'...
	remote: Enumerating objects: 4, done.
	remote: Counting objects: 100% (4/4), done.
	remote: Compressing objects: 100% (4/4), done.
	remote: Total 4 (delta 0), reused 0 (delta 0), pack-reused 0
	Receiving objects: 100% (4/4), 7.37 KiB | 7.37 MiB/s, done.
	$ ls
	 Animesongs      Desktop     Downloads   hello.py    jerryngittesti   Music        MyGunpla   Projekti2   Soturikissat   teemu2.txt   Templates            Videos
	 apachemoduuli   Documents   hello       important   Linux-HomeWork   MyGitRepos   Pictures   Public      teemu          teemuntyö   'UFW Salt tila.png'

This way it seems to be working but I also found out about the program called repo that's suppose to help with multiple git repositories. I tried to install this "repo" program but I couldn't get it to work.

	
