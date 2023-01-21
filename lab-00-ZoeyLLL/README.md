Lab 00
Part 0
Set Up Your Environment
To complete the labs for this course, you will need to learn how to work inside a UNIX command-line interface. Please read Chapter 0 of Learn a Command-line Interface by Kris Jordan: Getting Started (also available in this repository). Go through the Getting Started section to set up an Ubuntu Docker image on your computer. Having everyone use the same UNIX environment simplifies the coding and grading process.

Note: if you use a Linux-based operating system, you can follow the instructions for macOS, just find the respective Linux Docker installation instructions.

Learn the CLI
Read Chapters 1 and 2 of Learn a Command-line Interface by Kris Jordan: The Sorcerer's Shell and Directories, Files, and Paths. This will teach you everything you need to know about running programs and navigating directories in your UNIX environment. Make sure you practice running the commands in the environment! The shell will be your playground for the semester, so gain familiarity with it.

Learn Vim
Vim is an extensible text-editor program that is included in most UNIX systems. It is designed to make changing any kind of text very efficient, though it may not seem so at first. Start your Ubuntu environment that you set up earlier and enter the vimtutor command. When you press enter, a tutorial document will be opened with vim explaining how to use it.

Most likely, you will not remember everything from the tutor. We recommend you just learn enough from vimtutor to be comfortable enough to complete Part 1 of the assignment in vim, then later you can go back to vimtutor or look at online guides to learn more as you go.

In case the environment is compromised, all files are in learncli211/workdir.

Mac/Linux: When you run ./learncli.sh and start the Docker image, Docker will create the workdir directory that is bridged between the image and your native operating system, where you can copy and move files between the the two.

Windows: When you run ./learncli.ps1 and start the Docker image, Docker will create the workdir directory that is bridged between the image and your native operating system, where you can copy and move files between the the two.

Running exit in the Docker container will exit that container.

The following labs will assume that you are using vim, and we encourage you to take the opportunity to get a basic familiarity with vim during this class. Even if you do not become proficient in vim, a basic understanding can help you in later courses and in life, even outside of the domain of systems development.

Note that the vim in your Docker image has been optimized for the C programming language and may look different than vim on your home computer.

Setting up SSH authentication
In order to interact with GitHub from the command line, SSH authentication must be set up. This is a standard procedure and should only need to be done once.

Locally
Navigate to the learncli211 directory that contains the learncli.sh file, but do not execute it! This must be done outside of the container. If you are not sure whether or not your are in a container, then restart your console, and cd into learncli211.
Type ssh-keygen, type .ssh/id_rsa as the location to save the key, and press enter for no passphrase at the password prompt.
$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key (/home/root/.ssh/id_rsa): .ssh/id_rsa
Enter passphrase (empty for no passphrase): 
Enter same passphrase again: 
Your identification has been saved in .ssh/id_rsa.
Your public key has been saved in .ssh/id_rsa.pub.
The key fingerprint is:
SHA256:4yheFb7P2rzq/fJ71+AKPssyEQq7+bI0YcnK8+rzfr8 ceclia@topkek
The key's randomart image is:
+---[RSA 2048]----+
|                 |
|                 |
|        .        |
|   ... ...       |
|    =o .S.       |
| . o...+.o    .  |
|  + +oo o..  . ..|
|  .=++. oOo.  o o|
| .o=*=.oE*@B=+ . |
+----[SHA256]-----+
Inside of your learncli211 folder, a folder called .ssh should now exist. Running cat .ssh/id_rsa.pub should output the needed key as text to the console, which you should copy for the next part. For the macOS Terminal, highlighting the key and then pressing CTRL + C should copy it; on Windows Terminal, you must highlight it and then right-click the highlighted text to copy it. If nothing is highlighted in Windows Terminal, a right-click will paste.
GitHub
Click your profile in the top right corner.
Click Settings -> SSH and GPG keys -> New SSH Key.
Paste the contents of .ssh/id_rsa.pub into the "Key" section.
Give it a Title and click "Add SSH Key".
Part 1. Hello World
After authentication is set up, return to the container environment. Then, clone this Git repository within your container with the command git clone <respository> In place of where <respository> is, you should enter the SSH-based URL of your repository; e.g. git clone git@github.com:Comp211-SP23/lab-00-username.git. You can get this URL by clicking Code -> SSH.

In your repository, use mkdir to make a new directory named exactly 0-hello-world. Use cd to change your working directory to be this subdirectory. For reference on how to carry out either of these tasks, please refer to Chapter 2: Directories, Files, and Paths.

Next, you’ll want to edit a new file named hello.c. To begin editing this file in vim, simply run the command:

vim hello.c
Each source file in COMP 211 will begin with the standard header comment below. Note this header is checked by the autograder for an exact match. Please be sure to format your PID as a single 9-digit number with no spaces nor dashes. Additionally, be sure your capitalization and punctuation of the honor code pledge are correct. Since we do grade manually for style we do not include names on code listings to avoid biasing the grading.

// PID: 9DigitPidNoSpacesOrDashes
// I pledge the COMP 211 honor code.
Now refer to section 1.1 of C Programming Language to complete the rest of the assignment.

hello.c Requirements
The purpose of hello.c is to slightly extend the book's (C Programming Language) implementation of the same program on Page 9. Your implementation should print Hello, world. on one line, Welcome to C! on another line. This is case and punction-sensitive. It should then return EXIT_SUCCESS; to return EXIT_SUCCESS you will need to import stdlib.h, the header file which defines this constant. When main returns EXIT_SUCCESS, it indicates the program completed successfully via a success exit status. We will explore the idea of exit statuses later this semester. Additionally, in 211 we expect all function return types to be defined and main should return an int.

Compiling and Executing
You can compile and execute your program with the following shell commands:

gcc -Wall hello.c
./a.out
The -Wall flag tells gcc to print out all warnings.

Once your program compiles without warnings and meets the requirements, you can continue on.

Submit your assignment
Assignment submissions will be made through GradeScope.

You should already be enrolled in the COMP 211 Spring 2023 course on GradeScope. If you are not, please self enroll with entry code ZZB782. If you're unable to self enroll, please contact your cohort leader and we'll manually add you.

To submit your assignment, you must commit and push your work to this repository using git. You are likely unfamiliar with git at this point, so just follow these steps:

Navigate to the base folder of the repository within your container. Enter the command ls to confirm that it contains the directory 0-hello-world and ensure that the file hello.c is in that folder.
Type git status. You should see a list of changes that have been made to the repository.
Type git add -A. This signals that you want to place all modified/new files on the "stage" so that their changes can take effect.
Type git commit -m "Your Message Here". This shows that you are "committing" to the changes you put on the stage. Instead of Your Message Here, you should write a meaningful message about what changes you have made.
Type git push. This takes the commit that was made locally on your machine and "pushes" it to GitHub. Now, when you view this repository on GitHub you should be able to see the changes you've made.
Go to the COMP 211 course in GradeScope and click on the assignment called Lab 00.
Click on the option to Submit Assignment and choose GitHub as the submission method. You will be prompted to sign in to your GitHub account to grant access to GradeScope. When this occurs, make sure to grant access to the Comp211-SP23 organization.
You should see a list of your public repositories. Select the one named lab-00-yourname and submit it.
Your assignment should be autograded within a few seconds and you will receive feedback.
If you receive all the points, then you have completed this preliminary lab! Otherwise, you are free to keep pushing commits to your GitHub repository and submit for regrading up until the deadline of the lab.
Check your understanding
The purpose of this lab is to make sure you have some basic familiarity with the tools of this course, namely: your Ubuntu environment, vim, and git. You will earn full credit for this lab by simply submitting the short hello.c program, but it would be a good idea for you to spend some extra time learning the shell commands, vim keystrokes and understanding git. If you would like to learn more beyond what was included in the lab writeup, here are some additional resources created by Kris Jordan:

vim Tutorial - A beginner's guide to vim, a powerful text editor with a grammar.
What is a version control system? What is git?
git Fundamentals - add, commit, branch, checkout, merge
