# Repo Standards
#projects #github #repo #standards

- Follows [[🔧 Projects/Github Setup/README Standards]].
- Follows [[🔧 Projects/Github Setup/Profile README]].

## General
- **Name:** PascalCase and preferably 2-3 words
- **Description:** 2-3 line description with a descriptive emoji
- **Tags:** relevant technologies
- **Url:** Has demo (if possible)

## Settings
- **Social preview:** If public
- **Features:** Turn off unused feature (i.e. wiki, project)
- Always suggest updating pull request branches

#### Branches
- Default branch is called `main`
- Default branch has protections (if public):
	- Require a pull request before merging
	- Require status checks to pass before merging
		- CodeQL
		- Netlify (if applicable)
		- Vercel (if applicable)
- `dependabot` updates go to `dependencies` branch
	- This branch runs checks to make sure dependency update does not break anything

## Project
- Uses yarn with plug'n'play config

## GitHub Tools
- Use Github Projects to track issues on active projects
- If a package, deploy to npm and to github packages
- Add issues as needed
 
## Automations
- Runs `dependabot` if it uses npm or pip packages
- Runs `codeql`

