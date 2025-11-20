# Debian 13x VM Notes 25-11

## 2025-11-21 Fri.

- Installed i3-wm

```
sudo apt install i3-wm
```

## 2025-11-18 Tue.

I need to pull myself together.

## 2025-11-17

I think it's time for me to do some web projects.

Learn JavaScript (again).


## 2025-11-14

### Other Memos

- To live in a conscious way. To live consciously.
- [Strikesthrough](https://en.wikipedia.org/wiki/Strikethrough)

### TODO

- [x] Install tmux
- [x] Set "Alt + Number(1 to 5)" for window 0 to 4 in tmux
- [x] Set shutdown shortcut for this VM

### Install tmux

```
sudo apt install tmux
```

[Keyboard shortcut for Xfce shutdown?](https://forums.linuxmint.com/viewtopic.php?t=263504)

```bash
systemctl poweroff
```

Set "Alt + number" shortcut:

[Making TMUX use Alt+Num to select window](https://superuser.com/questions/680238/making-tmux-use-altnum-to-select-window)

```
# switch windows alt+number
bind-key -n M-1 select-window -t 1
bind-key -n M-2 select-window -t 2
bind-key -n M-3 select-window -t 3
bind-key -n M-4 select-window -t 4
bind-key -n M-5 select-window -t 5
bind-key -n M-6 select-window -t 6
bind-key -n M-7 select-window -t 7
bind-key -n M-8 select-window -t 8
bind-key -n M-9 select-window -t 9
```

Modify conf. above as follow:

```
bind-key -n M-1 select-window -t 0
bind-key -n M-2 select-window -t 1
bind-key -n M-3 select-window -t 2
bind-key -n M-4 select-window -t 3
bind-key -n M-5 select-window -t 4
```


## 2025-11-12

- The Truman Show (1998)
  - https://en.wikipedia.org/wiki/The_Truman_Show


## 2025-11-11

Cleared a drive for this VM.


## 2025-11-10

### Search apt package

```
apt-cache search --names-only 
```

### Install curl

```
sudo apt install curl
```

### (old ver)Change keyboard shortcut to open worknotes using Neovim

To open certain file with a command and maximize window:
```
gnome-terminal --maximize --command="nvim /path/to/filename"
```

To start GNOME Terminal at a particular directory:
```
gnome-terminal --working-directory=/path/to/dir
```

### Change keyboard shortcut to open worknotes using Neovim

25-1114 found this  message:

```
# Option “--command” is deprecated and might be removed in a later version of gnome-terminal.
# Use “-- ” to terminate the options and put the command line to execute after it.
```

To open certain file with a command and maximize window:
```
gnome-terminal --maximize -- nvim /path/to/filename
```

To start GNOME Terminal at a particular directory:
```
gnome-terminal --working-directory=/path/to/dir
```

Open  a  tab  in  the  window  with  the  given  profile.
```
gnome-terminal --tab-with-profile=PROFILENAME
```

### Start Gnome termianl in full screen

```
gnome-terminal --full-screen
```

### (Solved) Crackling Sound / Stuttering Audio

Where I found some possible solution:
1. https://www.reddit.com/r/vmware/comments/1hb2rsg/audiovideo_stuttering_on_linux_vm_using_vmware/
2. https://gitlab.freedesktop.org/pipewire/pipewire/-/wikis/Troubleshooting#stuttering-audio-in-virtual-machine

The solution on 2 worked for me.

> Normally this should not happen but is usually caused by jittery drivers. In a VM
this is most common because the device is emulated.
> 
> you can usually fix this problem by giving more headroom in the alsa device
ringbuffer.

(code and commands copied from 2nd link)

> Edit the WirePlumber configuration as follows

```
mkdir -p ~/.config/wireplumber/wireplumber.conf.d/
cd ~/.config/wireplumber/wireplumber.conf.d
```

> Then make ~/.config/wireplumber/wireplumber.conf.d/50-alsa-config.conf in an editor and add:

```
monitor.alsa.rules = [
  {
    matches = [
      # This matches the value of the 'node.name' property of the node.
      {
        node.name = "~alsa_output.*"
      }
    ]
    actions = {
      # Apply all the desired node specific settings here.
      update-props = {
        api.alsa.period-size   = 1024
        api.alsa.headroom      = 8192
      }
    }
  }
]

```

> Afterwards, restart everything via "systemctl --user restart wireplumber pipewire pipewire-pulse"

memo: I'm so glad this is solved for me


## 2025-11-08

Tutor to read: 2.2


## 2025-11-07

Setup this Debian 13 VM with VMware. 

Some problems still there, but it's good enough for coding and coding/streaming. 

The host is Windows 11.

- "Ctrl + Alt" to switch to host.
- "Ctrl + G" to switch to Guest.
- Registered Gmail: yumewalker86
- Registered Github: yumewalker86
- installed Vim

### Where does Cinnamon save custom key combinations?

source: https://forums.linuxmint.com/viewtopic.php?t=315472

They are stored in the dconf database.

To backup to a text file called ~/mykeybindings

```
dconf dump /org/cinnamon/desktop/keybindings/ > mykeybindings
```

To reload on another machine running Cinnamon transfer the file to ~/mykeybindings on the other machine and run

```
dconf load /org/cinnamon/desktop/keybindings/ < mykeybindings
```

### Removed some games that I won't play

I only kept Chess and Reversi.

### Use custome Date format

Default:

```
%A, %B %e, %H:%M
```

Custom:

```
%Y/%m/%d | %H:%M
```

### Installed Neovim

```
sudo apt install neovim
```

If you install this way, you usually get an older version. I got v0.10.4, where you usually see people using v0.11.x now (2025-11)

- Using 'nvim' command for now.
- To Learn: [Advent of Neovim](https://www.youtube.com/playlist?list=PLep05UYkc6wTyBe7kPjQFWVXTlhKeQejM)

See how much I can implement.

Command memo for "~/.config/nvimexample":
```
NVIM_APPNAME=nvimexample nvim
```

### To remove a single file from recent opened list

source: https://forums.linuxmint.com/viewtopic.php?t=440547

```
~/.local/share/recently-used.xbel
```

### Create .bookmarks folder

Collect bookmarks in markdown files


### Toggle Window Maximize

Alt + F10


