# Researching Commands
I chose the `grep` command.  

The first command option is `-c`, which prints out the number of lines which matches the pattern.  

Example 1:
```
[cs15lfa22hw@ieng6.ucsd.edu]:technical:1$ grep -c "attack" 911report/chapter-10.txt
29
```

Example 2:  
```
[cs15lfa22hw@ieng6.ucsd.edu]:technical:2$ grep -c "the" 911report/chapter-10.txt
336
```

Example 3:  
```
[cs15lfa22hw@ieng6.ucsd.edu]:technical:3$ grep -c "hello" 911report/chapter-10.txt
0
```

All the command is doing is counting the number of lines which match the pattern instead of returning the lines to the terminal. This command is beneficial if you want to scan lines with a certain pattern, but don't want to the print out all of them. This is especially useful if you are looking through a large file, since the pattern you enter may return thousands of lines if you are not careful. 

---
The second command line option is `-m NUM`, which prints out the first `NUM` lines which match the pattern.  

Example 1:  
```
[cs15lfa22hw@ieng6.ucsd.edu]:technical:4$ grep -m 10 "attack" 911report/chapter-10.txt
After the attacks had occurred, while crisis managers were still sorting out a number
narrowly escaped direct attack. Extraordinary security precautions were put in place
injured and protect against any further attacks, he said: "We will make no
State Colin Powell, who had returned from Peru after hearing of the attacks, joined
attacks. Eventually, 768 aliens were arrested as "special interest" detainees. Some
attacks and to prevent a subsequent attack. Ashcroft ordered all special interest
connections; in the chaos after the attacks, it was very difficult to reach law
investigation of the 9/11 terrorist attacks.
attacks to monitor the American homeland, including review of Muslims' immigration
guidance. However, the attacks of 9/11 changed everything. Less than one week after
```

Example 2:  
```
[cs15lfa22hw@ieng6.ucsd.edu]:technical:5$ grep -m 5 "attack" 911report/chapter-10.txt
After the attacks had occurred, while crisis managers were still sorting out a number
narrowly escaped direct attack. Extraordinary security precautions were put in place
injured and protect against any further attacks, he said: "We will make no
State Colin Powell, who had returned from Peru after hearing of the attacks, joined
attacks. Eventually, 768 aliens were arrested as "special interest" detainees. Some
```

Example 3:
```
[cs15lfa22hw@ieng6.ucsd.edu]:technical:6$ grep -m 10 "country" 911report/chapter-10.txt
States were grounded, stranding tens of thousands of passengers across the country.
director had already guessed might be needed for the country as a whole.
country take some action or the administration eventually determine that it had been
of Congress." Tonight," he said, "we are a country awakened to danger." The President blamed al Qaeda for 9/11 and the 1998
```

This command simply sets a maximum number of search results to the given number (ie. in the cases of examples 1 and 3, 10 lines were printed, in the case of edxample 2, 5 lines were printed). This option is extremely useful for printing out the first few lines in the file to verify that the pattern is working properly. 

---

The final command covered in this lab report is the `-i` option. It returns all lines matching the pattern, but is not case sensitive like grep usually is.  

Example 1:
```
[cs15lfa22hw@ieng6.ucsd.edu]:technical:7$ grep -i "war" 911report/chapter-10.txt
WARTIME
Rice said President Bush began the meeting with the words, "We're at war," and that Director of Central Intelligence George Tenet said
they were not aware of the issue at all until it surfaced much later in the media.
operations center made sure that the FBI was aware of the flights of Saudi nationals
PLANNING FOR WAR
advisers, a group he would later call his "war council."33This group usually
meeting, he stressed that the United States was at war with a new and different kind
agreed to every U.S. request for support in the war on terrorism. The next day, the
avoid malice toward any people, religion, or culture.
15-16, as President Bush convened his war council at Camp David.
proposed inserting CIA teams into Afghanistan to work with Afghan warlords who would
assign tasks for the first wave of the war against terrorism. It starts today."
Threat to the United States." The directive would now extend to a global war on
striking Iraq during "this round" of the war on terrorism.
for the war on terrorism specified three priority targets for initial action: al
President Bush told Bob Woodward that the decision not to invade Iraq was made at the
the war on terrorism.
Shelton told us the administration reviewed all the Pentagon's war plans and
Having issued directives to guide his administration's preparations for war, on
President Bush argued that the new war went beyond Bin Ladin." Our war on terror
in a cave complex called Tora Bora. In March 2002, the largest engagement of the war
```

Example 2:
```  
[cs15lfa22hw@ieng6.ucsd.edu]:technical:8$ grep -i "time" 911report/chapter-10.txt
WARTIME
While the plan at the elementary school had been to return to Washington, by the time  
    officer, quickly researched the options and, sometime around 10:20, identified  
For the first time in history, all nonemergency civilian aircraft in the United  
    government attorneys to seek denial of bond until such time as they were "cleared"  
    approved by the Justice Department was time-consuming, lasting an average of about  
    time for self-defense. The United States would punish not just the perpetrators of  
    time to act was now. He said we would need to build a coalition. The President noted  
    at the same time-not only Bin Ladin. Secretary Rumsfeld later explained that at the  
    time, he had been considering either one of them, or perhaps someone else, as the  
    denied, arguing that the time was not right. (CENTCOM also began dusting off plans  
    embassy bombings and, for the first time, declared that al Qaeda was "responsible  
```

Example 3: 
```
[cs15lfa22hw@ieng6.ucsd.edu]:technical:9$ grep -i "response" 911report/chapter-10.txt
IMMEDIATE RESPONSES AT HOME
In response to a request about the counterterrorism benefits of the 9/11 detainee
    chief had met with Mullah Omar and conveyed the U.S. demands. Omar's response was
    empty training sites. He thought the U.S. response should consider a wide range of
    military responses in Iraq during the summer before 9/11-a request President Bush
```

As I mentioned the -i tag allows for phrases to be searched without regarding case-sentitivity, which normal grep has. The great advantage of non-case sentitivity is that it catches words that may be excluded out of a search due to captilization. 