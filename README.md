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


Flashing the JFFS2 Image (spark)
================================

**ATTENTION THIS CAN BRICK YOUR HARDWARE!!! USE THIS AT YOUR OWN RISK**

The images to be flashed are located in the following folder:
- build/tmp-magpie/deploy/images/vulture-image-spark.jffs2
- build/tmp-magpie/deploy/images/uImage-spark.bin

Attention these are symbolic links to the latest image and have to be renamed.

> vulture-image-spark.jffs2 -> e2jffs2.img
> 
> uImage-spark.bin -> uImage-spark.bin


- Format USB-thumb drive with a single FAT32 partition
- Create an enigma2 folder on the USB-thumb drive
- Copy the files e2jffs2.img and uImage to the enigma2 folder onto the thumb drive
- Turn the Set-Top-Box off by the power switch
- Put the USB-Stick into the USB-Slot at the back of the STB. Not the front one!
- Press the **OK** at the Front-Panel and keep it pressed.
- Turn on the box by the power switch.
- Wait until you read "Forc" on the display
- Release the **OK** Button. Now you can press the Button **V+** -> (right).
- After this you can read __U LD__ on the display.
- The flashing of the image may take some minutes. After successfull flashing "SUCC" is written on the display and the box reboots.

---------------------------------------
If you find any bugs please report them here: https://github.com/project-magpie/setup-scripts/issues 
