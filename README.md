# My debut with GIT
Here is some basics commands to start using this powerful tool :hammer:


# Configure Git :gear:
To start using Git from your computer, you must enter your credentials to identify yourself as the author of your work. The username and email address should match the ones you use in GitLab.

In your shell, add your user name:

git config --global user.name "your_username"

Add your email address:

git config --global user.email "your_email_address@example.com"

To check the configuration, run:

git config --global --list

The --global option tells Git to always use this information for anything you do on your system. If you omit --global or use --local, the configuration applies only to the current repository.

You can read more on how Git manages configurations in the Git configuration documentation.

# Choose a repository :file_folder:
Before you begin, choose the repository you want to work in. You can use any project you have permission to access on GitLab.com or any other GitLab instance.

To use the repository in the examples on this page:

Go to https://gitlab.com/gitlab-tests/sample-project/.
In the top right, select Fork.
Choose a namespace for your fork.
The project becomes available at https://gitlab.com/<your-namespace>/sample-project/.

You can fork any project you have access to.

# Clone a repository
When you clone a repository, the files from the remote repository are downloaded to your computer, and a connection is created.

This connection requires you to add credentials. You can either use SSH or HTTPS. SSH is recommended.

# Clone with SSH
Clone with SSH when you want to authenticate only one time.

Authenticate with GitLab by following the instructions in the SSH documentation.
Go to your project’s landing page and select Clone. Copy the URL for Clone with SSH.
Open a terminal and go to the directory where you want to clone the files. Git automatically creates a folder with the repository name and downloads the files there.
Run this command:

git clone git@gitlab.com:gitlab-tests/sample-project.git

To view the files, go to the new directory:

cd sample-project

You can also clone a repository and open it directly in Visual Studio Code.

# Clone with HTTPS
Clone with HTTPS when you want to authenticate each time you perform an operation between your computer and GitLab.

Go to your project’s landing page and select Clone. Copy the URL for Clone with HTTPS.
Open a terminal and go to the directory where you want to clone the files.
Run the following command. Git automatically creates a folder with the repository name and downloads the files there.

git clone https://gitlab.com/gitlab-tests/sample-project.git

GitLab requests your username and password:
If you have 2FA enabled for your account, you must use a Personal Access Token with read_repository or write_repository permissions instead of your account’s password.
If you don’t have 2FA enabled, use your account’s password.
To view the files, go to the new directory:

cd sample-project

On Windows, if you enter your password incorrectly multiple times and an Access denied message appears, add your namespace (username or group) to the path: git clone https://namespace@gitlab.com/gitlab-org/gitlab.git.
Convert a local directory into a repository
You can initialize a local folder so Git tracks it as a repository.

Open the terminal in the directory you’d like to convert.
Run this command:

git init

A .git folder is created in your directory. This folder contains Git records and configuration files. You should not edit these files directly.

Add the path to your remote repository so Git can upload your files into the correct project.
Add a remote
You add a “remote” to tell Git which remote repository in GitLab is tied to the specific local folder on your computer. The remote tells Git where to push or pull from.

To add a remote to your local copy:

In GitLab, create a project to hold your files.
Visit this project’s homepage, scroll down to Push an existing folder, and copy the command that starts with git remote add.
On your computer, open the terminal in the directory you’ve initialized, paste the command you copied, and press enter:

git remote add origin git@gitlab.com:username/projectpath.git

After you’ve done that, you can stage your files and upload them to GitLab.

View your remote repositories
To view your remote repositories, type:

git remote -v

The -v flag stands for verbose.

# Download the latest changes in the project
To work on an up-to-date copy of the project, you pull to get all the changes made by users since the last time you cloned or pulled the project. Replace <name-of-branch> with the name of your default branch to get the main branch code, or replace it with the branch name of the branch you are currently working in.

git pull <REMOTE> <name-of-branch>

When you clone a repository, REMOTE is typically origin. This is where the repository was cloned from, and it indicates the SSH or HTTPS URL of the repository on the remote server. <name-of-branch> is usually the name of your default branch, but it may be any existing branch. You can create additional named remotes and branches as necessary.

You can learn more on how Git manages remote repositories in the Git Remote documentation.

# Branches
A branch is a copy of the files in the repository at the time you create the branch. You can work in your branch without affecting other branches. When you’re ready to add your changes to the main codebase, you can merge your branch into the default branch, for example, main.

Use branches when you:

Want to add code to a project but you’re not sure if it works properly.
Are collaborating on the project with others, and don’t want your work to get mixed up.
A new branch is often called feature branch to differentiate from the default branch.

Create a branch
To create a feature branch:

git checkout -b <name-of-branch>

Branch names cannot contain empty spaces and special characters. Use only lowercase letters, numbers, hyphens (-), and underscores (_).

Switch to a branch
All work in Git is done in a branch. You can switch between branches to see the state of the files and work in that branch.

To switch to an existing branch:

git checkout <name-of-branch>

For example, to change to the main branch:

git checkout main

View differences
To view the differences between your local unstaged changes and the latest version that you cloned or pulled:

git diff

View the files that have changes
When you add, change, or delete files or folders, Git knows about the changes. To check which files have been changed:

git status

Add and commit local changes
When you type git status, locally changed files are shown in red. These changes may be new, modified, or deleted files or folders.

To stage a file for commit:

git add <file-name OR folder-name>

Repeat step 1 for each file or folder you want to add. Or, to stage all files in the current directory and subdirectory, type git add ..

Confirm that the files have been added to staging:

git status

The files should be displayed in green text.

To commit the staged files:

git commit -m "COMMENT TO DESCRIBE THE INTENTION OF THE COMMIT"

Stage and commit all changes
As a shortcut, you can add all local changes to staging and commit them with one command:

git commit -a -m "COMMENT TO DESCRIBE THE INTENTION OF THE COMMIT"

Send changes to GitLab.com
To push all local changes to the remote repository:

git push <remote> <name-of-branch>

For example, to push your local commits to the main branch of the origin remote:

git push origin main

Sometimes Git does not allow you to push to a repository. Instead, you must force an update.

Delete all changes in the branch
To discard all changes to tracked files:

git checkout .

This action removes changes to files, not the files themselves. Untracked (new) files do not change.

Unstage all changes that have been added to the staging area
To unstage (remove) all files that have not been committed:

git reset

Undo most recent commit
To undo the most recent commit:

git reset HEAD~1

This action leaves the changed files and folders unstaged in your local repository.

A Git commit should not be reversed if you already pushed it to the remote repository. Although you can undo a commit, the best option is to avoid the situation altogether by working carefully.
You can learn more about the different ways Git can undo changes in the Git Undoing Things documentation.

Merge a branch with default branch
When you are ready to add your changes to the default branch, you merge the feature branch into it:

git checkout <default-branch>
git merge <feature-branch>

In GitLab, you typically use a merge request to merge your changes, instead of using the command line.

To create a merge request from a fork to an upstream repository, see the forking workflow
        
        SOURCE: ==> https://docs.gitlab.com/ee/gitlab-basics/start-using-git.html
