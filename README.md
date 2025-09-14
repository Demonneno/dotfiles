tmux Configuration README
This README documents the configuration file (.tmux.conf) for tmux, a terminal multiplexer, optimized for use on Pop!_OS or similar Linux distributions. It enhances productivity with custom key bindings, plugin support, and a visually appealing status bar.
Overview
The .tmux.conf file customizes tmux behavior, including:

Global access to Neovim integration.
Custom key bindings for pane navigation and synchronization.
A colorized status bar with weather information and current path.
Integration with the Tmux Plugin Manager (TPM) for additional functionality.

Prerequisites

tmux: Ensure tmux is installed (e.g., sudo apt install tmux on Pop!_OS).
Neovim: Optional, but assumed for certain workflows (installed via sudo apt install neovim or manually).
TPM (Tmux Plugin Manager): Install by cloning the repository:git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm


Dependencies: Install xsel for clipboard support (sudo apt install xsel).
Plugins: Ensure internet access to download plugins on first run.

Setup Instructions

Backup Existing Configuration:
cp ~/.tmux.conf ~/.tmux.conf.bak


Install Configuration:Save the provided .tmux.conf content to ~/.tmux.conf using:
nvim ~/.tmux.conf


Install TPM and Plugins:

Start tmux by running tmux.
Press Ctrl-a (prefix) followed by I (capital i) to fetch and install plugins.
Reload tmux configuration with Ctrl-a r to apply changes.


Apply Changes:Reload the configuration manually with:
tmux source-file ~/.tmux.conf



Configuration Details
Key Bindings

Reload Config: Ctrl-a r reloads .tmux.conf and displays "Config Reloaded!".
Copy to Clipboard: Uses xsel -ib for copy-pipe in copy mode (bindings: C-w, M-w, MouseDragEnd1Pane, Enter).
Window Switching: Ctrl-1 selects window 1.
Prefix: Changed to Ctrl-a (unbinds default Ctrl-b).
Pane Navigation: h (left), j (down), k (up), l (right).
Pane Synchronization: y turns on, Y turns off.
Virtual Environment: v activates .venv if present, or shows a message if not.

General Settings

Mouse Support: Enabled with set -g mouse on.
Indexing: Starts windows and panes at 1 (base-index 1, pane-base-index 1).
Clipboard: Enabled with set-clipboard on.
Detach Behavior: detach-on-destroy off keeps tmux running after session close.
Terminal: Uses tmux-256color for better color support.

Layout and Status Bar

Status Position: Top (status-position top).
Display Panes: q shows pane numbers for 0 seconds.
Zoom Indicator: Shows ( ) in red when a window is zoomed.
Colors:
Status background: #3A3A3A (dark gray).
Status foreground: #5c6370 (gray).
Window status: Custom icons and colors (e.g., #eeffff on #585858).
Current window: #82AAFF (blue) with bold text.
Status left: #ffaf00 (orange) with emojis.
Status right: Shows current path and weather in Chicago.



Plugins

TPM: Manages plugins (tmux-plugins/tpm).
tmux-prefixless: Enables prefix-less commands (toddyamakawa/tmux-prefixless).
tmux-weather: Displays weather (xamut/tmux-weather) with:
Location: Chicago.
Units: Metric (u).
Interval: 15 minutes.
Format: Condition + Temperature + Wind.



Usage

Start tmux: tmux or tmux new -s <session-name>.
Detach: Ctrl-a d.
Reattach: tmux attach.
Navigate Panes: Use h, j, k, l after Ctrl-a.
Sync Panes: Toggle with y or Y.
Activate .venv: Press v in the target pane.

Troubleshooting

Plugins Not Loading:
Ensure TPM is cloned to ~/.tmux/plugins/tpm.
Run Ctrl-a I in tmux to install.


Clipboard Issues:
Verify xsel is installed (which xsel).
Check permissions for clipboard access.


Color Problems:
Ensure terminal supports tmux-256color (e.g., set in .bashrc or terminal settings).


Weather Not Showing:
Confirm internet access and valid @tmux-weather-location.



Restoring Original Configuration
To revert:
cp ~/.tmux.conf.bak ~/.tmux.conf
tmux source-file ~/.tmux.conf

Additional Notes

Customization: Adjust colors, key bindings, or weather location in .tmux.conf.
Compatibility: Tested on Pop!_OS with GNOME Terminal; may need adjustments for other setups.
License: Provided as-is for personal use; modify as needed.

