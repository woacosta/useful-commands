wipe current line
ctrl e + ctrl u

home
ctrl a

end
ctrl e

delete whole line
ctrl u

clear terminal
clear

## Navigating the file system

see current directory
pwd

see files in directory
ls

see all files including hidden
ls -a

see files with more info like rw permissions
ls -l

see hidden and more info
ls -la

navigate to root
cd /

navigate home
cd ~

move down one level
cd ..

move down two levels
cd ../..

## Creating, Copying, Moving, Renaming, removing Files and Directories

create a file
touch file1.txt

see what's in a file
cat file1.txt

see file with paging
less file1.txt
quit less
q

rename file1 to file2
mv file1.txt file2.txt

move file1 to another folder named Subdir
mv file1.txt Subdir/

move file1 to another folder and rename newname.txt
mv file1.txt Subdir/newname.txt

copy file2 to file named file1
cp file2.txt file1.txt

copy file1 to another folder named folder2
cp file1.txt ../folder2/file1.txt

remove a file
rm file1.txt

create a directory named foldername
mkdir foldername

### Directories

copy contents of directory named TestDir to folder named CopyDir
cp -R TestDir/ CopyDir/

rename directory TestDir to new name OrigDir
mv TestDir OrigDir

copy all text files in directory to home folder using *
cp *.txt ~/

remove a directory named linux2 (if directory empty)
rmdir linux2

remove directory (if not empty) - use -R means recursive
rm -R linux2

show location of an application ex python
which python

show history of commands typed in terminal (500?)
history

## Find Command







run as root user
sudo

use package manager to install
apt-get install nameofpackage

use package manager to update
apt-get update

use package manager to remove
apt-get remove nameofpackage

see calendar
cal

go to location with option of returning to current directory
pushd folderpath
popd

pipe takes output of one command and uses it as input of the next command. show two files and then look at them in less
cat file1.txt file2.txt | less

append line to file using >>
echo "i added this line to the end" >> file1.txt

find a file in a folder by name
find -name filename

find something within a text file using grep
grep wordwanted filename

find a word using grep and move it into a new file
grep wordwanted filename > newfilename

download something from a link to current directory
wget link

indicate that the file is a script put hashbang at top
#!/bin/bash

make script file a program
chmod +x testscript

run the script "testscript" in the current directory
./testscript


## VIM commands

move to first line
:0

move to line n
:n

move to last line
:$

insert new text
:i

undo
u

write to new filename
:w! newfilename

write and quit
:wq

quit without changes
:q!

