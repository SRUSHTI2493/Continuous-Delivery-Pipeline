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

**Configure Service Access**

![image](https://github.com/SRUSHTI2493/Continuous-Delivery-Pipeline/assets/87080882/530a8a71-5427-4d89-8478-18ea09479639)

:small_blue_diamond: The Review page displays a summary of all your choices.

:small_blue_diamond: Choose Submit at the bottom of the page to initialize the creation of your new environment.

![image](https://github.com/SRUSHTI2493/Continuous-Delivery-Pipeline/assets/87080882/83151d31-225d-45af-ba23-9f54fc0db0dc)

**While waiting for deployment, you should see:**

A screen that will display status messages for your environment.
After a few minutes have passed, you will see a green banner with a checkmark at the top of the environment screen.
Once you see the banner, you have successfully created an AWS Elastic Beanstalk application and deployed it to an environment.

![image](https://github.com/SRUSHTI2493/Continuous-Delivery-Pipeline/assets/87080882/10b8f750-7c8a-4d4f-9a04-24565551c76c)

**:large_orange_diamond:Test your web app**

:small_blue_diamond: To test your sample web app, select the link under the name of your environment.
![image](https://github.com/SRUSHTI2493/Continuous-Delivery-Pipeline/assets/87080882/4fe8ef13-4b1b-4c97-9835-0ae8abf21272)

:small_blue_diamond: Once the test has completed, a new browser tab should open with a webpage congratulating you!
![image](https://github.com/SRUSHTI2493/Continuous-Delivery-Pipeline/assets/87080882/bd291005-7aaf-4fac-9177-d790c773af37)

# Module 3: Create Build Project
**In this module, you will configure and execute the application build process using AWS CodeBuild**

## Overview
In this module, you will use AWS CodeBuild to build the source code previously stored in your GitHub repository. AWS CodeBuild is a fully managed continuous integration service that compiles source code, runs tests, and produces software packages that are ready to deploy.

# What you will accomplish
**In this module, you will:**

:small_blue_diamond:  Create a build project with AWS CodeBuild

:small_blue_diamond:  Set up GitHub as the source provider for a build project

:small_blue_diamond:  Run a build on AWS CodeBuild

**:large_orange_diamond: configure the AWS Codebuild Project**

:small_blue_diamond: In a new browser tab, open the AWS CodeBuild console.

:small_blue_diamond: Choose the orange Create project button.

:small_blue_diamond: In the Project name field, enter Build-DevOpsGettingStarted.

:small_blue_diamond: Select GitHub from the Source provider dropdown menu.

:small_blue_diamond: Confirm that the Connect using OAuth radio button is selected.

:small_blue_diamond: Choose the white Connect to GitHub button. A new browser tab will open asking you to give AWS CodeBuild access to your GitHub repo.

:small_blue_diamond: Choose the green Authorize aws-codesuite button.

:small_blue_diamond: Enter your GitHub password.

:small_blue_diamond: Choose the orange Confirm button.

:small_blue_diamond: Select Repository in my GitHub account.

:small_blue_diamond: Enter aws-elastic-beanstalk-express-js-sample in the search field.

:small_blue_diamond: Select the repo you forked in Module 1. After selecting your repo, your screen should look like this:

![image](https://github.com/SRUSHTI2493/Continuous-Delivery-Pipeline/assets/87080882/7742d5ba-81fa-4076-9b6f-909b698f63e9)

:small_blue_diamond:  Confirm that Managed Image is selected.

:small_blue_diamond:  Select Amazon Linux 2 from the Operating system dropdown menu.

:small_blue_diamond:  Select Standard from the Runtime(s) dropdown menu.

:small_blue_diamond:  Select aws/codebuild/amazonlinux2-x86_64-standard:3.0 from the Image dropdown menu.

:small_blue_diamond:  Confirm that Always use the latest image for this runtime version is selected for Image version.

:small_blue_diamond:  Confirm that Linux is selected for Environment type.

:small_blue_diamond:  Confirm that New service role is selected.

**:large_orange_diamond: Create a BuildSpace file for object**

:small_blue_diamond: Select Insert build commands.

:small_blue_diamond: Choose Switch to editor.

:small_blue_diamond: Replace the Buildspec in the editor with the code below:

```
version: 0.2
phases:
    build:
        commands:
            - npm i --save
artifacts:
    files:
        - '**/*'
```

:small_blue_diamond: Choose the orange Create build project button. You should now see a dashboard for your project.

**:large_orange_diamond: Test the code build Project**

:small_blue_diamond: Choose the orange Start build button. This will load a page to configure the build process.

:small_blue_diamond: Confirm that the loaded page references the correct GitHub repo.

:small_blue_diamond: Choose the orange Start build button.

:small_blue_diamond: Wait for the build to complete. As you are waiting you should see a green bar at the top of the page with the message Build started, the progress for your build under Build log, and, after a couple minutes, a green checkmark and a Succeeded 
 message confirming the build worked.

# Module 4: Create Delivery Pipeline
**In this module, you will use AWS CodePipeline to set up a continuous delivery pipeline with source, build, and deploy stages**

## Overview
In this module, you will use AWS CodePipeline to set up a continuous delivery pipeline with source, build, and deploy stages. The pipeline will detect changes in the code stored in your GitHub repository, build the source code using AWS CodeBuild, and then deploy your application to AWS Elastic Beanstalk.

## What you will accomplish
**In this module, you will:**

:small_blue_diamond:Set up a continuous delivery pipeline on AWS CodePipeline

:small_blue_diamond:Configure a source stage using your GitHub repo

:small_blue_diamond:Configure a build stage using AWS CodeBuild

:small_blue_diamond:Configure a deploy stage using your AWS ElasticBeanstalk application

:small_blue_diamond:Deploy the application hosted on GitHub to Elastic Beanstalk through a pipeline

# Implementation

**:large_orange_diamond: Create a new pipeline**

:small_blue_diamond: In a browser window, open the AWS CodePipeline console.

:small_blue_diamond: Choose the orange Create pipeline button. A new screen will open up so you can set up the pipeline.

:small_blue_diamond: In the Pipeline name field, enter Pipeline-DevOpsGettingStarted.

:small_blue_diamond: Confirm that New service role is selected.

:small_blue_diamond: Choose the orange Next button.

**:large_orange_diamond: Configure the source stage**

:small_blue_diamond: Select GitHub version 1 from the Source provider dropdown menu.

:small_blue_diamond:Choose the white Connect to GitHub button. A new browser tab will open asking you to give AWS CodePipeline access to your GitHub repo.

:small_blue_diamond:Choose the green Authorize aws-codesuite button. Next, you will see a green box with the message You have successfully configured the action with the provider.

:small_blue_diamond:From the Repository dropdown, select the repo you created in Module 1.

:small_blue_diamond:Select main from the branch dropdown menu.

:small_blue_diamond:Confirm that GitHub webhooks is selected.

:small_blue_diamond:Choose the orange Next button

**:large_orange_diamond: Configure the build stage**

:small_blue_diamond: From the Build provider dropdown menu, select AWS CodeBuild.

:small_blue_diamond: Under Region confirm that the US West (Oregon) Region is selected.

:small_blue_diamond: Select Build-DevOpsGettingStarted under Project name.

:small_blue_diamond: Choose the orange Next button.

**:large_orange_diamond: Configure the Deploy stage**

:small_blue_diamond: Select AWS Elastic Beanstalk from the Deploy provider dropdown menu.

:small_blue_diamond:  Under Region, confirm that the US West (Oregon) Region is selected.

:small_blue_diamond:  Select the field under Application name and confirm you can see the app DevOpsGettingStarted created in Module 2.

:small_blue_diamond:  Select DevOpsGettingStarted-env from the Environment name textbox.

:small_blue_diamond:  Choose the orange Next button. You will now see a page where you can review the pipeline configuration.

:small_blue_diamond:  Choose the orange Create pipeline button.

**:large_orange_diamond: watch first pipeline Execution**

**While watching the pipeline execution, you will see a page with a green bar at the top. This page shows all the steps defined for the pipeline and, after a few minutes, each will change from blue to green.**

:small_blue_diamond: Once the Deploy stage has switched to green and it says Succeeded, choose AWS Elastic Beanstalk. A new tab listing your AWS Elastic Beanstalk environments will open.

:small_blue_diamond: Select the URL in the Devopsgettingstarted-env row. You should see a webpage with a white background and the text you included in your GitHub commit in Module 1.

# Module 5: Finalize Pipeline and Test
**In this module, you will add a review stage to your countinuous delivery pipeline using AWS CodePipeline**

## Overview
In this module, you will use AWS CodePipeline to add a review stage to your countinuous delivery pipeline.

As part of this process, you can add an approval action to a stage at the point where you want the pipeline execution to stop so someone can manually approve or reject the action. Manual approvals are useful to have someone else review a change before deployment. If the action is approved, the pipeline execution resumes. If the action is rejected—or if no one approves or rejects the action within seven days—the result is the same as the action failing, and the pipeline execution does not continue.

## What you will accomplish
**In this module, you will:**
:small_blue_diamond: Add a review stage to your pipeline

:small_blue_diamond: Manually approve a change before it is deployed

**:large_orange_diamond: Create review stage in pipeline**

:small_blue_diamond: Open the AWS CodePipeline console.

:small_blue_diamond: You should see the pipeline we created in Module 4, which was called Pipeline-DevOpsGettingStarted. Select this pipeline.

:small_blue_diamond: Choose the white Edit button near the top of the page.

:small_blue_diamond: Choose the white Add stage button between the Build and Deploy stages.

:small_blue_diamond: In the Stage name field, enter Review.

:small_blue_diamond: Choose the orange Add stage button.

:small_blue_diamond: In the Review stage, choose the white Add action group button.

:small_blue_diamond: Under Action name, enter Manual_Review.

:small_blue_diamond: From the Action provider dropdown, select Manual approval.

:small_blue_diamond: Confirm that the optional fields have been left blank.

:small_blue_diamond: Choose the orange Done button.

:small_blue_diamond: Choose the orange Save button at the top of the page.

:small_blue_diamond: Choose the orange Save button to confirm the changes. You will now see your pipeline with four stages: Source, Build, Review, and Deploy.

**:large_orange_diamond: Push new commit to your repo**

In your favorite code editor, open the app.js file from Module 1.

:small_blue_diamond: Change the message in Line 5.

:small_blue_diamond: Save the file.

:small_blue_diamond: Open your preferred Git client.

:small_blue_diamond: Navigate to the folder created in Module 1.

Commit the change with the following commands:

```
git add app.js
git commit -m "Full pipeline test"

```
:small_blue_diamond: Push the local changes to the remote repo hosted on GitHub with the following command:

```
git push
```

**:large_orange_diamond: Monitore the pipeline and manually approve the changes**

:small_blue_diamond: Navigate to the AWS CodePipeline console.

:small_blue_diamond: Select the pipeline named Pipeline-DevOpsGettingStarted. You should see the Source and Build stages switch from blue to green.

:small_blue_diamond: When the Review stage switches to blue, choose the white Review button.

:small_blue_diamond: Write an approval comment in the Comments textbox.

:small_blue_diamond: Choose the orange Approve button.

:small_blue_diamond: Wait for the Review and Deploy stages to switch to green.

:small_blue_diamond: Select the AWS Elastic Beanstalk link in the Deploy stage. A new tab listing your Elastic Beanstalk environments will open.

:small_blue_diamond: Select the URL in the Devopsgettingstarted-env row. You should see a webpage with a white background and the text you had in your most recent GitHub commit.

### Congratulations! :boom: You have a fully functional continuous delivery pipeline hosted on AWS.
