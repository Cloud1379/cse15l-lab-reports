James Goodwin <br>
3/13/23 <br>
Lab Report 5 <br><br>

For this lab, I have chosen to add on to lab report 3, where I explored options on `grep`. I will now explore the options for `find`. I did all of my commands within
the `docsearch` file from a previous lab. 

# Option 1
The first option that I tried out was `-type` which is used to search for files of a specific type. <br>

I first tried using it to search through `written_2/*` for files of the type `d` for directory. 
```
[cs15lwi23ade@ieng6-203]:docsearch:522$ find written_2/ -type d
written_2/
written_2/non-fiction
written_2/non-fiction/OUP
written_2/non-fiction/OUP/Abernathy
written_2/non-fiction/OUP/Berk
written_2/non-fiction/OUP/Castro
written_2/non-fiction/OUP/Fletcher
written_2/non-fiction/OUP/Kauffman
written_2/non-fiction/OUP/Rybczynski
written_2/travel_guides
written_2/travel_guides/berlitz1
written_2/travel_guides/berlitz2
```
This command looked through `written_2/*` and found all files that would be considered directories. It also searched through all subfiles within `written_2/*`. This
command is useful if you want to distinguish between which files are regular ones and which ones are directories. 

I then tried using it to search through docsearch for files of the type `f` for regular files. I also used the `-maxdepth` option so that I wouldn't also serach through
subfiles. 
```
[cs15lwi23ade@ieng6-203]:docsearch:543$ find -maxdepth 1 -type d
.
./.git
./lib
./written_2
[cs15lwi23ade@ieng6-203]:docsearch:544$ find -maxdepth 1 -type f
./DocSearchServer.class
./DocSearchServer.java
./FileHelpers.class
./Handler.class
./README.md
./Server.class
./Server.java
./ServerHttpHandler.class
./TestDocSearch.class
./TestDocSearch.java
./URLHandler.class
./berlitz1_sizes.txt
./berlitz2_sizes.txt
./count-txts.sh
./find-results.txt
./grep-results.txt
./kauffman_sizes.txt
./start.sh
./test.sh
./travel_guides_sizes.txt
```
This command looked through docserach to find all of the files that were of type `f`. What this did was return all of the regular files that were not directories. 
When I first tried running this command, I didn't use `maxdepth` and it gave me entirely too many files because it also looked through the subdirectories. 

# Option 2
The next option that I tried out for the `-find` command was `size` which searches for files of a certain size. 

I first tried looking through `docsearch` for files larger than 100 kilobytes. 
```
[cs15lwi23ade@ieng6-203]:docsearch:552$ find -size +100k
./.git/objects/pack/pack-ba9aa0ef27cfbc0f5d71f559a5512073bc7458de.pack
./lib/junit-4.13.2.jar
./written_2/non-fiction/OUP/Berk/CH4.txt
./written_2/non-fiction/OUP/Berk/ch2.txt
./written_2/travel_guides/berlitz1/WhereToFrance.txt
./written_2/travel_guides/berlitz1/WhereToIndia.txt
./written_2/travel_guides/berlitz1/WhereToItaly.txt
./written_2/travel_guides/berlitz1/WhereToJapan.txt
./written_2/travel_guides/berlitz1/WhereToMalaysia.txt
./written_2/travel_guides/berlitz2/Canada-WhereToGo.txt
./written_2/travel_guides/berlitz2/China-WhereToGo.txt
./written_2/travel_guides/berlitz2/Portugal-WhereToGo.txt
```
For this command, I added `+100k`. The `+` symbol is too look for files larger than the given size. The `100k` was to search for files larger than 100 kilobytes. 
This command could be useful for searching for which files take up the most system storage. 

I then tried looking through files less than one kilobyte. 
```
[cs15lwi23ade@ieng6-203]:docsearch:556$ find -size -1k
./travel_guides_sizes.txt
```
For this command, I added `-1k`. The `-` symbol is to look for files smaller than the given size. the `1k` was to search for files smaller than 1 kilobyte. 
I only found a single file that was smaller than the given size parameter. 

# Option 3
The next option that I tried was `-maxdepth`. I had already used this in previous commands, but I will now look into it further. This option specifies how far into 
the directories that `-find` will go. 

I first tried looking through `-docsearch` for directory-type files with a max depth of 1. 
```
[cs15lwi23ade@ieng6-203]:docsearch:562$ find -maxdepth 1 -type d
.
./.git
./lib
./written_2
```
I executed this command by using the `find` command followed by `-maxdepth 1`. The `1` was to specify to only serach one level deep, and `-type d` was to specify 
that only directories should be serached for. This command could be useful for specifying how deep within files that you want to actually look. 

I then tried looking through the same directory for directory-type files with a max depth of 3. 
```
[cs15lwi23ade@ieng6-203]:docsearch:563$ find -maxdepth 2 -type d
.
./.git
./.git/info
./.git/hooks
./.git/branches
./.git/refs
./.git/objects
./.git/logs
./lib
./written_2
./written_2/non-fiction
./written_2/travel_guides
```
I executed this command by doing the same thing as the previous command, but with `3` instead of `1`. This allowed me to serach two more levels deep, and this gave 
me more files that were considered directories. 

# Option 4
The last option that I tried was `-iname` which is the same as the `-name` command but is case-insensitive. 

I first tried looking for the directory named `Non-fiction`
```
[cs15lwi23ade@ieng6-203]:docsearch:582$ find -iname Non-fiction
./written_2/non-fiction
```
Technically, the directory `Non-fiction` doesn't exist, there is only `non-fiction`. However, since I used the option `-iname`, capitalization was not accounted for, 
so I was able to get a result. This is useful if you do not remember the capitalization of a file name. 

I then tried looking for the directory named `berk`. 
```
[cs15lwi23ade@ieng6-203]:docsearch:580$ find -iname berk
./written_2/non-fiction/OUP/Berk
```
The directory named `berk` doesn't actually exist, only `Berk` does. However, since I used `-iname`, I was able to find the directory when not accounting for 
capitalization. 

