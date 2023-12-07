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
```
file vuln 
```

