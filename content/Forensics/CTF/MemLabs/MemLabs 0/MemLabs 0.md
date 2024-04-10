
------------
Challenge Description
My friend John is an "environmental" activist and a humanitarian. He hated the ideology of Thanos from the Avengers: Infinity War. He sucks at programming. He used too many variables while writing any program. One day, John gave me a memory dump and asked me to find out what he was doing while he took the dump. Can you figure it out for me?

----------------------------

First get the image info
![[Screenshot from 2024-01-12 16-03-22.png]]

Then I use pslist command to list processes and take notes about suspicious processes  
![[Screenshot from 2024-01-12 16-05-50.png]]

After that I use cmdscan command to search what happened in cmd.exe. And there seen a python file executed with cmd
![[Pasted image 20240112160738.png]]

To search what was the output I used consoles command, and there is seen an encoded text as output of executed python file. But when I tried to decode it I didn't get any normal text just random characters. 
![[Pasted image 20240112160938.png]]

So I tried to use envars command to scan environment variables. And there is a clue Thanos variable with "xor and password" value
![[Pasted image 20240112161808.png]]

After decode the text with the right way in second attempt it gives us a string "1_4m_b3tt3r"}. Okey this should be something but this is not the flag. 

![[Screenshot from 2024-01-12 16-13-51.png]]

We decoded the text with xor but we didn't see any passwords so I use hashdump command to get NTLM hashes
![[Pasted image 20240112163357.png]]

Then I used hashcat for cracking hash. Also online tools can be very useful for cracking NTLM hashes.
![[Pasted image 20240112163506.png]]

Finally when you combine these two texts the flag is "flag{you_are_good_but1_4m_b3tt3r}"