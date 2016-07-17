# mv2 / cp2
move/copy files, renaming them if necessary to avoid overwrites

This is a simple shell script which allows you to copy/move files without worrying about overwrites. This is handy in situations where `mv -i` or `cp -i` are impractical (e.g. cron jobs, large number of files).

So, for example:

	$ ls
	the_first_file  the_second_file
	$ mv2 the_first_file the_second_file
	$ ls
	the_second_file  the_second_file_2
	$

An incrementing number is automagically added to the filename to prevent overwrites.

If called as `cp2` it behaves just as you'd expect:

	$ ls
	the_first_file  the_second_file
	$ cp2 the_first_file the_second_file
	$ ls
	the_first_file  the_second_file  the_second_file_2
	$

And it doesn't mess up your file extensions:

	$ ls
	the_first_file.jpg  the_second_file.jpg
	$ mv2 the_first_file.jpg the_second_file.jpg 
	$ ls
	the_second_file_2.jpg  the_second_file.jpg
	$

	$ ls
	the_first_file.jpg  the_second_file.jpg
	$ cp2 the_first_file.jpg the_second_file.jpg 
	$ ls
	the_first_file.jpg  the_second_file_2.jpg  the_second_file.jpg
	$ 

The script uses the real `mv` and `cp` underneath. Any arguments specified at the start of the command line that begin with `-` are passed directly to `mv`/`cp` without modification:

	$ mv2 -v the_first_file.jpg the_second_file.jpg 
	'the_first_file.jpg' -> './the_second_file_2.jpg'
	$ 

*NOTE* that the `mv --target` or `mv -t <dir>` argument is not supported by `mv2`

## Installation

Currently installation is entirely manual. To install, simply download `mv2` and place in your `PATH`. To use the script to copy, symlink `mv2` to `cp2`, and the script will handle the rest.

## Dependencies

Tested on bash 4.3.46, but should work on earlier versions. Pull requests with patches to support older versions welcome!
