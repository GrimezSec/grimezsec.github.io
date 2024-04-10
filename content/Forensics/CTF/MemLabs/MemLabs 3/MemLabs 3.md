------------------------------

**Challenge Description**

A malicious script encrypted a very secret piece of information I had on my system. Can you recover the information for me please?
Note-1: This challenge is composed of only 1 flag. The flag split into 2 parts.
Note-2: You'll need the first half of the flag to get the second.
You will need this additional tool to solve the challenge,
$ sudo apt install steghide
The flag format for this lab is: inctf{s0me_l33t_Str1ng}

---------------------------


First step let's get the image info
![[Pasted image 20240114061759.png]]

Then check the processes
![[Pasted image 20240114062152.png]]

I noted the processes I think suspicious
![[Pasted image 20240114062237.png]]

After I check cmd commands with cmdline 
![[Pasted image 20240114062747.png]]

And here there is 2 suspicious command. 
![[Pasted image 20240114062832.png]]

Let's try to extract these 2 files evilscript.py and vip.txt

![[Pasted image 20240114063556.png]]

This is the evilscript.py as you can see this code XOR encrypting the vipt.txt and encoding it with Base64
![[Screenshot from 2024-01-14 06-39-14.png]]

And this is the vip.txt
![[Pasted image 20240114064154.png]]

After decode it with CyberChef got something Key 3 is in format of our flag format in challenge description

![[Pasted image 20240114064244.png]]

After that in ctf challenge there says we will need to use steghide so I am going to search some images

First I checked for .png file extension which is a popular image file extension, and I got a lot of files but these files are not what we searching for (I checked some of them)
![[Pasted image 20240114064921.png]]

Then I checked .jpeg file extension. And here there is a file named "suspision1.jpeg" I know that this looks fake or a scam but don't forget that this is a CTF
![[Pasted image 20240114065309.png]]

Then I extracted the file, as you can see this image looks a random footage but in challenge description creator said we need to use steghide. 

![[Pasted image 20240114065634.png]]

When we try to extract file with Steghide we see there is a passphrase, while some bruteforce tries, I checked the description again and I saw there is a sentence "Note-2: You'll need the first half of the flag to get the second."

![[Pasted image 20240114070428.png]]

The passphrase is first part of the flag "inctf{0n3_h4lf". We extracted file let's check what is in it
![[Screenshot from 2024-01-14 07-08-33.png]]

And here it is there is the second part of the flag. So flag of this challenge is  "inctf{0n3_h4lf_1s_n0t_3n0ugh}"
![[Screenshot from 2024-01-14 07-10-08.png]]