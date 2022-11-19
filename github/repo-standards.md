# Repo Standards
- Follows README standards
- Has 2 line description and tags
- Follows naming convention
- Has url to demo (if possible)

## Branches
- Default branch is called `main`
- Deploys are done from branch called `production` 
- Default branch has protections:
	- Require a pull request before merging

## Automations
- Runs `dependabot` if it uses npm packages
- Runs `codeql`