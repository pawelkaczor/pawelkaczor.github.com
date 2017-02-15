# myrepos && vcsh && prezto - User Guide

This document serves as a single source of information related to configuration of **myrepos & vcsh & prezto (zsh)** combo.

# myrepos

https://github.com/joeyh/myrepos

**mr** - a tool to manage all your version control repos

**mr** is configured by .mrconfig file, which list the repositories.

**mr** supports vcsh repositories!

#### vcsh repository configuration file - example

```
[$HOME/.config/vcsh/repo.d/documents.git]
checkout = vcsh clone $DOCUMENTS_GIT_REPO documents
vcsh_status = vcsh documents status ~/Documents
grep = ack-grep "$@"
```

---
 * **Note**

    **mr grep** will not work for vcsh repository unless the **grep** command is defined (as shown above).
    
    Make sure **ack-grep** is installed. 

    Leave empty line at the end of the repo configuration file! This is necessary because the repo configs are **included** from the ~/.mrconfig file.

    Define **vcsh_status** only if you do not generate .gitignore file (see vcsh section for more details).

---


#### Commands

- **mr ci** - Commits changes to each repository. (By default, changes are pushed to the remote repository too, when using distributed systems like git) The optional -m parameter allows specifying a commit message.


# vcsh

https://github.com/RichiH/vcsh

vcsh - Version Control System for $HOME - multiple Git repositories in $HOME

>> vcsh was designed with myrepos, a tool to manage Multiple Repositories, in mind and the two integrate very nicely. The myrepos tool (mr) has native support for vcsh repositories


vcsh repositories are by default located under **$XDG_CONFIG_HOME/vcsh/repo.d**

#### Ignored files

>> vcsh can generate per-repo .gitignore files (in .gitignore.d/<repo_name>) by running vcsh write-gitignore <repo_name>. That will cause each git repo to ignore anything that is not specifically tracked in itself. This covers not only the git status use case but a few others as well.

---
* **Note**

   Do not run **vcsh write-gitignore** for a repo if you expect new files to arrive often in that repo. 

   If you do not generate .gitignore file for a repo, make sure you define **vcsh_status** command (see mr section above). Otherwise **mr st** and **vcsh status** commands will report many untracked files (because different git repos share the same ($HOME) working directory) - if I remember correctly. 

   Once you run **vcsh write-gitignore** for a repo, newly added files will not be tracked automatically! You will have to add them manually to the repo!. The git add command can be used to add ignored files with the -f (force) option.

   After adding a file to the repo manually, you should rerun **vcsh write-gitignore** command.

---

#### vcsh-modules

https://github.com/lierdakil/vcsh-modules/wiki

vcsh-modules is intended for improving support of **git submodules** in vcsh.

# Prezto

https://github.com/sorin-ionescu/prezto

My fork: https://github.com/pawelkaczor/prezto

Prezto is a configuration framework for Zsh.

The Prezto git repository should be cloned to **~/.zprezto** directory. It contains **git submodules** that point to external git repositories hosting **Prezto modules**. 

---
 * **Note**

   To update the Prezto modules run: ```git submodule update --init --recursive``` from ~/.zprezto directory.

   You should fork the Prezto and clone from the fork.

   Add **upstream** remote (eg. https://github.com/sorin-ionescu/prezto) to your local prezto git repository if you cloned from your fork, so you can merge changes from the upstream.    

   For some reason I have not configured Prezto as a vcsh repository. Perhaps because of some issues with **git submodules**. **TODO**: update **vcsh-modules** and try to configure Prezto as a vcsh repository.

---
  