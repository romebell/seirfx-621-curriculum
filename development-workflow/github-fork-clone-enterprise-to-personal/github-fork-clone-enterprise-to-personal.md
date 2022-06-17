## How to fork and clone from GitHub enterprise and push from GitHub personal

To fork and clone an Enterprise repository and push to your personal GitHub:

1. Fork the Enterprise repository.
2. Click the green "Code" button and copy the URL.
3. Clone the repo to your local machine `git clone https://git.generalassemb.ly/<Enterprise username>/<repository name>.git`
4. Remove the `.git` folder: `rm -rf .git`
5. Replace the `.git` folder: `git init`
6. Go to your personal GitHub account.
7. Click green "New" repository button, or click on your avatar and select "Your repositories" and click green "New" repository button.
8. Select owner (if necessary) and copy/paste the repo title.
9. Click green "Create Repository" button.
10. Copy and paste the first two commands from the second option "…or push an existing repository from the command line":
      ```
        git remote add origin git@github.com:<personal GitHub username>/<personal remote repository name>.git
        git branch -M main
      ```
11. Creating a new local repository will mean you have unsaved changes. You can check your status: `git status`, and then save your changes: `git add -A`
12. You can check that your changes have been saved: `git status`
13. Now you can push up to your remote repository: `git push -u origin main`
