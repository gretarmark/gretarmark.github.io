---
layout: post
title: Using Github with STM32 Cube IDE
published: true
---

I use Github a lot to store my codes. I use both private and public repositories. 
When I started doing STM32 projects I thought it would be a great idea to store the projects on Github so the codes will not be lost.
In this post I will list down the steps how to add code to Github using STM32 Cube IDE.

# Installation

First of all, you will need to download EGit from the Eclipse Marketplace.
1. Open STM32 Cube IDE
2. Go to help
3. Choose Eclipse Marketplace
4. In search, write EGit.
5. Install EGit - Git Integration for Eclipse x.x.x

# Setup

1. Go to Window
2. Go to show view
3. Other
4. Git Repositories

Now we want to get our repository on the local drive of the computer so STM32 Cube IDE will recognize the repository on Github.
The repository will not be our workspace.
If you don't have a repository on Github you should create one.

1. Go to the repository
2. Press code
3. Under HTTPS there is a link
4. Copy the link
5. Go to STM32 Cube IDE
6. Under the Git Repository view select clone a repository
7. Paste the repository url under Location->URL
8. HOST should be github.com
9. repository path should be e.g. /gitusername/STM32-Projects.git or similar
10. Protocol: https
11. Authentication is your username and password for your Github account, then press next
12. Check the checkbox for main
13. Choose when fetching a commit, also fetch its tags
14. Next you can choose your directory path and then press finish

# Using EGit inside of STM32 Cube IDE

## Import and commit

Now you should have your repository visable under Git Repositories in STM32 Cube IDE.
You can now use "import" to import a project from the repository into STM32 Cube IDE.
After you import a project into STM32 Cube IDE, the IDE will track the changes and you will be able to push the changes of your project back to Github.

1. If you change a file inside of STM32 Cube IDE after import, the file will have a little carrot on it
2. If you want to push the file to Github, head over to Git Perspective
3. Select the repository
4. Under unstaged changes you will see all the files that have been changed
5. Now you can add those files to "staged changes"
6. You can add a comment to the commit manager
7. Next you can press commit push
8. Now if you go to your Github page you will see the changes there.

## Commit new project from workspace to Github repository

To add project to Github do the following
1. Open a project in STM32
2. Right click on the project under the project explorer
3. Choose Teams and choose share project
4. Choose your te directory where your repository is on your local drive and click finish
5. Now go to Git Staging. If you don't find it it's under "window" and then "show view"
6. Now you can see your project in "unstaged changes"
7. Press add files
8. 

...Post in progress...

#### Useful links

[1] Intelligent Systems Engineer. Youtube. [Link](https://www.youtube.com/watch?v=8kc77A6so7o)
