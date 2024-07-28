---
layout: post
title: Using Github with STM32 Cube IDE
published: false
---

I use Github a lot to store my codes. 
When I started doing STM32 projects I thought it would be a great idea to store the projects on Github so the codes will not be lost.
In this post I will list down the steps how to add projects to Github using STM32 Cube IDE so you will not loose your codes.

# Installation

First of all, you will need to download EGit from the Eclipse Marketplace. This is how I do this but you can also use Git for this.
1. Open STM32 Cube IDE
2. Go to help
3. Choose Eclipse Marketplace
4. In search, write EGit.
5. Install EGit - Git Integration for Eclipse x.x.x

# Setup

1. In STM32 Cube IDE, go to Window under the top menu bar
2. Go to show view
3. Choose other
4. Choose Git Repositories

Now we want to get our repository on the local drive of the computer so STM32 Cube IDE will recognize the repository on Github.
The repository will not be our workspace.
If you don't have a repository on Github you should create one before you proceed further.

1. Go to the repository
2. Press code
3. Under HTTPS there is a link
4. Copy the link
5. Go to STM32 Cube IDE
6. Under the Git Repository view select clone a repository
7. Paste the repository url under Location->URL
8. HOST should be github.com
9. repository path should be the link you copied, something like "/gitusername/STM32-Projects.git" or similar
10. Protocol: https

Now when you are asked for username and password you cannot use the same password you have on your Github account.
Github changed the rules since 2021 and now you need to make tokens to access your Github through softwares like STM32 Cube IDE.
To create a token do the following.

11. Log into your Github account online
12. Go to settings under your profile picture
13. Choose developer settings
14. Under personal access tokens you should choose Tokens(classic)
15. Press generate new token (classic)
16. Give it a name
17. Expiration can be chosen as no expiration
18. Check the checkboxes of repo and workflow. It should be enough
19. Generate the token

Now you can go back to STM32 Cube IDE
20. For username you use your github username
21. For password you use your generated token. Keep it save somewhere
22. then press next
23. Check the checkbox for main
24. Choose when fetching a commit, also fetch its tags
25. Next you can choose your directory path and then press finish

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
3. Choose Team and choose share project
4. Choose your repository in the dropdown list under "Repository:"
5. You don't really need a path unless you want it, then you can add it
6. Press finish
7. Now go to Git Staging. If you don't find it it's under "window" and then "show view"
8. Now you can see your project in "unstaged changes"
9. Press add files
10. Now the files move to "staged changes"
11. Write your commit message (for example: Initial commit)
12. Press commit and push


#### Useful links

[1] Intelligent Systems Engineer. Youtube. [Link](https://www.youtube.com/watch?v=8kc77A6so7o)

[2] V Develop. Youtube. [Link](https://www.youtube.com/watch?v=XKLnnXNe_qs)
