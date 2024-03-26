In this project we will integrate SonarQube in Jenkins and automate security testing with a
CI/CD pipeline.

Technologies:
- Jenkins (Local installation)
- SonarQube (Dockerized)
We will use a vulnerable web application named Vulnado
(https://github.com/ScaleSec/vulnado) for testing.

Jenkins installation
There are different way to install jenkins but I chose the easiest way to install jenkins. You
can install jenkins with package managers like apt/snap or you can follow these installation
method https://www.jenkins.io/doc/book/installing/linux/ . Also you can run Jenkins on
Docker but this is not preferred.

![[Pasted image 20240326153707.png]]

Docker installation
We are installing Docker to run SonarQube on Docker. You can use apt/snap package
managers for installing Docker too. If you can’t reach these package managers you can use
other installation methods.

![[Pasted image 20240326153728.png]]
Okey now we have installed Jenkins and Docker. We will install SonarQube on Docker but
before that let’s configure Jenkins.
After your installation you can reach Jenkins’s web interface from browser localhost:8080
(default)
hint: jenkins starts on the 8080 port by default. You can change the port in web interface but
sometimes you need to start jenkins from a different port. To make it you you should go to
jenkins directory /opt/jenkins/ or /snap/jenkins generally. And run this command
java -jar jenkins.war --httpPort=<port_number>

And here we have Jenkins

![[Pasted image 20240326153755.png]]

This is how I learned the password.
![[Pasted image 20240326153811.png]]

After you logged in Jenkins asks which plugins to install. I chose suggested plugins
(sometimes installation of some plugins may be fail, this is not a big problem just click “retry”
button and it generally works)

![[Pasted image 20240326153828.png]]

After installing plugins Jenkins asks you to create first admin user. You can skip this step or
you can create an account. I am going to create an account.

![[Pasted image 20240326153843.png]]

In final step of installation Jenkins asks you the url. If you are not in cloud this is not a
necessary but 8080 port is a common port that many applications use as default port.
Changing the port maybe have some advantages.

![[Pasted image 20240326153902.png]]

And here Jenkins main page.

![[Pasted image 20240326153914.png]]

Let’s start to create the pipeline. Press “New Item” select Pipeline and give a name to item

![[Pasted image 20240326153936.png]]

In the opened page scroll down and get to the Pipeline. This is the editor we are going to edit our pipeline.

![[Pasted image 20240326153952.png]]


Jenkins have a syntax for pipeline scripting. But it is easy to understand and use.

In first step of our pipeline will be the installation step. We are going to install Vulnado with
git so we need to install git before.

![[Pasted image 20240326154018.png]]


This will be the first part of our pipeline, installation of project.

![[Pasted image 20240326154104.png]]

Second part of our pipeline, building the project (before build ‘sudo apt-get install maven -y’)

![[Pasted image 20240326154112.png]]

After build the project your pipeline should look like this.

![[Pasted image 20240326154137.png]]

Okey, we have installed and builded the project in Jenkins. This is good so let’s start security
testing 

We have installed docker. I run ‘docker pull sonarqube’ command on terminal 

![[Pasted image 20240326154214.png]]

We have pulled the sonarqube image now we will run this image in a container (you may
need to use docker with super user privileges)

![[Pasted image 20240326154219.png]]

After running container checking is it working

![[Pasted image 20240326154243.png]]

In localhost:9000 I can reach the web interface for sonarqube default credential is
admin:admin

![[Pasted image 20240326154259.png]]

Reset your password

![[Pasted image 20240326154310.png]]

Choose “Create a local project”

![[Pasted image 20240326154325.png]]

Fill the name and key

![[Pasted image 20240326154329.png]]

Choose “Use global settings”

![[Pasted image 20240326154407.png]]

Choose Jenkins as analysis method

![[Pasted image 20240326154423.png]]

Choose GitHub

![[Pasted image 20240326154431.png]]

Choose maven, and SonarQube gave us a Jenkins file but this script is not okey to use we
will modify it later

![[Pasted image 20240326154438.png]]


Now in SonarQube click account and go to my account

![[Pasted image 20240326154517.png]]

In profile choose security > generate new token and choose global analysis token then
generate token. We will use this token in Jenkins for integration

Now go to Jenkins Dashboard and click “Manage Jenkins”

![[Pasted image 20240326154536.png]]

Jenkins Dashboard > Manage Jenkins > Plugins > Available plugins > search “SonarQube”

![[Pasted image 20240326154551.png]]

Go back to Manage Jenkins > Credentials > Add credential

![[Pasted image 20240326154604.png]]

manage jenkins > credentials > system > Global credentials select secret text and paste

SonarQube Global Analysis Token to the secret and write an id

![[Pasted image 20240326154634.png]]

Manage Jenkins > System > Sonarqube installations. Give a name for your sonarqube
installation to use in scripts. Write the url of SonarQube and choose secret text for server
authentication token

![[Pasted image 20240326154652.png]]

In final your pipeline should look like this

![[Pasted image 20240326154708.png]]

And this is how stages should look like this

![[Pasted image 20240326154720.png]]

And this is SonarQube dashboard

![[Pasted image 20240326154733.png]]