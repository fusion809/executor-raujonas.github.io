# Executor extension fork with click actions and tooltips
![Executor extension with click actions](https://fusion809.github.io/images/executor-raujonas.github.io/executor-raujonas.github.io/LFS_screenshot_26-07-2026_2.png)
**Figure 1: Executor in use on my Linux From Scratch developmental (systemd init) virtual machine on 26 July 2026. Only active on the centre and right of the panel.**

I wanted click actions and tooltips (with both text and command fields) for the [Executor extension](https://github.com/raujonas/executor); this is my fork to achieve this. It was forked from version 30 of the upstream extension. The default click actions are those I use. The tooltip command output is shown below the corresponding tooltip text in the tooltip. 

The `open-wallpaper.sh` and `updates_no.sh` scripts called by this extension are defined in [lfs-scripts](https://github.com/fusion809/lfs-scripts). This extension assumed it is located ~/. The `update` and `updates` functions are defined in scripts within my [host's scripts shell/user/21-lfs.sh, shell/user/lfs-autobuild.sh, and shell/user/lfs-updates.sh](https://github.com/fusion809/NixOS-configs/tree/26.05/shell/user).

![Executor extension with KDE Frameworks 6.27->6.28 updates listed in tooltip](https://fusion809.github.io/images/executor-raujonas.github.io/LFS_screenshot_11-07-2026_r13.0-143.png)
**Figure 2: Executor extension with updates KDE Frameworks 6.27->6.28 update shown in tooltip.**

## Installation
Simply git clone this repo to ~/.local/share/gnome-shell/extensions and this should suffice to install it. I guess you might need to run `glib-compile-schemas schemas` in its root. 

At most the installation may entail running:

```zsh
git -C ~/.local/share/gnome-shell/extensions clone https://github.com/fusion809/executor-raujonas.github.io
glib-compile-schemas ~/.local/share/gnome-shell/extensions/executor-raujonas.github.io/schemas
```

## Documentation
If you open GNOME Extensions and navigate to Executor's settings, you'll find that for "Left", "Centre" and "Right" tabs the settings within are virtually identical and look like Figures 3, 4, and 5.

![Executor's left settings](https://fusion809.github.io/images/executor-raujonas.github.io/Left_Extension_settings.png)

**Figure 3: Executor's left tab settings.**

![Executor's centre settings](https://fusion809.github.io/images/executor-raujonas.github.io/Centre_Extension_settings.png)

**Figure 4: Executor's centre tab settings.**

![Executor's right settings](https://fusion809.github.io/images/executor-raujonas.github.io/Right_Extension_settings.png)

**Figure 5: Executor's right tab settings.**

**Table 1: Settings within left, centre and right tabs.**

| Setting              | Default         | Type                  | Function |
|----------------------|-----------------|-----------------------|----------|
| Active               | On              | Binary (Off/On)       | Determines whether command output will be shown in this part of the GNOME panel. |
| Index in status bar  | 2               | Non-negative integer  |  Position relative to other items in this part of the GNOME panel. |
| Command              | Depends on tab. | Bash command          | Shell command to execute. Its stdout is shown in the GNOME panel. More than one command can be specified per tab. |
| Interval             | 5               | Positive integer      | Interval in seconds between command executions. |
| Left-click command   | Depends on tab. | Bash command          | Command to run upon left-clicking the relevant part of the GNOME panel. |
| Middle-click command | Depends on tab. | Bash command          | Command to run upon middle-clicking the relevant part of the GNOME panel. |
| Right-click command  | Depends on tab. | Bash command          | Command to run upon right-clicking the relevant part of the GNOME panel. |
| Tooltip text         | Depends on tab. | String                | Text to show when hovering over the relevant part of the GNOME panel. |
| Tooltip command      | Depends on tab. | Bash command          | Command to run whose stdout is shown below the tooltip text when hovering over the relevant part of the GNOME panel. |

![General extension settings](https://fusion809.github.io/images/executor-raujonas.github.io/General_Extension_settings.png)

**Figure 5: Executor's general settings.**

The one setting under "General", namely "Click actions" decides whether clicking executor output will run the commands you have specified.

If you want to export your settings, you can with the command `dconf dump /org/gnome/shell/extensions/executor/ > executor-settings.dconf` and import them with `dconf load /org/gnome/shell/extensions/executor/ < executor-settings.dconf` per the [upstream docs](https://raujonas.github.io/executor/).
