# Repo Standards
#github #repo #standards

- Follows [[_README Standards|README standards]].
- Follows []

## Description
- Has 2 line description and tags
- Follows naming convention <projectname.type> or <type.projectname>
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

## Project
- Uses yarn with plug'n'play config

## GitHub Tools
- Use Github Projects to track issues
- If a package, deploy to npm and to github packages
- Add issues as needed
 
## Automations
- Runs `dependabot` if it uses npm or pip packages
- Runs `codeql`

