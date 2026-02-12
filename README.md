### Some useful hacks may you need some day

#### Clean OS memory cache
    sync && echo 3 | sudo tee /proc/sys/vm/drop_caches

#### Flatpak hacks
    flatpak uninstall --delete-data zoom
    flatpak uninstall --unused --delete-data

#### Create a repo from terminal (requires having gh installed and authenticated)
    git init
    gh repo create NombreDelRepo --public --source=. --remote=origin
    git add .
    git commit -m "Changes"
    git branch -M main
    git push -u origin main

#### Useful hacks for gnome fresh installed
    gsettings set org.gnome.shell.extensions.dash-to-dock click-action 'minimize'
    gsettings set org.gnome.shell.extensions.dash-to-dock middle-click-action 'previews'
    gsettings set org.gnome.mutter check-alive-timeout 60000

#### Left4dead2 for laptops, add this to video.cfg
    "setting.mat_tonemapping_occlusion_use_stencil"		"1"

#### Clean snap from Ubuntu 24.04
    sudo snap remove --purge {snapd,core22,bare,snapd-desktop-integration,snap-store,gtk-common-themes,gnome-42-2204,firefox,firmware-updater}
    sudo apt purge --autoremove snapd*
    sudo vim /etc/apt/preferences.d/nosnap.pref
        Package: snapd
        Pin: release a=*
        Pin-Priority: -10
    sudo apt update

#### Sync gdm with desktop resolution
    sudo ln ~/.config/monitors.xml ~gdm/.config/monitors.xml

#### Retroarch n64 hacks for joystick (for PS1, download following BIOS from github scph7502.bin)
    vim /opt/retropie/configs/all/retroarch-joypads
        input_l_x_plus_axis = "+0"
        input_l_x_minus_axis = "-0"
        input_l_y_plus_axis = "+1"
        input_l_y_minus_axis = "-1"

#### Connect by RDP to a Windows VM having webcam, microphone and sound
> * use latest version of Freerdp: https://ci.freerdp.com/job/freerdp-nightly-binaries *

    /opt/freerdp-nightly/bin/xfreerdp3 /v:win11.local:3389 /u:vagrant /p:vagrant /size:1600x900 /dynamic-resolution /dvc:rdpecam /sound:sys:pulse /microphone:sys:pulse +clipboard
