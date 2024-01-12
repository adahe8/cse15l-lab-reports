# Week 1: Remote Access and Filesystems
## Lab 1 Blog
1.  `cd` changes current working directory
- **with no arguments**
  initial working directory: `/home/lecture 1/` \
  ![Image](cdnoargs.png)
  When `cd` has no arguments, it means that the user hasn't specified a directory. The command then just switches the working directory over to the one accessed last (the working directory before this current one), or to the base directory if there was no other directory accessed previously.

- **with path to directory as an argument**
  working directory: `/home`
  ![Image](cdtodirectory.png)
  The current directory is now set to the directory path specified by the coder/ user.
  
- **with path to file as an argument**
  working directory: `/home/lecture1/messages` \
  ![Image](cdfilename.png)
  This gives an error because `cd` is used to select a current directory, and a full path to file is not a directory; no files can be manipulated or created inside of a file the way you can inside a working directory, so a file path cannot be a working directory.

2. `ls` lists out contents of the directory (other files and folders in it)
- **with no arguments**
  working directory: `/home`\
  ![Image](cdfilename.png)

- **with path to directory as argument**
  working directory: `/home`\
  ![Image](cdfilename.png)

- **with path to file as an argument**
  working directory: `/home`\
  ![Image](cdfilename.png)

  3. `cat` concatenates file contents; prints them out in the command line
- **with no arguments**
  working directory: `/home`\
  ![Image](cdfilename.png)

- **with path to directory as argument**
  working directory: `/home`\
  ![Image](cdfilename.png)

- **with path to file as an argument**
  working directory: `/home`\
  ![Image](cdfilename.png)
