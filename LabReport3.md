James Goodwin
2/13/23
Lab Report 3

For this lab report, I have chosen to focus on the `grep` command. I found all of the commands used through ChatGPT by inputting "Can you give examples of `grep` command 
line options?

# Example 1

The first option that I used was `-i` which ignored case disctinctions in the pattern and the input files. 

I first tried using it to search through `written_2/*` for the word "Paella." When I searched without using `-i` it gave me two results, and when I used `-i` it gave
me four. 

```
[cs15lwi23ade@ieng6-203]:skill-demo1-data:396$ grep "Paella" written_2/* -r -l -c
2
[cs15lwi23ade@ieng6-203]:skill-demo1-data:397$ grep "Paella" written_2/* -r -l -i -c
4
```

I then tried it on a single file. 
```
[cs15lwi23ade@ieng6-203]:skill-demo1-data:401$ grep "Often" written_2/travel_guides/berlitz2/Costa-WhatToDo.txt -c
1
[cs15lwi23ade@ieng6-203]:skill-demo1-data:402$ grep "Often" written_2/travel_guides/berlitz2/Costa-WhatToDo.txt -c -i
4
```

# Example 2

The next option that I tried was `-A` which printed out the given number of lines of trailing context after each matching line. 
```
[cs15lwi23ade@ieng6-203]:skill-demo1-data:417$ grep "floreador" written_2/* -r -A 1
written_2/travel_guides/berlitz2/Vallarta-WhatToDo.txt:The exception is in Acapulco. The Centro de Convenciones offers arguably the best Fiesta Mexicana in the country, and is the closest you’ll come to an authentic display of Mexican culture and dance. Along with beautifully performed folkloric dances from all over Mexico, you’ll witness a pre-Hispanic ceremony called Los Voladores de Papantla, which represents an invocation to the four cardinal points and a prayer for fertility; a floreador roping exhibition; and the vibrant sounds of the mariachi. This fiesta is held every Monday, Wednesday, and Friday from 7 to 10pm. Reservations are recommended, to ensure a good table. For reservations, call Tel. (7) 484-7046.
written_2/travel_guides/berlitz2/Vallarta-WhatToDo.txt-In Puerto Vallarta one fiesta that stands out from the rest is not a traditional Fiesta Mexicana at all, but an evening at the secluded Caletas cove, accessible only by boat. Ritmos de la Noche (“Rhythms of the Night”) is a truly magical experience. You travel by fast catamarans to the former home of John Huston, where you’ll be greeted by native drums and abundant tiki torches — there is no electricity here — then dine by candlelight at tables set along the secluded beach. Following dinner, the jungle, sounds of nature, and a replica of a pyramid are the backdrop for a performance of pre-Hispanic dances with a unique contemporary choreographic twist. The show is held from Monday through Saturday. Call Tel. (3) 221-0657, for reservations.
```

I tried this again on a single file. 
```
[cs15lwi23ade@ieng6-203]:skill-demo1-data:418$ grep "drums" written_2/travel_guides/berlitz2/Vallarta-WhatToDo.txt -A 1
In Puerto Vallarta one fiesta that stands out from the rest is not a traditional Fiesta Mexicana at all, but an evening at the secluded Caletas cove, accessible only by boat. Ritmos de la Noche (“Rhythms of the Night”) is a truly magical experience. You travel by fast catamarans to the former home of John Huston, where you’ll be greeted by native drums and abundant tiki torches — there is no electricity here — then dine by candlelight at tables set along the secluded beach. Following dinner, the jungle, sounds of nature, and a replica of a pyramid are the backdrop for a performance of pre-Hispanic dances with a unique contemporary choreographic twist. The show is held from Monday through Saturday. Call Tel. (3) 221-0657, for reservations.
Nightlife
```

# Example 3

The next option that I tried was `-q` which is used to run `grep` in quiet mode and only returns an exit status that indicates whether any lines were selected or not.
I tried two different lines to get the two different exit status possibilities. 
```
[cs15lwi23ade@ieng6-203]:skill-demo1-data:423$ grep "the" written_2/* -r -q
[cs15lwi23ade@ieng6-203]:skill-demo1-data:424$ echo $?
0
```

```
[cs15lwi23ade@ieng6-203]:skill-demo1-data:425$ grep "aaiowfivuowt" written_2/* -r
[cs15lwi23ade@ieng6-203]:skill-demo1-data:426$ echo $?
1
```

# Example 4

The last option that I tried was `--with-filename` which displays the filename before the matching lines. 
```
[cs15lwi23ade@ieng6-203]:skill-demo1-data:428$ grep "Lucayans" written_2/* -r --with-filename
written_2/travel_guides/berlitz2/Bahamas-History.txt:Centuries before the arrival of Columbus, a peaceful Amerindian people who called themselves the Luccucairi had settled in the Bahamas. Originally from South America, they had traveled up through the Caribbean islands, surviving by cultivating modest crops and from what they caught from sea and shore. Nothing in the experience of these gentle people could have prepared them for the arrival of the Pinta, the Niña, and the Santa Maria at San Salvador on 12 October 1492. Columbus believed that he had reached the East Indies and mistakenly called these people Indians. We know them today as the Lucayans. Columbus claimed the island and others in the Bahamas for his royal Spanish patrons, but not finding the gold and other riches he was seeking, he stayed for only two weeks before sailing towards Cuba.
written_2/travel_guides/berlitz2/Bahamas-History.txt:The Spaniards never bothered to settle in the Bahamas, but the number of shipwrecks attest that their galleons frequently passed through the archipelago en route to and from the Caribbean, Florida, Bermuda, and their home ports. On Eleuthera the explorers dug a fresh-water well — at a spot now known as “Spanish Wells” — which was used to replenish the supplies of water on their ships before they began the long journey back to Europe with their cargoes of South American gold. As for the Lucayans, within 25 years all of them, perhaps some 30,000 people, were removed from the Bahamas to work — and die — in Spanish gold mines and on farms and pearl fisheries on Hispaniola (Haiti), Cuba, and elsewhere in the Caribbean.
```
I also tried it with a single file. 
```
[cs15lwi23ade@ieng6-203]:skill-demo1-data:434$ grep "arroz" written_2/travel_guides/berlitz2/CostaBlanca-WhatToDo.txt --with-filename
written_2/travel_guides/berlitz2/CostaBlanca-WhatToDo.txt:Excellent rice (arroz) has grown on the Costa Blanca’s doorstep since Moorish times; hence the many rice dishes and, king of them all, world-famous paella. Paella is named after the large, shallow iron pan in which it is cooked and served. The basis is rice, soaked in stock coloured yellow with locally grown saffron, and fried. Paella valenciana adds meat, usually crisply fried chicken and pork, and a seasonal variety of peas, green beans, peppers, and other vegetables. Paella alicantina is the same, plus generous portions of whole prawns, mussels, small whole crabs, octopus, and slices of lemon. A good one is a gastronomic thrill!
written_2/travel_guides/berlitz2/CostaBlanca-WhatToDo.txt:dessertun postrericearroz
```



