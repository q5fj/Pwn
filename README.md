# Challenge 1
## Description
Let's start off simple, can you overflow the correct buffer?

### Two files were comrades in the challenge. (vuln.c , vuln)
#### vlun.c
<img src="https://github.com/q5fj/Pwn/assets/88992167/76c5aa29-ee1d-4098-bd72-92e7207f575c">

We note that in the code the binary file will not work unless the binary file path contains a file named flag.txt
<img src="https://github.com/q5fj/Pwn/assets/88992167/0a7f786c-8fbc-4524-832f-c38b7a61fcf3">

Also notice we have "gets" in the user input 

##### gets - get a string from standard input (DEPRECATED)
<img src="https://github.com/q5fj/Pwn/assets/88992167/0ae608e9-5726-4212-8449-47e2ea331cb7">

Now that have analyzed the source, let us move to the binary file:
#### vuln
#### Command :-
```
file vuln 
```
<img src="https://github.com/q5fj/Pwn/assets/88992167/0b59e5e3-38cb-4508-926f-0961f43efe8e">

The file is 32 bit, let's check the security features : 
#### Command :-
```
checksec vuln 
```
<img src="https://github.com/q5fj/Pwn/assets/88992167/598555c8-43eb-48d6-a71e-04da7dcd334e">
No stack canary, assume BOF.

Now let's start examining the file closely :)

I will use gdb tool
```
gdb ./vuln -q
```
I will display the functions inside the file 
#### Command :-
```
info functions
```


