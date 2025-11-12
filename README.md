<!---
{
  "id": "35eb6085-0a91-4740-a611-b7f7077e91fc",
  "teaches": "Understanding and Using Git Tags",
  "depends_on": [],
  "author": "Stephan Bökelmann",
  "first_used": "2025-04-20",
  "keywords": ["git", "tags", "version control", "GitHub", "release management"]
}
--->

# Understanding and Using Git Tags

> In this exercise you will learn how to create, manage, and push Git tags both locally and remotely. Furthermore we will explore how tags are used in release workflows, how to list and delete them, and how to reference them in GitHub.

### Introduction

Git tags are markers that point to specific commits in your Git history. They are often used to label release versions (e.g., `v1.0`, `v2.1.3`) in a project's lifecycle. Unlike branches, tags are not meant to change—once set, they usually remain fixed to the commit they were assigned to. There are two main types of tags: lightweight and annotated. Lightweight tags are like bookmarks to a commit, whereas annotated tags are stored as full objects in the Git database with metadata such as the tagger name, date, and a message. This makes annotated tags better suited for public release points.

When you push code to GitHub, tags are not pushed automatically unless specified. However, GitHub uses tags extensively to create releases, navigate project history, and automate deployment pipelines. Understanding tags is essential for effective version control and collaboration, especially in larger teams or open-source projects.

### Further Readings and Other Sources

- [Git Tags - Git SCM Documentation](https://git-scm.com/book/en/v2/Git-Basics-Tagging)
- [GitHub Docs: Creating Releases](https://docs.github.com/en/repositories/releasing-projects-on-github/about-releases)
- [Pro Git Book, Chapter 2.6: Tagging](https://git-scm.com/book/en/v2/Git-Basics-Tagging)
- [YouTube: Git Tags Explained](https://www.youtube.com/watch?v=ZDR433b0HJY)

### Tasks

#### Task 1: Create a Lightweight Tag
1. Clone a Git repository of your choice (or initialize a new one):
   ```bash
   git clone https://github.com/your-username/sample-repo.git
   cd sample-repo
   ```
2. Make a commit if none exist:
   ```bash
   echo "Initial commit" > README.md
   git add README.md
   git commit -m "Initial commit"
   ```
3. Create a lightweight tag:
   ```bash
   git tag v0.1
   ```
4. Verify the tag was created:
   ```bash
   git tag
   ```

#### Task 2: Create an Annotated Tag
1. Create a new commit:
   ```bash
   echo "Feature A" > feature.txt
   git add feature.txt
   git commit -m "Add Feature A"
   ```
2. Create an annotated tag:
   ```bash
   git tag -a v1.0 -m "Release version 1.0 with Feature A"
   ```
3. List all tags and show details:
   ```bash
   git show v1.0
   ```

#### Task 3: Push Tags to GitHub
1. Push all tags to GitHub:
   ```bash
   git push origin --tags
   ```
2. Alternatively, push a single tag:
   ```bash
   git push origin v1.0
   ```
3. Visit your GitHub repository and navigate to the 'Tags' or 'Releases' section to see the tags.

#### Task 4: Checkout a Tag
1. Use a tag to view a specific version of the code:
   ```bash
   git checkout v1.0
   ```
2. Git will put you in a "detached HEAD" state. Verify with:
   ```bash
   git status
   ```
3. To return to your main branch:
   ```bash
   git checkout main
   ```

#### Task 5: Delete and Re-tag
1. Delete a local tag:
   ```bash
   git tag -d v0.1
   ```
2. Delete the tag on GitHub:
   ```bash
   git push origin --delete v0.1
   ```
3. Re-tag a different commit (e.g., the latest one):
   ```bash
   git tag v0.1
   git push origin v0.1
   ```

### Advice

When working with Git tags, always decide whether you need a lightweight or annotated tag. For most versioning and release workflows, annotated tags are preferred because they include essential metadata. Be careful when pushing tags to remote repositories; tags cannot be edited directly once pushed—they must be deleted and recreated. Use tags strategically to mark meaningful milestones in your project. If you're automating deployments or generating changelogs, tagging can serve as a powerful tool to anchor those processes. Don't forget that tagging can also be helpful in collaborative environments to synchronize progress or code states among team members. You can refer to the exercise sheet on [Git Branching and Merging](#) for complementary knowledge.

