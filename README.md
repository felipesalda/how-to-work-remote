# how-to-work-remote

Here i'm sharing the best practices i've learned to work on remote projects: git/github bases, team work and more.

**Disclaimer:** I'm a Data Scientist with background of Industrial Engineering so if you see i'm using an 'not better/easy/safe way to do it', im open to learn an update this resource for a better understanding of everyone.

## Working from different places
In my case, i use to work from home at a desktop pc and a laptop outside. So the first thing we have to do is set the public keys of the devices 

```bash 
000281268@PPJEFPLANEA MINGW64 ~
$ ls -al ~/.ssh
total 21
drwxr-xr-x 1 000281268 1049089   0 Nov  9 12:08 ./
drwxr-xr-x 1 000281268 1049089   0 Jan 19 16:27 ../
-rw-r--r-- 1 000281268 1049089 656 Nov  9 12:08 known_hosts
-rw-r--r-- 1 000281268 1049089 392 Nov  9 11:46 known_hosts.old

000281268@PPJEFPLANEA MINGW64 ~
$ ssh -T git@github.com
git@github.com: Permission denied (publickey).


000281268@PPJEFPLANEA MINGW64 ~
$ ssh-keygen -t ed25519 -C "YOUR@EMAIl.com"
Generating public/private ed25519 key pair.
Enter file in which to save the key (/c/Users/000281268/.ssh/id_ed25519):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /c/Users/000281268/.ssh/id_ed25519
Your public key has been saved in /c/Users/000281268/.ssh/id_ed25519.pub
The key fingerprint is:
SHA256:YOURNUMBER YOUR@EMAIl.com
The key's randomart image is:
+--[ED25519 256]--+
|oO*              |
[Your  fingerprint]
|    . BB++==*.   |
+----[SHA256]-----+

000281268@PPJEFPLANEA MINGW64 ~
$ ^C

000281268@PPJEFPLANEA MINGW64 ~
$ ls -al ~/.ssh
total 27
drwxr-xr-x 1 000281268 1049089   0 Mar  9 13:53 ./
drwxr-xr-x 1 000281268 1049089   0 Jan 19 16:27 ../
-rw-r--r-- 1 000281268 1049089 464 Mar  9 13:53 id_ed25519
-rw-r--r-- 1 000281268 1049089 106 Mar  9 13:53 id_ed25519.pub
-rw-r--r-- 1 000281268 1049089 656 Nov  9 12:08 known_hosts
-rw-r--r-- 1 000281268 1049089 392 Nov  9 11:46 known_hosts.old

000281268@PPJEFPLANEA MINGW64 ~
$ clip <~/.ssh/id_ed25519.pub

000281268@PPJEFPLANEA MINGW64 ~
$ clip < ~/.ssh/id_ed25519.pub

000281268@PPJEFPLANEA MINGW64 ~
$sssh -T git@github.com                                                         Enter passphrase for key '/c/Users/000281268/.ssh/id_ed25519':
Hi youruser! You've successfully authenticated, but GitHub does not provide shell access.

000281268@PPJEFPLANEA MINGW64 ~
$
```


git cmd
```shell
(venv) C:\Users\000281268\Documents\DS_Projects\How to work remote>deactivate
C:\Users\000281268\Documents\DS_Projects\How to work remote>git pull origin main
git@github.com: Permission denied (publickey).
fatal: Could not read from remote repository.

Please make sure you have the correct access rights
and the repository exists.

C:\Users\000281268\Documents\DS_Projects\How to work remote>git pull origin main
Enter passphrase for key '/c/Users/000281268/.ssh/id_ed25519': 
remote: Enumerating objects: 4, done.
remote: Counting objects: 100% (4/4), done.
remote: Compressing objects: 100% (4/4), done.
remote: Total 4 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (4/4), 1.67 KiB | 74.00 KiB/s, done.
From github.com:felipesalda/how-to-work-remote
 * branch            main       -> FETCH_HEAD
 * [new branch]      main       -> origin/main
fatal: refusing to merge unrelated histories

C:\Users\000281268\Documents\DS_Projects\How to work remote>git push origin main                          
error: src refspec main does not match any
error: failed to push some refs to 'github.com:felipesalda/how-to-work-remote.git'

C:\Users\000281268\Documents\DS_Projects\How to work remote>git push origin main 
error: src refspec main does not match any
error: failed to push some refs to 'github.com:felipesalda/how-to-work-remote.git'

C:\Users\000281268\Documents\DS_Projects\How to work remote>git pull origin main --allow-unrelated-histories
Enter passphrase for key '/c/Users/000281268/.ssh/id_ed25519': 
From github.com:felipesalda/how-to-work-remote
 * branch            main       -> FETCH_HEAD
CONFLICT (add/add): Merge conflict in .gitignore
Auto-merging .gitignore
Automatic merge failed; fix conflicts and then commit the result.

C:\Users\000281268\Documents\DS_Projects\How to work remote>git add .

C:\Users\000281268\Documents\DS_Projects\How to work remote>git commit -m "connected git with github"
[master 8800479] connected git with github

C:\Users\000281268\Documents\DS_Projects\How to work remote>git push origin main
error: src refspec main does not match any
error: failed to push some refs to 'github.com:felipesalda/how-to-work-remote.git'

C:\Users\000281268\Documents\DS_Projects\How to work remote>git status
On branch master
nothing to commit, working tree clean

C:\Users\000281268\Documents\DS_Projects\How to work remote>git push origin master
Enter passphrase for key '/c/Users/000281268/.ssh/id_ed25519': 
Enumerating objects: 8, done.
Counting objects: 100% (8/8), done.
Delta compression using up to 4 threads
Compressing objects: 100% (5/5), done.
Writing objects: 100% (6/6), 687 bytes | 343.00 KiB/s, done.
Total 6 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
remote: 
remote: Create a pull request for 'master' on GitHub by visiting:
remote:      https://github.com/felipesalda/how-to-work-remote/pull/new/master
remote:
To github.com:felipesalda/how-to-work-remote.git
 * [new branch]      master -> master

C:\Users\000281268\Documents\DS_Projects\How to work remote>git git branch --list
git: 'git' is not a git command. See 'git --help'.

The most similar command is
        init

C:\Users\000281268\Documents\DS_Projects\How to work remote>git branch --list     
* master

C:\Users\000281268\Documents\DS_Projects\How to work remote>git checkout main
Switched to a new branch 'main'
Branch 'main' set up to track remote branch 'main' from 'origin'.

C:\Users\000281268\Documents\DS_Projects\How to work remote>git branch -v
* main   0230f12 Initial commit
  master 8800479 connected git with github

C:\Users\000281268\Documents\DS_Projects\How to work remote>git merge master
Updating 0230f12..8800479
Fast-forward
 .gitignore | 7 +++++++
 1 file changed, 7 insertions(+)

C:\Users\000281268\Documents\DS_Projects\How to work remote>git add .

C:\Users\000281268\Documents\DS_Projects\How to work remote>git commit -m "branch main and master merged"
On branch main
Your branch is ahead of 'origin/main' by 2 commits.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean

C:\Users\000281268\Documents\DS_Projects\How to work remote>git merge main  
Already up to date.

C:\Users\000281268\Documents\DS_Projects\How to work remote>git merge master
Already up to date.

C:\Users\000281268\Documents\DS_Projects\How to work remote>git log
commit 880047902187f3285c98c45ad61085a9d07b4d81 (HEAD -> main, origin/master, master)
Merge: 176c84d 0230f12
Author: Felipe Saldarriaga @ U <felipe.salda@hotmail.com>
Date:   Wed Mar 9 14:06:25 2022 -0500

    connected git with github

commit 0230f1280c4b17c6a51998ee226c1333faac5b99 (origin/main)
Author: Carlos Felipe Saldarriaga Bejarano <46731424+felipesalda@users.noreply.github.com>
Date:   Wed Mar 9 13:40:10 2022 -0500

    Initial commit

commit 176c84d9ae1640e876c0a2899649a630cb9a2ebe
Author: Felipe Saldarriaga @ U <felipe.salda@hotmail.com>
Date:   Wed Mar 9 12:23:46 2022 -0500


C:\Users\000281268\Documents\DS_Projects\How to work remote>git log
commit 880047902187f3285c98c45ad61085a9d07b4d81 (HEAD -> main, origin/master, master)
Merge: 176c84d 0230f12
commit 880047902187f3285c98c45ad61085a9d07b4d81 (HEAD -> main, origin/master, master)
Merge: 176c84d 0230f12
commit 880047902187f3285c98c45ad61085a9d07b4d81 (HEAD -> main, origin/master, master)
Merge: 176c84d 0230f12
Author: Felipe Saldarriaga @ U <felipe.salda@hotmail.com>
Date:   Wed Mar 9 14:06:25 2022 -0500

    connected git with github

commit 0230f1280c4b17c6a51998ee226c1333faac5b99 (origin/main)
Author: Carlos Felipe Saldarriaga Bejarano <46731424+felipesalda@users.noreply.github.com>
Date:   Wed Mar 9 13:40:10 2022 -0500

    Initial commit

commit 176c84d9ae1640e876c0a2899649a630cb9a2ebe
Author: Felipe Saldarriaga @ U <felipe.salda@hotmail.com>
Date:   Wed Mar 9 12:23:46 2022 -0500

C:\Users\000281268\Documents\DS_Projects\How to work remote>git branch --delete master
Deleted branch master (was 8800479).

C:\Users\000281268\Documents\DS_Projects\How to work remote>git add .

C:\Users\000281268\Documents\DS_Projects\How to work remote>git commit -m "erased master branch"
On branch main
Your branch is ahead of 'origin/main' by 2 commits.
  (use "git push" to publish your local commits)

nothing to commit, working tree clean

C:\Users\000281268\Documents\DS_Projects\How to work remote>git checkout main
Already on 'main'
Your branch is ahead of 'origin/main' by 2 commits.
  (use "git push" to publish your local commits)

C:\Users\000281268\Documents\DS_Projects\How to work remote>git push
Enter passphrase for key '/c/Users/000281268/.ssh/id_ed25519': 
Total 0 (delta 0), reused 0 (delta 0), pack-reused 0
To github.com:felipesalda/how-to-work-remote.git
   0230f12..8800479  main -> main

C:\Users\000281268\Documents\DS_Projects\How to work remote>git add .

C:\Users\000281268\Documents\DS_Projects\How to work remote>git branch --delete master
error: branch 'master' not found.

C:\Users\000281268\Documents\DS_Projects\How to work remote>git commit -m "erased master branch"
[main ee6af1d] erased master branch
 1 file changed, 133 insertions(+)

C:\Users\000281268\Documents\DS_Projects\How to work remote>git push         
Enter passphrase for key '/c/Users/000281268/.ssh/id_ed25519': 
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 325 bytes | 162.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To github.com:felipesalda/how-to-work-remote.git
   8800479..ee6af1d  main -> main

C:\Users\000281268\Documents\DS_Projects\How to work remote>git add .

ted"
[main 9c08cff] .gitignore updated
 1 file changed, 3 deletions(-)

C:\Users\000281268\Documents\DS_Projects\How to work remote>git push
Enter passphrase for key '/c/Users/000281268/.ssh/id_ed25519':
Enumerating objects: 5, done.
Counting objects: 100% (5/5), done.
Delta compression using up to 4 threads
Compressing objects: 100% (3/3), done.
Writing objects: 100% (3/3), 326 bytes | 326.00 KiB/s, done.
Total 3 (delta 1), reused 0 (delta 0), pack-reused 0
remote: Resolving deltas: 100% (1/1), completed with 1 local object.
To github.com:felipesalda/how-to-work-remote.git
   ee6af1d..9c08cff  main -> main

C:\Users\000281268\Documents\DS_Projects\How to work remote>
```


