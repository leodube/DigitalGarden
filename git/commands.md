# Commands
#git #todo:format
A collection of useful git commands. When using these commands, only copy the text AFTER the “$”.

Initializing Git
	1. In empty directory run command: $ git init 
	2. Verify by running: $ ls -a

Git Tracking
	1. To check what Git has done to changes, run: $ git status
	2. If there is a new file added to the project directory, run: $ git add <name>
	3. To commit new changes to project directory, run: $ git commit -m 	“<description of changes>”
	4. To check the commit was successful, run: $ git log
	5. To tell Git where the remote repository is, use command: $ git remote add <short nickname> <url of repository>
	6. Check successful remote add: $ git remote -v
	7. Push code to repository: $ git push <nickname> master

Cloning from Git
	1. If you have a properly set up repository, you can clone it using: $ git clone <repository url>


Suggested Usage
	0. Create a remote project repository on github.com
	1. Initialize git in project directory: $ git init
	2. Add files to git: $ git add <name>
	3. Commit regularly: $ git commit -m “<description of changes>”
	4. Add remote repository: $ git remote add <short nickname> <url of repository>
		(you only need to do this once per directory)
	5. Push code to repository: $ git push <nickname> master

Tips
	* $ git add .
		Stages new and modified, without deleted

	* $ git add -u
		Stages modified and deleted, without new

	* $ git add -A
		Stages All

	* $ git clone <url>
		Pulls a repository from github
