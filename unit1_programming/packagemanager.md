# Installing a package manager

A *package manager* is a piece of software that runs on the command line and makes it easier to install lots of software quickly without lots of clicking. We are going to install one now!

You'll need to start by opening your [command line](commandline.md)

### Windows Users
Install [chocolatey](https://chocolatey.org/docs/installation) by copying and pasting these commands (in powershell, you paste simply by right-clicking). You may need to answer some questions and follow some instructions, so keep an eye on it!
```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force 
iex ((New-Object System.Net.WebClient).DownloadString('https://chocolatey.org/install.ps1'))
refreshenv
```

Once this is installed, you should be able to type `choco --version` and get a response like `0.10.13`

### Mac Users
Install [homebrew](https://brew.sh) by copying-and-pasting this command. You'll have to answer some questions, so keep an eye on it!
```powershell
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```

Once it is isntalled, you should be able to type a command like `brew --version` and get a response (not an error!)