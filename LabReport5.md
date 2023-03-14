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
<br>
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

# Option 3

# Option 4
