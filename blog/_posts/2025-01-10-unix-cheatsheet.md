---
layout: post
title: Shell Cheatsheet
description: >
  A quick reference sheet for the basics of unix shell!
sitemap: false
hide_last_modified: true
---

###### print statements
```run-shell
echo (-n: don't print newline) "message" #prints message
```
###### filtering
```run-shell
grep (-v: select everything not including the following) (-E extended regex) (-o: print all occurences of matching pattern) (-c count number of lines matching) [pattern] [filename] #filters [filename] for [pattern]
```
```run-shell
#grep and strings
right=hello
wrong=bye
echo $right | grep -E "^h"
echo $wrong | grep -E "^h" #won't print if it does not match the condition
```
###### word counts
```run-shell
wc (-n: omit newline) (-c: bytecount) (-l: count lines) (-m: count chars) [file/string] #counts (byte/lines/chars/etc) of [file/string]
```
###### sorting
```run-shell
sort (-n: sort by numerical) (-r: desc) 
head (-5) [file] #print first 5 lines
tail (-5) [file] #print last 5 lines
```
###### user input
```run-shell
read (-p: add message) "message" [variable_name] #saves user response to "message" to [variable_name]
echo $variable_name
```
###### arithmetic
```run-shell
#base shell
expr \( 4 + 2 - 3 \) \* 5 
echo "$(expr \( 4 + 2 - 3 \) \* 5)" #prints it

declare (-i: integer type) (-r: readonly) [variable_name]=4 #set integer type variable - try to set it to string later and it will be set to 0

answer=`expr 5 + 5` #command substitution - set variable to product of commands
```
```run-shell
#bash specific
answer=$(( (4+2-3)*5 )) #math operations
echo $answer
```
###### regex
```run-shell
#basic conditions
grep (-E: doesn't require backslashes) "^ex|er$" [filename] #begins with ex OR ends with er

grep -E "^[Ff][0-9]" [filename] #starts with F or F then anything from 0-9 (e.g F9, f5)

grep -E -v "[[:digit:]][[:punct:]]" [filename] #doesnt include digit/punctuation

[[:alpha:]] #any uppercase or lowercase english letter
[[:upper:]] #lowercase english letters
[[:digit:]] #0-9
[[:alnum:]] #alpha or digit
[[:xdigit:]] # digit or upper/lower [a:f]
[[:punct:]] #punctutation
. # any character
"e$" #end in e
"^e" #start with e
```

###### working with csv

```run-shell
cut (-d - delimiter) , (-f - select certain fields) 3-4 #cut out the 3rd and 4th field separated by commas

#returns unique values - NOTE: must sort before passing into the command
uniq (-c: returns distinct values + number of occurences)
uniq myfile # will take the first value if there are multiple
```

