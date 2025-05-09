# Create New Repo
#git

```bash
# First create a new repo on github
# Then run the following commands
echo "# test" >> README.md
git init
git add README.md
git commit -m "Initial commit"
git branch -M main
git remote add origin <repo url>
git push -u origin main
```