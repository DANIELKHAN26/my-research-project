
### 1. Install Git

brew install git

Verify:

git --version



### 2. Configure Your Identity

git config --global user.name  "Daniel Khan"
git config --global user.email "daniel.khan1@students.mq.edu.au"
git config --global init.defaultBranch main
git config --global color.ui auto

Verify:

git config --global --list

### 3. Generate SSH Key

ssh-keygen -t ed25519 -C "daniel.khan1@students.mq.edu.au"

- Press **Enter** to accept default location
- Press **Enter** to skip passphrase

Start the SSH agent and add the key:

eval "$(ssh-agent -s)"
ssh-add --apple-use-keychain ~/.ssh/id_ed25519


Copy the key to clipboard:

pbcopy < ~/.ssh/id_ed25519.pub


Add to GitHub:
1. Go to **github.com → Settings → SSH and GPG Keys → New SSH Key**
2. Paste the key → Save

Test the connection:

ssh -T git@github.com

### 4. Create Project Folder

mkdir my-research-project
cd my-research-project

Create the folder structure:

mkdir -p data/raw data/processed data/interim notebooks scripts reports figures config


Create a README:

touch README.md

Initialise Git:

git init

### 5. Create .gitignore

touch .gitignore
open .gitignore

Paste this in and save:

# Data
data/raw/
data/processed/
*.csv
*.parquet
*.pkl
*.h5
*.db

# Python
__pycache__/
*.pyc
.venv/
venv/
.ipynb_checkpoints/

# Credentials
.env
secrets.yaml

# Mac
.DS_Store

# Editors
.vscode/
.idea/

### 6. First Commit

git add .
git commit -m "Initial project structure"

### 7. Connect to GitHub
1. Go to **github.com → + → New Repository**
2. Name it `my-research-project`
3. Leave all checkboxes **unchecked**
4. Click **Create repository**

Then in Terminal:

git remote add origin git@github.com:DANIELKHAN26/my-research-project.git
git push -u origin main

## PART 2 — DAILY WORKFLOW

### Step 1 — Navigate to your project
cd ~/my-research-project

### Step 2 — Pull latest from GitHub (start of every session)
git pull

### Step 3 — Add your files
Drag and drop files into the folder in Finder:
`/Users/danielkhan/my-research-project/`

Or copy from Terminal:

cp /path/to/yourfile.ipynb ~/my-research-project/notebooks/


Put files in the right subfolder:

| Jupyter notebooks | `notebooks/` 
| Python / R scripts | `scripts/` 
| Raw data files | `data/raw/` 
| Cleaned data | `data/processed/` 
| Charts and plots | `figures/` 
| Papers, summaries | `reports/` 

### Step 4 — Check what Git sees

git status

Red = not yet staged. Green = staged and ready to commit.

### Step 5 — Stage your changes
All files at once:

git add .

One specific file:

git add notebooks/analysis.ipynb


### Step 6 — Commit

git commit -m "Describe what you did"


### Step 7 — Push to GitHub

git push


### Step 8 — Check on GitHub
Go to:

github.com/DANIELKHAN26/my-research-project


## PART 3 — USEFUL EXTRA COMMANDS


| See full commit history | `git log --oneline` |
| See what changed in files | `git diff` |
| Undo changes to one file | `git restore filename` |
| Unstage a file | `git restore --staged filename` |
| Fix last commit message | `git commit --amend -m "New message"` |
| Save work in progress temporarily | `git stash` |
| Restore stashed work | `git stash pop` |
| See all files in current folder | `ls -la` |
| Create a new experiment branch | `git switch -c experiment/my-test` |
| Switch back to main | `git switch main` |
| Merge experiment into main | `git merge experiment/my-test` |
| Tag a milestone (e.g. submission) | `git tag -a v1.0 -m "First submission"` |
| Push tags to GitHub | `git push --tags` |

## PART 4 


# in this order:

cd ~/my-research-project          ← go to your project
git pull                          ← get latest from GitHub
git status                        ← see what has changed
git add .                         ← stage everything
git commit -m "what you did"      ← save a snapshot
git push                          ← send to GitHub

