# Windows with the WSL

This doc assumes you are using the WSL in the way described in the 201 prework, or in [this guide](https://github.com/michaeltreat/Windows-Subsystem-For-Linux-Setup).

## Create Directory

Create a directory `$wr/codefellows/301/` to hold your work for this course, by running the command:
```
mkdir -p $wr/codefellows/301
```

## Install Heroku CLI

Go to [this link](https://devcenter.heroku.com/articles/heroku-cli) and follow the **standalone** install instructions. This will install the Heroku CLI on your Ubuntu FS. This allows the CLI to run in a POSIX environment, fixing the `Heroku:pg push` issue that exists on Windows.

**Verify Installation**

From the command line, type `heroku --version` to verify that your Heroku installation was successful. Skip taking a screenshot (for your canvas assignment) until you can verify PostgreSQL as well. 

You are now done with the Heroku CLI! Next you will be installing PostgreSQL 10!

## Install PostgreSQL using WSL

This doc explains how to install PostgreSQL 10 for Windows WSL

We are installing this through the Ubuntu command line since we want this software to run in the Linux environment. You can check out the PostgreSQL Linux install docs [here](https://www.postgresql.org/download/linux/ubuntu/).

## Install
1. Open a terminal (the Ubuntu app) and then go to the root of the Ubuntu Subsystem by typing `cd ~ `.
2. Run `lsb_release -a` and make note of the `Codename` listed.
3. Type `sudo nano ../../etc/apt/sources.list`. This will open a file on Ubuntu using the Nano editor.
4. At the bottom of this file, paste in the line `deb http://apt.postgresql.org/pub/repos/apt/ CODENAME-pgdg main`, replacing CODENAME with the word you noted in step 2.
5. When that's done, press `ctrl + x` together to close the file, press `y` when prompted to save your changes, and `enter` to finally close.
6. Next, copy these 2 lines and paste them into your terminal:
  ```
  wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
  sudo apt-get update
  ```
  This will add postgresql 10 to your repositories so you can install the latest version of Postgresql.

7. After the update is complete, enter in the line `sudo apt-get install postgresql-10` and press `y` when prompted.
8. To launch the postgres service, type `sudo service postgresql start`.

## Postgres User Setup

**Verifying Installation And Setting A Password**
- You should be able to run the command `sudo -u postgres psql`. You will be asked for your administrator password - this is what you usually enter when you run `sudo` commands. This will log you into the psql prompt as the user postgres.
- You should now have a prompt that looks like `postgres=#`. You can run SQL commands from here, which must end in semicolons.
- If you were not prompted for a default user or password, we will set one using psql. If you type `\du`, you can get a list of users associated with PostgreSQL. You should see a single user, `postgres`. You will need to set up a new role for your machine's default user. This is the username that appears at the beginning of your terminal prompt, and when you log into your machine.
- In your SQL shell, type the following: `CREATE ROLE your-username-here WITH LOGIN PASSWORD 'your-password-here';`, replacing "your-password-here" with whatever you want it to be. Remember that your password must be wrapped in quotes. The username should not be wrapped in quotes. *Don't forget the semicolon*.
- If successful, you will receive the feedback `CREATE ROLE`.
- Now we need to grant that user administrative control. In your SQL shell, type the following: `ALTER ROLE your-username-here WITH superuser;`, replacing "your-username-here" with the username you created a role for in the previous step.
- If successful, you will receive the feedback `ALTER ROLE`.
- Next, we need to create a default database for your new user and assign ownership of it to your new account. In the SQL shell, type the following: `CREATE DATABASE your-username-here;`, replacing "your-username-here" with your username. On success, you will receive the feedback `CREATE DATABASE`.
  - Note: You might get a `WARNING: could not flush dirty data: Function not implemented` warning many times when you run this command. This is okay! Let the command keep running, and you should eventually see success.
- To change the owner of your database from the `postgres` user to your user, type the folliwing: `ALTER DATABASE your-username-here OWNER TO your-username-here;`, replacing "your-username-here" with your username. On success, you will receive the feedback `ALTER DATABASE`.
- Close your SQL shell with `\q` or `ctrl-D`. Type `psql` again and your SQL shell should now open as your default user. Hooray!

## Suggestion

Since typing out `sudo service postgres start` all the time can be tedious, and you'll need to run this when you restart your computer, we recommend you set up an alias for this. 

1. Open a terminal and type `cd ~`, then type `nano .profile`. This will open your `.profile` which controls what your terminal does and looks like.
1. Add this line next to any other aliases that you have:
```
alias pgstart='sudo service postgresql start'
```
This will allow you to type `pgstart` to start running the psql service. This is an example of a Quality of Life enhancement, something that makes your life easier and faster as a developer. 

You can change `pgstart` to what ever you want, but just be careful you don't overwrite something that postgres might use.

### <a id="final-steps">Final Steps</a>

When you are finished installing the Heroku CLI and PostgreSQL, please move here to complete your [Final Steps](../final_steps.md).
