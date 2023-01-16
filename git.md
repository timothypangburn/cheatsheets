#GIT Command and Notes

## Create a Pull Request
1. Find a project you want to contribute to.
2. Fork it.
3. Clone it to your local system.
4. Add "upstream" repo - the original you forked from to allow eaiser PM back
5. Make a new branch.
6. Make your changes.
7. Push it back to your repo.
8. Click the Compare & pull request button.
9. Click Create pull request to open a new pull request.

## Git Push and Merge work between remotes with no central hub
1. Create a branch of your work 
    $ git checkout -b <newbranchname>
2. Push branch to upstream remote ( this assumes you have the remote setup. See remote setup)
    $ git push -u <upstreamRemoteName> <newbranchname>`
3. Merge your branch back into your master 
    $ git checkout master
    $ git merge <newbranchname>
4. On remote machine do the same
    $ git checkout master
    $ git merge <newbranchname>

## Git - Fetch Remote Branch
    $ git fetch <upstreamRemoteName> <upstreamBranchName>:<localBranchName>
  
## Do not ignore but do further track changes to a file
```
$ git update-index --assume-unchanged <file>
```
### To start tracking it again
```
$ git update-index --no-assume-unchanged <file>
```
