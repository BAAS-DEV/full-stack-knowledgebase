# Setup - Windows 10/11

Here is a comprehensive tutorial on setting up a Windows 10/11 operating system for TypeScript development with Visual Studio Code (VSCode) and the installation requirements:

## Prerequisites
Before you begin, you will need to have the following installed on your Windows system:

1. Git: Git is a version control system that is used to manage and track changes to your code. You can download and install Git from the Git website.

2. nvm: Node Version Manager (nvm) is a command-line tool that allows you to easily install and manage multiple versions of Node.js on your Windows system. This is useful if you want to test your code against different versions of Node.js, or if you want to switch between stable and experimental versions of Node.js.

## Installing nvm

To install nvm on Windows, follow these steps:

Open a command prompt window and run the following command to download the nvm installation script:
```Powershell
@"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "iex ((New-Object System.Net.WebClient).DownloadString('https://raw.githubusercontent.com/coreybutler/nvm-windows/master/install.ps1'))" && SET "PATH=%PATH%;%ALLUSERSPROFILE%\nodejs"
```

Close the command prompt window and open a new one to apply the changes.

Run the following command to verify that nvm is installed:

```nvm --version```

### Using nvm
To use nvm, you can use the following commands:

```nvm install <version>:``` Install the specified version of Node.js. For example, to install the latest stable version of Node.js, you can run nvm install node.

```nvm use <version>```: Switch to the specified version of Node.js. For example, to switch to the latest stable version of Node.js, you can run nvm use node.

```nvm ls```: List all installed versions of Node.js.

```nvm ls-remote```: List all available versions of Node.js that can be installed.

```nvm uninstall <version>```: Uninstall the specified version of Node.js.

---

For example, to install the latest stable version of Node.js and switch to it, you can run the following commands:

```nvm install node```

```nvm use node```

---

To switch back to the default version of Node.js that is installed on your system, you can run the following command:

```nvm use system```


3. Node.js: Node.js is a JavaScript runtime that is used to execute your TypeScript code. You can download and install Node.js from the Node.js website.

4. Visual Studio Code: A free, standard ide.

### Installing Visual Studio Code
To install Visual Studio Code on Windows, follow these steps:

1. Download the VSCode installer from the VSCode website.

2. Run the installer and follow the prompts to install VSCode.

If the installation was successful, you should see the VSCode icon in the start menu.

#### Installing the TypeScript extension
To install the TypeScript extension for VSCode, follow these steps:

Open VSCode and click on the "Extensions" icon in the left sidebar.

In the search bar, type "TypeScript" and press Enter.

Click on the "Install" button for the "TypeScript" extension.

Wait for the installation to complete and then click on the "Reload" button to apply the changes.

Configuring TypeScript in VSCode
To configure TypeScript in VSCode, follow these steps:

Open VSCode and create a new project by clicking on the "File" menu and selecting "Open Folder".

In the terminal window, navigate to the project directory and run the following command to initialize a new TypeScript project:

Copy code
tsc --init
This will create a tsconfig.json file in your project directory. Open the file and modify the compiler options to match your project needs. For example, you can set the target option to "ES6" to specify that you want to use the latest version of JavaScript.

In the terminal window, run the following command to install the TypeScript definitions for the Node.js runtime:

```
npm install @types/node
```

Open a TypeScript file in VSCode and you should see syntax highlighting and code completion for TypeScript.

#### Debugging TypeScript in VSCode

To debug TypeScript in VSCode, you need to create a launch configuration file that specifies how to run your code. You can do this by following these steps:

Open VSCode and click on the "Debug" icon in the left sidebar.

Click on the "Create a launch.json file" button.

In the dropdown menu, select "Node.js" as the environment.

Modify the launch configuration to match your project needs. For example, you can set the program option to the path of your TypeScript entry point file, and the outFiles option to the path of the compiled JavaScript files.

To start debugging, click on the "Start Debugging" button in the Debug toolbar.

Set breakpoints in your TypeScript code by clicking on the left margin of the editor window.

Run your code and the debugger will stop at the breakpoints you set.

Use the debugger controls in the Debug toolbar to step through your code, inspect variables, and evaluate expressions.

