### Practice assigment Research Data Management with GitHub

##### Start

To start with this exercise do the following:

reate a GitHub account on [GitHub.com](https://www.github.com).
[Install](https://help.github.com/articles/set-up-git/) Github and Gitshell on your own device 

Open github and gitshell

Now create a repo (repository) on your own device, containing your own reserach data.
Read the folloing information about it on github.com: [Creating a Repo](https://help.github.com/articles/create-a-repo/)

On github.com ou log in and you create a repo on your own device

```
1. Clicj the plus-icon on the top left
2. Name your repo (your name + project number)
3. Enter a sort description
4. Create the public repository
5. Choose "create a readme"
6. Choose "create repository"
```

In your repository there will be an empty file called *read me*.
Click it, select edit and enter your student ID, describe your data and what you aim to do with it.

The local GitHub porgram on your device is still empty because you haven't synchroinzed your remote (=online) version of your GitHub repo to your device. From your onlien GitHub page (ongithub.com) copy your repository's URL from the menu to the right of your repository overview.

In gitshell, navigate to your local github folder (probably C:\Users\Name\Documents\GitHub ) by typing into the Gitshell command window:

```
cd C:\Users\[YourName]\Documents\GitHub
```

If you located you github folder somewhere else, navigate to it using the file explorer, right click, choose properties, and copy the URL from there.
Then,  you "clone" the repository to your local GitHub using the command clone:

```
git clone [URL of your repository]
```

Later  you can adapt your local repository to the remote (online) version using the command *git pull* (more about this later). 

Your new folder under Documents/GitHub can now be used to store and manage your research data. 
Once your ready adding your data (in .csv) and you can send it to your remote repository on the GutHub servers by doing the following:

```
cd "[pathtoyourrepository]" 
git add -A 
git commit -m "[type a message describing what you edited - a "commit message"]"
git push
```

This sequence of commands makes sure all files from your local repository are sent to the remote, and they are matched and merged based on file name. Every change will be adapted or added. Now you've added all your data correctly to the GitHub server.  

Instead of using these commands in the gitshell command window you can also use the GitHub program on your device to create, clone and synchronize repositories. Adapting your local repo to the latest version of the remote repo you can do with either the commance hit pull, or by clicking 'sync' in the right top of the GitHub program interface.


##### Collaborating on GitHub

GitHub enables collaborators to simultaneaously work on one file, much like Google Drive does. Researchers can collaborate on code, but also on research data. Contrary to Google Drive,  GitHub also offers good version control. GitHub enables you to keep track of everyone's changes, restore them and to solve possible conflicts between adaptations of different collaborators. This facilitates safe and efficient collaboration and maybe more importantly: it forces you to develop workflows and protocols beforehand with you colleagues to be able to merge your research data at all. This can be achieved by creating a "master" repository, for which permission from the project leader is needed before your changes are implemented into the master version of a project. 
ome important considerations may be:
- who manages the master dataset?
- ill the master dataset be managed publicly or privately?
- which adaptations are permitted and which are not?
- nd who can make these adaptations or contributions?

To get an idea of the subject you can read the following atricles about version control using GitHub:
[Google Drive or GitHub?](https://www.quora.com/How-do-I-explain-to-someone-the-difference-between-GitHub-and-Dropbox-Google-Docs-and-Drive)
[Version Control](https://git-scm.com/book/en/v2/Getting-Started-About-Version-Control)

You might already expect for instance that if everyone gets access to the master version, things get messy and difficult to track quite soon. Moreover, a participant could accidentally delete anothers contribution unknowingly and it might take a while before someone figures out why. We, and most collaborating groupd on GitHub, will use a technique called "forking", which that everyone makes a copy of th master dataset (a fork), a remote as well as a local copy. On your local version, you can implement new features or adapt parts, accompanied by a "commit message". The local, adapted version, will be pushed mack to the remote version (or fork). To see our proposed changes implemented in the master repository we send a "pull request", which is a request to have our changes implemented in the master version, which the manager of the master version will have to permit first. This way, everyone can work on the project and contribute and proposed changes are integrated automatically using Git's merging and adding conflict resolution algorithms, without everyone being able to directly change others' work.

###### Forking:

To practice the procedure outlined above (not with your own data yet, this you will do later), browse to:
[UvA Research data Management](https://github.com/UvARDM/FirstSteps)

Here's a .txt file called "test". Read its message.

Fork this repository y clicking "fork"  the upper right corner. On your own GitHub.com page a copy the repo will appear. To get it on your local device as well, copy your remote fork's URL, and use the clone command in gitshell.( git clone [URL] )

Open the .txt file on your own device and add something nice to it. Save it in your GitHub folder (probably Documents/GitHub/TestData)

Send these changes back to the remote repo as follows:

```
cd ..[thtoyourfolder]/GitHub/FirstSteps
git add -A 
git commit -m "[type a commit message]"
git push
```

So far the changes have only been sent to your own remote fork. To have it added to the master branch, send a "pull request" to the master branch. he pull request means that you request the master branch's manager to "pull in" your changes.

###### Pull requests:

Navigate to your fork on github.com. Click on the green button on the top left (compare, retire, pull request). This menu gives you an overview of everything that has changed between your version and the master branch. Also it indicates whether a merge can be executed succesfully or not. If this is not the case, you've probably changed some fundamental formatting in your version (or the master branch has accepted such a change). If merging is possible you can send a pull request. n the comment, state exactly what you've done and add your students ID.  Now the manager of the master branch can asses whether he/she wants to pull in your changes, or ask you to make some necessary adaptations before this can be done.

If your pull request is acknowledged, your little story will be added to the .txt file in the master branch. If you've added your story, and so have you classmates, you can check the result of all additions by resynchronizing your fork with the master branch:

Navigate to the original master branch on github.com and copy its URL.

```
cd "[pathtoyourfolder]\GitHub\FirstSteps"
git remote -v
git remote add upstream [copied URL]
```

o check whether this worked:

```
git remote -v
```

Under "origin" it should say the URL of your fork
Under "upstream" it should say the URL of the master branch

Now that you've told Git where to get "upstream" changes from, you can have your fork synchronized by:

```
git fetch upstream
git checkout master
git merge upstream/master
```

Be prepared that if you've changed essential formatting in your fork, merging with th master branch, even if your pull request gets accepted at all, may yield some merging errors. As soon as all students have contributed all their stories/research data, the course staff will check everyone's contributions, ask for adaptations and then qcknowledge your pull requests. The final product is checked and cleaned once more. Then, once youve set up the synchronization between your fork and the master branch, you can use the "git pull" commando to get all the changes from your remote fork (synchronized to the master branch) to your local repo:

```
cd "[pathtoyourfolder]\GitHub\FirstSteps"
git pull
```

Now you can check what your classmates have done.
Issueing a git pull before the course staff has merged and cleaned the data will not result in any changed (i.e., they have not acknowledged the pull requests yet). Pulling when they are in the process of cleaning may result in wrong or broken files being pulled into your local repo and replacing your own data. You'll have to restore this by resetting your repo to the previous version, or wait for the correct data to appear. It is strongly advised to always save your data on multiple devices; make sure you still have your own original data on a USB somewhere. 

