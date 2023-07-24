# My tmux setup/config

## tmux key-binding

| Description | key-binding |
| :-- | :-- |
| prefix | ctrl-space | 
| vertical pane | prefix + " |
| horizontal pane | prefix + % |
| detach | prefix + d |

## tmux commands 

`tmux new -s session_name`- start a new session named session_name.

`tmux attach -t session_name` - re-attach to an existing tmux session.

`tmux list-sessions` - lists existing tmux sessions.

`tmux info` - list out every session, window, pane, etc.

`tmux source-file ~/.tmux.conf` - reloads tmux configuration.

# Link
 - [A tmux Crash Course](https://thoughtbot.com/blog/a-tmux-crash-course)

## My tmux.conf setup

```
set-option -sa terminal-overrides ",xterm*:Tc"
set -g mouse on

# Set prefix
unbind C-b
set -g prefix C-Space
bind C-Space send-prefix

# Start window and pane index at 1 instead of 0
set -g base-index 1
set -g pane-base-index 1
set-window-option -g pane-base-index 1
set-option -g renumber-windows on

set -g @plugin 'tmux-plugins/tpm'
set -g @plugin 'tmux-plugins/tmux-sensible'
set -g @plugin 'dreamsofcode-io/catppuccin-tmux'

run '~/.tmux/plugins/tpm/tpm'

# set vi-mode
set-window-option -g mode-keys vi

# keybindings
bind-key -T copy-mode-vi v send-keys -X begin-selection
bind-key -T copy-mode-vi C-v send-keys -X rectangle-toggle
bind-key -T copy-mode-vi y send-keys -X copy-selection-and-cancel

# open panes in current directory: % for horizontal and " for vertical
bind '"' split-window -v -c "#{pane_current_path}"
bind % split-window -h -c "#{pane_current_path}"

# Resize current Tmux panes: left, right, up, down
## Eg. <ctrl-space> , :resize-pane -U 2 [go up 2 lines]
## Eg. <ctrl-space> , :resize-pane -L 2 [go left 2 lines]

```
