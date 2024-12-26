### What is `git stash`?  
Imagine we’re working on some code, but our work isn’t complete yet. Suddenly, we need to switch to another branch or do something else without committing our changes (because they’re not ready). **`git stash` is like a temporary storage box** where we can "stash" your uncommitted changes and get back to a clean working directory.

### Why use it?  
1. To temporarily save our work without committing it.  
2. To avoid conflicts when switching branches or pulling updates.

### How does it work?  
- **Stash your changes**:  
  Run `git stash`. This saves your changes and resets our working directory to match the last commit.

- **View stashes**:  
  Use `git stash list` to see all stashed changes. Each stash gets a name like `stash@{0}`, `stash@{1}`, etc.

- **Apply a stash**:  
  To retrieve your changes, use `git stash apply`. This applies the changes back but keeps the stash.

- **Pop a stash**:  
  Use `git stash pop` to apply the stash and **remove** it from the stash list.

- **Drop a stash**:  
  If we no longer need a stash, use `git stash drop stash@{0}` to delete it.



### Types of Stashing  
1. **Include untracked files**:  
   Use `git stash -u` if we also want to stash new files (not added to Git yet).  
2. **Create a stash with a message**:  
   `git stash save "WIP: fixing bugs"` helps identify your stash later.



## Scenarios

#### with two different branches:
 -  main and branch2 
 
