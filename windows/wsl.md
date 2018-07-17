# Windows with the WSL

This doc assumes you are using WSL in the way described in the 201 prework, or in [this guide](https://github.com/michaeltreat/Windows-Subsystem-For-Linux-Setup)


## Install Heroku CLI

Go to [this link](https://devcenter.heroku.com/articles/heroku-cli) and follow the Ubuntu install instructions. This will install the Heroku CLI on your Ubuntu FS. This allows the CLI to run in a POSIX environment, fixing the `Heroku:pg push` issue that exists on Windows.

**Verify Installation**

From the command line, type `heroku --version` to verify that your Heroku installation was successful. Skip taking a screenshot (for your canvas assignment) until you can verify PostgreSQL as well. 

You are now done with the Heroku CLI! Next you will be installing PostgreSQL 10!

## Install PostgreSQL using WSL

This doc explains how to install PostgreSQL 10 for Windows WSL

We are installing this through the Ubuntu command line since we want this software to run in the Linux environmnet. You can check out the PostgreSQL Linux install docs [here](https://www.postgresql.org/download/linux/ubuntu/).

## Install
1. Open a terminal (the Ubuntu app) and then go to the root of the Ubuntu Subsystem by typing `cd ~ `.
2. Type `sudo nano ../../etc/apt/sources.list`. This will open a file on Ubuntu using the Nano editor.
3. At the bottom of this file, paste in this line `deb http://apt.postgresql.org/pub/repos/apt/ xenial-pgdg main`
  - Change the last part of the line above from `xenial-` to whichever version of Ubunutu you are running.
4. When that's done, press `ctrl + x` together to close the file, and press `y` when prompted to save your changes, and `enter` to finally close.
5. Next, copy these 2 lines and paste them into your terminal:
```
wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo apt-key add -
sudo apt-get update
```
This will add postgresql 10 to your repositories so you can install the lastest version of Postgresql. Press `enter` when the last line pops up.

6. After the update is complete, enter in this line `sudo apt-get install postgresql-10` and press `y` when prompted.

## Postgres User Setup

postgresql-10 runs under the user `postgres`. We need to give this user a password so that postgres can allow this user to connect to the database.

1. To set the password for postgres, type `sudo passwd postgres`.
2. You will get a prompt to enter in your password. It will not show when you are typing, but it is still registering your key-strokes.
3. Close and reopen the terminal. 

## Using psql

After your first install, and each time you restart your machine you will have to also restart the postgres service, or else you will get a `Is the server running?` error. 

1. To start the service, type `sudo service postgresql start`.
2. To conntect to postgres, type `sudo -u postgres psql`. 

You should get a prompt asking for your password. If this doesn't work, then you can try the second option listed below.

1. Switch users to postgres by typing `su - postgres`.
2. Type `psql`.

When this is successful you will see the command line change to look like this `postgres=#`

## Suggestion

Since typing out `sudo service postgres start` and `sudo -u postgrest psql` all the time can be tedious, I would recommend you set up a couple aliases for this. 

1. Open a terminal and type `cd ~`, then type `sudo nano .profile`. This will open your `.profile` which controls what your terminal does and looks like.
1. Add these two lines next to any other aliases that you have:
  - `alias pgstart='sudo service postgresql start'`
  - `alias runpg='sudo -u postgres psql'`
This will allow you to type `pgstart` to start running the psql service, and `runpg` to quickly log into the psql prompt. This is an example of a Quality of Life enhancement, something that makes your life easier and faster as a developer. 

You can change `pgstart` and `runpg` to what ever you want, but just be careful you don't overwrite something that postgres might use. 

### <a id="final-steps">Final Steps</a>

When you are finished installing the Heroku CLI and PostgreSQL, please move here to complete your [Final Steps](../final_steps.md)
