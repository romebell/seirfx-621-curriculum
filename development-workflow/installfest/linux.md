# Linux

For the first portion of the class, we'll be working exclusively inside of the browser and Node. We'll be installing the following tools.

* Slack
* Homebrew
* Git
* Node
* Oh my ZSH
* iTerm
* Postgres.app

**TIP:** Use `CTRL+SHIFT+V` to paste into terminal

## Slack

We will be using slack to communicate throughout the course. You should've received an invite to our channels via e-mail. You can login via the web browser, but downloading / installing the app is highly recommended.

[Download Slack](https://slack.com/downloads)

## GIT

Before we do this process, please make sure you have signed up for an account on [Github](http://www.github.com). We will be installing a version of GIT from home brew and also configuring it.

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

#### Setting up SSH Key

You might find your self having to re-authenticate GIT every time you work on your command line. Setup SSH Keys to let Github remember your machine in the future.

* [Github Generating SSH Keys](https://help.github.com/articles/generating-ssh-keys/)

## Node

```
curl -sL https://deb.nodesource.com/setup_6.x | sudo -E bash -

sudo apt-get install -y build-essential nodejs
```

Verify the installation afterwards by running

```
node -v
npm -v
```

The above should display without any errors.

To finish up your installation, run this command to allow for global installations of npm tools.

```
sudo chown -R $USER /usr/local/lib
```



## Install Oh My ZSH

Oh my ZSH?!!! We will be tricking out commandline with another shell. A shell is an interface into our computer, and we will be using a lot to run commands.

We'll be using a shell and configuration package called [Oh-My-Zsh](https://github.com/robbyrussell/oh-my-zsh)

To install, we will run

```
sudo apt-get update
sudo apt-get install git-core zsh
chsh -s /bin/zsh
wget --no-check-certificate http://install.ohmyz.sh -O - | sh
sudo shutdown -r 0
```

(the last command will restart your computer)

## Postgres

### Install Postgres

We will be using a relational database called Postgres for Node and Rails portion our class. Download by running:

```
sudo apt-get install postgresql-client postgresql postgresql-contrib
```

### Configure Postgres User

You'll also need to configure a user for your Postgres database.

```
sudo -u postgres psql postgres

\password postgres
```

Choose an easy to remember password then type `\quit` to exit psql. MAKE SURE YOU REMEMBER THIS PASSWORD YOU WILL NEED IT LATER.

### Create a Postgres Alias

To make it easier to start postgres we're going to create a couple aliases. Edit your zshrc file by typing `subl ~/.zshrc` add these lines to the bottom of the file:

```
alias psql="sudo -u postgres psql"
alias pgserver="sudo -u postgres service postgresql start"
```

**pgserver** will be used to start the postgres server

**psql** will be used to access the psql termainal

While we're here, add these two functions and environment variables to make it easier to access, change and refresh our ZSH configuration file in the future. Copy and paste these to the end of the file.

```
export VISUAL=subl
export EDITOR="$VISUAL"

function zedit() {
  subl ~/.zshrc
}

function zrefresh() {
  echo "Refreshing your ZSH configuration."
  source ~/.zshrc
}
```

Save the file, close Sublime, and restart your terminal.

### Install Postgres GUI

```
sudo apt-get install pgadmin3
```

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

## Installing MongoDB

Follow the official installation instructions on MongoDB.com:

[https://docs.mongodb.com/v3.0/tutorial/install-mongodb-on-ubuntu/#install-mongodb](https://docs.mongodb.com/v3.0/tutorial/install-mongodb-on-ubuntu/#install-mongodb)

### Testing the MongoDB server

```
#Start the MongoDB server
mongod
```

Press `control-c` to stop the server.

### Install MongoDB GUI

We'll be using **RoboMongo**. Install here:

[https://robomongo.org/](https://robomongo.org)

