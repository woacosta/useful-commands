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

repeat the last word from the previous command ex below same as cd environments
mkdir environments
cd !$

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

find all the files in current directory and subdirectories
find . -type f

find all the files in current directory only by setting maxdepth
find . -type f -maxdepth 1

find all directories in current directory
find . -type d

find files that begin with 'test'
find .type f -name "test*"

find files that begin with 'test' case insensitive
find .type f -iname "test*"

find files that are of type .py
find .type f -name "*.py"

find files modified in last x minutes ex 10 minutes
find .type f -mmin -10

find files modified in more than x minutes ago
find .type f -mmin +10

find files modified more than 1 min ago but less than 5 min ago
find .type f -mmin +1 -mmin -5

find files modified in less than x days ago
find .type f -mtime -10

find files accessed or changed - use same formula as above but with below
amin atime, cmin ctime

find files by file size in current directory ex 5 megabytes. use k or G for kilobytes and Gigabytes
find . -size +5M

find all jpg files in current directory and then delete them all. note that the curly brackets are to include all the results of find and the + is to end the command
find . -type f -name "*.jpg" -maxdepth 1 -exec rm {} +


## Grep command (global regular expression print)
look for string in file called names.txt
grep "John Williams" names.txt

look for sting in file but only as a whole world - case sensitive
grep -w "John Williams" names.txt

look for sting in file but only as a whole world. NOT case sensitive
grep -wi "John Williams" names.txt

look for sting in file and the line number. NOT case sensitive
grep -win "John Williams" names.txt

look for string in file with line numbers and items (B)efore, (A)fter, or both (C)ontext. ex 4 lines before, 4 lines after, and 2 lines before and after
grep -win -B 4 "John Williams" names.txt
grep -win -A 4 "John Williams" names.txt
grep -win -C 2 "John Williams" names.txt

look for string in every file in the directory, every .txt file
grep -win "John Williams" ./*
grep -win "John Williams" ./*.txt

look for string in all files and subdirectories. use -r recursive search
grep -winr "John Williams" .

see which files contain a match, how many times there is a match in a file (wirc)
grep -wirl "John Williams" .
grep -wirc "John Williams" .

pipe grep searches - pipe history to grep "git commits" then grep for "dotfile
history | grep "git commit" | grep "dotfile"

use regex to search for phone numbers. the (.) means any character
grep "...-...-...." names.txt

use perl based regex to search for digits (works for python and linux. mac must install GNU grep using homebrew for it to work)
grep -P "\d{3}-\d{3}-\d{4}" names.txt

see which version of grep you have
grep -V

## Regular Expressions (Regex)

MetaCharacters (Need to be escaped with \):
.[{()\^$|?*+
ex \. searches for all dots

.       - Any Character Except New Line
\d      - Digit (0-9)
\D      - Not a Digit (0-9)
\w      - Word Character (a-z, A-Z, 0-9, _)
\W      - Not a Word Character
\s      - Whitespace (space, tab, newline)
\S      - Not Whitespace (space, tab, newline)

\b      - Word Boundary
\B      - Not a Word Boundary
^       - Beginning of a String
$       - End of a String

[]      - Matches Characters in brackets
[^ ]    - Matches Characters NOT in brackets ex [^a-z] matches all lowercase non-alphabetical
|       - Either Or
( )     - Group - you can also use groups for replacing

Quantifiers:
*       - 0 or More
+       - 1 or More
?       - 0 or One ex. Mr\.? matches Mr with 0 period or one
{3}     - Exact Number
{3,4}   - Range of Numbers (Minimum, Maximum)


examples
[1-7]   - numbers 1-7
[a-zA-Z] - all alphabetical
^Start  - matches word 'Start' only at beginning of string
end$    - matches the letters 'end' at the end of a string
[^b]at  - all 3 letter words ending in bat except for 'bat' ie starting w/ b
\d{3}.\d{3}.\{4} - 10 digit phone number
M(r|s|rs)\.? - Mr, Ms, or Mrs or Mr. Ms. or Mrs.
[a-zA-Z0-9_.+-]+@[a-zA-Z0-9-]+\.[a-zA-Z0-9-.]+ - matches emails

These two below will match urls. then find and replace match with just groups two and three ex https://www.google.com becomes just google.com
https?://(www\.)?(\w+)(\.\w+)
$2$3

## cURL command - query urls
grab the information from the url - in this case it is a json
curl http://localhost:5000/json-test

grab the details from the url like content type in addition to the content
curl -i http://localhost:5000/json-test
curl --include

download from a url and save as test.jpg -o can be --output
curl -o test.jpg http://localhost:5000/test-pic



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

