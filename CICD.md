# CICD

Continous integration, continous delivery.

continous integeration helps engineers, devs  and everyone collaborate together. 

webhook triggger: an automatic type of trigger that listens for a certain type of data, much like event triggers.

CICD stands for Continuous Integration and Continuous Deployment (or Continuous Delivery). It is a set of practices and processes used in software development to automate the building, testing, and deployment of applications (more can be read here at semaphoreci)[https://semaphoreci.com/blog/cicd-pipeline].


Most software releases go through a couple of typical stages:
![Alt text](images/cicd-pipeline-introduction-1024x422-1.jpg)

1. In most cases, a pipeline run is triggered by a source code repository. A change in code triggers a notification to the CI/CD tool, which runs the corresponding pipeline.
2. We combine the source code and its dependencies to build a runnable instance of our product that we can potentially ship to our end users.
3. we run automated tests to validate our code’s correctness and the behavior of our product.
4. Once we have a built a runnable instance of our code that has passed all predefined tests, we’re ready to deploy it. There are usually multiple deploy environments.

# Jenkins

Jenkins is an open-source automation server that helps in automating various tasks in software development, including building, testing, and deploying applications. enkins allows developers to automate repetitive tasks and facilitates collaboration within a development team.

Typical stages are:

1. building the application, 
2. running tests, 
3. deploying to a staging environment, 
4. deploying to production

More specifically, the stages we covered are:

1. the Multi-stage build, pipelines
2. The execution of shell
3. creation of enviornment variables, (Jenkins Enviornment and Node)
4. Store files in Jenkins, ( "file.pem" and "tech230-masum-Jenkins" )


# Other tools

1. GitLab CI/CD: GitLab provides an integrated CI/CD solution that is tightly integrated with its source code management platform.
2. CircleCI: CircleCI is a CI/CD platform that supports running jobs in Linux, macOS, and Windows environments.
3. TeamCity: TeamCity is a powerful CI/CD server developed by JetBrains, which supports a wide range of build and deployment configurations.


# Implementing:
Navigate to:

```
3.9.13.91:8080
```

## Create Jenkins Jobs

Jenkin jobs are the tasks we do in Jenkins. 

Select `New item`.. Enter details and select `Freestyle`:

![Alt text](images/Screenshot%202023-05-30%20121620.png)

ensure these are selected:

![Alt text](images/Screenshot%202023-05-30%20121757.png)

Scroll down to `Build` and select `Execute Shell`: 

![Alt text](images/Screenshot%202023-05-30%20121853.png)

to find the version, type:

```
uname -a
```

Apply and save it.

navigate to `Build Now`, this essentially launches it:

![Alt text](images/Screenshot%202023-05-30%20122453.png)

It results in:

![Alt text](images/Screenshot%202023-05-30%20122520.png)

Select the dropdown:

![Alt text](images/Screenshot%202023-05-30%20122556.png)

Here is the console output:

![Alt text](images/Screenshot%202023-05-30%20122653.png)



