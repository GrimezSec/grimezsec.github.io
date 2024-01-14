
----------------------------------

**Challenge Description**

My system was recently compromised. The Hacker stole a lot of information but he also deleted a very important file of mine. I have no idea on how to recover it. The only evidence we have, at this point of time is this memory dump. Please help me.
Note: This challenge is composed of only 1 flag.
The flag format for this lab is: inctf{s0me_l33t_Str1ng}

-------------------------

First step let's get the image info

![[Screenshot from 2024-01-14 07-18-09.png]]

Then I checked processes, but I didn't see any suspicious processes except of StickyNot.exe and dllhost.exe

![[Screenshot from 2024-01-14 07-23-16.png]]


After that I use cmdscan command but I didn't get anything suspicious then I use cmdline command and I get something about "dllhost.exe"
![[Screenshot from 2024-01-14 07-28-18.png]]

Then I used consoles command but there was nothing suspicious after that I tried to get deeper for StickyNot.exe but there was nothing. After some failures I tried to search some files and here. There is a file I found named Important.txt

![[Pasted image 20240114075855.png]]

And let'st dump it.. what? Okey dumpfiles command can't extract the file 

![[Pasted image 20240114080143.png]]

After some searches about Windows forensics I find something interesting. In NTFS - New Technology File System (weird name..) there is a table named MFT - Master File Table, MFT table contains these informations about files; where is file, data in file and metadata information (I wish I had to know it until today)

And the best part about this information that Volatility can export MFT! (This process can take minutes)

![[Screenshot from 2024-01-14 08-23-03.png]]

The export txt file was 9.5 Mb and 173544 lines... Okey let's open it in a text editor and try to find something about Important.txt

And this is what we got about Important.txt luckily I have some experiences in Malware Analysis so I'm a bit used to screens like this
![[Screenshot from 2024-01-14 08-28-20.png]]

This is just Hexdump you can read it easilly or you can decode it. Finally the flag is : "inctf{1_is_n0t_EQu4l_7o_2bUt_th1s_d0s3nt_m4ke_s3ns3}"