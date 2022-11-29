# Repo Standards
#github #repo

- Follows [[readme-standards|README standards]].

## Description
- Has 2 line description and tags
- Follows naming convention <projectname.type>
- Has url to demo (if possible)

## Branches
- Default branch is called `main`
- Default branch has protections:
	- Require a pull request before merging
	- Require status checks to pass before merging
		- CodeQL
		- Netlify (if applicable)
		- Vercel (if applicable)
	- Do not allow bypassing the above settings
- `dependabot` updates go to `develop` branch

## Project
- Uses yarn with plug'n'play config
- Does not have `frontend/` and `backend/` separations
 
## Automations
- Runs `dependabot` if it uses npm or pip packages
- Runs `codeql`