# Repo Standards
#github #repo

- Follows README standards
- Has 2 line description and tags
- Follows naming convention
- Has url to demo (if possible)

## Branches
- Default branch is called `main`
- Default branch has protections:
	- Require a pull request before merging
	- Require status checks to pass before merging
		- CodeQL
		- Netlify (if applicable)
		- Vercel (if applicable)
- `dependabot` updates go to `develop` branch

## Automations
- Runs `dependabot` if it uses npm or pip packages
- Runs `codeql`