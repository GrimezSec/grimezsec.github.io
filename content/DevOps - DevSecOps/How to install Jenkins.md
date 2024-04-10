---
tags:
  - devops
  - devsecops
---

`sudo wget -O /usr/share/keyrings/jenkins-keyring.asc \`
  `https://pkg.jenkins.io/debian-stable/jenkins.io-2023.key`
`echo deb [signed-by=/usr/share/keyrings/jenkins-keyring.asc] \`
  `https://pkg.jenkins.io/debian-stable binary/ | sudo tee \`
  `/etc/apt/sources.list.d/jenkins.list > /dev/null`
`sudo apt-get update`
`sudo apt-get install jenkins`

![[Screenshot from 2024-03-11 00-18-48.png]]

After your installation Jenkins works on 'localhost:8080' 

![[Pasted image 20240311001957.png]]

You can use cat command or a text editor to see admin password (directory can be changed depending installation your way)

![[Pasted image 20240311002350.png]]

After you login and installed plugins you can create admin user

![[Pasted image 20240311004103.png]]

After you filled the form, you can change port and url of you Jenkins instance

![[Pasted image 20240311004242.png]]

And here we successfully installed Jenkins 

![[Pasted image 20240311004411.png]]