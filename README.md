## Git Command Line



### **Git global configuration**

To used view git contributions on graph by user commit

```
git config --global user.name "YOUR NAME"
git config --global user.email "YOUR EMAIL ADDRESS"
```



### **Find and restore deleted files with git**

Don’t be afraid to delete files from your git repository. You can get restore them. You can even search for a string in a deleted file. Here is how to find a deleted file and its commit:

```
git log --diff-filter=D --summary                  # all deleted files ever
git log --diff-filter=D --summary .                # all deleted files in cwd 
git log --diff-filter=D --author=Batman --summary  # all files deleted by Batman
```

How to restore a deleted file:

`git checkout <commit>~1 <filename>`




###  **Search the contents of deleted files**

But lets say I don’t remember the filename of that file I deleted in a fit of cleanup passion. I do remember the name of one of the functions in it though. Here is how to deal with that. Search the contents of all files that have ever existed in git for a string:


`git log --summary -S<string> [<path/to/file>] [--since=2009.1.1] [--until=2010.1.1]`

Another way to do this:

`git rev-list --all | xargs git grep 'string'`



###  **Git branching and push, pull**

```
git branch <branch-name>         			# create git branch
git branch -d <branch-name>				# used for`delete branch locally
git branch -m <new_name>				# Rename the current local branch
git push origin -u <new_name>				# Push the <new_name> local branch
git push origin --delete <branch-name>			# used for delete remote branch
git checkout <branch-name>				# login in created branch 
git branch						# used see all git branches
git add .						# add changes code on the local
git commit -m “git push in dev branch”   		# used for git commit
git commit -m "Test" --date=format:short:2020-11-06  	# used for commit specific date
git commit --amend -m "New commit message"  		#Changing an Older or Multiple Commits
git push origin dev	 				# used for push in dev branch
git checkout master 					# used for loing master branch
git fetch origin dev					# used for fetching code from dev branch
git merge dev						# used for code merge with dev in mister branch
git add .						# used for adding all updated code
git commit -m “push in master branch”  			# used for git commit 
git push origin master 					# used for push code in master branch
```



### **Git ignore**

Create a **.gitignore** file for your repository.

```
$ touch .gitignore
```

If you want to ignore a file that is already checked in, you must untrack the file before you add a rule to ignore it. From your terminal, untrack the file.

```
$ git rm --cached <FILENAME>
```



###  **Git logs**

`git log --oneline --graph					# to see git online logs with graps`



### **Git tagging**

#####  how to create a tag in a GitHub repository:

`git tag <v1.0>								# used for create new tag`

This will create a local tag with the current state of the branch you are on. When pushing to your remote repo, tags are NOT included by default. You will need to explicitly say that you want to push your tags to your remote repo:

`git push origin –tags						# used for push all tag in remote repo`

**if you just want to push a single tag:**

`git push origin <tag>						# used for push single repository`




Listing the existing tags in Git is straightforward. Just type `git tag` (with optional `-l` or `--list`):

```
$ git tag
v1.0
v2.0
```

This command lists the tags in alphabetical order; the order in which they are displayed has no real importance.

You can also search for tags that match a particular pattern. The Git source repo, for instance, contains more than 500 tags. If you’re interested only in looking at the 1.8.5 series, you can run this:

```
$ git tag -l "v1.8.5*"
v1.8.5
v1.8.5-rc0
v1.8.5-rc1
v1.8.5-rc2
v1.8.5-rc3
v1.8.5.1
v1.8.5.2
v1.8.5.3
v1.8.5.4
v1.8.5.5
```



###  **Annotated Tags**

Creating an annotated tag in Git is simple. The easiest way is to specify `-a` when you run the `tag` command:

```
$ git tag -a v1.4 -m "my version 1.4"
$ git tag
v0.1
v1.3
v1.4
```

The `-m` specifies a tagging message, which is stored with the tag. If you don’t specify a message for an annotated tag, Git launches your editor so you can type it in.

You can see the tag data along with the commit that was tagged by using the `git show` command:

```
$ git show v1.4
```



### **Deleting Tags**

To delete a tag on your local repository, you can use `git tag -d <tagname>`. For example, we could remove our lightweight tag above as follows:

```
$ git tag -d v1.4-lw
```


