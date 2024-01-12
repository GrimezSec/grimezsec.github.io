Challenge Description
My sister's computer crashed. We were very fortunate to recover this memory dump. Your job is get all her important files from the system. From what we remember, we suddenly saw a black window pop up with some thing being executed. When the crash happened, she was trying to draw something. Thats all we remember from the time of crash.

First get the image info
![[Pasted image 20240112133345.png]]
Scan the console outputs
![[Pasted image 20240112134019.png]]
As you can see there is an encoded text, when you decode the text it gives us the first flag 
![[Pasted image 20240112134123.png]]

For the second stage I extracted memory page of mspaint.exe process.  

![[Pasted image 20240112134217.png]]

Then I opened the extracted file with GIMP ant it gives me the second flag flag{ G00d_Boy_good_girL}

![[Screenshot from 2024-01-12 13-50-57.png]]

For the last stage, I started to investigate what the user did in Winrar. And it seems that the user opened a file called Important.rar

![[Pasted image 20240112135351.png]]
I use filescan command to find Important.rar then I dumped it with dumpfiles command
![[Pasted image 20240112135546.png]]
When I tried to unrar the rar file I found that the file was password protected but a hint was left
![[Pasted image 20240112135722.png]]

I used hashdump command for getting Alissa Simpson's NTLM hash and here it is

![[Screenshot from 2024-01-12 16-01-31.png]]

I extracted the RAR Archive
![[Pasted image 20240112140124.png]]

And this is the last flag of Lab1
![[Pasted image 20240112140159.png]]

