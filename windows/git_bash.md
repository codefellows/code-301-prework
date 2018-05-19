# Heroku CLI and Postgres for Git Bash

This doc will help you get Heroku CLI and PostgreSQL setup on your machince. 

## Install Heroku CLI

Follow [these directions](https://devcenter.heroku.com/articles/getting-started-with-nodejs#introduction) for installing the Heroku CLI. *Note: you only need to complete the "Introduction" and "Set Up" sections.*

**Verify Installation**

From the command line, type `heroku --version` to verify that your Heroku installation was successful. You will also need to verify that your PostgreSQL installation (below) was successful, so please wait until the end of the prework steps to verify one after the other and submit a single screenshot in the corresponding Canvas assignment.

You are now done with this section. Next we will be installing PostgreSQL.

## Install PostgreSQL Database Software
*Please note that if you have a previously installed version of PostgreSQL on any operating system, you should be aware of any username and password that you've set for that installation. If you're unsure please uninstall and reinstall a fresh copy, which will also install the latest stable version. Additionally, if you are using a version before 9.5, you should uninstall and reinstall. You will be unable to complete certain labs if you are using version 9.4 or previous!*

Please follow the default installation instructions taking care not to change values such as the default port numbers (You may be prompted to change them, but should also be given default values).

### Windows with Git Bash

*For reference, these instructions are taken from the following documentation: http://www.postgresqltutorial.com/install-postgresql/*

- Your **Default** database super user is: *postgres*
- You will be asked to enter and confirm a database password.
- **Be sure you document your default user and password**, as you will need them later in the course. We are working securely on your computer, so a simple password like `1234` will suffice, and there's no need to change the default user.

**There are three steps to complete the PostgreSQL installation**:

1. Download PostgreSQL installer for Windows
1. Install PostgreSQL
1. Verify the installation

**Downloading the installer**

- Go to the PostgreSQL [official website](http://www.postgresql.org/download/windows/).
- Click on the [download installer from EnterpriseDB](https://www.enterprisedb.com/downloads/postgres-postgresql-downloads#windows). Choose the latest version to download. It takes a few minutes to complete the download.

**Installing**

Double click on the installer file. An installation wizard will appear and guide you through multiple steps where you can choose different options that you would like to have in PostgreSQL. For now, just select default values. Once it's done installing then move to the next step.

At the time of writing, PostgreSQL does not get added to your path by default, so we will need to add it manually, but future versions may fix that. So let's check real quick:

- Open Git Bash and type `psql -U postgres` .
- If you get a prompt asking for a password then PostgreSQL was installed and added to your PATH. You can skip to the Verify Installation section below.

- If you get and error similar to `bash: psql command not found` then that means you will need to add Postgres to your path. Follow the steps below to do that.

**Adding psql to your PATH**

Normally when programs are installed ( like VScode for Windows) they are automatically added to your PATH which means you can type a quick command to execute the program ( like `code` for VScode for example). Here is how you add the psql command to your PATH which will allow you to launch PostgreSQL in Git Bash.

- Copy this line, `C:\Program Files\PostgreSQL\<version>\bin` and put the version number of PostgeSQL inside of \<version\>. IE `C:\Program Files\PostgreSQL\10\bin`.
- Open your system settings. (On Windows 10, you can right click on the start menu and navigate to settings.)

- You should see a search bar. Type `env` and the search will populate with a couple options. Choose the option that says "Edit the System Enviroment Settings".
![](https://i.imgur.com/ZT7xvD9.png)

- A small window will pop-up. At the bottomm, directly above the cancel button, is another button that says Enviroment Variables. Click that.
![](https://i.imgur.com/IjkiSrk.png)

- Another window will pop-up. This is where you can see all of your enviroment variables. Click on the one that says PATH, and then click edit.
![](https://i.imgur.com/t25DE7n.png)

- Finally, this last page will show you all of the things that are attached to your PATH. If you have installed Node and VS Code you may seem them in here! Click on New and you'll see a text entry box appear in the middle of the page. Paste in the line that you copied from step 1. Hit enter and then make sure to click Okay on all 3 previous boxes!
![](https://i.imgur.com/1RmmVdh.png)
 
- Close out of all windows, restart your computer, and move to Verify Installation!


**Verify Installation**

- Open the Git  Bash terminal and type `psql -U postgres`. It should prompt you for a password. If you get the error `bash: psql command not found`, and you already followed the steps for adding psql to your path then try restarting your computer then going through the above steps again to see if PostgreSQL is still attached to your PATH. If it's not, then and add it again. Restart and try again this step again. 

**If it still isn't working, then let the instructor know and skip to the Alternate Verify Installation section.**

- If it did work and you were prompted to enter a password then psql has been successfully added to your PATH.  
- In the password field, enter the password that you gave when you installed PostgreSQL.
- If it works, then your terminal window will change to the PostgreSQL interface.
- In this window, you can enter SQL statements, which must end with semicolons. 

> Note: If you used a different username then you can specify that after the `-U` in `psql -U <username>`. In most cases, by default the username is postgres, but it may have been changed to the username that you're currently logged into your computer account with. 

Congratulations, you've installed PostgreSQL correctly! Continue to [final steps](#final-steps).

**If you are having issues with the installation, please inform your instructor and try the Alternate Verify Installation.**

**Alternate Verify Installation**

When you installed PostgreSQL, the installer also installed some extra tools. One of them is psql (it may be called SQL Shell).

- Open the SQL shell program.
- When it prompts you for input, just hit enter to select default values until it asks for a password. You will put in the password you entered during installation.
- You should have a window that [looks like this](http://www.postgresqltutorial.com/wp-content/uploads/2012/08/psql.png).
- In this window, you can enter SQL statements, which must all end with semicolons. Congratulations, you've installed correctly! Continue to the final section.

**If you are having issues with the installation, please contact your instructor.**

### <a id="final-steps">Final Steps</a>

When you are finished installing the Heroku CLI and PostgreSQL, please move here to complete your [Final Steps](./final_steps.md)
