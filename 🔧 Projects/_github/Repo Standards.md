# Repo Standards
#github #repo #standards

- Follows [[_README Standards|README standards]].
- Follows []

## General
- **Name:** PascalCase and preferably 2-3 words
- **Description:** 2-3 line description with a descriptive emoji
- **Tags:** relevant technologies
- **Url:** Has demo (if possible)

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

