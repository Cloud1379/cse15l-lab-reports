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
The next option that I tried out for the `-find` command was `size` which searches for files of a certain size. 

I first tried looking through `docsearch` for files larger than 100 kilbytes. 
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
For this command, I added `-1k`. The `-` symbol is to look for files smaller than the given size. the `1k` was to search for files smaller than 1 kilotype. 
I only found a single file that was smaller than the given size parameter. 

# Option 3

# Option 4
