# Awsome-yabai-skhd
yabai, yabai, yabai

from: https://blog.dsubachev.com/install-a-tiling-window-manager-on-your-mac/

## yabai
```bash
#!/usr/bin/env sh
# meta operation
yabai -m signal --add event=dock_did_restart action="sudo yabai --load-sa"
sudo yabai --load-sa

#2 try
yabai -m rule --add app=Notion space=11

yabai -m rule --add app=WeCom space=4
yabai -m rule --add app=HTTPie space=4
yabai -m rule --add app=wpsoffice space=4

yabai -m rule --add app="GitHub Desktop" space=5

# sync mouse and focus
yabai -m config focus_follows_mouse          off
yabai -m config focus_follows_mouse          autofocus
yabai -m config mouse_follows_focus          on

# borders
yabai -m config window_border                on
yabai -m config active_window_border_topmost on
yabai -m config window_shadow                on
yabai -m config window_border_width          5
yabai -m config active_window_border_color   0xffff3050
yabai -m config normal_window_border_color   0xffaaaaaa

# general space settings
yabai -m config layout                       bsp
yabai -m config top_padding                  6
yabai -m config bottom_padding               6
yabai -m config left_padding                 10
yabai -m config right_padding                10
yabai -m config window_gap                   5

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

# with key ctrl + alt + cmd
ctrl + alt + cmd - i : open -na iTerm
ctrl + alt + cmd - 1 : open -na Google\ Chrome
ctrl + alt + cmd - g : open -na GitHub\ Desktop
ctrl + alt + cmd - c : open -na Visual\ Studio\ Code
ctrl + alt + cmd - r : brew services restart yabai

# meta operation
ctrl + alt + cmd - space  : yabai -m space --layout bsp
ctrl + alt + cmd - return : yabai -m space --mirror y-axis

# Navigation
alt - h : yabai -m window --focus west
alt - j : yabai -m window --focus south
alt - k : yabai -m window --focus north
alt - l : yabai -m window --focus east
alt - n : yabai -m window --focus stack.next || yabai -m window --focus stack.first

# ctrl + alt used to move window
## swap windows
shift + alt - h : yabai -m window --warp west
shift + alt - j : yabai -m window --warp south
shift + alt - k : yabai -m window --warp north
shift + alt - l : yabai -m window --warp east
## stack windows
ctrl + alt - h : yabai -m window --stack west || yabai -m window --stack east
ctrl + alt - j : yabai -m window --stack south || yabai -m window --stack north
ctrl + alt - k : yabai -m window --stack north || yabai -m window --stack south
ctrl + alt - l : yabai -m window --stack east || yabai -m window --stack west
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

## Resize window: just use mouse

```
