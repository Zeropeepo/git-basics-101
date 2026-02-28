# git-basics-101
<p align="center">
  <img width="100%" src="img/P1.png" alt="pic1">
</p>


Hi fellow BCC Interns, this is an introduction on how to use git and collab with it, especially in Data Science projects. Hope u enjoy it yaa :)

## What You'll Learn
By following this step, you will learn:

- **Creating a Repository:** How to set up a new repository on GitHub.
- **Cloning an Existing Repository:** How to copy a GitHub repository to your local system.
- **Making Changes and Pushing to GitHub:** How to create, track, and upload changes.
- **Branch Management:** How to create, switch, and list branches for better collaboration.
- **Colab & Kaggle Integration:** How to sync your notebooks directly to GitHub.
- **Data Science Best Practices:** How to handle heavy datasets and avoid `.ipynb` merge conflicts.

## Windows Installation

1. Download Git
- Visit the official Git website: [Git](https://git-scm.com/downloads) for Windows 
- Click the download button to get the latest installer.

2. Install Git
- Open the downloaded .exe file.
- Follow the installation wizard, keeping the default settings unless you need custom configurations.
- Ensure that "Git Bash" and "Git GUI" options are selected during installation.

3. Check Version
- Open Git Bash or Command Prompt and run:
```bash
git --version
```
*(skip the linux installation if u use windows, or.... you're interested in linux? hihihi)*

## Linux Installation

1. Before using Git, you need to install it on your system. Open terminal and follow the steps below to install Git:

For Debian/Ubuntu-based systems:
```bash
sudo apt update  # Update package lists  
sudo apt install git  # Install Git
```

For Arch-based systems:
```bash
sudo pacman -S git
```

2. Check Version
```bash
git --version
```

## Basic Git Setup
Whether you use Windows or Linux the only difference is in the installation process. Once Git is installed, all the commands and steps remain the same across both operating systems.

1. Set Up Your Name and Email
```bash
git config --global user.name "Your Name" #Fill with your name (U can use your username github)
git config --global user.email "your.email@example.com" #Fill with your gmail
git config --global --list #Check your list
```
2. Initialize a Git Repository
```bash
mkdir test-ds-git #make a folder
cd test-ds-git  
git init 
git status #Check if you successfully initialized a Git repository
```
*Possible Output:*
> On branch master
> No commits yet
> nothing to commit (create/copy files and use "git add" to track)

3. Create and Commit a File
```bash
echo "World Hello" > hello.txt  # Create a new file named hello.txt  
git add hello.txt  # Stage the file to be included in the next commit  
git commit -m "First commit"  # Save the changes with a meaningful commit message
```
*Possible Output:*
> [master (root-commit) 213883c] First commit
>  1 file changed, 1 insertion(+)
>  create mode 100644 hello.txt


## Basic Github
1. Create Repository
   - Go to GitHub and log in.
   - Click New Repository -> Enter a repository name -> Choose Public or Private -> Click Create repository.

<p align="center">
  <img width="100%" src="img/P2.png" alt="pic2">
</p>



2. Clone an Existing Repository
```bash
cd
mkdir ds-github
cd ds-github
git clone [https://github.com/your-username/your-repo-name.git](https://github.com/your-username/your-repo-name.git)  
cd your-repo-name
```

3. Use the Token for Git Authentication
```bash
git remote set-url origin [https://YOUR_GITHUB_USERNAME:TOKEN@github.com/YOUR_GITHUB_USERNAME/YOUR_REPO.git](https://YOUR_GITHUB_USERNAME:TOKEN@github.com/YOUR_GITHUB_USERNAME/YOUR_REPO.git)
git fetch
```


**How do I get the token?** <br>
i. First go to the profile and go to settings
<p align="center">
  <img width="100%" src="img/P3.png" alt="pic3">
</p>


ii. After that scroll down and search for 'developer settings'
<p align="center">
  <img width="100%" src="img/P4.png" alt="pic4">
</p>


iii. From there click Personal Access Tokens and go to generate new token , choose "generate new token classic"
<p align="center">
  <img width="100%" src="img/P5.png" alt="pic5">
</p>


iv. Name the token whatever u want and check some permission that you need and click generate token
<p align="center">
  <img width="100%" src="img/P6.png" alt="pic6">
</p>

4. Make Changes and Push to GitHub
```bash
touch test.py
git add .  # Stage all changes (or use git add test.py)
git status # You can see the changes
git commit -m "Add file test.py"
git push origin main
```
5. Create a New Branch
```bash
git branch #Check current branch
git branch -a #List all branches	
git checkout -b new_branch #Create & switch to a new branch	
git switch main # Switch to an existing branch	
```
6. Push and Delete a Branch
```bash
git push origin new_branch #Push new branch to github repo
git branch -d new_branch #Delete a local branch	
git push origin --delete new-feature #Delete a remote branch
```
7. Pulling the Newest Changes
```bash
git fetch  # Retrieve the latest changes from the remote repository without merging them
git pull origin main  # Fetch and merge the latest changes made by your collaborators
git pull origin <branch-name>
```

---

## ☁️ Google Colab Integration
If your team uses Google Colab, you don't need to manually download and upload `.ipynb` files. 

**Saving to GitHub:**
1. In Colab, click **File** > **Save a copy in GitHub**.
2. Authorize Colab to access your GitHub account.
3. Select your repository, choose your branch, and write a commit message.
<p align="center">
  <img width="100%" src="img/P7.png" alt="pic7">
</p>

**Opening from GitHub:**
1. Go to Google Colab and select the **GitHub** tab on the welcome screen.
2. Paste the repository URL or search for it.
3. Click the notebook you want to edit.

## 📊 Kaggle Integration
Kaggle provides built-in Git sync, which is perfect for competitions or storing model experiments.

1. **Link Account:** Go to your Kaggle Profile > **Settings** > **Linked Accounts** > Connect GitHub.
2. **Push to GitHub:** Inside a Kaggle Notebook, click the **GitHub icon** (top right). Link this repository.
3. Every time you click **Save Version**, go to **Advanced Settings** and check the box to **Save to GitHub**.

<p align="center">
  <img width="100%" src="img/P8.png" alt="pic8">
</p>

## ⚠️ Data Science & AI Best Practices
Collaborating on ML/AI projects requires some extra rules:
1. **Never push datasets or model weights:** Files like `.csv`, `.pt`, `.pth`, or large image datasets will break your repo. Always add them to a `.gitignore` file.
2. **Notebook Merge Conflicts:** `.ipynb` files are basically huge JSON files. If two people edit the same notebook simultaneously, the conflict is extremely hard to fix. 
   * *Solution:* Assign one notebook per person (e.g., `EDA_Budi.ipynb`, `Model_Siti.ipynb`), or move stable architecture code into `.py` scripts.

---

## Video
-Still confused? You can watch a 40 minutes GitHub tutorial for a clearer understanding. [Full Youtube Video](https://www.youtube.com/watch?v=tRZGeaHPoaw&t=725s)

## Bonus
- `git merge` -> Combine changes from one branch into another. (Be careful with conflicts! You need to resolve them first before you can successfully complete the merge.)
- `git log` -> View commit history.
- `git reset <file>` -> Unstage a file before committing.
- `git stash` -> Temporarily save uncommitted changes.

### Note:
I highly recommend starting with the basics and using the CLI version of Git. Once you're familiar with it, you can transition to [GitHub Desktop](https://desktop.github.com/download/) for a more visual experience. (still i love CLI)

---

## Assignment

1. **Personal Repo:** Make your own repository for personal use and you can use that repository to clone another material in the future. <br> You can use this format: `TeamNumber-YourName` (Use Full Name). *ex = 1-Pieter*
2. **Team Repo:** Set up a team repository to collaborate and store code with your team. <br> You can use a structured format like this: `TeamNumber-MemberName1-MemberName2` (Use FullName). *ex = 1-Pieter-Toni*
3. **DS Repo** Try out collaborating with your team in your DS projects by making sure your .ipynb files are in the same repositories.

## Source:
- [Git](https://git-scm.com/docs/gittutorial)
- [Git](https://docs.github.com/en/get-started/getting-started-with-git/set-up-git)
- [Github](https://docs.github.com/en/get-started)

---
### ✨ BCC Contributors

1. Afe
2. Neva
