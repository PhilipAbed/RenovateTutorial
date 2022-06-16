# Renovate Hands-on tutorial

## Introduction

Welcome to Renovate’s installation & onboarding tutorial.

In this tutorial we will learn how to install and run renovate, along with some of its basic features.

There are multiple ways to run Renovate, using CLI, self-hosted server or docker, but the easiest way to start with is the [GitHub Renovate App](https://github.com/apps/renovate).

## Installation

- Make sure you are logged in to github.com.
- Fork [this](https://github.com/PhilipAbed/RenovateTutorial) repository
- Make sure `issues` are enabled on github, by navigating to the main page of the forked repository and then go to `settings` ->`general` -> and check the `issues` checkbox under the Features section.
![image](https://user-images.githubusercontent.com/42116482/173985257-60e87a90-a920-4ffd-a357-366bfa543d58.png)

- Install the Renovate app to your account - go to the [Renovate App GitHub page](https://github.com/apps/renovate), install it, and configure the Repository Access to mark `Only select repositories` and make sure to select the forked RenovateTutorial repo.
![image](https://user-images.githubusercontent.com/42116482/173985330-bbdbbe94-b883-4daf-a4d5-b0393e767200.png)
![image](https://user-images.githubusercontent.com/42116482/173985535-44ccc750-50aa-452b-b9dc-4fafb65bfc75.png)

- Note - granting access to all repositories or change repo selections can be modified at anytime on the [Renovate App GitHub page](https://github.com/apps/renovate)

## Onboarding

- After installing and configuring the Renovate app, an onboarding Renovate Pull Request will be automatically generated. 
- This PR is there to help you understand Renovate and its default configurations before regular Pull Requests begin.
- Navigate to the `Pull Requests` section in GitHub, and open the newly generated PR - `Configure Renovate`.
- The onboarding PR contains: 
  - A list of all the package files detected in your code, based on Renovate scanning results.
  - A description of the default configuration settings that will be applied (can be modified later according to the documentation).
  - What to expect - A list indicating the dependency updates PRs that Renovate is about to create.
  - Link to Renovate’s official [documentation](https://docs.renovatebot.com/). 
- Merge this pull request. 
- Upon merging this pull request, a `renovate.json`, which is Renovate’s configuration file, will be created and Renovate will begin working in the background.
- The `renovate.json` file in your repository will contain a default configuration [preset](https://docs.renovatebot.com/key-concepts/presets/) `config:base`

## Perform your first automated Renovate dependency update

- After merging the onboarding PR, Renovate is now working on generating update PRs. (PRs may take a couple of minutes to appear)
- According to Renovate’s default settings, Renovate will create 2 update PRs, based on a rate limit of 2 PRs created per hour, as stated before in the onboarding PR.
- You should already see notifications for these pull requests in the `Pull Requests` section of the repository.
- Navigate to it and open the `Update dependency lodash to x.y.z` PR.
![image](https://user-images.githubusercontent.com/42116482/173989635-935ac533-76da-4acb-8b6a-c5836c780f83.png)
- Each update PR consists of:
  -Dependency information (name and version) and its `Merge Confidence` values (will be thoroughly explained in a different tutorial).
  - Up-to-date release notes.
  - Configuration related info.
  - Option to rebase the PR.
  - Link to view renovate logs.
![image](https://user-images.githubusercontent.com/42116482/173989747-a9ff5a27-ecfc-42eb-a666-4a98d0434821.png)
-Upon decision to merge Renovate’s pull request suggestion to your repository, merge the pull request and the dependency will be updated across your repository.
![image](https://user-images.githubusercontent.com/42116482/173990014-2995099b-0f71-43b3-8e79-242ab6213650.png)


## Dependency Dashboard

- Renovate also has a tool that lets you manually manage and monitor Renovate’s activity in your repository, called the dependency Dashboard.
- Navigate to it, located in the `Issues` section in GitHub.
- The dependency dashboard includes:
  - Visibility into rejected/deferred updates.
  - Overview of all updates that are still `to-do` (open, Rate Limited, Pending Approval, Awaiting Schedule, Pending Status Checks).
  - Information of previously closed PRs. 
![image](https://user-images.githubusercontent.com/42116482/173990209-be4c6f0d-2665-4bdd-b8fa-70eff06844da.png)

- A user can manually generate the creation of dependency updates directly from the dashboard. 
	give it a try - check the box next to (name of update PR) and navigate to the `Pull requests` section to see the generated PR (might take a few minutes).
- The dependency dashboard also provides a list of all the detected dependencies and package managers in your repository.
- You are also capable of re-running Renovate manually directly from the dependency dashboard.

##
**Congratulations!!!** 

**You have successfully completed your first Renovate Dependency Update.**

**now its time to configure Renovate to the rest of your repositories and let Renovate do the work.**
