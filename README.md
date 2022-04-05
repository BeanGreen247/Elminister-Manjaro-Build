# Elminister Manjaro Build
My Manjaro Linux Build for my Elminister rig

### Step 0

Get Manjaro Linux ISO file, I picked the KDE version

https://manjaro.org/get-manjaro/

Burn ISO to USB drive

Balena Etcher - https://www.balena.io/etcher/

dd - https://man7.org/linux/man-pages/man1/dd.1.html

Once done go into your BIOS and change boot priority to make sure that the usb drive is the first option. Then save and exit.

SUGGESTION >>> UNPLUG DRIVES THAT YOU DO NOT WANT TO INSTALL LINUX TO.

## Step 0.5
Make sure to use opensource drivers, since I am using an AMD GPU.

## Step 1
Launch installer from desktop and pick American English as language.

Pick the prefered timezone, Europe/Prague in my case.

Pick your keyboard layout. In my case Generic 105-key PC English (US) Default.

If you are using a VM, or scared of the manual part then just use Erase disk and Swap (with Hibernate).

Now click on Next.

Next fill out all the information needed.
* name: Thomas Mozdren
* login: beangreen247
* Computer Name: Elminister
* Password: not_gonna_dox_myself

And tick Use the same login for admin account

Now click on Next and you shlould see a system summary. Click Install. If a windows pops up, click Install now.

Make sure to reboot after the install has finished.

## Step 2
Once you reboot make sure to switch Dekstop Session from Plasma (Wayland) to Plasma(X11).

Open a terminal (Konsole) and type in sudo pacman -Syyuu to do a full system update and upgrade. After it is done, just reboot.

## Step 3
Install some packages (will be expanded)
```
sudo pacman -S neofetch htop git base-devel kdevelop multilib-devel vulkan-devel jre-openjdk jre11-openjdk jre8-openjdk jdk-openjdk jdk11-openjdk jdk8-openjdk gcc glibc yay notepadqq obs-studio
```
```
yay -S codium intellij-idea-community-edition google-chrome
```

Sidenote: if you install google chrome this way, it will automatically change in your taskbar, automatically replacing firefox. Oh sorry furryfox.

## Step 4
Download and use the update script

https://github.com/BeanGreen247/ArchLinuxUpdateScript

## Step 5

installing discord, steam and other gaming stuff
```
sudo pacman -S steam discord --noconfirm
```
installing aditional packages
```
sudo pacman -Sy wine-staging giflib lib32-giflib libpng lib32-libpng libldap lib32-libldap gnutls lib32-gnutls mpg123 lib32-mpg123 openal lib32-openal v4l-utils lib32-v4l-utils libpulse lib32-libpulse libgpg-error lib32-libgpg-error alsa-plugins lib32-alsa-plugins alsa-lib lib32-alsa-lib libjpeg-turbo lib32-libjpeg-turbo sqlite lib32-sqlite libxcomposite lib32-libxcomposite libxinerama lib32-libgcrypt libgcrypt lib32-libxinerama ncurses lib32-ncurses opencl-icd-loader lib32-opencl-icd-loader libxslt lib32-libxslt libva lib32-libva gtk3 lib32-gtk3 gst-plugins-base-libs lib32-gst-plugins-base-libs vulkan-icd-loader lib32-vulkan-icd-loader cups samba alsa alsa-utils alsa-tools gnutls libpng wine-mono lib32-libxml2 lib32-mpg123 lib32-lcms2 lib32-giflib lib32-libpng lib32-gnutls lib32-libpulse lib32-fontconfig lib32-libxcomposite lib32-libxrender lib32-libxslt lib32-gnutls lib32-libxi lib32-libxrandr lib32-libxinerama lib32-libcups lib32-freetype2 lib32-libpng lib32-openal python-pyopencl lib32-v4l-utils lib32-libxcursor lib32-mpg123 lib32-sdl xf86-video-intel lib32-mesa-libgl nss-mdns ninja nasm git-lfs jq oniguruma yarn gulp semver nodejs tmux nvm --noconfirm
```
```
yay -S dxvk-bin
```
Open steam and go to Steam >> Settings >> Steam Play >> Enable Steam Play for all titles and leave Proton Experimental
```
sudo pacman -S gamemode
```
Make sure to reboot

## Step 6 (needs some work)
DXVK stuff
```
sudo pacman -S vulkan-radeon lib32-vulkan-radeon amdvlk lib32-amdvlk vulkan-icd-loader lib32-vulkan-icd-loader vulkan-mesa-layers lib32-vulkan-mesa-layers
```
//this is for AMD GPUs for more go here https://wiki.archlinux.org/title/Vulkan#Installation

after this reboot

https://github.com/doitsujin/dxvk/releases download the latest .tar.gz and extract it to your downloads folder

next open two or three file explorers and open the dxvk folder in one and open these two dirs next
```
/home/beangreen247/.steam/steam/steamapps/common/Proton - Experimental/files/lib/wine/dxvk
```
and
```
/home/beangreen247/.steam/steam/steamapps/common/Proton - Experimental/files/lib32/wine/dxvk
```
and copy and replace them in this fassion

everything in `/home/beangreen247/Downloads/dxvk-version/x32/` into here `/home/beangreen247/.steam/steam/steamapps/common/Proton - Experimental/files/lib/wine/dxvk`

everything in `/home/beangreen247/Downloads/dxvk-version/x64/` into here `/home/beangreen247/.steam/steam/steamapps/common/Proton - Experimental/files/lib64/wine/dxvk`

And in steam add this into the launch options of each game to see if it works or not
```
DXVK_HUD=version,fps,gpuload %command%
```

## Step 7
Remapping Home dirs

sudo nano ~/.config/user-dirs.dirs
```
XDG_DESKTOP_DIR="/mnt/01D807332FB88CE0/Desktop"
XDG_DOWNLOAD_DIR="/mnt/01D807332FB88CE0/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="/mnt/01D807332FB88CE0/Documents"
XDG_MUSIC_DIR="/mnt/01D807332FB88CE0/Music"
XDG_PICTURES_DIR="/mnt/01D807332FB88CE0/Pictures"
XDG_VIDEOS_DIR="/mnt/01D807332FB88CE0/Videos"
```
sudo nano /etc/xdg/user-dirs.defaults
```
DESKTOP=/mnt/01D807332FB88CE0/Desktop
DOWNLOAD=/mnt/01D807332FB88CE0/Downloads
TEMPLATES=Templates
PUBLICSHARE=Public
DOCUMENTS=/mnt/01D807332FB88CE0/Documents
MUSIC=/mnt/01D807332FB88CE0/Music
PICTURES=/mnt/01D807332FB88CE0/Pictures
VIDEOS=/mnt/01D807332FB88CE0/Videos
```
Reboot in order for them to aplly.

## Step 8
Terminal stuff yay!!!

Apply my custom zshrc file and set the blue color scheme https://github.com/BeanGreen247/zsh-config

Open Konsole and go to Settings and untick Main Toolbar and Session Toolbar under Toolbars Shown for a clean look.

nano ~/.tmux.conf
```
set-option -g default-shell /bin/zsh
```

# Some scripts
cpu-pinning.sh
```bash
# force linux to use only all cpus exect for 10,11 (11,12)
taskset -c 2-10 /usr/lib/vmware/bin/vmware-vmx
systemctl set-property --runtime -- user.slice AllowedCPUs=0-11
systemctl set-property --runtime -- system.slice AllowedCPUs=0-11
systemctl set-property --runtime -- init.slice AllowedCPUs=0-11
```
to run use sudo for root access

cpu-relsease.sh
```bash
# force linux to use whole cpu
taskset -c 1-12 /usr/lib/vmware/bin/vmware-vmx
systemctl set-property --runtime -- user.slice AllowedCPUs=0-11
systemctl set-property --runtime -- system.slice AllowedCPUs=0-11
systemctl set-property --runtime -- init.slice AllowedCPUs=0-11
```
to run use sudo for root access

performance-mode.sh
```bash
#!/bin/bash
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
for file in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor; do echo "performance" > $file; done
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
```
to run use sudo for root access

Some info
* cpu-pinning.sh - make sure to run before launching the VM
* cpu-relsease.sh - run after closing/killing the VM
* performance-mode.sh - to enable performace cpu governor

## what is next?
we will look into more performace improvements and tweaks, this VM is used for video editing and gaming if the game is proprietary and has anticheat software or drm built in.

## Step 9
virtio/kvm gaming VM

to be done
