---
title: "A guide to Tmux"
date: 2021-09-10T09:55:46+05:30
draft: false
categories:
- "utilities"
tags:
- "tmux"
- "terminal"
- "multiplexer"
- "linux"
---

Tmux is an abbreviation for terminal multiplexer. It is an application that lets you manage multiple terminal screens within a single terminal window. It uses the client/server architecture.

When you start the tmux, a server is run in a background process. Each tmux window that you create becomes a client connected to that server. Tmux sessions can be created, detached and reattached. Each session will be stored on the tmux server, so you can detach and reattach to session at any time. With tmux, you can load and run multiple programs within a single terminal window using window panes. It uses a prefix command to differentiate tmux commands from commands used in other programs. This avoids conflicts with commands used by other programs that are loaded into tmux window panes.

The default prefix for tmux command is `C-b / Ctrl+b`

You can configure tmux to your likeness using tmux configuration file. In the configuration file, you can add or modify key bindings and default settings. The configuration file must be placed within your $HOME directory.

### Session

| Description | Command |
| --- | --- |
| Start a new session | tmux new -s |

### Window

| Description | Command |
| --- | --- |
| Create Tmux window | ctrl+b c |
| Rename Tmux window | ctrl+b , |
| Move to next Tmux window | ctrl+b n |
| Move to previous Tmux window | ctrl+b p |
| List Tmux active windows | ctrl+b w |
| Kill Tmux window | ctrl+b & |

### Pane

| Description | Command |
| --- | --- |
| Split Tmux window into vertical panes | ctrl+b % |
| Split Tmux window into horizontal panes | ctrl+b " |
| Swap panes | ctrl+b o |
| Kill pane | ctrl+b x |
| pane count | ctrl+b q |
| Enable Scroll in Pane | ctrl+b [ |
| Quit Scroll in Pane | q |

### Miscellaneous Commands

| Description | Command |
| --- | --- |
| Big digital clock | ctrl+b t |

### Links

-   [TMux commands](http://www.dayid.org/comp/tm.html)
-   Brian P. Hogan, Tmux: Productive Mouse-Free Development
-   Victor Quinn et al., Getting Started with Tmux
-   Mark McDonnell, Tmux Taster