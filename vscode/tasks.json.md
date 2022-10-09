```json
{
  "version": "2.0.0",
  "tasks": [
    {
      "label": "Clean",
      "type": "npm",
      "script": "clean",
      "icon": {
        "id": "wrench",
        "color": "terminal.ansiWhite"
      }
    },
    {
      "label": "Build Admin",
      "command": "yarn",
      "args": ["build"],
      "options": {
        "cwd": "${workspaceFolder}/admin"
      },
      "group": {
        "kind": "build"
      },
      "presentation": {
        "group": "build"
      },
      "icon": {
        "id": "tools",
        "color": "terminal.ansiBlue"
      }
    },
    {
      "label": "Build Frontend",
      "command": "yarn",
      "args": ["build"],
      "group": {
        "kind": "build"
      },
      "presentation": {
        "group": "build"
      },
      "icon": {
        "id": "tools",
        "color": "terminal.ansiMagenta"
      }
    },
    {
      "label": "Build",
      "dependsOn": ["Build Admin", "Build Frontend"],
      "dependsOrder": "sequence",
      "group": {
        "kind": "build",
        "isDefault": true
      },
      "icon": {
        "id": "tools",
        "color": "terminal.ansiGreen"
      }
    },
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
      "label": "Build and Start",
      "dependsOn": ["Build", "Start"],
      "dependsOrder": "sequence",
      "icon": {
        "id": "run-all",
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