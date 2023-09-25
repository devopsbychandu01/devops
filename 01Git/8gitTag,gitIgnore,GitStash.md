git ignore: This means we can ignore some files

#shows all the tags
git tag
git tag -l "v1.*"

git tag <tagName>

git tag <tagName> <commitID>

git show <tag>

git push origin <tagName>

git tag -d <tagName>

git push origin --delete <tagName>


## Git Stash
## edit some file on the branch, not create files. The edit code is not required for this sprint but it required for the future sprint. In that situation we need stash memory.
vi file1 --> update some information
git status --> only modified files will go to stash.
git Stash
git stash list
git status
vi file2 --> update some information
git status
git Stash
git status
git stash list



## number 0 is the recent stash info ##


git stash apply ## stash will be not removed but changes will come back to local ##
git stash apply
git stash apply stash@{1} ## the changes of both stash memory 0 and 1 will appear. ##
git stash drop 0 ## delete the stash memory 0 ##
git stash clear ## this will clear the entire stash memory ##
git stash pop ## stash will be removed also changes will come back to local ##
git stash pop ## default 0 will be popped up ##
git stash pop stash@{1} ## both stash memory 0 and 1 will popped up ##
git stash pop 1


git stash
git stash list
git stash pop stash@{1}
git stash pop
git stash apply

