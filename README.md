# Awsome-yabai-skhd
yabai, yabai, yabai

from: https://blog.dsubachev.com/install-a-tiling-window-manager-on-your-mac/

## yabai
```bash
#!/usr/bin/env sh
#2 try
##0.5 label space
yabai -m space 1 --label mole
yabai -m space 2 --label git
yabai -m space 3 --label shell
yabai -m space 4 --label try
yabai -m space 5 --label xxx
yabai -m space 6 --label del
yabai -m space 7 --label info
yabai -m space 8 --label more
yabai -m space 9 --label awsome
yabai -m space 10 --label dev
# sync mouse and focus
yabai -m config focus_follows_mouse autofocus
yabai -m config mouse_follows_focus          on
# old window occupies more? now is default value 0.5
yabai -m config split_ratio 0.5

# borders
yabai -m config window_border                on
yabai -m config window_shadow                on
yabai -m config window_border_width          6
yabai -m config active_window_border_color   0xffff3050
yabai -m config normal_window_border_color   0xffaaaaaa

# general space settings
yabai -m config layout                       bsp
yabai -m config top_padding                  5
yabai -m config bottom_padding               5
yabai -m config left_padding                 5
yabai -m config right_padding                5
yabai -m config window_gap                   06

# yabai auto focus to previously focused window after killing a window
function record_display_id {
  display_id=$(yabai -m query --windows --window | jq '.display')
  python $HOME/.config/yabai/autofocus/display_focus.py write $display_id
}
function focus_current_display {
  yabai -m display --focus $(python $HOME/.config/yabai/autofocus/display_focus.py read)
}
yabai -m signal --add event=window_focused action="${functions[record_display_id]}"
yabai -m signal --add event=application_front_switched action="${functions[record_display_id]}"
yabai -m signal --add event=window_destroyed action="${functions[focus_current_display]}"
yabai -m signal --add event=application_terminated action="${functions[focus_current_display]}"
```

## skhd
```bash
#2 try

# meta operation
ctrl + alt + cmd - r : brew services restart yabai

# Navigation
alt - h : yabai -m window --focus west
alt - j : yabai -m window --focus south
alt - k : yabai -m window --focus north
alt - l : yabai -m window --focus east

# ctrl + alt used to move window
## swap windows
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
