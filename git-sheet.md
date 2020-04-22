### Get all commits from latest tag to HEAD

```
git log $(git describe --tags --abbrev=0)..HEAD --pretty=format:"%s"
```
