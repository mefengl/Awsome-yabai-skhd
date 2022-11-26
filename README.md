# Awsome-yabai-skhd
yabai, yabai, yabai

from: https://blog.dsubachev.com/install-a-tiling-window-manager-on-your-mac/

## yabai
```bash
#!/usr/bin/env sh

yabai -m config focus_follows_mouse          on
yabai -m config mouse_follows_focus          on

yabai -m config window_border                on

yabai -m config layout                       bsp
yabai -m config top_padding                  5
yabai -m config bottom_padding               5
yabai -m config left_padding                 5
yabai -m config right_padding                5
yabai -m config window_gap                   06

# prevent border from being under the active window
yabai -m config active_window_border_topmost on
yabai -m config window_shadow                on
yabai -m config window_opacity               off
yabai -m config window_border_width          6
yabai -m config active_window_border_color   0xffff3050
yabai -m config normal_window_border_color   0xffaaaaaa
```

## skhd
```bash
# Navigation
alt - h : yabai -m window --focus west
alt - j : yabai -m window --focus south
alt - k : yabai -m window --focus north
alt - l : yabai -m window --focus east

# ctrl + alt used to move window
## windows swap
shift + alt - h : yabai -m window --warp west
shift + alt - j : yabai -m window --warp south
shift + alt - k : yabai -m window --warp north
shift + alt - l : yabai -m window --warp east
## window => space
alt - 1 : yabai -m window --space 1
alt - 2 : yabai -m window --space 2
alt - 3 : yabai -m window --space 3
alt - 4 : yabai -m window --space 4
alt - 5 : yabai -m window --space 5
alt - 6 : yabai -m window --space 6
alt - 7 : yabai -m window --space 7
alt - 8 : yabai -m window --space 8
alt - 9 : yabai -m window --space 9
alt - 0 : yabai -m window --space 10

# shift + alt used to custom window itself
## Resize windows
ctrl + alt - h : \
    yabai -m window --resize left:-100:0 ; \
    yabai -m window --resize right:-100:0
ctrl + alt - j : \
    yabai -m window --resize bottom:0:100 ; \
    yabai -m window --resize top:0:100
ctrl + alt - k : \
    yabai -m window --resize top:0:-100 ; \
    yabai -m window --resize bottom:0:-100
ctrl + alt - l : \
    yabai -m window --resize right:100:0 ; \
    yabai -m window --resize left:100:0

# Change desktop
# use system's mission control keyboard shortcut
# ctrl - 1 : yabai -m space --focus 1
# ctrl - 2 : yabai -m space --focus 2
# ctrl - 3 : yabai -m space --focus 3
# ctrl - 4 : yabai -m space --focus 4
# ctrl - 5 : yabai -m space --focus 5
```
