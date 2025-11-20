My Arch Linux Dotfiles Repository

This guide explains how to install and manage your configuration files using the provided install.sh script.

Required Repository Structure

The install.sh script relies on this specific nested structure within a top-level directory (where install.sh lives). You should clone your repository into a convenient location (e.g., ~/.dotfiles).

my-dotfiles-repo/
├── install.sh         # The installation script (run this)
├── README.md          # This file
└── Dotfiles/
    ├── Config/
    │   ├── matugen/      -> Symlinked to ~/.config/matugen
    │   ├── waybar/       -> Symlinked to ~/.config/waybar
    │   ├── hyprland.conf -> Symlinked to ~/.config/hypr/hyprland.conf
    │   ├── kitty.conf    -> Symlinked to ~/.config/kitty/kitty.conf
    │   ├── rclone.conf   -> Symlinked to ~/.config/rclone/rclone.conf
    │   └── base.yml      # Ignored by the script
    ├── Fonts/
    │   └── *.ttf, *.otf  -> Copied to /usr/share/fonts/ttf/ (Requires SUDO)
    ├── Music/
    │   └── *.mp3         -> Copied to ~/Music/
    ├── Pictures/
    │   └── *.jpg         -> Copied to ~/Pictures/
    └── Scripts/
        └── *.sh          -> Copied to ~/.local/bin/


Installation Steps

These instructions assume you are on an Arch Linux-based distribution and have git installed.

1. Clone the Repository

Clone this repository and navigate to the root directory (where install.sh is located).

git clone <your-repo-url> ~/.dotfiles
cd ~/.dotfiles


2. Run the Installation Script

The install.sh script is designed to automate the entire setup process in a safe manner:

Package Installation: Installs matugen, waybar, cmus, dunst, mpv, rclone, starship, yazi, and btop using pacman -S --noconfirm.

Backup: Backs up any existing configuration files found in your home directory to a timestamped folder (e.g., ~/.dotfiles_backup_YYYYMMDD_HHMMSS).

Symlinking: Creates symbolic links for all configuration files to ensure future updates only require a git pull.

Asset Copying: Copies fonts (requires sudo for system installation and fc-cache), media, and local scripts.

Execution:

# Make the script executable
chmod +x install.sh

# Run the script
./install.sh


3. Finalize

Once the script finishes:

Reload Shell: If you installed starship or other shell configurations, you may need to reload your shell.

exec $SHELL


Reboot/Log Out: For configurations related to desktop environments (like Waybar and Hyprland), you will need to log out and log back in, or reboot, to ensure the new files are correctly loaded.
