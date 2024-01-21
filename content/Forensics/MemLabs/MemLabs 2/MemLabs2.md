---
tags:
  - cyber
  - forensics
  - memory-forensics
  - threat-hunting
---
---------------------

**Challenge Description**

One of the clients of our company, lost the access to his system due to an unknown error. He is supposedly a very popular "environmental" activist. As a part of the investigation, he told us that his go to applications are browsers, his password managers etc. We hope that you can dig into this memory dump and find his important stuff and give it back to us.

----------------------------------


First get the image info

![[Pasted image 20240112142532.png]]

In the description "environmental" keyword gives us a hint so lets scan environment variables
When we scan environment variables we can see there is a encoded string "ZmxhZ3t3M2xjMG0zX1QwXyRUNGczXyFfT2ZfTDRCXzJ9"
![[Pasted image 20240112141500.png]]When we decode the string it gives us the first flag
![[Pasted image 20240112141528.png]],

User uses Keepass as password manager so we have to look file extension for keepass
![[Pasted image 20240112141140.png]]

Then we should search and dump the .kdbx file
![[Pasted image 20240112143457.png]]
Alright we dumped the file but we don't know the password yet. Let's go on investigating 

I tried to search files have .txt extension or files named password but I can't find anything about password
![[Pasted image 20240112144246.png]]

Then I tried to search password keyword with grep -i to ignore case and here, there is a file named Password.png
![[Screenshot from 2024-01-12 14-45-08.png]]
So let's dump the fie
![[Pasted image 20240112144632.png]]
![[Pasted image 20240112144735.png]]
Good then I installed Keepass on my Windows 10 VM and I opened the password database in Keepass. And there is the second flag
![[Pasted image 20240112150321.png]]

In the description also browser is quoted so let's look at the browser history
![[Pasted image 20240112150938.png]]

Dump the file
![[Pasted image 20240112151128.png]]

And open it in SQLite
![[Pasted image 20240112151057.png]]
When you browse history there is a link "https://mega.nz/#F!TrgSQQTS!H0ZrUzF0B-ZKNM3y9E76lg" 
![[Screenshot from 2024-01-12 15-13-23.png]]
Let's check the link, there is a file named Important.zip. Try to unzip it
![[Screenshot from 2024-01-12 15-15-46.png]]

This zip archive is password protected. But there is a hint 

![[Pasted image 20240112151746.png]]

Encode stage 3 flag from lab1 with sha and here is the password for zip archive
	![[Screenshot from 2024-01-12 15-25-00.png]]
And there is the last flag in Lab 2
![[Pasted image 20240112152638.png]]