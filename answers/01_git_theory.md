Git & project foundations

1.Git has three places a change can live: the working directory, the staging area, and the repository.Describe each, and explain what you would lose if the staging area did not exist.
Answer: Working Directory: This is the actual location where the actual files are editing and are exists for working on the local computer
Staging Area: This is an area where the recent changes made on the file of working directory are included in the next commit.
Repository: This is the place where all the commit made are recorded as changes made for future track.
Staging area works as the check point to track the differences between the working directory and repository. So, we will loose the track on the editing and commiting on the file if staging area does not exists.

2. git init and git clone both leave you with a Git repository. Explain what each one actually does,and give a situation where each is the right choice.
Answer:  git init: this command is used to create or initilize the new git repository. It greate .git directory that includes the history and other related git configuration files. This is the right choice while starting new project with git.
Git clone: This command is used to copy or clone the existing git repository from a remote location to the local computer. This is write choice if want to work on existing project that is already in the remote repository and is shared with you.


3.What does a commit store, and why is "committing" not the same as "saving a file"? Why is Git muchless useful if user.name and user.email are unset or wrong?
Answer: Commit store the snapshot the project files in the provided time frame along with the other important metadata about the author’s information, action date and time, meaningful commit message to identify the changes made on that particular commit point and the project file contents.

Saving a file do not track the changes made on it for who, when,what and why. It store the complete file only while committing maintains the version of the file for future track and other details to answer the question like who made the changes, when the changes are made and what and why the changes are made.

If the user.name and user .email are unset the commit action can not be performed because of the missing author details. Where as wrong user.name and user.email are set it hard to identify actually who made the changes on the file in future. 

4.git status, git log, and git diff answer three different questions. State the question each oneanswers, and describe a moment in your workflow where you would reach for each.
Answer: Git status command provide overall status of the git tacked project. This gives which files have been modified, which files are staged and which files are untracked. This is useful before making any commit to identify the status of the files.

Git log command is used for showing the action histories made for the git version controlled project. This is useful while someone involved in the repository wants to identify the actual last update made on the projects and other related information.

Git diff command shows the line by line difference between the git versioned files and the uncommitted file. This command is useful to identify the changes made on the file as compared to the previous file and also helpful for  resoling the conflicts in the commit.

5.Explain what makes a commit message good. Why is "update" a genuine problem for a team sixmonths later, and when is it worth writing a message body rather than just a summary line?
Answer: The good commit message is clear, more precise and actual description or identification about the changes made in the file rather than short and repeated messages.

In long run change message line “update“ can create problem on tracking the changes existing the particular version of the project.

For small changes a summary line is usually enough but message body is worthwhile when the changes need additional context especially when the reason for the change is not obvious for the code. 


Remotes and the everyday workflow 

6.Explain the relationship between your local repository and origin . What do push and pull each move, in which direction, and why is pulling before pushing the habit to build? 
Answer: local repository is the Git repository on local computer. It contains files, commits, branches, and history.
origin is simply the conventional name Git gives to the remote repository that cloned from. It usually points to a repository hosted on a service such as GitHub.

Git push transmits local updates to the remote repository, synchronizing it with new commits. In contrast, git pull retrieves updates from the remote repository and integrates them into the local branch. 

Let us consider the situation remote repository has the recent commit that do not have locally. If you try to push your updates with new commit, the git may reject the your push reject because your local registry is behind the remote git version. This is the reason 


7.git fetch and git pull are not the same command. What is the difference, and when would you deliberately choose fetch ?
Answer: git fetch downloads new commits and other updates from the remote repository into your local Git repository. It updates your remote-tracking branches, such as origin/main, but it does not automatically change your current branch or working files. After fetching, you can inspect what changed before deciding whether to integrate it.

git pull essentially performs a fetch and then integrates the fetched changes into your current branch (typically by merge or rebase, depending on configuration). eg. git pull origin main


Branching, merging, pull requests

8.A branch in Git is often described as "just a pointer." Explain what that means, and explain concretely what goes wrong on a team when everyone commits directly to main .
Answer: Branch is not a copy of the code. It is just a label pointing at a commit just like adding sticky note to remembering things. When new commit are done the existing label is changed to new one.

If everyone make commits directly to main branch
It become hard to identify the author for the changes
The issue of code overwriting may occur
Hard to track the ongoing development or there is a high chances of broken code to deploy in production.
Branches exist so people can work separately before joining their work back together. Skip that, and main turns into chaos.


9.A merge conflict happens when two branches change the same lines of the same file. Explain why Git cannot resolve this automatically, what the <<<<<<< , ======= , >>>>>>> markers mean, and what you must do to finish the merge. 
Answer:Git can auto-merge when two branches change different lines. But if both change the same line, Git doesn't know which one you actually want — that's a human decision, not a coding one.
So it marks both versions in the file:
<<<<<<< HEAD — your version starts here
======= — divider
>>>>>>> branch-name — the incoming version ends here
To fix it: pick (or combine) the correct code, delete the markers, save, git add the file, then commit.
10.You could merge a branch locally with git merge and push. What does opening a Pull Request add that a local merge does not? What belongs in a PR
Answer: A local merge gets the code in, but a PR able to adds the things like tag someone for review the changes, comment on specific lines, record of what and why changes are mode for future reference and adding automated tests. A good PR includes: what changed, why, how to test it, and any related ticket/issue link.
Issues

11.Explain the purpose of labels and assignees on an Issue, and what Fixes #12 in a merged PR does. Why is linking work to Issues better than closing them by hand? Answer: Labels categorize an issue — things like bug, feature, urgent, docs. Makes it easy to filter and see what kind of work is piling up. Assignees show who's responsible for the issue, so it's clear who's supposed to act on it. Fixes #12 in a PR description tells GitHub  "this PR resolves issue #12." When that PR gets merged, the issue auto-closes.

Linking issues is better than closing them by hand as it provide better traceability, no chances of forgetting and also reduces the chances of making mistakes.


Project structure, environments, secrets

12.Why should .gitignore be one of your first commits? If a file is already tracked, does adding it to .gitignore stop Git from tracking it — and if not, what do you do instead?
Answer: .gitignore should be one of your first commits because it tells Git which files should not be tracked before you accidentally add generated files, secrets, virtual environments, or temporary files.

If a file is already tracked, adding it to .gitignore does not stop Git from tracking it. .gitignore mainly affects untracked files. To stop tracking an already-tracked file while keeping it on your computer, use folowing commnd; For example, if the file is .env:
git rm --cached .env
git commit -m "Stop tracking .env"

13.Explain the difference between .env and .env.example , and why they get opposite treatment. If a real API key was committed three weeks ago, why is deleting it in a new commit not a fix, and what should actually be done?
Answer: env contains the real, private configuration values, such as API keys and passwords. It should normally be ignored by Git.  
.env.example contains placeholder values showing what variables a developer needs.

They receive opposite treatment because .env contains secrets, while .env.example contains only safe instructions/placeholders.

If a real API key was committed three weeks ago, deleting it in a new commit is not enough. The old commit still exists in Git history, so someone who has access to the repository may still retrieve the key.The first step is to revoke/rotate the exposed API key immediately and replace it with a new secret. Then remove the secret from the repository and, if necessary, rewrite the repository history to remove the old secret. The important point is that once a secret has been committed, you should assume it is compromised.



14.What problem do a virtual environment and requirements.txt solve together? Why is venv/ itself never committed, when requirements.txt always is? 
Answer: A virtual environment and requirements.txt solve the problem of Python dependencies.A virtual environment provides an isolated place where a project's Python packages are installed. It prevents one project's packages from interfering with another project's environment. Where as requirements.txt records which packages and versions the project needs.

You don't commit venv/ because it contains machine-specific installed files, which can be large and are reproducible from the dependency list.
You do commit requirements.txt because it is the portable description of the project's dependencies.

15.Explain what git push --force does to a shared branch and whose work it can destroy. How does -- force-with-lease behave differently, and why is that safer?
Answer: git push --force tells Git to update the remote branch even when doing so would normally be rejected because the remote history has diverged.This can destroy other developers' commits that were on the shared remote branch but aren't in your rewritten local history.

git push --force-with-lease is safer because Git checks that the remote branch is still at the state you last knew about. If someone else has pushed new work since then, Git refuses the force push instead of silently overwriting it.
