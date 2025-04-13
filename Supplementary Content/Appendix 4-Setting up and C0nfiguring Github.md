### Appendix 4: Setting up and Configuring “Git” application on your Linux Machines and establishing your unique personal GitHub repository for code development, version control
This Appendix, apart from some specific information pertaining to the MockBot project , can be mostly disregarded if you already have done this, 
Also posted to this Github, document how to set up and configure the Microsoft ™ “**VS Co  
de**” code development and management package, that includes GitHub management functions.
A comprehensive guide to Git is the book “Git Pro” online : https://git-scm.com/book/en/v2 or  eBook pdf form by download.  


#### Establish your own github.com
To follow are the basic steps to establish your own **github.com** cloud based account and set up your **github remote web repository**. The following is a summary from the github.com documentation. Refer to each of the following web sites for further information

https://docs.github.com/en/get-started/start-your-journey/about-github-and-git

GitHub is a cloud-based platform where you can store, share, and work together with others to write code. Git is a version control system that intelligently tracks changes in files. Git is particularly useful when you and a group of people are all making changes to the same files at the same time.

With a personal account on GitHub, you can import or create repositories, collaborate with others, and connect with the GitHub community.

The “**Github**” a “**Remote**” repository, stores documents, code and other data that you write during your robot experimntation and developemnt. This Appendix 4 describes the essential steps to set this up and configure in the cloud based “github.com” server. It is available no-charge for non-commercial use that is yours to exclusively and privately administer. The code and data can be uploaded and downloaded to/from any of your Local repositories, such as those on your Raspberry Pi Robot and Desktop Workstation Machines.  

####Getting Started with your Github account

Navigate to https://github.com/ to Create an Account to configure a user name and password (following the prompts). This will enable you to log into github.com and view your personal github.
            
          As described below, it is suggested you configure a “Personal Access Token(classic)” that will facilitate various actions during the code development process by allowing users access to various resources in the Remote Robot and Local Desktop Machines “Command Line Terminal”. (Disregard the other security methods, for the purpose of this project). 
https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens          

Suggest Install the “command line” “git” on your Linux Desktop Workstation and Robot Raspberry Pi

Install on Linux, following installing Git from Default Packages and Setting up Git
https://www.digitalocean.com/community/tutorials/how-to-install-git-on-ubuntu 

$ sudo apt-get update  
$ sudo apt-get install git  
$ git --version


#### Remote Robot Setup
Set up using the **Remote Robot (SBC)** and **Local Desktop Machine** credentials configured when setting up your Git Account  

$ git config –global user.email “Your email Address”  
$ git config --global user.name "Your Name"  * This is the Name that appears on the “Overview” page of your personal github.com
$ git config --global user.email "youremail@domain.com"

It is necessary to establish **Passwords: Personal access tokens (classic)** are recommended (and mandatory most of the time) are an alternative to using passwords for authentication to GitHub when using the command line, as described here : https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens 

After opening your newly configured “Github.com” and logging in, follow the procedure “Creating a personal access token (classic) . Be sure to copy your personal access token now. You will not be able to see it or recover it again when you close this browser. Copy the code to your clipboard and paste into a text file ( using gedit, vim, or nano) saved to a convenient place (Like User/Desktop on your Remote Robot and Local Desktop machine. 

So now enter these values on **email** & **password** request , when you run various git commands, such as **Push** to update your github repository from your local repository in your workspace.


Verify the local and global configuration  
$ git config –list  
Or  
$ git config –global –list

So now you can create a **New Repository** with a defined Name in your Remote github.com. Then work on it in your Robot Machine by:  
$ git clone Repository Name in to your Local Machine workspace

https://docs.github.com/en/repositories/creating-and-managing-repositories/creating-a-new-repository

There are many Git commands to perform operations on and between your Local and Remote Repositories, that are described in the “Pro Git” book and online in docs.github.com. These include init, clone, add, commit, pull, push, branch, checkout. 

From a Terminal, 'git help -a' and 'git help -g' list available subcommands and some concept guides. See 'git help <command>' or 'git help <concept>' to read about a specific subcommand or concept. See 'git help git' for an overview of the system.

#### Configuring a .gitignore to prevent tracking certain local files:

On both the Ubuntu Desktop and Robot (Raspberry Pi), configure a .gitignore file in the root directory (the directory with the .git file)  of each created repository to define files or directories in that repository that should NOT be tracked and NOT pushed to the Remote Repository.  

Here is a list of sample gitignore files: https://github.com/github/gitignore . Suggest using the ROS.gitignore file and add these several additional lines if vscode and Git is deployed on the Remote Desktop and Robot Single Board Computer (SBC) machines

#### Using .gitignore
To exclude an already tracked file, from local repository root, adding these lines to the existing .gitignore. Note the “/filename” means in the git root directory, No  “/” means this directory and below, filename/ designates a directory.  


\# Catkin custom files  
CATKIN_IGNORE


\# VSCode  
/.vscode/
**/.vscode/
log/
build/
install/


\# .gitignore  

/.gitignore

\# Git .DS_Store  
.DS_Store


To remove an existing tracked file:  
$ git rm -r  -–cached \<filename>  

To update your github:  
$ git add .  
$ git commit -m ‘revise .gitignore’  
$ git push
