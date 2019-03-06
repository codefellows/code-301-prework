## Setup of Your Laptop Dev Environment (Canvas assignment)

Completion of the following setup tasks are all to be submitted in a single Canvas assignment. Keep a log of any errors or difficulties you encounter, and include those with your submission.

**Windows Users: please go [here](./windows/wsl.md)**

### Create Directory

Create a directory `~/codefellows/301/` to hold your work for this course, by running the command:
```
mkdir -p ~/codefellows/301
```

### Install Heroku CLI

Follow [these directions](https://devcenter.heroku.com/articles/getting-started-with-nodejs#introduction) for installing the Heroku CLI. *Note: you only need to complete the "Introduction" and "Set Up" sections.*

**Verify Installation**

From the command line, type `heroku --version` to verify that your Heroku installation was successful. You will also need to verify that your PostgreSQL installation (below) was successful, so please wait until the end of the prework steps to verify one after the other and submit a single screenshot in the corresponding Canvas assignment.

### Install Nodemon

In Code 301, Nodemon is a tool that is used to restart the server when changes are made in your server code.

In your terminal, run `npm i -g nodemon`. Run the command `nodemon --version` to confirm proper installation of Nodemon.

### Install PostgreSQL Database Software
*Please note that if you have a previously installed version of PostgreSQL on any operating system, you should be aware of any username and password that you've set for that installation. If you're unsure please uninstall and reinstall a fresh copy, which will also install the latest stable version. Additionally, if you are using a version before 9.5, you should uninstall and reinstall. You will be unable to complete certain labs if you are using version 9.4 or previous!*

For both Windows and Linux users, please follow the default installation instructions taking care not to change values such as the default port numbers (You may be prompted to change them, but should also be given default values).

### Linux

*For reference, these instructions are taken from the following documentation: https://www.postgresql.org/download/*

- If asked to provide or set a username and password, **be sure to document the username and password**, as you will need them later in the course.
- `sudo apt-get install postgresql`
- You will be prompted with the message that a certain amount of disk space will be used and asked if this is OK. Type `y`, then hit enter.
- Several commands will automatically run, this may take a few minutes.
- **You will likely NOT be prompted for a default username or password.** You will need to set one in psql if this is the case.

**Verifying Installation And Setting A Password**
- You should be able to run the command `sudo -u postgres psql`. You will be asked for your administrator password - this is what you usually enter when you run `sudo` commands. This will log you into the psql prompt as the user postgres.
- You should now have a prompt that looks like `postgres=#`. You can run SQL commands from here, which must end in semicolons.
- If you were not prompted for a default user or password, we will set one using psql. If you type `\du`, you can get a list of users associated with PostgreSQL. You should see a single user, `postgres`. You will need to set up a new role for your machine's default user. This is the username that appears at the beginning of your terminal prompt, and when you log into your machine.
- In your SQL shell, type the following: `CREATE ROLE your-username-here WITH LOGIN PASSWORD 'your-password-here';`, replacing "your-password-here" with whatever you want it to be. Remember that your password must be wrapped in quotes. The username should not be wrapped in quotes. *Don't forget the semicolon*.
- If successful, you will receive the feedback `CREATE ROLE`.
- Now we need to grant that user administrative control. In your SQL shell, type the following: `ALTER ROLE your-username-here WITH superuser;`, replacing "your-username-here" with the username you created a role for in the previous step.
- If successful, you will receive the feedback `ALTER ROLE`.
- Next, we need to create a default database for your new user and assign ownership of it to your new account. In the SQL shell, type the following: `CREATE DATABASE your-username-here;`, replacing "your-username-here" with your username. On success, you will receive the feedback `CREATE DATABASE`.
- To change the owner of your database from the `postgres` user to your user, type the following: `ALTER DATABASE your-username-here OWNER TO your-username-here;`, replacing "your-username-here" with your username. On success, you will receive the feed back `ALTER DATABASE`.
- Close your SQL shell with `\q`. Type `psql` again and your SQL shell should now open as your default user. Hooray! Continue to [final steps!](#final-steps).

**If you are having issues with installation, please contact your instructor.**

### MacOS

You should have already verified that you have Homebrew installed, from the Code 201 Prework. Use Homebrew to install PostgreSQL.

To install PostgreSQL, open your Terminal, and enter:
`brew update && brew install postgresql`

This will create a user for you, that matches your logged in user account. Run the `whoami` command in the terminal if you aren't sure what that is. This user has a blank password set as the default.

*You will need to run this command whenever you first start or restart your computer and open up the terminal in order to start your Postgres server:*

`brew services start postgresql`

If you'd like to shut down your database server, you can run:

`brew services stop postgresql`

### <a id="final-steps">Final Steps</a>

When you are finished installing the Heroku CLI and PostgreSQL, please move here to complete your [Final Steps](./final_steps.md)
