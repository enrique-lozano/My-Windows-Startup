# My Windows startup 💥💯

Set of steps you perform when starting with a new windows device

## Setting my apps 💻​

The first step is to uninstall all the applications that are installed by default on the computer, and that you are not going to use. Once this is done, winget is used to import and download the apps that were previously installed. To install this apps, open a powershell (with admin privileges) and type:

```sh
winget import -i .\winget_backup.json
```

In this case, you have the file winget_backup.json in the _resources_ folder of this repository. If you want to create a new import file because you have new apps or have updated some, type:

```sh
winget export -o .\winget_backup.json
```

If everything has gone correctly, a new import file should have been created in the current directory.

## Setting the terminal ▶️​

From now on it is recommended to **always use the app Windows Terminal**, with the new Powershell by default (not to be confused with the old Windows Powershell 5.x). This new powershell should have been installed in the previous steps, when importing winget json file.

This new powershell includes by default the PSReadLine module, which allows us to have autocomplete among other options.

Optionally we can install [posh-git](https://github.com/dahlbyk/posh-git), by using:

```sh
Install-Module posh-git -Scope CurrentUser -Force
```

In addition, [oh my posh](https://ohmyposh.dev/) will be used, a library to configure your terminal to your liking. This library should have been installed when we did the winget installation.

To start configuring the terminal we must open its configuration file, using the following command:

```sh
notepad $PROFILE
```

If the command fails because the file does not exist we can try with:

```sh
New-Item -Path $PROFILE -Type File -Force
```

Once we have the file open, we add the following lines:

```sh
Import-Module posh-git
oh-my-posh init pwsh
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
Set-PSReadLineKeyHandler -Key DownArrow -Function HistorySearchForward
Set-PSReadLineOption -PredictionSourceHistory
Set-PSReadLineOption -HistoryNoDuplicates
```

Restart your terminal after this and if there are no errors, everything is fine so far.

To fully customize the appearance of your terminal you can type the following:

```sh
Get-PoshThemes
```

This will give you a list of available oh-my-posh themes, along with instructions on how to apply them. You can select one of them via (`Ctrl + Click`), and edit its json file for further customization. In this repository is also the customization json file that I use.

If you don't see all the characters and icons in your terminal it's because you haven't yet installed a compatible font for the terminal. These are called Nerd Fonts, and you can find them [here](https://www.nerdfonts.com/font-downloads).

## Visual Studio Code 🧑‍💻​

There is little to do here. Simply sign in with your github or Microsoft account so that all extensions and settings are synced to their previous state.

To make the font used in the code look more beautiful, the use of [FiraCode](https://github.com/tonsky/FiraCode) is recommended.

Also, if you haven't already done so and if you prefer to use the terminal in vscode, you'll need to set the vscode terminal font to the same as your Windows Terminal, using the (`terminal.integrated.fontFamily`) option. You may also have to change your default vscode terminal.
