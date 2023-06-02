# Lauching Jenkins on AWS

## Step 1: Set-up EC2 instance and connect

Like we have done many times, set up an EC2 instance, Ubuntu 18.04:

Include the secuirty group: and add the ssh rule aswell.

![Alt text](Jen-images/Screenshot%202023-06-02%20115114.png)

a

![Alt text](Jen-images/Screenshot%202023-06-02%20115311.png)

like done before, select `Connnect` on the instance and enter the `SSH` command to the terminal. 

![Alt text](Jen-images/Screenshot%202023-06-02%20115927.png)

## step 2: Install Java

We will now install Java to the instance, run:

```
sudo apt update
```

Next install the Jaa packae:

```
 sudo apt install default-jre -y
```

Confirm it. 

### PROGRESS CHECK:
we can verify this has worked bby checking the version, use:
```
java -version
```
This resuleted in:

![Alt text](Jen-images/Screenshot%202023-06-02%20120523.png)

## Step 3: Install java enviornment variables

use:
```
sudo nano /etc/environment
```
We are now in the file and can put in the variables:
```
JAVA_HOME="/usr/lib/jvm/java-8-openjdk-amd64"
JRE_HOME="/usr/lib/jvm/java-8-openjdk-amd64/jre"
```

![Alt text](Jen-images/Screenshot%202023-06-02%20121938.png)

To check the changes have been made, i ran:
```
echo $JAVA_HOME
```
it produced the path:

![Alt text](Jen-images/Screenshot%202023-06-02%20122620.png)


## Step 4: Install JENKINS

add the jenkins repo key:

```
wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
```
it returned what i wanted:

![Alt text](Jen-images/Screenshot%202023-06-02%20122920.png)

Next, we need to add the Jenkins repo to the package manager:
```
$ echo deb https://pkg.jenkins.io/debian-stable binary/ | sudo tee /etc/apt/sources.list.d/jenkins.list
```

returning:
![Alt text](Jen-images/Screenshot%202023-06-02%20123142.png)

### Step 4b: Update and install jenkins

Now update and install jenkins, run:
```
sudo apt update
```
I ran into an error which meant i had to manually copy the key, i ran:
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 5BA31D57EF5975CA
```

thereafter, i tried running the update again, which gave me:

![Alt text](Jen-images/Screenshot%202023-06-02%20123911.png)

I can now install jenkins through:
```
sudo apt install jenkins
```
then start jenkins:
```
sudo sudo systemctl start jenkins
```
check the status:
```
sudo sudo systemctl status jenkins
```

![Alt text](Jen-images/Screenshot%202023-06-02%20143358.png)

then navigate to the IP address of the EC2 instance followed by port "8080":

![Alt text](Jen-images/Screenshot%202023-06-02%20144532.png)

navigate to mange jenkins -> plugins -> available plug-ins and search for the nodeJS plugin:

![Alt text](Jen-images/Screenshot%202023-06-02%20144903.png)

## Step 5: Creating Jobs on Jenkins

After navigating to the url with the specified port, create a new job:

This is essentially what was done in the CICD repo, but some slight changes.

### Setup webhook

naviagte to the repo, settings, add webhook, and add the webhook of the jenkins page:

![Alt text](Jen-images/Screenshot%202023-06-02%20155123.png)

### Setup nodeJS

Nodejs should also be configured. head to `Manage jenkins`, `Tools`, scroll down, and install nodejs:

![Alt text](Jen-images/Screenshot%202023-06-02%20161536.png)

### CI build:

here is the exact build:
enable `GitHub project`:

![Alt text](Jen-images/Screenshot%202023-06-02%20155426.png)

Under `Source Code`, select `Git` and add the key.
rememeber this is the private key and can be found through `ssh`ing and using `cat` to access the key, theres a tutorial in cicd repo.

it should let you selecet it and look like this:

![Alt text](Jen-images/Screenshot%202023-06-02%20161043.png)

and the branch should be `dev`. 

select NodeJS:

![Alt text](Jen-images/Screenshot%202023-06-02%20161802.png)

and umder execute shell:
```
cd app
npm install
npm test
```

and set up the builds like we did before, the ci and ci-merge.



