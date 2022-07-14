# Renovate - Hands On Tutorial


## Introduction

Welcome to the Renovate hands-on tutorial.

The easiest way to start is using the [Renovate GitHub App](https://github.com/apps/renovate). you can also run Renovate as a CLI tool or a self-hosted application.

In this tutorial, you will learn how to configure Renovate to your GitHub account and become familiar with some of Renovate’s basic features.

Although this tutorial is based in the GitHub App, the concepts discussed apply to all environments.

What you will learn: 
1) Installation
2) Onboarding
3) Getting to know Renovate’s update PRs
4) Dependency Dashboard 


We will begin this tutorial by providing basic `getting started` information. This includes: Renovate App configuration and installation, default settings, and basic Renovate functionality. 

Later, we will dive deeper into functional use-cases, advanced features, and `best practices` capabilities in order to use Renovate to its fullest.

## Part 1 - Installation

Let’s start by forking the tutorial repo to your account, installing the Renovate GitHub App, and configuring it to your repo.
 
1) Make sure you are logged in to GitHub.com
2) Fork this [RenovateTutorial](https://github.com/PhilipAbed/RenovateTutorial) repository. The tutorial instructions will be based on the contents of this repository
3) The following instructions are directed at those that don’t have Renovate installed:
   - Install the Renovate App to your account by navigating to the [Renovate App GitHub installation page](https://github.com/apps/renovate) and select Install:
   ![image](https://user-images.githubusercontent.com/42116482/178490796-f4627b8d-53d9-4d70-ad54-4df5d9df6de1.png)
4) If you do have Renovate installed:
   - navigate to the [Renovate app page](https://github.com/apps/renovate) and select configure:
   ![image](https://user-images.githubusercontent.com/42116482/178491021-a0b7ba34-3bc7-4953-8452-416fbd3d6ec9.png)
5) You will reach an installation configuration page where you are asked to configure Repository Access. 

> **Note**
> for existing users, installation configuration appears at the bottom of the page.

   - Mark `Only select repositories` and make sure to select the forked RenovateTutorial repo
   
       > **Note**
       > each selected repo gets an onboarding PR. 

       If you select `All repositories`, forked repos will be skipped by default (including RenovateTutorial). 
   - click on `Install` (“Save” for existing users) 
   
![image](https://user-images.githubusercontent.com/42116482/178491902-6f6b446a-eb38-45db-9c63-ddf5ba3ac5ba.png)


For new installs:	
- You will be redirected to our “Thank you for installing Renovate” page while we are setting up your account. 

![image](https://user-images.githubusercontent.com/42116482/178492276-ac0f5c03-db21-482c-95e9-07dc229ac298.png)

- After a few seconds, you will be automatically directed to a dashboard where you can login and view the Renovate logs. We recommend saving this link for future use.

![image](https://user-images.githubusercontent.com/42116482/178492370-97532d6e-b9b7-4f95-a793-ed0281bd33e9.png)

**Congratulations! You have successfully installed Renovate to your account.** 🎈


## Part 2 - Onboarding

Now that you have Renovate installed, we can begin onboarding.

Let’s review the concepts of the Onboarding PR and learn about Renovate’s initial settings.

> **Note**
> For your convenience, Renovate will not make any changes to your repo or raise PRs until after you finish onboarding.

- Upon installing Renovate, an onboarding PR will be automatically generated.
- This PR is there to help you understand Renovate and its default settings before Renovate starts running on your repository.
- The Onboarding PR creates a configuration file called `renovate.json`, which contains Renovate’s default settings and can be modified during onboarding.

Now let’s review the onboarding PR - 
1) Navigate to the `Pull Requests` section in GitHub, and open the newly generated PR - `Configure Renovate`

![image](https://user-images.githubusercontent.com/42116482/178493669-d905570e-7a87-4990-a4c3-c71f1185edff.png)

![image](https://user-images.githubusercontent.com/42116482/178493786-6f3ff65b-32b3-4c50-8368-c1799cdbcb84.png)


#### The onboarding PR contains:

   - **Detected Package Files** - All package files detected by Renovate in your code.
   - **Configuration Summary** - The default configuration settings that will be applied.
   - **What to Expect** - The dependency update PRs that Renovate is about to automatically create.
   - The link to Renovate’s official [documentation](https://docs.renovatebot.com/).
   - The link to review jobs logs in the [Renovate dashboard](https://app.renovatebot.com/dashboard).
   
> **Note**
> Renovate will not create dependency update PRs until the onboarding PR will be merged.


#### These are some of the default configurations of Renovate:

   - Enables creation of the “Dependency Dashboard” - a dashboard that shows an overview of the state of your repositories' dependencies.
   - PRs will be created at a rate of 2 PRs per hour.
   - The limit of simultaneous open Renovate PRs is set to 10.
   - Renovate automatically groups known monorepo packages to a single PR (example can be seen in the `date-io` PR under the **what to expect** section).

Renovate offers the ability to change configurations before merging the onboarding PR as well as preview the results of these changes. At this point, Renovate has created a branch called renovate/configure which contains the `renovate.json` configuration file. By default, Renovate limits branch creation to 2 per hour:

<img width="829" alt="onboarding warning hourly" src="https://user-images.githubusercontent.com/102745725/178961193-2f1f1548-5282-4d33-b8ef-6e141f0a643d.png">

Example

As a user, despite Renovate’s suggestion to limit hourly PR creation to 2, we might want to increase the limit to a different number. Let’s try changing this hourly limitation to 3:

1) Go to the newly created branch - `renovate/configure`:

![image](https://user-images.githubusercontent.com/42116482/178494805-a3f7c209-a683-4fa9-8e75-dfe63e5d0e56.png)

2) Go into the `renovate.json` file:

![image](https://user-images.githubusercontent.com/42116482/178494908-89189f2e-632a-42ee-a49a-16941a40101b.png)

3) Add the following code segment:
```
{
  "prHourlyLimit": 3
}
```
![image](https://user-images.githubusercontent.com/42116482/178495049-06a93b8d-ba82-44a2-a837-1b35c8351838.png)

4) Commit the changes
5) Revisit the onboarding PR and notice how the onboarding PR automatically updates to reflect the changes you made to the configuration 

<img width="830" alt="onboarding warning hourly update" src="https://user-images.githubusercontent.com/102745725/178960884-40077a5c-8fe1-422f-81c1-567ea1e6619b.png">

> **Note**
> May take a few moments to update.

6) Merge the onboarding pull request.

**Congratulations! You have successfully onboarded Renovate.** 🎈

## Part 3 - Getting to know Renovate’s update PRs

Now that you have merged the onboarding PR, Renovate will generate Update PRs to the most recent dependency version based on your configuration. 

> **Note**
> PRs may take a couple of minutes to appear

Here we will review the basic concepts of Renovate update PRs and merge it.

- By default, Renovate will create up to 2 update PRs per hour. However, if you completed the onboarding section of this tutorial, Renovate will now create 3 PRs.
- You should already see notifications for these pull requests in the `Pull Requests` section of the repo.

Let’s go ahead and take a look at a Renovate update PR:
1) Navigate to the `Pull requests` section and open - `Update dependency lodash to x.y.z`

![image](https://user-images.githubusercontent.com/42116482/178495779-fae0cb03-be56-4cac-a3c5-70de4e20a40f.png)

### Each update PR contains:
- Dependency information (name and version changes)
- [Merge Confidence](https://docs.renovatebot.com/merge-confidence/) values
- Up-to-date release notes
- Renovate configuration-related info
- Option to rebase PR
- Link to view Renovate logs

![image](https://user-images.githubusercontent.com/42116482/178495994-7cce93f1-db65-4f09-b682-7506dc242fdc.png)

- Renovate’s update PRs will update the relevant dependency across your entire repo. In our RenovateTutorial repo, this will be both the `package.json` file and the `package-lock.json` file:

![image](https://user-images.githubusercontent.com/42116482/178496208-81bb23b4-0da7-43eb-8d60-8a9bfe7aed3d.png)

2) Merge this pull request

>Note - Renovate is highly configurable and supports:
>
>- On-demand PR creation.
>- Automatic merging of PRs.
>- Settings for specific dependencies/package managers.
>- Scheduling.
>- Grouping. 
>
>  All the above and more will be discussed in future parts of the tutorial.

**Congratulations! You have now updated your first dependency with Renovate.** 🎈

## Part 4 - Dependency Dashboard

Renovate’s Dependency Dashboard is a GitHub Issue that enables you to manage and monitor Renovate’s activity in your repo. In this section, we will go over some of its main functionalities and capabilities.

Let’s begin by creating and enabling the Dependency Dashboard. Since GitHub defaults to disable `issues` on forked repositories, we need to enable it on the forked RenovateTutorial repo:

1) Navigate to the main page of the repo and go to `settings` -> `general`
2) Check the `issues` checkbox under the Features section:

![image](https://user-images.githubusercontent.com/42116482/178508319-32c3ef67-c030-4965-b0d8-773589dbf474.png)

- In order for the Dependency Dashboard to become available, we will need to re-run Renovate by triggering a webhook (for example, closing an update PR).
  
> **Note**
> This is usually done in a click via the Dependency Dashboard.


3) Go to the `Pull requests` section
4) Select `Update dependency php to v8.1` and select `Close pull request`
5) This will trigger Renovate to run and the Dependency Dashboard will appear under the `Issues` section - navigate to it

> **Note**
> it may take a minute to appear.


### The Dependency Dashboard includes:
  - Overview of all updates that are still to-do:

    - **Open** PRs
    - **Rate Limited** - PRs blocked by rate limit setting and will be opened based on preferences.
    - **Pending Approval** - PRs that require manual triggering based on configurations.
    - **Awaiting Schedule** - PRs creation blocked by Renovate scheduling settings.
    - **Pending Status Checks** - updates that await pending status checks in order to be created.
  
  - Visibility into **rejected/deferred updates**.
  - List of all the **detected dependencies** and **package managers** in your repository.
  
  ![image](https://user-images.githubusercontent.com/42116482/178509682-3d772940-fe94-4338-ad1d-f7c4ef36fe6c.png)

Users can manually trigger the creation of dependency updates directly from the dashboard. 

You can also re-run the Renovate bot manually directly from the Dependency Dashboard by enabling the “Check this box to trigger a request Renovate to run again on this repository” option:

 ![image](https://user-images.githubusercontent.com/42116482/178509789-3ebfe3c7-b0b1-4041-85df-8e5da0cd4c4c.png)
 

Let’s dive into one of the dependency dashboard capabilities - **the Pending Approval feature**. 

Say we want to take extra measures before updating major versions of a package (either to reduce noise or to handle it more carefully). Renovate offers an option to prevent automatic creation of major version update PRs and create such PRs only upon manual request from the Dependency Dashboard. 

In the Dependency Dasboard, under the `Rate Limited` section, the `Update dependency commander to vX` is waiting to be created.

> **Note**
> based on the previously set `prHourlyLimit` configuration, 3 PRs per hour in our case, this PR will be created within an hour.

<img width="928" alt="commander in Rate Limited" src="https://user-images.githubusercontent.com/102745725/178960104-c254c12f-08fb-4508-824d-20df60b2290f.png">

Since we decided that we want to handle it manually, we will edit configurations and see how the depndency dashboard is affected by this change. 

In order to limit all major updates to on-demand creation:

1) Add this code segment to your `renovate.json` file:
```
"packageRules": [
    {
      "matchUpdateTypes": ["major"],
      "dependencyDashboardApproval": true
    }
  ]
```

<img width="924" alt="change in config - pending approval" src="https://user-images.githubusercontent.com/102745725/178962677-612e8172-fac7-45fb-937b-46a559d848f0.png">

2) Commit the changes

> **Note**
> Changing the `renovate.json` configuraion file is a webhook that triggers Renovate to re-run.

3) Now go back to the Dependency Dashboard in the Issues section

4) As you can see, `commander` major update PR now appears under the **Pending Approval** section and **will not** be opened unless manually triggered

     > **Note**
     > it make take a minute to complete Renovate's run 

<img width="926" alt="commander in pending approval" src="https://user-images.githubusercontent.com/102745725/178962735-84f1ae00-df4c-4fed-adf5-12fefeb94e9f.png">

5) You can now decide to manually open this PR by checking the box next to it

6) Navigate to the `Pull requests` section to review the generated PR and merge it to the repo.


**Congratulations! You are now familiar with Renovate’s Dependency Dashboard.** 🎈

## What have we learned so far:
  - How to install Renovate
  - Onboarding Renovate by reviewing, configuring, and merging the onboarding PR
  - How to update a dependency with Renovate
  - How to utilize the Dependency Dashboard
  
### General Comments:
  - Granting access to all repositories or change repo selections can be modified at any time on the [Renovate App GitHub page](https://github.com/apps/renovate).
  - Renovate configuration can be modified by manual configurations, global organization configurations and existing Renovate presets.

### Congratulations! You have successfully completed Renovate’s hands-on tutorial and have taken your first steps to automate dependency updates in your projects.

### Now, it's time to configure Renovate on the rest of your repositories and let Renovate manage your dependencies' health.

### Upcoming Tutorials:

We have more advanced Renovate tutorials in the pipeline and will post updates when they are published.

What’s coming next?
  - Merge confidence
  - Auto Merge
  - Labeling
  - Grouping
  - Schedule
  - Package Rules
  - GitHub actions
  - Assignees and reviewers
  - Regex Managers



