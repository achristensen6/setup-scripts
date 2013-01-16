These are the setup scripts for the Angstorm buildsystem. If you want to (re)build packages or images for Angstrom, this is the thing to use.

To configure the scripts and download the build metadata, do:

	$ MACHINE=spark ./oebb.sh config spark

You can change the 'spark' in the commandline above into the machine you are targeting.

To start a build of the kernel, do:

	$ source ~/.oe/environment-project-magpie
	$ bitbake virtual/kernel

To start a build of the image, do:
        
	$ source ~/.oe/environment-project-magpie
	$ bitbake core-image-base 

To update the metadata, do:

	$ git pull
	$ ./oebb.sh update

The oebb.sh script tries hard to keep your local changes while at the same time keeping close to the original config. Please keep the following in mind:

	* it will reset the origin URI based on layers.txt, so update layers.txt when changing a repo
	* it will do a 'git reset --hard <ref>' on locked down repos, so please create a new branch for your changes
	* As noted above, it will NOT switch branches, so be carefull when using the update function after you branched a repo

If you find any bugs please report them here: https://github.com/project-magpie/setup-scripts/issues 
