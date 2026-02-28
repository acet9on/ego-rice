# Frutiger ego

This is a rice based off of Frutiger Ego, a subsection of the Frutiger family. The baseline for this project was : diinki-aero (huge thx for doing the hard part lmao)
This also uses the infamous Hyprland Scrolling plugin, which of I have made i3 based binds on "https://gitlab.com/sayokimi/hypr-i3-binds"


# !!! WARNING !!!

This uses the Slovakian keyboard, since I am based in Slovakia. In further intergration, I will make a script for installing and choosing the keyboard (but thats for the future) 

# Installation Steps 🖥️

You need to install the following dependencies on your system:

- `eww` for widgets
- `hyprland` the tiling window manager
- `nemo` the file explorer
- `waybar` the taskbar
- `wofi` the application launcher.
- I use the `kitty` terminal too, but you do you.

On arch, you can install some of the above with `sudo pacman -S hyprland nemo waybar wofi kitty`, installing `eww` has to
be done separately, easiest way is from the AUR with yay.

To install, copy all the folders in the `config` directory, to the `~/.config` directory on your system; make sure to backup your previous configs if you have them.

The `.config` directory is where most applications will store their config files.

You will need to make edits to config files, as not all configs are drag & drop, the files are commented in
order to help.

## Weather Widget ☁️

The weather widget uses `openweathermap.org` as a backend. They give you 2000 free api calls / day, which is more than enough.

You need to create an account there, get an API key, and then edit
the `eww/scripts/weather.sh` file with the following details. I've commented more specific instructions in that bash file.

The bash file stores the weather data in `~/.cache/eww/weather` every time `weather.sh --getdata` is called; as such, I recommend creating a
cronjob for calling `~/.config/eww/scripts/weather.sh --getdata` every 30 minutes.

## GTK theme & Icon Pack 🖌️

To install the icon theme, copy the `crystal-remix-icon-theme-diinki-version` directory in `IconTRheme` to your `~/.local/share/icons` or `/usr/share/icons` directories
and then set the theme to the one in use either with `gsettings` or the `dconf` applications; which you can download with most linux package managers.

To install the GTK theme, copy the `diinki-aero` folder in `GTKTheme` to your `~/.themes` directory,
and then set the GTK theme to "diinki-aero" with either `gsettings` or the `dconf` application.

# The Default Keybinds ⌨️

You can edit the keybinds in the hyprland config file as needed to match your preference, by default the most important ones:

- `MOD` is the super key/windows key by default in this config.
  - `MOD + Enter` = opens terminal (by default, kitty, you need to have it installed or edit the config file).
  - `MOD + R` = Launch wofi
  - `MOD + D` = Resize the windows
  - `MOD + E` = open the file explorer (you need nemo, or edit the config file)
  - `MOD + G` = Toggle a window from tiling to floating.
  - `Copilot Key` = Launch Brave
  - `MOD + mouse2 drag` = Resize a window
  - `MOD + Q` = Exit/Close an application
  - `MOD + SHIFT + (n)` = Move the window to a workspace with that ID.

# Setup the hyprscrolling plugin

## This is what should be in the config
```
bind = Super, left, layoutmsg, move -col
bind = Super, right, layoutmsg, move +col
bind = Super, up, movefocus, u
bind = Super, down, movefocus, d
bind = Super Shift, left, layoutmsg, movewindowto l
bind = Super Shift, right, layoutmsg, movewindowto r
bind = Super Shift, up, layoutmsg, movewindowto u
bind = Super Shift, down, layoutmsg, movewindowto d
bind = Super, D, submap, resize
submap = resize
bind = , left, layoutmsg, colresize -conf
bind = , right, layoutmsg, colresize +conf
bind = , up, resizeactive, 0 -10
bind = , down, resizeactive, 0 10
bind = Super, D, submap, reset
submap = reset
plugin {
    hyprscrolling {
        explicit_column_widths = 0.1, 0.2, 0.3, 0.4, 0.5, 0.6, 0.7, 0.8, 0.9, 1,
    }
}
```

## Install hyprscrolling

```
hyprpm update
hyprpm enable hyprscrolling
```

then to ~/.config/hypr/hyprland

```
general {
    layout = scrolling
}
```

# HUGE THANKS TO DIINKI-KOT AGAIN!
