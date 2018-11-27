#### ALL USERS: Startup and Create some databases

1. Login to psql.
  - For Mac, type `psql` from terminal.
    - If the response is, "Can't find database *yourUserName*", run `createdb -U yourUserName`, then run `psql` again.
  - For Linux, run `psql`.
  - For WSL, run `pgstart` and `psql` and enter your password if prompted.
2. You should be at a prompt that looks like `postgres=#` or `<your-username-here>=#`.
3. Enter the following command: `CREATE DATABASE city_explorer;`. *Note the semicolon. If you forget it, your prompt will go to a new line and look like* `postgres-#`. *This means you have an unterminated command and the prompt will just keep going to new lines until you enter a semicolon*.
  - You should receive the feedback "CREATE DATABASE".
4. Verify that your databases were created by running `\l` (no semicolon). You should see a list of databases, including `city_explorer`. You should be able to connect to a database by running `\c DATABASE_NAME`, e.g. `\c city_explorer`.
> If running `\l` puts you into a view with the highlighted word `(END)` at the bottom of your terminal, you can type `q` to escape that view.

---

Congrats! You're all done. :wink:
