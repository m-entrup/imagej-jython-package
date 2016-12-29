# imagej-jython-package
A minimal environment to package Jython modules with maven.

## Motivation

With ImageJ it is possible to use self written Jython modules to extend the functionality. Packages and modules can be placed at the directory `jars/Lib`. ImageJ's Jython is configured to add `jars/Lib` to the default search path for packages and modules.

If you want to use the [Updater] to distribute Jython packages and modules, it can be handy pack these files as a singe Jar file. As mavens is designed to create Jar files, it can be used to automate the packaging. This repository is a template for a maven project to achieve the given goal.

## How-to use it

The prerequisite for using this template is to have maven installed. Afterwards only four steps will allow you to use [batch_opener.py].

1. Clone this repository.

	```Bash
	git clone git@github.com:m-entrup/imagej-jython-package
	```
1. Create the jar file by running maven.

	```Bash
	cd imagej-jython-package
	mvn package
	```
1. Copy the jar file to `jars/Lib`. `Lib` may not exist, yet.

	```Bash
	mkdir -p path-to-ImageJ/jars/Lib
	cp target/imagej-jython-package-0.1.0-SNAPSHOT.jar path-to-ImageJ/jars/Lib/
	```
1. Start ImageJ and run the following Jython script.

	```Python
	# @File(label='Choose a directory', style='directory') import_dir

	from examplePackage import batch_opener

	images = batch_opener.batch_open_images(import_dir, recursive=True)
	for image in images:
		print(image)
	```

[Updater]: http://imagej.net/Updater
[batch_opener.py]: http://imagej.net/Jython_Scripting#A_batch_opener_using_os.walk.28.29
