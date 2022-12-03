---
layout: default
title: Coding
nav_order: 2
permalink: /code
---

# What is this session about??
This is an introductory session for the asspirant developers in HITAM where in collaboration with the **Coding Club - HITAM** we were able to make the participants aware about the functionalities of GitHub, and how is it important in Version Control.

# What is GitHub?

![GitHub](../assets/images/render-2.jpg)

* Git is a version control management and collaboration software
* Git is an online application that provides:
    * A visual interface
    * Free cloud storage

## Why is GitHub useful??
1. **Version Control:** Can always go back to any version
2. **Collaboration:** Integrates edits from multiple people.
3. **Documentation:** All scripts in a single readme file.
4. **Reproducibilty:** You can create and modify an script create after a long time.
5. **Visibility:** Showcase your work to the world.

# The Excersices we performed were!!

## 1. Installing GitBash on Windows machines.
For the purpose of the rest of walk-through we should have a git command line tool where the one which we use was **Git-Bash** you can download it from [here](https://www.git-scm.com/). Install the Git Bash on your local machine and **MAKE SURE YOU ADD IT TO THE PATH!!**.

## 2. Create a GitHub Account!!
To follow through this walk-along please go ahead create your GitHub accout : [www.github.com](https://www.github.com).

Signup as you do on any other platform and fill the details accordingly.

After you are done with your account setup head to the dashborad.

## 3. Creating a Repository from the GitHub Site.

You can store a variety of projects in GitHub repositories, including open source projects. With open source projects, you can share code to make better, more reliable software. You can use repositories to collaborate with others and track your work. For more information, see ["About repositories."](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/creating-a-repository-on-github/about-repositories) To learn more about open source projects, visit [OpenSource.org](https://docs.github.com/en/github/creating-cloning-and-archiving-repositories/creating-a-repository-on-github/about-repositories).

* In the upper-right corner of any page, use the drop-down menu, and select **New repository**. 

![New repo](https://docs.github.com/assets/cb-11427/images/help/repository/repo-create.png)


* Type a short, memorable name for your repository. For example, "hello-world". 

![Naming](https://docs.github.com/assets/cb-25139/images/help/repository/create-repository-name.png)

* Optionally, add a description of your repository. For example, "My first repository on GitHub."

![Desc](https://docs.github.com/assets/cb-26377/images/help/repository/create-repository-desc.png)

* Choose a repository visibility. For more information, see ["About repositories."](https://docs.github.com/en/repositories/creating-and-managing-repositories/about-repositories#about-repository-visibility)

![viz](https://docs.github.com/assets/cb-20877/images/help/repository/create-repository-public-private.png)

* Select **Initialize this repository with a README.**
![readme](https://docs.github.com/assets/cb-49938/images/help/repository/initialize-with-readme.png)

* Click **Create repository.**
![create](https://docs.github.com/assets/cb-49938/images/help/repository/initialize-with-readme.png)

## 4. Cloning Repository
### When you create a repository on GitHub.com, it exists as a remote repository. You can clone your repository to create a local copy on your computer and sync between the two locations.

You can clone a repository from GitHub.com to your local computer to make it easier to fix merge conflicts, add or remove files, and push larger commits. When you clone a repository, you copy the repository from GitHub.com to your local machine.

Cloning a repository pulls down a full copy of all the repository data that GitHub.com has at that point in time, including all versions of every file and folder for the project. You can push your changes to the remote repository on GitHub.com, or pull other people's changes from GitHub.com. For more information, see "[Using Git](https://docs.github.com/en/github/getting-started-with-github/using-git)".

You can clone your existing repository or clone another person's existing repository to contribute to a project.

* On GitHub.com, navigate to the main page of the repository.
* Above the list of files, click 📥 Code. 

    ![clone](https://docs.github.com/assets/cb-20363/images/help/repository/code-button.png)

* Copy the URL for the repository.
    * To clone the repository using HTTPS, under "HTTPS", click 📋
    * To clone the repository using an SSH key, including a certificate issued by your organization's SSH certificate authority, click **SSH**, then click 📋. 
    * To clone a repository using GitHub CLI, click GitHub CLI, then click 📋. 
![copy link](https://docs.github.com/assets/cb-33207/images/help/repository/https-url-clone-cli.png)

* Open Terminal.
* Change the current working directory to the location where you want the cloned directory.

* Type `git clone`, and then paste the URL you copied earlier.
> `$ git clone https://github.com/YOUR-USERNAME/YOUR-REPOSITORY`

* Press **Enter** to create your local clone.


{% highlight sh %}
    $ git clone https://github.com/YOUR-USERNAME/YOUR-REPOSITORY
    > Cloning into `Spoon-Knife`...
    > remote: Counting objects: 10, done.
    > remote: Compressing objects: 100% (8/8), done.
    > remove: Total 10 (delta 1), reused 10 (delta 1)
    > Unpacking objects: 100% (10/10), done.

{% endhighlight %}