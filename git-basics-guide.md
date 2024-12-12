# Essential Git Commands for Beginners
## A Practical Guide to Version Control

### 1. First-Time Git Setup
```bash
# Set your identity
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```
**What it does**: Tells Git who you are. This information will be used in your commits.

### 2. Starting a Project

```bash
# Initialize a new Git repository
git init
```
**What it does**: Creates a new Git repository in your current folder. Think of it as creating a photo album for your project - now you can start taking snapshots of your code.

```bash
# Clone an existing repository
git clone https://github.com/username/repository-name.git
```
**What it does**: Downloads a copy of a project that already exists. Like making a copy of someone else's photo album.

### 3. Basic Daily Commands

```bash
# Check status of your files
git status
```
**What it does**: Shows you what files have changed, what's ready to be saved, and what's not being tracked. Like checking what photos are ready to go into your album.

```bash
# Add files to staging area
git add filename.txt    # Add specific file
git add .              # Add all files
```
**What it does**: Prepares files to be committed (saved). Like choosing which photos you want to put in your album.

```bash
# Commit your changes
git commit -m "Your message describing the changes"
```
**What it does**: Saves your changes with a description. Like putting photos in your album with a caption explaining what they are.

### 4. Working with Remote Repositories

```bash
# Add a remote repository
git remote add origin https://github.com/username/repository-name.git
```
**What it does**: Connects your local repository to GitHub. Like connecting your photo album to an online backup service.

```bash
# Push your changes
git push origin main
```
**What it does**: Uploads your commits to GitHub. Like uploading your photos to the cloud.

```bash
# Get latest changes from remote
git pull origin main
```
**What it does**: Downloads latest changes from GitHub. Like downloading the latest photos that others have added to the shared album.

### 5. Branching Commands

```bash
# Create a new branch
git branch branch-name
```
**What it does**: Creates a new version of your project to work on. Like starting a new chapter in your photo album.

```bash
# Switch to a branch
git checkout branch-name
# or (newer version)
git switch branch-name
```
**What it does**: Moves you to a different branch. Like moving to a different chapter in your album.

```bash
# Create and switch to new branch
git checkout -b branch-name
# or (newer version)
git switch -c branch-name
```
**What it does**: Creates a new branch and moves to it in one step.

### 6. Viewing History

```bash
# View commit history
git log
```
**What it does**: Shows you the history of all saves (commits) you've made. Like looking through your album's timeline.

```bash
# View changes in files
git diff
```
**What it does**: Shows what's changed in your files since the last commit. Like seeing what photos have been edited.

### 7. Undoing Changes

```bash
# Undo changes in working directory
git restore filename.txt
# or
git checkout -- filename.txt
```
**What it does**: Discards changes in your working files. Like undoing edits to a photo.

```bash
# Unstage files
git restore --staged filename.txt
```
**What it does**: Removes files from staging area. Like taking photos out of the "to be added" pile.

### 8. Common Workflows

#### Starting a New Feature
```bash
git checkout main          # Make sure you're on main branch
git pull                   # Get latest changes
git checkout -b feature    # Create new feature branch
# Make your changes
git add .                  # Stage changes
git commit -m "Add feature"# Commit changes
git push origin feature    # Push to GitHub
```

#### Updating Your Project
```bash
git checkout main          # Switch to main branch
git pull                   # Get latest changes
git checkout your-branch   # Switch back to your branch
git merge main            # Merge main into your branch
```

### 9. Best Practices

1. **Commit Messages**
   - Use present tense ("Add feature" not "Added feature")
   - Be descriptive but concise
   - Start with a capital letter
   - Keep under 50 characters

2. **When to Commit**
   - After completing a feature
   - After fixing a bug
   - When you want to save your progress
   - Before trying something experimental

3. **Branch Names**
   - Use descriptive names
   - Use hyphens for spaces
   - Include feature/bug reference numbers
   Example: `feature-user-login` or `fix-header-alignment`

### 10. Common Issues and Solutions

1. **Merge Conflicts**
```bash
# When you get a merge conflict:
1. Open the conflicted files
2. Look for <<<<<<, ======, and >>>>>> markers
3. Edit the file to resolve the conflict
4. Remove the conflict markers
5. git add the resolved files
6. git commit to complete the merge
```

2. **Wrong Branch**
```bash
# If you committed to wrong branch:
git checkout correct-branch
git cherry-pick commit-hash
```

3. **Bad Commit Message**
```bash
# Fix last commit message:
git commit --amend -m "New message"
```

Remember:
- Don't be afraid to make mistakes
- Always create a new branch for new features
- Commit often but meaningfully
- Pull before you push
- When in doubt, `git status`