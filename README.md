# dotfiles

## Restore from this repo Instructions

1. `xcode-select --install` (Command Line Tools are required for Git and Homebrew)
2. `git clone https://github.com/ayoungh/dotfiles.git ~/.dotfiles`. We'll start with `https` but switch to `ssh` after everything is installed.
3. `cd ~/.dotfiles`
4. If necessary, `git checkout <another_branch>`.
5. Do one last Software Audit by editing [Brewfile](Brewfile) directly.
6. You will need to [install Homebrew](https://brew.sh/)
7. Run [`./install`](install)
8. Restart computer.
9. Setup up Dropbox (use multifactor authentication!) and allow files to sync before setting up dependent applications. Alfred settings are stored here. Mackup depends on this as well (and thus so do Terminal and VS Code).
10. [Generate ssh key](https://help.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh), add to GitHub, and switch remotes.

    ```zsh
    # Generate SSH key in default location (~/.ssh/config)
    ssh-keygen -t ed25519 -C "404328+ayoungh@users.noreply.github.com"

    # Start the ssh-agent
    eval "$(ssh-agent -s)"

    # Create config file with necessary settings
    << EOF > ~/.ssh/config
    Host *
      AddKeysToAgent yes
      UseKeychain yes
      IdentityFile ~/.ssh/id_rsa
    EOF

    # Add private key to ssh-agent 
    ssh-add -K ~/.ssh/id_rsa

    # Copy public key and add to github.com > Settings > SSH and GPG keys
    pbcopy < ~/.ssh/id_rsa.pub

    # Test SSH connection, then verify fingerprint and username
    # https://help.github.com/en/github/authenticating-to-github/testing-your-ssh-connection
    ssh -T git@github.com

    # Switch from HTTPS to SSH
    git remote set-url origin git@github.com:ayoungh/dotfiles.git
    ```


### Manual Steps

#### Alfred

1. `System Preferences > Keyboard > Shortcuts > Spotlight > Show Spotlight search (cmd+space)` uncheck.
2. `Alfred Preferences > Powerpack` add License.
3. `Alfred Preferences > General > Request Permissions`.
4. `Alfred Preferences > General > Alfred Hotkey` change to `cmd+space`.
5. `Alfred Preferences > Advanced > Set preferences folder` and set to `~/Dropbox/dotfiles/Alfred`.


#### How to SYMLINK files from our `.dotfiles` folder in our home directory

`ln -s ~/.dotfiles/zshrc ~/.zshrc`

Renamed `zshrc` file to not have the dot so it is not hidden

We now use Dotbot for this, so we do not have to manually do it. 

Added Dotbot, with a basic config.
[Dotbot Repo](https://github.com/anishathalye/dotbot)


#### Homebrew 

We now use a Brewfile to install all apps and tools - In the `.dotfiles` directory run `brew bundle dump --force --describe` to get a new updated brewfile with descriptions




---


## Decommission Computer

[Create a bootable USB installer for macOS](https://support.apple.com/en-us/HT201372).

Software audit:
- Uninstall unwanted software (e.g. GarageBand, iMovie, Keynote, Numbers, Pages)
- Install missing software (look at `/Applications`, panes in System Preferences , maybe `~/Applications`, etc.)

Backup / sync files:
- Commit and Push to remote repositories
- Run `code --list-extensions > vscode_extensions` from `~/.dotfiles` to export [VS Code extensions](vscode_extensions)
- Time Machine
- Dropbox / Google Drive
- Manual Backups (external drives, redundant cloud services)
- Contacts, Photos, Calendar, Messages (Google, iCloud)
- etc.

Deactivate licenses or logout:
- Google Drive (`Preferences > Settings > Disconnect`)
- Dropbox (`Preferences > Account > Unlink`)
- Sign Out of App Store (`Menu > Store > Sign Out`)
- iTunes, etc.





---

Originally Inspired by https://github.com/wesbos/dotfiles to create this repo of my dotfiles...and then brought the course and I ***learned*** about dotfiles at [dotfiles.eieio.xyz](http://dotfiles.eieio.xyz), and so can you!
