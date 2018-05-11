# Introduction
This little guide is going to explain you how to deal with a static website hosted on the *Italian Agile Days* (IAD) server [www.agileday.it](http://www.agileday.it).

## How it works
Every website is basically a Git repo hosted on IAD webserver.
Deploy is simple as pushing to `master` branch.

### 1. Contact the Italian Agile Movement board
Drop a mail to [consiglio@agilemovement.it](mailto:consiglio@agilemovement.it) to let us know you want to organize an event.
After the discussion, you will get all the elements to start working on your website.

### 2. Get the data (username, certificate, ...)
To push changes to the repo, you need:
* The url of the Git repo on IAD webserver
* A valid [http://how2ssl.com/articles/working_with_pem_files/](.pem certificate) to allow you to push changes to that repository

You can write to [ferdinando.santacroce@agilemovement.it](mailto:ferdinando.santacroce@agilemovement.it) or [ferdinando.santacroce@gmail.com](mailto:ferdinando.santacroce@gmail.com) to obtain these data.

# How to develop your website
1. Create a local repo for your website
2. Push it to a default Git remote of choice (eg. GitHub) to collaborate, if you like; this will be your `origin` remote

# How to deploy
In this example, we use `127.0.0.1` server URL, user `johndoe`, `website-repo.git` repo and `example.pem` certificate.

1. Put the certificate in a folder of choice, eg. `~/.ssh/`
2. Add this line to your `~/.ssh/config` file:

```
Host 127.0.0.1
    Hostname 127.0.0.1
    User johndoe
    IdentityFile ~/.ssh/example.pem
```

3. Add a new remote to your local Git repository that point to AgileDays server; in this example, we call it `live`:

```ssh
git remote add live ssh://johndoe@127.0.0.1/path/to/website-repo.git
```

To deploy, just issue a `git push live master` command.
