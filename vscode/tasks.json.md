```json
{
  "version": "2.0.0",
  "tasks": [
    {
      "label": "Start Admin",
      "command": "yarn",
      "args": ["develop"],
      "isBackground": true,
      "options": {
        "cwd": "${workspaceFolder}/admin"
      },
      "presentation": {
        "group": "none"
      },
      "icon": {
        "id": "debug-start",
        "color": "terminal.ansiBlue"
      },
      "problemMatcher": []
    },
    {
      "label": "Start Frontend",
      "command": "yarn",
      "args": ["develop"],
      "isBackground": true,
      "presentation": {
        "group": "none"
      },
      "icon": {
        "id": "debug-start",
        "color": "terminal.ansiMagenta"
      },
      "problemMatcher": []
    },
    {
      "label": "Start",
      "dependsOn": ["Start Admin", "Start Frontend"],
      "icon": {
        "id": "debug-start",
        "color": "terminal.ansiGreen"
      }
    },
    {
      "label": "Start Postgres",
      "type": "shell",
      "command": "pg_ctl",
      "args": ["restart", "-D", "/usr/local/var/postgres"],
      "isBackground": true,
      "problemMatcher": [],
      "runOptions": {
        "runOn": "folderOpen"
      },
      "presentation": {
        "reveal": "silent",
        "panel": "dedicated",
        "showReuseMessage": false
      },
      "icon": {
        "id": "database",
        "color": "terminal.ansiYellow"
      }
    }
  ]
}

```