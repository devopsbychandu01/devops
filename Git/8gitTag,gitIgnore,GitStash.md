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

git stash
git stash list
git stash pop stash@{1}
git stash pop
git stash apply

