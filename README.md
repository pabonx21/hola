## some useful hacks may you need some day 

### clean OS memory cache
    sync && echo 3 | sudo tee /proc/sys/vm/drop_caches

### flatpak hacks
    flatpak uninstall --delete-data zoom
    flatpak uninstall --unused --delete-data

### create a repo from terminal (requires having gh installed and authenticated)
    git init
    gh repo create NombreDelRepo --public --source=. --remote=origin
    git add .
    git commit -m "Changes"
    git branch -M main
    git push -u origin main

### useful hacks for gnome fresh installed
    gsettings set org.gnome.shell.extensions.dash-to-dock click-action 'minimize'
    gsettings set org.gnome.shell.extensions.dash-to-dock middle-click-action 'previews'
    gsettings set org.gnome.mutter check-alive-timeout 60000

### left4dead2 for laptops, add this to video.cfg
    "setting.mat_tonemapping_occlusion_use_stencil"		"1"

### clean snap from Ubuntu 24.04
    sudo snap remove --purge {snapd,core22,bare,snapd-desktop-integration,snap-store,gtk-common-themes,gnome-42-2204,firefox,firmware-updater}
    sudo apt purge --autoremove snapd*
    sudo vim /etc/apt/preferences.d/nosnap.pref
        Package: snapd
        Pin: release a=*
        Pin-Priority: -10
    sudo apt update

### sync gdm with desktop resolution
    sudo ln ~/.config/monitors.xml ~gdm/.config/monitors.xml

### retroarch n64 hacks for joystick
    vim /opt/retropie/configs/all/retroarch-joypads
        input_l_x_plus_axis = "+0"
        input_l_x_minus_axis = "-0"
        input_l_y_plus_axis = "+1"
        input_l_y_minus_axis = "-1"
    for ps1, download following bios from github scph7502.bin

### connect by RDP to a Windows VM having webcam, microphone and sound
### Fist install latest version of freerdp: https://ci.freerdp.com/job/freerdp-nightly-binaries/
    /opt/freerdp-nightly/bin/xfreerdp3 /v:win11.local:3389 /u:vagrant /p:vagrant /size:1600x900 /dynamic-resolution /dvc:rdpecam /sound:sys:pulse /microphone:sys:pulse +clipboard
