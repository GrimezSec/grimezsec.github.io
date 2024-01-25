---
tags:
  - ctf
  - cyber
  - forensics
  - memory-forensics
  - threat-hunting
  - volatility
---

--------------
**Challenge Description**

We received this memory dump from our client recently. Someone accessed his system when he was not there and he found some rather strange files being accessed. Find those files and they might be useful. I quote his exact statement,

    The names were not readable. They were composed of alphabets and numbers but I wasn't able to make out what exactly it was.

Also, he noticed his most loved application that he always used crashed every time he ran it. Was it a virus?

Note-1: This challenge is composed of 3 flags. If you think 2nd flag is the end, it isn't!! :P

Note-2: There was a small mistake when making this challenge. If you find any string which has the string "L4B_3_D0n3!!" in it, please change it to "L4B_5_D0n3!!" and then proceed.

Note-3: You'll get the stage 2 flag only when you have the stage 1 flag.

---------------------------------------------------

First step let's get the image info
![[Pasted image 20240121054613.png]]

In second step I use pslist command for listing processes and I found these suspicious procceses for now
![[Pasted image 20240121055059.png]]

cmdscan and consoles commands didn't show anything the I used pstree command and here I can see that some of our suspicious processes TCPSVCS.exe and WerFault.exe triggered by services.exe 

![[Screenshot from 2024-01-21 05-53-10.png]]

With cmdline command I found a rar file, I am going to try dump this file

![[Screenshot from 2024-01-21 05-56-21.png]]

Here I found and dumped the file 

![[Screenshot from 2024-01-21 05-59-26.png]]

Okey this rar archive is password protected I will use envars command

![[Screenshot from 2024-01-21 06-01-16.png]]

envars command and some other commands doesn't help with password but I found a file with iehistory command. The name of this file looks like and encrypted string let'st decode it. 

![[Pasted image 20240121060835.png]]

And here! There is a flag "flag{!!_w3LL_d0n3_St4g3-1_0f_L4B_5_D0n3_!!}". The description says that there are 3 flags in this lab and we cannot pass to the 2nd stage without the first flag. If we are lucky this is the first flag

![[Pasted image 20240121061309.png]]

Yes! The first flag is the password for rar archive

![[Pasted image 20240121061838.png]]

There was only an image file in the rar archive and I find second flag but description says we have one more flag

![[Pasted image 20240121061927.png]]

For the last stage I am going to inverstigate another suspicious process NOTEPAD.exe
![[Screenshot from 2024-01-21 06-28-19.png]]

I found and dumped the suspicious exe and here I dumped 3 files (I changed names to write easily) 

![[Screenshot from 2024-01-21 06-31-38.png]]

file.dat was the file we were looking for. This was an .exe actually. So I tried to analyze exe. I used different PE analysis tools, string scanning tools and Detect-It-Easy but I can't find anything. After these attempts I decided to start reverse engineering. After spending some time in Ghidra and IDA Free I found the flag with IDA Graph View. The last flag was "bios{M3m_l4B5_OVeR_!}"

![[Screenshot from 2024-01-21 07-00-02.png]]