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

