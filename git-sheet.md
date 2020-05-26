### Get all commits from latest tag to HEAD

```
git log $(git describe --tags --abbrev=0)..HEAD --pretty=format:"%s"
```


### Push to upstream branch based on current branch (without tracking)

```
git push origin $(git branch --show-current)
```
