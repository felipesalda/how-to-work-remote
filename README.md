# how-to-work-remote

Here i'm sharing the best practices i've learned to work on remote projects: git/github bases, team work and more.

**Disclaimer:** I'm a Data Scientist with background of Industrial Engineering so if you see i'm using an 'not better/easy/safe way to do it', im open to learn an update this resource for a better understanding of everyone.

## Working from different places
In my case, i use to work from home at a desktop pc and a laptop outside. So the first thing we have to do is set the public keys of the devices

```bash 
$ ls -al ~/.ssh # This command shows existing keys
total 0

$ ssh-keygen -t rsa -b 4096 -C "YOUR@EMAIl.com" #This one will create you the device's keys
Generating public/private id_rsa key pair.
Enter file in which to save the key (/path/and/name):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /path/ssh/id_rsa
Your public key has been saved in /path/id_rsa.pub
The key fingerprint is:
SHA256:YOURNUMBER YOUR@EMAIl.com
The keys randomart image is:
+----[BLABLABLA]-----+
|oO*                 |
[Your  fingerprint   ]
|     . BB++==*.     |
+----[BLABLABLA]-----+

$ ls -al ~/.ssh # Now we got our public and private keys
-rw-r--r-- 1  464 Mar  9 13:53 id_rsa #Private
-rw-r--r-- 1  106 Mar  9 13:53 id_rsa.pub #Public
```

Now we have to let know to github our key in order to be recognized everytime we work with our repos

first we copy our key like this:

```
$ clip < ~/.ssh/id_rsa.pub
```
Then we go to our GitHub Settings>SSH and GPG Keys> New SSH key and paste our key

![SSH and GPC Keys](/images/2.png)

Now we can verify the connection like this at  bash:
```bash
$ssh -T git@github.com                                                         Enter passphrase for key '/c/Users/000281268/.ssh/id_ed25519':
Hi youruser! You've successfully authenticated, but GitHub does not provide shell access.
$
```

Now it's time to notice to our device that we are reaching a github repo. at the cmd of our repo:
```shell
git remote set-url origin git@github.com:gitusername/your-reto-link.git
#👆🏼 Notice that this is the SSH link at github
```
We can confirm that all is set:
```shell
git remote -v
origin  git@github.com:gitusername/your-reto-link.git (fetch)
origin  git@github.com:gitusername/your-reto-link.git (push)
```
Now we can push, pull and work with our repo everywhere, ***but alwas take care of your keys***.


## Problem #1: main and master conflict

From Octuber 2020 GitHub change the name of the principal branch, from master to main, but git keeps calling master so in the moment you'll connect them you will have as a result two branches: main and master.

In order to avoid this i've found two solutions:

1. for an existing repo with this two branches you can use this command at master:

```bash
git branch-M main
```

- `M` = moves all the existing changes at `master` to `main`

but this is something additional to do everytime, so there is when comes the next one to solve it once and for all.

2. In Git's Bash we can set the configuration of every repo we will create from now with the name of the principal branch like this:

```bash
git config --global init.defaultBranch main
```

![Tux, the Linux mascot](/images/1.png)

Now we have ***one less, one less problem🎶*** 