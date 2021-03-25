# Djefferson Saintilus 


1. Gathering information

This is a file without extension but I inspect all of strings in this before to go far and
I found some strings very interesting like as :

### First Step
```
/lib64/ld-linux-x86-64.so.2
```
This note tell us that our file is a ELF file and we have to launch it with a exec convenable

### Second Step
```
https://www.youtube.com/watch?v=Lruk56czW4w
```
This is a Youtube link for see a music-video of JOSSIE ESTEBAN(LO MEJOR DE LO MEJOR) where the 
title is *Se Me Murio Mi Canario* of the Channel Ricardo Santana

### Third Step ( Suspected )
```
Get the real flag on f2tcmrxuoxmw7uvl.onion tcp/31337
```
I visited this but I had an ERROR 'MOUNT : permission denied' and I received the bad page but I learned
there is something on the port 31337


### Quard Step 
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
This is just a banner nothing anynmore, continued ...

### Fifth Step
```
GCC: (Ubuntu 9.3.0-17ubuntu1~20.04) 9.3.0
```
For this information I am searching if he has some vulnerabilities about this version if I can 
exploit them for get the flag

### Sixth Step 
```
flag
__stack_chk_fail
vuln
```
I think there are some file/directory but I must to search about for verified


### Seventh Step
```
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
[HEllO]
I am going to analyse everystrings one by one in the objectives to find some indices.
```
[Strings]
nth paddr      vaddr      len size section type  string
―――――――――――――――――――――――――――――――――――――――――――――――――――――――
0   0x00002000 0x00002000 49  56   .rodata utf8  \n💀🐤 https://www.youtube.com/watch?v=Lruk56czW4w\n\n blocks=Basic Latin,Miscellaneous Symbols and Pictographs
0   0x00003000 0x00004000 54  55   .data   ascii Get the real flag on f2tcmrxuoxmw7uvl.onion tcp/31337\n
1   0x00003040 0x00004040 122 144  .data   utf8  \n\e[1;35m● \e[36m● \e[31m●\e[37m F2TC\n\e[1;36m● \e[31m● \e[35m●\e[0;37m Cybersecurity\n\e[1;35m● \e[36m● \e[31m●\e[0;36m Research Labs\n blocks=Basic Latin,Geometric Shapes
2   0x000030d0 0x000040d0 7   11   .data   utf8   🔥\e[0m\n blocks=Basic Latin,Miscellaneous Symbols and Pictographs 
```

#

.data:0000000000004000                 public flag
.data:0000000000004000 flag            db 'Get the real flag on f2tcmrxuoxmw7uvl.onion tcp/31337',0Ah,0
.data:0000000000004000                                         ; DATA XREF: sub_1355+83↑o
.data:0000000000004000                                         ; sub_1355+93↑o
.data:0000000000004037                 align 20h

