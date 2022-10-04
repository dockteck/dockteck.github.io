# Github Pages
```
type nul > .gitignore
echo node_modules/ _book >> .gitignore

git init
git add --all
git commit -m "first commit"
git remote add origin https://github.com/{YOUR-GITHUB-ACCOUNT}/{YOUR-GITHUB-PROJECT}.git
git branch -M master
git push -u origin master


または


git remote add origin https://github.com/(user name)/(repository name).git

npm run deploy
```