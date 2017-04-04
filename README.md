# Code 301 Pre-work: Intermediate Software Development

## Computer Setup

## Install Atom

If you haven't already, install [Atom](https://atom.io). If you have used an advanced text editor like Sublime Text, then Atom will feel familiar to you. Atom is free, open-source, cross-platform, and has a wide array of useful plug-ins available. Please use Atom during Code 301. (If you are proficient with another text editor that you *love*, you may use that instead, but please note that your instructional team may not be able to assist with debugging any issues with your editor)

[Atom's documentation](https://atom.io/docs/latest) is top-notch. Review it now to familiarize yourself with the basics. Make sure you're looking at the docs for the latest version. If you find that you are unable to call atom in the terminal, you may need to enable shell commands through Atom by first opening it through your graphical desktop interface, and selecting `Install Shell Commands` in the drop-down menu.

----

## Install Node

*Note* If you get an error while installing these packages such as "try again as root/administrator", you may need to use the `sudo` command to get administrator access. For example `sudo apt-get install nodejs`.

#### Linux instructions

  To install Node, open your Terminal, and copy and paste the following line, then hit Enter:

  `sudo apt-get install nodejs`

  If this did not work, do a Google search on the particular error message you received and try to track it down. If you are still running in to problems, send an email or Slack message to your instructor and make a plan for working out a solution.

#### Mac instructions

  If you took Code 201, you should already have Homebrew installed. If you have not, follow the guide on [this page](https://github.com/codefellows/code-201-prework/blob/master/prework/mac/2_homebrew.md#install-homebrew).

  To install Node, open your Terminal, and enter:

  `brew update && brew install node`

#### Windows instructions

  To install Node, go [here](https://nodejs.org/en/download/), and then download and run the Windows Installer. Make sure you do not deselect any of the Node components such as NPM during the installation.

### Verify the Node installation
Now let's verify that it is installed. Enter the following into your terminal:

`node -e 'console.log("works")'`

You should get a response that says "works". If not, try reinstalling Node again

----

## Install eslint and live-server Node packages

Now that you have Node installed, you can install Node packages using its package manager, **NPM**. Open your Terminal (Git Bash on Windows) and enter:

`npm -g i eslint live-server git-open`

You should see a lot of feedback as it installs.

### Verify the Node packages installation
Now let's verify that it is installed. Enter the following into your terminal:

`npm list -g --depth=0`

You should get a list back that includes `live-server` and `eslint`.

![](http://i.imgur.com/1ITioP1.png)

----

### What is this linter thing?

Linting is the process of running a program that will analyze code for potential errors. It is an important part of the quality assurance process.

> `lint` was the name originally given to a particular program that flagged some suspicious and non-portable constructs (likely to be bugs) in C language source code. The term is now applied generically to tools that flag suspicious usage in software written in any computer language.

That means the linter is your friend! It will help you write syntactically correct code, so you can catch errors in your text editor, rather than having to hop over the browser, refresh your page, and search for errors. Faster feedback makes for happier developers (that's you!).

## Install linter and linter-eslint Atom packages

For this next part, you will have Atom's package manager **apm** install some packages. Go [here](https://atom.io/docs/v0.194.0/using-atom-atom-packages#command-line) to verify it's enabled. Once you have verified that apm commands will work, enter this on your Terminal:

`apm install linter linter-eslint`

You should get two success messages while it installs the linter and linter-eslint packages.

### Verify the Atom packages installation

Enter the following into your Terminal:

`apm ls`  
You should get back a long list, and at the end you should receive a list of packages you installed for Atom.   
Linter and linter-eslint should be on that list, like in this screen shot:

 ![screen shot 2016-05-28 at 11 33 31 pm](https://cloud.githubusercontent.com/assets/12869788/15631728/a816191c-252c-11e6-8cb4-5c757f240a50.png)

 ----

## Install PostgreSQL Database Software
*Please note that if you have a previously installed version of PostgreSQL on any operating system, you should be aware of any username and password that you've set for that installation. If you're unsure please uninstall and reinstall a fresh copy, which will also install the latest stable version.*

For both Windows and Linux users, please follow the default installation instructions taking care not to change values such as the default port numbers (You may be prompted to change them, but should also be given default values).

#### Windows

Follow the download and installation instructions on this page: [Installing Postgresql](http://www.postgresqltutorial.com/install-postgresql)

- Your **Default** database super user is: *postgres*
- You will be asked to enter and confirm a database password.
- **Be sure you document your default user and password**, as you will need them later in the course. We are working securely on your computer, so a simple password like `1234` will suffice, and there's no need to change the default user.

#### Linux

Follow the download and installation instructions on this page for your Linux distribution: [Installing Postgresql](https://www.postgresql.org/download/)

- If asked to provide or set a username and password, **be sure to document the username and password**, as you will need them later in the course.

#### MacOS

You should have already verified during the Node installation that you have Homebrew installed. Please see that section above for more details if not.

To install PostgreSQL, open your Terminal, and enter:
`brew update && brew install postgresql`

This will create a user for you, that matches your logged in user account. Run the `whoami` command in the terminal if you aren't sure what that is. This user has a blank password set as the default.

### Startup and Create some databases

Read the output of the above installation instructions carefully. It should tell you what you need to do, in order to start Postgres. There might be 2 different options (one to start it automatically, one to start it manually). Pick one, and run the command. Once again, read the output of the command. If postgres is running correctly, the `psql` command should run without error and put you into a `pg>` prompt. 

Now that Postgres is running, you should be able to create some databases to use in the class. From a command prompt, run these commands, utilizing the username and password form your set up. :

```
createdb -U USERNAME kilovolt
createdb -U USERNAME portfolio
```

These commands should run without an error (or any feedback really). If a message does print, read it carefully and use the info to troubleshoot.  
----

Congrats! You're all done. Well, except for your class-specific directory instructions :wink:
