<!---
{
  "id": "35eb6085-0a91-4740-a611-b7f7077e91fc",
  "teaches": "Understanding and Using Git Tags",
  "depends_on": ["https://github.com/STEMgraph/474307f2-a30c-4639-9379-298bf1a4c00b"],
  "author": "Stephan Bökelmann",
  "first_used": "2025-04-20",
  "keywords": ["git", "tags", "version control", "local development", "release management"]
}
--->

# Understanding and Using Git Tags

> In this exercise you will learn how to create, manage, and work with Git tags locally. Furthermore we will explore how tags are used in release workflows, how to list and delete them, and how to reference them in your local Git repository.

### Introduction

Git tags are markers that point to specific commits in your Git history. They are often used to label release versions (e.g., `v1.0`, `v2.1.3`) in a project's lifecycle. Unlike branches, tags are not meant to change—once set, they usually remain fixed to the commit they were assigned to. There are two main types of tags: lightweight and annotated. Lightweight tags are like bookmarks to a commit, whereas annotated tags are stored as full objects in the Git database with metadata such as the tagger name, date, and a message. This makes annotated tags better suited for marking release points and important milestones.

Tags provide a powerful way to organize your local development workflow, mark stable versions, and navigate through your project's history. Understanding tags is essential for effective version control and project management, whether you're working alone or in a team environment.

### Further Readings and Other Sources

- [Git Tags - Git SCM Documentation](https://git-scm.com/book/en/v2/Git-Basics-Tagging)
- [Pro Git Book, Chapter 2.6: Tagging](https://git-scm.com/book/en/v2/Git-Basics-Tagging)
- [Git Documentation: git-tag](https://git-scm.com/docs/git-tag)
- [Atlassian Git Tutorial: Git Tag](https://www.atlassian.com/git/tutorials/inspecting-a-repository/git-tag)

### Tasks

#### Task 1: Create a Lightweight Tag
1. Initialize a new Git repository in a local directory:
   ```bash
   mkdir my-project
   cd my-project
   git init
   ```
2. Create an initial commit:
   ```bash
   echo "# My Project" > README.md
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

#### Task 3: Work with Multiple Tags and History
1. Create another commit and tag:
   ```bash
   echo "Bug fixes and improvements" >> README.md
   git add README.md
   git commit -m "Update documentation with bug fixes"
   git tag -a v1.1 -m "Minor update with bug fixes"
   ```
2. List all tags in chronological order:
   ```bash
   git tag -l --sort=version:refname
   ```
3. View the history with tag information:
   ```bash
   git log --oneline --decorate
   ```

#### Task 4: Checkout a Tag and Explore History
1. Use a tag to view a specific version of the code:
   ```bash
   git checkout v1.0
   ```
2. Git will put you in a "detached HEAD" state. Verify with:
   ```bash
   git status
   ```
3. Examine the file contents at this tagged version:
   ```bash
   cat README.md
   ```
4. Return to the latest commit:
   ```bash
   git checkout -
   ```

#### Task 5: Delete and Re-tag
1. Delete a local tag:
   ```bash
   git tag -d v0.1
   ```
2. Verify the tag was deleted:
   ```bash
   git tag
   ```
3. Re-tag a different commit (e.g., the latest one):
   ```bash
   git tag v0.1
   ```
4. Create a tag for a specific commit using its hash:
   ```bash
   git log --oneline
   git tag v0.2 <commit-hash>
   ```

#### Task 6: Advanced - Tags with Branches (Only if you've completed [Git Branching and Merging](https://github.com/STEMgraph/2f4d1f4f-a53b-485e-a290-2da6b69353b2))
**Prerequisites:** Complete understanding of Git branches, merging, and merge commits.

1. Create and switch to a feature branch:
   ```bash
   git checkout -b feature/new-feature
   ```
2. Make commits on the feature branch:
   ```bash
   echo "New feature implementation" > new-feature.txt
   git add new-feature.txt
   git commit -m "Implement new feature"
   ```
3. Switch back and merge the feature branch:
   ```bash
   git checkout master
   git merge feature/new-feature
   ```
4. Tag the merge commit:
   ```bash
   git tag -a v2.0 -m "Major release with new feature"
   ```
5. Examine the merge commit and its relationship to the tag:
   ```bash
   git show v2.0
   git log --oneline --graph --all
   ```

### Advice

When working with Git tags, always decide whether you need a lightweight or annotated tag. For most versioning and release workflows, annotated tags are preferred because they include essential metadata such as the tagger's name, email, date, and a descriptive message. Use tags strategically to mark meaningful milestones in your project such as releases, stable versions, or important development phases. Tags are immutable references that help you navigate your project's history and can serve as anchors for build scripts, deployment automation, or changelog generation.

In this exercise, you've learned to work with tags in a linear commit history. However, in real-world development, tags are most commonly applied after merging feature branches into the main branch. [**Your next step should be learning Git branching and merging**](https://github.com/STEMgraph/2f4d1f4f-a53b-485e-a290-2da6b69353b2), which will give you the complete picture of how tags fit into modern development workflows. Once you understand branches, you'll see how tags typically mark stable points after integrating new features through branch merges.

Remember that once created, tags should generally not be moved to different commits—if you need to correct a tag, it's better to delete and recreate it.

