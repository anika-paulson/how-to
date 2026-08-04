# How to git

This is a my guide to review how to use git, cause I always forget the details. Currently I only know how to do it on linux... have not tested on windows or mac.

Happy hunting,
Anika Paulson
2026-07-30


## Installing and configuring git

<details>
  <summary>Once per computer. Or so.</summary>

I don't know how to use the desktop app because it doesn't work on linux (to the best of my knowledge), so these instructions only include command line methods. I have not tested Mac.

1. [Install](https://git-scm.com/install/windows)

```
# Windows
  # you need winget, I'm not sure how to install that
  winget install --id Git.Git -e --source winget

# Linux - Debian/Ubuntu
  sudo apt update
  sudo apt upgrade

  apt-get install git
  or
  sudo apt install git-all

# Mac?
  # install homebrew 
  brew install git
  # or macports
  sudo port install git

# Check
git --version
```

2. [Configuring](https://www.geeksforgeeks.org/git/using-git-on-commandline/)

```
git config --global user.name "anika-paulson"
git config --global user.email "paul0805@umn.edu"
```

<details>
  <summary> 3. Maybe just for windows, configure the R drive as safe </summary>
  
```
# example
git config --global --add safe.directory %(prefix)///rds01.storage.umn.edu/cla_psyc_grissom_labshare/Projects/Anika/data/extincts
# or edit the config directly
# https://stackoverflow.com/questions/11868447/how-can-i-remove-an-entry-in-global-configuration-with-git-config
git config --global --edit
# to save on windows :wq
# https://stackoverflow.com/questions/13239368/how-to-close-git-commit-editor
```

</details>

<details>
  <summary>3. Maybe just for Linux, making an authentication key</summary>

*[Generate key](https://docs.github.com/en/authentication/connecting-to-github-with-ssh)*

```
ssh-keygen -t ed25519 -C "paul0805@umn.edu"
# "Enter a file in which to save the key", press enter
# enter a passphrase
```

*Start agent and add key*

```
eval "$(ssh-agent -s)" # start SSH agent in background
ssh-add ~/.ssh/id_ed25519 # add key to agent;
# change file name if you did not choose default
```

*[Add new ssh key to your account](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account)*

```
cat ~/.ssh/id_ed25519.pub
# copy terminal output
```

Open Account settings on github.com. Under Access, find SSH and GPG keys. Add/New SSH key. Choose a descriptive name, paste output into 'Key'.

*To reconnect:*

```
ssh -T git@github.com
# enter passcode
```
</details>

</details>

## Creating a repository from a local directory

<details>
<summary>At beginning of each project.</summary>

I've used [this site](https://kamileyagci.github.io/GitHubRepo_from_Local/) to help me understand how to create a git repository from a local directory. I'm just synthesizing that info here.

Consider this folder, '/home/gus/Documents/how-to/'

**Step 1 -- Initialize local repository**

```
cd /home/gus/Documents/how-to
git init
```

**Optional edit -- change 'master' to 'main'**

```
hint: Using 'master' as the name for the initial branch. This default branch name
hint: is subject to change. To configure the initial branch name to use in all
hint: of your new repositories, which will suppress this warning, call:
hint: 
hint: 	git config --global init.defaultBranch <name>
hint: 
hint: Names commonly chosen instead of 'master' are 'main', 'trunk' and
hint: 'development'. The just-created branch can be renamed via this command:
hint: 
hint: 	git branch -m <name>
```

*Cause 'master' is racist*

**Optional step -- git ignore**

Go [here](https://kamileyagci.github.io/GitHubRepo_from_Local/) for instructions

**Step 2 -- Add files**

```
git add *
```

**Step 3 -- Commit changes**

```
git commit -am ‘Initial commit’
```

**Step 4 -- Create remote repository**

1. On your github repository page (you must have an account first, oc), click 'New' (upper left)
2. Enter a ‘Repository name’.
3. Choose privacy setting - we need to check with IT to see how unpublished data can be kept
4. UNCHECK ‘add a README file’ and ‘gitignore’

**Step 5 -- Push local repository to remote**

On the quick set up page, use the instructions under ‘…or push an existing repository from the command line’.

1. Connect your local repository to GitHub repository

```
cd /home/gus/Documents/how-to
git remote add origin https://github.com/anika-paulson/how-to.git
```

2. Create the main branch

```
git branch -M main
```

3. Push the local repository to GitHub

```
git push -u origin main
```


</details>


## Deleting a repository

<details>
<summary>For me, more often than I should.</summary>

**To delete the remote and keep the local directory**

```
rm -r .git
```

**To delete both**

```
rm -r project_test
```

**Delete the GitHub repository in the settings menu**

</details>

## Pushing updates

<details>
  <summary>Every time damn it.</summary>

Does it ask for a key?

**Step 0 -- SSH authentication**

```
ssh -T git@github.com
```

**Step 1 -- Add new files and updates**

```
cd /home/gus/Documents/how-to
git add -A
```

**Step 2 -- Commit changes**

```
git commit -m ‘update’
```

**Step 1 and 2 alt**

Skip the git add before git commit with -am

```
git commit -am 'update'
```

**Step 3 -- Push to Github**

```
git push
```
</details>




## Pulling updates

<details>
  <summary>Every damn time.</summary>
  
If you've (or anyone has) changed it elsewhere, you need to [pull updates](https://github.com/git-guides/git-pull).
  
```
cd /home/gus/Documents/how-to
git pull
```

</details>

## Cloning

<details>
  <summary>For your other computer. Or someone else's or, you know.</summary>

```
git clone git@github.com:anika-paulson/how-to.git
```

Remember: pull and push, like the moon

</details>
