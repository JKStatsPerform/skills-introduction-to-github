## Step 0: Create and clone a repository

_Welcome to GitHub! :wave:_

Before we dive into the exciting world of GitHub collaboration, let's start with the fundamentals: creating your own repository and getting it on your local machine.

**What is GitHub?**: GitHub is a collaboration platform that uses _[Git](https://docs.github.com/get-started/quickstart/github-glossary#git)_ for versioning. It's a popular place where millions of developers share and contribute to projects. For more information, see "[About GitHub and Git](https://docs.github.com/en/get-started/using-git/about-git)".

:tv: [Video: What is GitHub?](https://www.youtube.com/watch?v=pBy1zgt0XPc)

**What is a repository?**: A _[repository](https://docs.github.com/get-started/quickstart/github-glossary#repository)_ (or "repo" for short) is a project containing files and folders. A repository tracks versions of files and folders, allowing you to see the history of changes and collaborate with others. For more information, see "[About repositories](https://docs.github.com/en/repositories/creating-and-managing-repositories/about-repositories)".

**What is cloning?**: _[Cloning](https://docs.github.com/get-started/quickstart/github-glossary#clone)_ a repository means creating a local copy of a repository that exists on GitHub. This allows you to work on your project on your own computer. For more information, see "[Cloning a repository](https://docs.github.com/en/repositories/creating-and-managing-repositories/cloning-a-repository)".

### :keyboard: Activity: Create a new repository

1. In the upper-right corner of any page on GitHub, use the **+** drop-down menu, and select **New repository**.

   ![screenshot showing the new repository button](https://docs.github.com/assets/cb-31554/mw-1440/images/help/repository/repo-create.webp)

2. In the **Repository name** box, type a name for your repository (for example, `my-first-repo`).

3. In the **Description** box, type a short description (optional but recommended).

4. Select **Public** to make your repository visible to everyone.
   
   > **Note:** Public repositories are visible to everyone on the internet. Private repositories are only visible to you and people you explicitly share access with.

5. Select **Add a README file**. This creates a README.md file in your repository, which is a great place to describe your project.

   ![screenshot showing repository creation form](https://docs.github.com/assets/cb-69942/mw-1440/images/help/repository/create-repository-name.webp)

6. Click **Create repository**.

Congratulations! 🎉 You've created your first repository. Now let's get it on your local machine.

### :keyboard: Activity: Clone the repository

To work with your repository on your local computer, you'll need to clone it. There are several ways to clone a repository, but we'll use HTTPS for this exercise.

> **Note:** Make sure you have [Git installed](https://git-scm.com/downloads) on your computer before proceeding.

1. On GitHub.com, navigate to the main page of your newly created repository.

2. Above the list of files, click the green **<> Code** button.

   ![screenshot highlighting the code button](https://docs.github.com/assets/cb-13128/mw-1440/images/help/repository/code-button.webp)

3. In the "Clone" section, select the **HTTPS** tab, then click the copy icon to copy the URL.

   ![screenshot showing the clone URL dialog](https://docs.github.com/assets/cb-45942/mw-1440/images/help/repository/https-url-clone-cli.webp)

4. Open your terminal (or Git Bash on Windows).

5. Navigate to the location where you want to store your repository. For example:
   ```bash
   cd ~/Documents
   ```

6. Type `git clone`, and then paste the URL you copied earlier. It will look like this:
   ```bash
   git clone https://github.com/YOUR-USERNAME/my-first-repo.git
   ```

7. Press **Enter** to create your local clone.

   ```
   $ git clone https://github.com/YOUR-USERNAME/my-first-repo.git
   Cloning into 'my-first-repo'...
   remote: Enumerating objects: 3, done.
   remote: Counting objects: 100% (3/3), done.
   remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
   Receiving objects: 100% (3/3), done.
   ```

8. Navigate into the cloned repository:
   ```bash
   cd my-first-repo
   ```

Excellent! 🎊 You now have a local copy of your repository. You're ready to start making changes and learning more about Git and GitHub!

### What's next?

Now that you have your repository set up both on GitHub and on your local machine, you're ready to learn about branches, commits, and collaboration. Continue to the next step to learn about creating branches!

<details>
<summary>Having trouble? 🤷</summary><br/>

If you encounter issues:
- **Can't create a repository?** Make sure you're signed in to GitHub and have verified your email address.
- **Don't have Git installed?** Download it from [git-scm.com](https://git-scm.com/downloads).
- **Clone command not working?** Double-check that you copied the correct URL from GitHub and that you have an internet connection.
- **Authentication issues?** You may need to set up a personal access token. See "[Creating a personal access token](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens)".

</details>
