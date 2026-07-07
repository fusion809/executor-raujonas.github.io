# Executor extension fork with click actions
![Executor extension with click actions](https://fusion809.github.io/images/executor-raujonas.github.io/Screenshot_2026-07-07_19-23-43.png)
**Figure 1: Executor in use on my Linux From Scratch developmental (systemd init) virtual machine on 7 July 2026.**

I wanted click actions and tooltips (with both text and command fields) for the [Executor extension](https://github.com/raujonas/executor); this is my fork to achieve this. It was forked from version 30 of the upstream extension. The default click actions are those I use. The tooltip command output is shown below the corresponding tooltip text in the tooltip. 

The open-wallpaper.sh and updates_no.sh scripts called by this extension are defined in [lfs-scripts](https://github.com/fusion809/lfs-scripts). This extension assumed it is located ~/. The `update` and `updates` functions are defined in scripts within my [host's scripts shell/user/21-lfs.sh, shell/user/lfs-autobuild.sh, and shell/user/lfs-updates.sh](https://github.com/fusion809/NixOS-configs/tree/26.05/shell/user).

