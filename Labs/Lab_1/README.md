# Lab 1

![Alt Text](https://github.com/JohnMFB/CPE-322/blob/main/Assets/Lab_1.png)

Installed

- 7z2301-x64.exe
- gtkwave-3.3.117.tar.gz
- ghdl-MINGW32.zip V3

## Setup

<img width="596" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/50668e40-e879-430d-aa5f-9f377270720d">

### Environment Path 

<img width="276" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/3b99c825-bc2d-47e7-b3d2-d1ce6f4428d3">

Manual installation of ghdl and gtkwave within root dir not being seen by vscode

<img width="417" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/83acd850-975f-4d17-a0f6-619911f80fd9">

<details>
  <summary>Click to see my settings.json</summary>

{
  "[jsonc]": {
    "editor.defaultFormatter": "vscode.json-language-features"
  },
  "[cpp]": {
    "editor.defaultFormatter": "ms-vscode.cpptools"
  },
  "C_Cpp.default.cppStandard": "gnu++14",
  "C_Cpp.errorSquiggles": "enabled",
  "C_Cpp.inactiveRegionOpacity": 0.5,
  "C_Cpp.clang_format_fallbackStyle": "Google",
  "editor.tabSize": 2,
  "editor.detectIndentation": false,
  "editor.defaultFormatter": "ms-vscode.cpptools",
  "C_Cpp.clang_format_style": "Google",
  "terminal.integrated.shell.windows": "C:\\msys64\\usr\\bin\\bash.exe", 
  "terminal.integrated.env.windows": {
    "MSYSTEM": "MINGW64",
    "CHERE_INVOKING": "1",
    "workspaceFolder": "${workspaceFolder}",
    "MSVSCODE": "1"
  },
  "[python]": {
    "editor.defaultFormatter": "ms-python.python"
  },
  "[json]": {
    "editor.defaultFormatter": "vscode.json-language-features"
  },
  "remote.SSH.showLoginTerminal": true,
  "launch": {
    "version": "0.2.0",
    "configurations": [
      {
        "name": "(gdb) Launch",
        "type": "cppdbg",
        "request": "launch",
        "program": "${fileDirname}\\${fileBasenameNoExtension}.exe",
        "args": [],
        "stopAtEntry": false,
        "cwd": "${workspaceFolder}",
        "environment": [],
        "externalConsole": false,
        "MIMode": "gdb",
        "miDebuggerPath": "C:\\msys64\\mingw64\\bin\\gdb.exe",
        "setupCommands": [
          {
            "description": "Enable pretty-printing for gdb",
            "text": "-enable-pretty-printing",
            "ignoreFailures": true
          }
        ],
        "preLaunchTask": "C/C++: g++.exe build active file"
      }
    ]
  },
  "C_Cpp.default.browse.path": [
    "C:\\msys64\\mingw64\\x86_64-w64-mingw32\\include"
  ],
  "terminal.integrated.profiles.windows": {
    "PowerShell": {
      "source": "PowerShell",
      "icon": "terminal-powershell"
    },
    "Command Prompt": {
      "path": [
        "${env:windir}\\Sysnative\\cmd.exe",
        "${env:windir}\\System32\\cmd.exe"
      ],
      "args": [],
      "icon": "terminal-cmd"
    },
    "Git Bash": {
      "source": "Git Bash"
    },
    "bash (MSYS2)": {
      "path": "C:\\msys64\\usr\\bin\\bash.exe",
      "args": [
        "--login",
        "-i"
      ]
    }
  },
  "terminal.integrated.defaultProfile.windows": "bash (MSYS2)",
  "redhat.telemetry.enabled": true,
  "explorer.compactFolders": false,
  "terminal.integrated.automationProfile.linux": {}
}

</details>

pacman -Syu
pacman -S mingw-w64-x86_64-ghdl
pacman -S mingw-w64-x86_64-gtkwave

## Post Upgrade

<img width="593" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/854343cf-3f3f-4ff4-abab-675d8f6f02e9">

## Installing ghdl Pacman

<img width="603" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/58f6329c-d188-463f-969a-ed84e1562bf0">

## Installing gtkwave Pacman

<img width="602" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/96bb6062-d330-4f01-a84f-c8d15a39c80f">

<img width="587" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/48a38446-67dd-4acf-8f23-91455b09df55">

<img width="127" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/2223b81d-3991-4791-bb57-c074e6d684cf">

## Success

<img width="594" alt="image" src="https://github.com/JohnMFB/CPE-322/assets/122575719/8df7aa8e-c72a-4a03-b782-487668f72714">

