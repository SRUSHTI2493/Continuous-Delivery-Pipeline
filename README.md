# :rocket: Create Continuous Delivery Pipeline :rocket:

## Overview
In this Project, we will create a continuous delivery pipeline for a simple web application. You will first use a version control system to store your source code. Then, you will learn how to create a continuous delivery pipeline that will automatically deploy your web application whenever your source code is updated

## What you will accomplish
This Proejct will walk you through the steps to create the continuous delivery pipeline discussed above. You will learn to:

:small_blue_diamond: Set up a GitHub repository for the application code

:small_blue_diamond: Create an AWS Elastic Beanstalk environment to deploy the application

:small_blue_diamond: Configure AWS CodeBuild to build the source code from GitHub

:small_blue_diamond: Use AWS CodePipeline to set up the continuous delivery pipeline with source, build, and deploy stages

## Prerequisites
Before starting this Project, you will need:

:small_blue_diamond: An AWS account

:small_blue_diamond: A GitHub account

:small_blue_diamond: Git installed on your computer

## Application architecture
The following diagram provides a visual representation of the services used in this tutorial and how they are connected. This application uses GitHub, AWS Elastic Beanstalk, AWS CodeBuild, and AWS CodePipeline.

As we go through the tutorial, we will discuss the services in detail and point to resources that will help you get up to speed with them.

![image](https://github.com/SRUSHTI2493/Continuous-Delivery-Pipeline/assets/87080882/9963f77d-3986-4005-91b7-943e7a5006b5)

## Modules
This Project is divided into five short modules. You must complete each module in order before moving on to the next one.

:small_blue_diamond: Set Up Git Repo (5 minutes): Set up a GitHub repository to store the application code.

:small_blue_diamond: Deploy Web App (10 minutes): Create the environment where the web application will be deployed using AWS Elastic Beanstalk.

:small_blue_diamond: Create Build Project (5 minutes): Configure and start the build process for the application using AWS CodeBuild.

:small_blue_diamond: Create Delivery Pipeline (10 minutes): Create a pipeline to automatically build and deploy the application using AWS CodePipeline.

:small_blue_diamond: Finalize Pipeline and Test (5 minutes): Add a review stage to the pipeline and test the pipeline.

:small_blue_diamond: Set Up Git Repo


# Module 1: Set Up Git Repo
**In this module, you will set up a Git repo for your code so it can be easily accessed over the Internet**

## Overview
In this module, you will set up a repository for your code so it can be easily accessed over the Internet. In this example, we will be using GitHub, but there are other Git-compatible options you can use, including AWS CodeCommit. In one of the following modules you will connect this hosted repo to our pipeline, so every time you push a new commit to it your build process is started.

## What you will accomplish

**In this module, you will:**

:small_blue_diamond: Fork a GitHub repository to create a new one

:small_blue_diamond: Store code and metadata in GitHub

:small_blue_diamond: Interact with a code repository using Git

 # Implementation

**:large_orange_diamond:fork the starter repo**

assumes you have an existing GitHub account and Git installed on your computer. If you don't have either of these two installed, you can follow these step-by-step instructions.

:small_blue_diamond: In a new browser tab, navigate to GitHub and make sure you are logged into your account.

:small_blue_diamond: In that same tab, open the (https://github.com/SRUSHTI2493/Continuous-Delivery-Pipeline) repo.

:small_blue_diamond:Choose the white Fork button on the top right corner of the screen. Next, you will see a small window asking you where you would like to fork the repo.

:small_blue_diamond: Verify it is showing your account and choose Create a fork. After a few seconds, your browser will display a copy of the repo in your account under Repositories.

**:large_orange_diamond:Push a chnage to your new repo**

:small_blue_diamond: Go to the repository (https://github.com/SRUSHTI2493/Continuous-Delivery-Pipeline) and choose the green Code button near the top of the page.

:small_blue_diamond: To clone the repository using HTTPS, confirm that the heading says Clone with HTTPS. If not, select the Use HTTPS link.

:small_blue_diamond: Choose the white button with a clipboard icon on it (to the right of the URL).
![image](https://github.com/SRUSHTI2493/Continuous-Delivery-Pipeline/assets/87080882/5a14962d-d084-435a-8228-c390fa42cfe9)

:small_blue_diamond:  If you're on a **Mac or Linux computer**, open your terminal. If you're on Windows, launch Git Bash.

:small_blue_diamond:  In the terminal or Bash platform, whichever you are using, enter the following command and paste the URL you just copied in Step 2 when you clicked the clipboard icon. Be sure to change "YOUR-USERNAME" to your GitHub username. You should see a message in your terminal that starts with Cloning into. This command creates a new folder that has a copy of the files from the GitHub repo.

```
git clone https://github.com/SRUSHTI2493/Continuous-Delivery-Pipeline.git
```

:small_blue_diamond: In the new folder there is a file named app.js. Open app.js in your favorite code editor.

:small_blue_diamond: Change the message in line 5 to say something other than "Hello World!" and save the file.

:small_blue_diamond: Go to the folder created with the name Continuous-Delivery-Pipeline/ and Commit the change with the following commands:

```
git add app.js
git commit -m "change message"

```

:small_blue_diamond: Push the local changes to the remote repo hosted on GitHub with the following command. Note that you need to configure Personal access tokens (classic) under Developer Settings in GitHub for remote authentication.

```
git push

```

**:large_orange_diamond:Test your change**

:small_blue_diamond: In your browser window, open GitHub.

:small_blue_diamond: In the left navigation panel, under Repositories, select the one named Continuous-Delivery-Pipeline.

:small_blue_diamond: Choose the app.js file. The contents of the file, including your change, should be displayed

# Module 2: Deploy Web App
**In this module, you will create and deploy a web application using AWS Elastic Beanstalk**

## Overview
In this module, you will use the AWS Elastic Beanstalk console to create and deploy a web application. AWS Elastic Beanstalk is a compute service that makes it easy to deploy and manage applications on AWS without having to worry about the infrastructure that runs them. You will use the Create web app wizard to create an application and launch an environment with the AWS resources needed to run your application. In subsequent modules, you will be using this environment and your continuous delivery pipeline to deploy the Hello World! web app created in Module 1

## What you will accomplish

**In this module, you will:**
:small_blue_diamond: Configure and create an AWS Elastic Beanstalk environment

:small_blue_diamond: Deploy a sample web app to AWS Elastic Beanstalk

:small_blue_diamond: Test the sample web app 

# Implementation

**:large_orange_diamond:Configure an AWS Elastic Bensstalk Console**

:small_blue_diamond: In a new browser tab, open the AWS Elastic Beanstalk console.

:small_blue_diamond: Choose the orange Create Application button.

:small_blue_diamond: Choose Web server environment under the Configure environment heading.

:small_blue_diamond: In the text box under the heading Application name, enter DevOpsGettingStarted.

:small_blue_diamond: In the Platform dropdown menu, under the Platform heading, select Node.js . Platform branch and Platform version will automatically populate with default selections.

:small_blue_diamond: Confirm that the radio button next to Sample application under the Application code heading is selected.

:small_blue_diamond: Confirm that the radio button next to Single instance (free tier eligible) under the Presets heading is selected.

:small_blue_diamond: Select Next.

**Configure environment**

![image](https://github.com/SRUSHTI2493/Continuous-Delivery-Pipeline/assets/87080882/f3eb23d8-9658-4f8a-ba5c-99f507eae6a5)




 **On the Configure service access screen, choose Use an existing service role for Service Role.**

:small_blue_diamond: For EC2 instance profile dropdown list, the values displayed in this dropdown list may vary, depending on whether you account has previously created a new environment.

:small_blue_diamond: Choose one of the following, based on the values displayed in your list.

:small_blue_diamond: If aws-elasticbeanstalk-ec2-role displays in the dropdown list, select it from the EC2 instance profile dropdown list.

:small_blue_diamond: If another value displays in the list, and it’s the default EC2 instance profile intended for your environments, select it from the EC2 instance profile dropdown list.

:small_blue_diamond: If the EC2 instance profile dropdown list doesn't list any values to choose from, expand the procedure that follows, Create IAM Role for EC2 instance profile.

:small_blue_diamond: Complete the steps in Create IAM Role for EC2 instance profile to create an IAM Role that you can subsequently select for the EC2 instance profile. Then, return back to this step.

:small_blue_diamond: Now that you've created an IAM Role, and refreshed the list, it displays as a choice in the dropdown list. Select the IAM Role you just created from the EC2 instance profile dropdown list.

:small_blue_diamond: Choose Skip to Review on the Configure service access page.

  **This will select the default values for this step and skip the optional steps.**
