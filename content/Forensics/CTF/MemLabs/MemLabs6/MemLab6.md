

----------
**Challenge Description**


We received this memory dump from the Intelligence Bureau Department. They say this evidence might hold some secrets of the underworld gangster David Benjamin. This memory dump was taken from one of his workers whom the FBI busted earlier this week. Your job is to go through the memory dump and see if you can figure something out. FBI also says that David communicated with his workers via the internet so that might be a good place to start.

**Note**: This challenge is composed of 1 flag split into 2 parts.

The flag format for this lab is: **inctf{s0me_l33t_Str1ng}**

-----------------

The description make me very excited. So let's start

First step let's get the image info

![[Screenshot from 2024-01-21 07-25-59.png]]

Then I listed the processes with the pslist command. chrome.exe, firefox.exe and WinRAR.exe are the suspicious ones that we will focus on for now. The description says that the suspect communicates over the internet, so I will analyze more about browser history and network traffic

![[Screenshot from 2024-01-21 07-27-38.png]]

But before things about internet. Let's check the rar files to see what suspect did on WinRAR

![[image.png]]

I dumped it and tried to unrar but it was password protected and there was no clue so we will go back in later. In description there says *"This challenge is composed of 1 flag split into 2 parts."* so I believe that the password of this RAR archive is the first part of flag.

So let's look what suspect did on the internet. We can scan network also we can dump browser histories. So I am going 
to look for browser histories as first step.


Okey this is the Google Chrome history but where is Firefox history
![[Screenshot from 2024-01-21 07-45-57.png]]

After some searching I found an article about where Firefox history stored [Article:](https://medium.com/@jsaxena017/web-browser-forensics-part-2-firefox-browser-3dc6ef104607)

![[Screenshot from 2024-01-21 07-48-20.png]]

Now let's dump and analyze these browser histories (the second command was just a miss-click don't mind it)
![[Screenshot from 2024-01-21 07-56-01.png]]

You can open browser histories with DB Browser, First I choosed Chrome history and there was literally nothing... Just some searches about cars and stuff and download history of WinRar (from official website)

So let's check the Firefox history, and there are, there is a encoded text. Also different mails about a Mega Drive Key

![[Screenshot from 2024-01-21 08-04-12.png]]

Okey.. I can't find anything about these encoded text. I went to back to look at Chrome history and I realized I had missed something

![[Screenshot from 2024-01-21 08-15-54.png]]

This is the note in URL (if you can't reach website use VPN)

![[Pasted image 20240121081849.png]]

And this is the document which URL is given in the note. The text in this document is only Lorem Ipsum 

(Lorem Ipsum is a meaningless block of text used to replace text in design templates. It is often used by designers)

![[Screenshot from 2024-01-21 08-20-38.png]]

But there is a mega link hidden in this lorem ipsum. Now we have a key and a mega link

![[Screenshot from 2024-01-21 08-25-03.png]]

And when we go to this link mega asks us for a key. The text that I thought was encrypted is actually the key to this file. And there is just one file in link "flag.png". Bu as you can see we can't open this file as an image
![[Screenshot from 2024-01-21 08-29-23.png]]

I have tried many things with this file but with no results, I will come back to this later


Now let's back to the password protected rar archive. I tried to scan files about password but there was no result so I tried to use envars command and there it is.. I can't believe how easy it is
![[img2.png]]

This is the file in password protected Rar archive. This is the second part of our flag.

![[Pasted image 20240121084043.png]]

Yes.. we still have a password protected image file and there is no clue. Also there was an another big big problem. Steghide throws an error about file format

![[Pasted image 20240121084828.png]]

When I use exiftool I can see the problem but I can't understand what exactly is the problem and how can I solve it

![[img3.png]]

After some googling (like 3 seconds) I understand the problem and I know how to solve problem. I am going to change hex data. 

![[img4.png]]

Every file format has a hexadecimal text palette called "magic number" in IT. If you change those hexadecimal file signs you you will change the format of file. This method is also used by attackers for unauthorized file uploads.

So when we back to the our file there is just a small problem, small enough to be annoying. As you can see there is written "iHDR" it should be "IHDR"

![[Pasted image 20240121090529.png]]

There was written 69 (i in ASCII table) I changed it to the 49 (I in ASCII table) 

![[Screenshot from 2024-01-21 09-06-40.png]]

And here it is, the file actually wasn't password protected it was just broken. 

![[Pasted image 20240121091159.png]]

And finally our flag is `inctf{thi5_cH4LL3Ng3_!s_g0nn4_b3_?_aN_Am4zINg_!_i_gU3Ss???}`


