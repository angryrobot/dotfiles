### Dotfiles

<https://github.com/angryrobot/dotfiles>

- i3 (i3-gaps)
- i3blocks
- bumblebee-status
- rofi
- compton (transparency)

This is my custom i3-gaps config file that I configured over the past few months.

Feel free to copy or fork any of these files and edit them to your liking.

This config is for a dual monitor setup.

The config file for i3-gaps is a little messy but i'm working on cleaning it up.

There is a i3blocks config although i've recently switched to bumblebee-status which is much easier to use as it doesn't use a config file.

Rofi is configured in a nice dark theme.

The compton.conf file is very simple.

**i3bar**

Here is my i3bar which is setup for use with two monitors. Notice the output line which consists of ```$disp1``` and ```$disp2```.  Also there are two instances of ```bar```. One displays the ```bumblebee-status``` bar on one screen and the other displays the ```i3status``` bar on the other screen. At the top of my i3 config you will find these two lines which set the displays:

```set $disp2 HDMI-0
set $disp2 HDMI-0
set $disp2 DVI-I-1
```

Which set the respective displays. Type ```xrandr``` in a terminal to find out what your monitors are labeled.

```sh
bar {
	font pango:DejaVu Sans Mono, FontAwesome 8
    output $disp1
	status_command /home/raven/.config/i3/bumblebee-status/bumblebee-status -m spotify mpd nic disk:root cpu memory battery date time pasink pasource caffeine -p root.path=/ time.format="%I:%M" date.format="%a, %b %d %Y" -t iceberg-rainbow
	position top
	mode dock
	modifier None
    workspace_buttons yes
colors {
        background #253941
        statusline #e7dfd9
        separator  #081419
        focused_workspace  #2aa198 #073642 #eee895
        active_workspace   #073642 #859900 #839496
        inactive_workspace #002b36  #002b36   #586e75
        urgent_workspace   #cb4b16 #dc322f #fdf6e3
    }
}

bar {
    output $disp2
    status_command i3status
    position top
}
```