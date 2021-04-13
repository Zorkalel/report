# Djefferson Saintilus

#challenge Pwn **cerebrofrito**


### Gathering information
-------------------------------
1. First step,we have a lot of information that we don't now what everything mean, then I suggest to 
check one by one line for better understand the challenge this file and why not try to find flag :].

When I found the file I tried to extract all strings who is in the source code and I obtained that,
```
/lib64/ld-linux-x86-64.so.2
```
This first line indicate only a that our file is a file with extension .elf

```
 https://www.youtube.com/watch?v=Lruk56czW4w
```
In this link I saw a videos on youtube **Jossie Esteban Se Me Murio Mi Canario** where the channel name
is RICARDO SANTANA
```
Get the real flag on f2tcmrxuoxmw7uvl.onion tcp/31337
```
It will be genial if it was the real flag on this link but I didn't see anything who mark the presence
of the flag. What I found it was just the file cerebrofrito who seems be executed. 

```
[1;35m
[36m
[31m
[37m F2TC
[1;36m
[31m
[35m
[0;37m Cybersecurity
[1;35m
[36m
[31m
[0;36m Research Labs
```
That it is just a banner of the system nothing anymore

```
GCC: (Ubuntu 9.3.0-17ubuntu1~20.04) 9.3.0
```
That it just the signature of the system exploitation followed to compilator GCC for execute a program
coded with the language C

```
flag
__stack_chk_fail
vuln
.symtab
.strtab
.shstrtab
.interp
.note.gnu.property
.note.gnu.build-id
.gnu.hash
.dynsym
.dynstr
.text
.rodata
.eh_frame_hdr
.eh_frame
.dynamic
.data
.bss
.comment
```
Here I don't see what can I say but I can say they are directories.


### grossoMODO

I tried to execute the file and I obtained that
```
└─$ ./cerebrofrito 

● ● ● F2TC
● ● ● Cybersecurity                                                                                                                                                   
● ● ● Research Labs                                                                                                                                                   
🧠 🔥                                                                                                                                                                 
F�SVh����i�R�p���i�R�w��R��1�������a��i�R�0�SV�i�R���S�i�R6�����a�`�SVw��R����R����R�˄�R�zsh: killed     ./cerebrofrito
```
And I thought the best way to advance it to know the type of file even if I had it in the source code but I verified it
more clearly 
`cerebrofrito: ELF 64-bit LSB shared object, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, BuildID[sha1]=044761719190d5ed4db5ec9bedefeb47101e731d, not stripped`




2. Second step, we are going to analyse the file in a debugger & disassembler for see what information more we can obtain 
for to can resolve the challenge 

**ANALYSE IT while ELF64**
-------------------------------------------------
ANALYSE ELF64, while analysing I found multi libraries in the disassembler but some libraries do a veritable action in the
script then bellow I noted the library most important.

<li>vuln library</li>

<li>sub_1355 library : this library is responsable of the program because in this library there is a much function</li>

