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

Next up Drive partitioning. Here is how I calculate it.
* Take the toltal capacity (1TB in my case) and divide that by 6, round that up and I get 170gb for the root os (root) partition
  * In my test VM with a 256GB Drive it is like 43GB
* We need to convert this number to MiB so
  * 170 GB = 162125 NiB
  * 43 GB = 41008MiB
    * here is how you calcualte it
    * take the size you want in GB and multiply it by 953.674
    * however linux calculates it diferently, so it is 1024,023255813953
    * 170 * 1024,023255813953 = 174083,953488372 round it up to 174084
    * 43 * 1024,023255813953 = 44033
* Next up is the swap partition, I usually give the same size as my system RAM, so 32GB to MiB is 30517.6 and round it up to 30518
  * My VM has 8GB of RAM so 8GB to MiB is 8192,186046511624 and round it up to 8193
* The rest of the drive will be left for the home partition as personal storage

With all that do the manual partitioning only on the main rig. If you are using a VM, or scared of the manual part then just use Erase disk and Swap (with Hibernate).
* Click New Partition Table and pick GPT if you have drives larger than 2TB
* Next clik Create and create the partitions as follows
  * Change the size to the sizes calculated before
  * and pick the right flags and mount points
  * for the EFI partition
    * Size: 128 MiB
    * File System: fat32
    * Mount Point: /boot
    * FS Label: boot
    * Flags: bios-grub
  * for the swap partition it is as follows
    * Size: (pick based if VM ot not)
    * File System: linuxswap
    * Mount Point: none
    * FS Label: swap
    * Flags: swap
  * click OK
  * for the os (root) partition it is as follows
    * Size: (pick based if VM ot not)
    * File System: ext4
    * Mount Point: /
    * FS Label: root
    * Flags: root
  * click OK
  * for the swap partition it is as follows
    * Size: (rest of the drive)
    * File System: ext4
    * Mount Point: /home
    * FS Label: home
    * Flags: none
  * click OK

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

sudo pacman -S neofetch htop git base-devel kdevelop multilib-devel vulkan-devel jre-openjdk jre11-openjdk jre8-openjdk jdk-openjdk jdk11-openjdk jdk8-openjdk gcc glibc yay notepadqq obs-studio

yay -S vscode intellij-idea-community-edition google-chrome

quick notepadqq note

Go to Settings > Preferences > Appearance and set Color scheme to material

Sidenote: if you install google chrome this way, it will automatically change in your taskbar, automatically replacing firefox. Oh sorry furryfox.

## Step 4
some stuff
