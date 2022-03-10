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
Now we can push, pull and work with our repo everywhere, ***but always take care of your keys***.


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

![commands initializing main branch](/images/1.png)

Now we have ***one less, one less problem🎶*** 

## 🍪 A Template for Data Science

Another tip i've learned is to **have a template for the DS projects**. We usually (always, actually) have workflows of ETL (Extract, Transform and Load) and the structure of our projecs probably looks like this:

![A Data Science Project Template](/images/3.png)
- A folder for data (Raw and Processed)
- A folder with Notebooks.
- Readme and Environment files.

This is the minimun we use for a project and we can have it automated like this:

```shell
(base) C:\path> conda activate cookiecutter-personal

(cookiecutter-personal) C:\path\DS_Projects

(cookiecutter-personal) C:\path\DS_Projects>cookiecutter https://github.com/felipesalda/cookiecutter-personal
# You can use this template at my github for your own cookies (DS Projects) 😊

project_title [Cookiecutter Personal]: DS Project with template
project_slug [ds_project_with_template]:
project_description [Building dreams with data]: this is a DS project template created with cookiecutter
project_author_name [Felipe Saldarriaga @aprendeconfelipe]:
Select project_packages:
1 - All
2 - Minimal
Choose from 1, 2 [1]: 1
python_version [3.7]:
←[Let's do it! You're are going to build a dream with data!
Creating project at C:\path\DS_Projects\ds_project_with_template←[
Almost done!
Initializing a git repository...
Initialized empty Git repository in C:/path/DS_Projects/ds_project_with_template/.git/
[main (root-commit) 8fbf8b4] Initial commit
 8 files changed, 24 insertions(+)
 create mode 100644 .gitignore
 create mode 100644 README.md
 create mode 100644 data/.gitkeep
 create mode 100644 data/processed/.gitkeep
 create mode 100644 data/raw/.gitkeep
 create mode 100644 environment.yml
 create mode 100644 notebooks/.gitkeep
 create mode 100644 notebooks/0.0-ds_project_with_template-introduction.ipynb
The beginning of your destiny is defined now! Create and have fun!
```

Only with this instructions and a conda environment with cookiecutter we obtained  all the files, folders and even the environment created with all we need to start a Data Science Project.

**But, ¿how can we do this?**
We just need to install conda at your device (from the official page), open the Anaconda Prompt and do this:

```shell
conda config --add channels conda-forge
#generate a channel for our cookiecutter environment

conda create --name cookiecutter-personal cookiecutter=1.7.3
#Important: this is an stable version for the config we need
```

There are ***many*** details and parametters we can add for our template like: 
- Initializing the repo as it's created.
- Hooks.
- Scripting.
- And even more.

The next level of template personalization is up to your curiosity and the [official documentation.](https://cookiecutter.readthedocs.io/en/1.7.2/README.html) ¡go for it!.
