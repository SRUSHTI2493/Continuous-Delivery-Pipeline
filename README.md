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

**fork the starter repo**
assumes you have an existing GitHub account and Git installed on your computer. If you don't have either of these two installed, you can follow these step-by-step instructions.

:small_blue_diamond: In a new browser tab, navigate to GitHub and make sure you are logged into your account.
:small_blue_diamond: In that same tab, open the aws-elastic-beanstalk-express-js-sample repo.
:small_blue_diamond:Choose the white Fork button on the top right corner of the screen. Next, you will see a small window asking you where you would like to fork the repo.
:small_blue_diamond: Verify it is showing your account and choose Create a fork. After a few seconds, your browser will display a copy of the repo in your account under Repositories.
