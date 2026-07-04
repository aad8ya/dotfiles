# Dotfiles

My personal configuration files for Neovim and Tmux, managed using `gnu-stow`.

## First-Time Setup (Prerequisites)

Before linking, ensure `stow` is installed on your machine.

* **macOS:** `brew install stow`
* **Ubuntu/Debian:** `sudo apt install stow`

## Installation / Cloning

1. Clone this repository directly into a `.dotfiles` directory in your home folder:
   ```bash
   git clone https://github.com/aad8ya/dotfiles.git ~/.dotfiles
   ```

2. Navigate into the repository:
   ```bash
   cd ~/.dotfiles
   ```

3. Symlink the configurations using `stow`:
   ```bash
   stow nvim
   stow tmux
   ```

   *Note: If you get a conflict error about existing files, back up and delete the conflicting files in your `~/.config` or `~` directory, then run the stow commands again.*

4. Install the Tmux Plugin Manager (TPM):
   ```bash
   git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
   ```

5. Start (or reload) tmux, then install the plugins by pressing `Ctrl+s I` (the prefix in this config is remapped from `Ctrl+b` to `Ctrl+s`), followed by capital `I`:
   ```
   Ctrl+s I
   ```

   *This reads the `set -g @plugin '...'` lines in `~/.tmux.conf` and installs each plugin into `~/.tmux/plugins/`.*

## How to Unstow (Removing Symlinks)

If you need to safely remove the symlinks from your home directory without deleting the actual configuration files:

1. Navigate to the repository:
   ```bash
   cd ~/.dotfiles
   ```

2. Pass the delete (`-D`) flag to stow:
   ```bash
   stow -D nvim
   stow -D tmux
   ```

## Adding New Configurations

To track a new configuration file (e.g., a `.zshrc` file):

1. Create a folder for it in the repo matching your home directory structure (e.g., `~/.dotfiles/zsh/.zshrc`).
2. Move your local file into that folder.
3. Run `stow zsh` from the repository root to link it back.

