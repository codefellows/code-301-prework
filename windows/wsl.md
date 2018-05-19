### Windows with the Windows Subsystem for Linux

The best setup to give you the best of both worlds (data accessible from both Linux and Windows) is to install Postgres on Windows, and use a slightly-modified command from your Linux terminal to access the database.

- Go to the PostgreSQL [official website](http://www.postgresql.org/download/windows/).
- Click on the [download installer from EnterpriseDB](https://www.enterprisedb.com/downloads/postgres-postgresql-downloads#windows). Choose the latest version to download. It takes a few minutes to complete the download.
- Open the installer and follow the installation instructions. Make sure to leave ports (i.e. 5432) at their default setting, and remember the password you type in for the postgres user. (You do not need to reinstall Git, but you should install the other optional tools.)

Once this installation finishes, you should have a program installed on Windows called "SQL Shell (postgres)", which will open a dedicated terminal connected to Postgres. However, you'll also want to be able to access the `psql` command from your Linux terminal.

- Open your terminal and type `which psql`. If you get back a line like `/usr/bin/psql`, you should be all set! If not, run `sudo apt-get install postgresql-client-common` to install that command.
- Your standard line to connect to your database will be `psql -U postgres -h localhost`. You'll be prompted for your password, which is the postgres password you set during the Windows installation.
- If this connection is successful, you'll be in the PostgresQL interface, with a line that looks like `postgres=#` as the prompt. Hooray! Continue to [creating a database](#create-database).
- If you get an error message asking you to install `postgres-client-<version>`, never fear! Run `sudo apt-get install postgres-client-9.5`, then try the `psql` line again. (You may get a warning that you're using different versions of postgres on Linux and Windows; that won't be an issue.)

### Final Steps

When you are finished installing the Heroku CLI and PostgreSQL, please move here to complete your [Final Steps](./final_steps.md)