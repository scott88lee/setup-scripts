
## GIT

Before we do this process, please make sure you have signed up for an account on  [Github](http://www.github.com/). We will be installing a version of GIT from home brew and also configuring it.

To install GIT

```
sudo apt-get install git-all

```

#### Configuring GIT

Using your email credentials for GIT, run these commands with your user and email configured.

```
git config --global user.name "YOUR-USERNAME"
git config --global user.email "YOUR-EMAIL-ADDRESS"
git config --global push.default simple
git config --global credential.helper cache
```

## Node & NPM
Run the following commands in order in the terminal. Wait for each to complete before running the next.

-   `sudo apt-get update && sudo apt-get upgrade`
-   `curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -`
-   `sudo apt-get install -y nodejs`
    -   `mkdir ~/.npm`
    -   `npm config set prefix '~/.npm'`
    -   `echo 'export PATH="$HOME/.npm/bin:$PATH"' >> ~/.bashrc`
    -   `source ~/.bashrc`
-   `node -v`  (Checks the installed version of NodeJS)
-   `npm -v`  (Checks the installed version of npm)
## Installing PostgreSQL

-   Any database system contains at least 2 parts: the database server itself, and the database client.
    
-   **Installing the PostgreSQL client**
    
-   Open a WSL terminal and run the following commands in order.
-   `sudo apt-get install postgresql-client postgresql postgresql-contrib postgresql-client-common`

### Configure Postgres User

You'll also need to configure a user for your Postgres database.

```
sudo -u postgres psql postgres

\password postgres

```

Choose an easy to remember password then type  `\quit`  to exit psql. MAKE SURE YOU REMEMBER THIS PASSWORD YOU WILL NEED IT LATER.

### Create a Postgres Alias

To make it easier to start postgres we're going to create a couple aliases. Edit your bashrc file by typing  `subl ~/.bashrc`  add these lines to the bottom of the file:

```
alias psql="sudo -u postgres psql"
alias pgserver="sudo -u postgres service postgresql start"

```

**pgserver**  will be used to start the postgres server

**psql**  will be used to access the psql termainal

### Testing Postgres Setup

Quit terminal and reopen it before testing.

**Start Server**

```
pgserver

```

**enter psql terminal**

```
psql

```

Should enter psql terminal and have no error.

**exit psql**

```
\q

```

### Passwordless Postgres

Set no-password on postgres for your computer, so that it's easier to work with.

Edit postgres configuration file:

```
sudo sublime /etc/postgresql/POSTGRE_VERSION/main/pg_hba.conf

```

The file will look like this:

Change all configuration access to:

```
 # Database administrative login by Unix domain socket
 local   all             all                                     trust

 # TYPE  DATABASE        USER            ADDRESS                 METHOD

 # "local" is for Unix domain socket connections only
 local   all             all                                     trust
 # IPv4 local connections:
 host    all             all             127.0.0.1/32            trust
 # IPv6 local connections:
 host    all             all             ::1/128                 trust

```

Restart postgres server

```

 sudo /etc/init.d/postgresql restart

```

[](https://wdi-sg.github.io/gitbook-2019/00-config-deployment/installfest/windows/readme.html)[  
](https://wdi-sg.github.io/gitbook-2019/00-config-deployment/installfest/windows/install3.html)