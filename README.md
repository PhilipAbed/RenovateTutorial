# Renovate - Hands On Tutorial


## Introduction


Welcome to the Renovate hands-on tutorial.


The easiest way to start is using the Renovate GitHub App. you can also run Renovate as a CLI tool or a self-hosted application.


In this tutorial, you will learn how to configure Renovate to your GitHub account and become familiar with some of Renovate’s basic features.


Although this tutorial is based in the GitHub App, the concepts discussed apply to all environments.


What you will learn: 
1) Installation
2) Onboarding
3) Getting to know Renovate’s update PRs
4) Dependency Dashboard 


We will begin this tutorial by providing basic “getting started” information. This includes: Renovate App configuration and installation, default settings, and basic Renovate functionality. 


Later, we will dive deeper into functional use-cases, advanced features, and “best practices” capabilities in order to use Renovate to its fullest.


## Part 1 - Installation

Let’s start by forking the tutorial repo to your account, installing the Renovate GitHub App, and configuring it to your repo.
 
1) Make sure you are logged in to GitHub.com
2) Fork our RenovateTutorial repository. The tutorial instructions will be based on the contents of this repository
3) The following instructions are directed at those that don’t have Renovate installed:
   - Install the Renovate App to your account by navigating to the Renovate App GitHub installation page and select Install:
   ![image](https://user-images.githubusercontent.com/42116482/178490796-f4627b8d-53d9-4d70-ad54-4df5d9df6de1.png)
4) If you do have Renovate installed:
   - navigate to the Renovate app page and select configure:
   ![image](https://user-images.githubusercontent.com/42116482/178491021-a0b7ba34-3bc7-4953-8452-416fbd3d6ec9.png)
5) You will reach an installation configuration page where you are asked to configure Repository Access. 

   Note - for existing users, installation configuration appears at the bottom of the page.

   - Mark `Only select repositories` and make sure to select the forked RenovateTutorial repo
   
       Note - each selected repo gets an onboarding PR. 

       If you select `all repositories`, forked repos will be skipped by default (including RenovateTutorial). 
   - click on `install` (“save” for existing users) 
   
![image](https://user-images.githubusercontent.com/42116482/178491902-6f6b446a-eb38-45db-9c63-ddf5ba3ac5ba.png)


For new installs:	
- You will be redirected to our “Thank you for installing Renovate” page while we are setting up your account. 

![image](https://user-images.githubusercontent.com/42116482/178492276-ac0f5c03-db21-482c-95e9-07dc229ac298.png)

- After a few seconds, you will be automatically directed to a dashboard where you can login and view the Renovate logs. We recommend saving this link for future use.

![image](https://user-images.githubusercontent.com/42116482/178492370-97532d6e-b9b7-4f95-a793-ed0281bd33e9.png)

Congratulations! You have successfully installed Renovate to your account. 





