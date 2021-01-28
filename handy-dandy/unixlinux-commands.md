---
title: unix/linux commands
layout: default

---

## output a certain part (lines) of a file onto clipboard for pasting
### print a certain line
sed -n _x_p _file_name
### print a line range
sed -n _x_,_y_p _file_name
### print a mixture of line range and line numbers
sed -n -e _x_,_y_p -e _z_p _file_name
### mac: to pipe output onto clipboard 
pbcopy
### an example
sed -n -e 400001,500000p -e 600000p td2 | pbcopy

## find all files containing specific text on Linux
grep -rnw '/path/to/somewhere/' -e 'pattern'
-r or -R is recursive,
-n is line number, and
-w stands for match the whole word.
-l (lower-case L) can be added to just give the file name of matching files.
Along with these, --exclude, --include, --exclude-dir flags could be used for efficient searching:

This will only search through those files which have .c or .h extensions:
grep --include=\*.{c,h} -rnw '/path/to/somewhere/' -e "pattern"

This will exclude searching all the files ending with .o extension:
grep --exclude=*.o -rnw '/path/to/somewhere/' -e "pattern"

For directories it's possible to exclude a particular directory(ies) through --exclude-dir parameter. For example, this will exclude the dirs dir1/, dir2/ and all of them matching *.dst/:
grep --exclude-dir={dir1,dir2,*.dst} -rnw '/path/to/somewhere/' -e "pattern"

## replace string1 in files with string2
### g flag to replace all the occurrences on a line
find ./ -type f -exec sed -i 's/string1/string2/g' {} \;
### For global case insensitive:
find ./ -type f -exec sed -i 's/string1/string2/gI' {} \;
### recursively search and replace
grep -rli 'old-word' * | xargs -i@ sed -i 's/old-word/new-word/g' @

## install and uninstall brew on mac
### install
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
### uninstall
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/uninstall)"

## timeout on a command with a defined signal
### set a timeout on a telnet command and kill -9 when reaches timeout
timeout --signal=9 30 telnet __host__ __port__

## list of all SIG
kill -l

