# Test Project

This project demonstrates basic Git and GitHub workflows including version control, branching, and ignoring files.

## 1. Initialize Git Repository

Created a project folder and initialized it as a Git repository.

```bash
mkdir test-project
cd test-project
git init
```

## 2. Track Changes with Commits
Added README.md and text files, then committed the changes with clear messages.

```
touch README.md
echo "This is the first file" >> README.md

touch notes.txt
echo "This is the first text document" >> notes.txt

git add .
git commit -m "First commit"
```

## 3. Branching and Merging
Created a new branch, made changes, switched back to ```main```, and merged. No merge conflicts.
```
git checkout -b new_branch

touch notes2.txt
echo "Second notes file" >> notes2.txt

# Edited the notes.txt file
echo "Added this line while in new_branch" > notes.txt

git add .
git commit -m "new_branch contents"

git checkout main
git merge new_branch
# If merge conflict occurred, manually resolve conflict in files
# Then:
git add .
git commit -m "Resolve merge conflict"
```

## 4. Push Project to GitHub
Created a remote repository, linked it to the local repo, and pushed commits.
```
git remote add origin https://github.com/LINNETWAHOME02/test_project.git
git branch -M main
git push -u origin main
```

## 5. Ignoring files
Initialized a virtual environment, installed django, created django project and made migrations
```
# Creating gitignore file
touch .gitignore

# Create and initialize venv
python -m venv venv
venv/Scripts/activate.ps1

# Install django
django-admin startproject 'djangoapp' .

# Migrations to get the db.sqlite3 file
python manage.py makemigrations
python manage.py migrate
```
Files and folders added to .gitignore: ```venv```, ```__pycache__```, ```db.sqlite3```, ```*.log```

## 6. Issues encountered
venv pushed to github despite being in .gitignore

- Solution: removed the folder from Git's tracking history (without deleting it locally) and then committed the changes
```
git rm -r --cached venv
git rm -r --cached .venv
git commit -m "Remove virtual environment from version control and updated README.md"
git push
```

## 7. Fork
Forked beccanj/geoflexwebsite, made changes a text file and created a pull request
```
# Cloned the repo into my local machine
git clone https://github.com/LINNETWAHOME02/geoflexwebsite.git
cd geoflexwebsite

# Set up a remote for the original  repo
git remote add upstream https://github.com/beccanj/geoflexwebsite.git

# Created my own branch
git checkout -b linnet

# Made changes in dont_look.txt
nano dont_look.txt

# Staged and committed my changes
git add .
git commit -m 'Changes by linnet'
git push
```
