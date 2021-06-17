# dotfiles

To get started with this, create a `.dotfiles` folder in your home dir

### SSH setup

Use the github guide - https://docs.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent

### SYMLINK files from our `.dotfiles` folder in our home directory

`ln -s ~/.dotfiles/zshrc ~/.zshrc`

Renamed `zshrc` file to not have the dot so it is not hidden

Added Dotbot, with a basic config. - https://github.com/anishathalye/dotbot
To run this we run ` ./install` in the `.dotfiles` directory

---

Originally Inspired by https://github.com/wesbos/dotfiles to create this repo of my dotfiles...Still in progress. 