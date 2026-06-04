# Step by step guide on the commands to make your distro

## Optional step if you are on windows

Installing wsl2 on your machine, the following commands downloads wsl and an ubuntu image 
```PowerShell
wsl --install -d  Ubuntu-22.04
```

Afterwards, you will be prompted to create an user and a password for that user.

### Verifying the instalation

We need to verify if it is all set before continuing this big adventure **you** decided that **you** wanted to go through
The following command should give the list of wsl systems installed on you machine an which version of wsl it is set to run on:
```PowerShell
wsl --list --verbose
# Response
NAME                 STATE                 VERSION
Ubuntu-22.04         Running               2
```

In case the VERSION says one, you can run this command to fix this
```PowerShell
wsl --set-version Ubuntu-22.04 2
```
Now you are all set to start building your own distro on windows

## On wsl

### Setting up phase

For starters the first thing you should do is update everything on your computer, and how do you do that on your ubuntu vm:
```bash
sudo apt update && sudo apt upgrade -y
```

Now that your machine is running on the latest version possible, we can start.
For starters, we are going to need to download a lot of dependencies to create our own linux and here is the list inserted on a single command:
```bash
sudo apt update && sudo apt install -y \
    build-essential \
    libncurses-dev \
    bison \
    flex \
    libssl-dev \
    libelf-dev \
    bc \
    cpio \
    wget \
    xorriso \
    grub-pc-bin \
    grub-efi-amd64-bin \
    grub-common \
    mtools \
    squashfs-tools \
    qemu-system-x86 \
    tar \
    xz-utils
```

Now we got the tools to start building our own distro lets install the well oiled motor that makes the connection between software and hardwar, the beatiful linux kernel:
```bash
sudo wget https://cdn.kernel.org/pub/linux/kernel/v6.x/linux-6.1.60.tar.xz
```

As you can see we are downloading the compressed version of the linux kernel, so we need to run a command and decompress it:

```bash
sudo tar -xvf linux-6.1.60.tar.xz
```
This command will show all of the files being decompressed but if you want to wait blindly while it decompresses it you can run:
```bash
sudo tar -xf linux-6.1.60.tar.xz
```
Just take the verbose flag -v out and now you can't see what is going on.

### Building stuff

After the kernel decompresses there will be a linux-6.1.60 directory on you current directory so lets dive in there to start the build process:
```bash
cd linux-6.1.60
```
So now we need to make a configuratio file for our linux image buider, but news flash linux has 30 million components at least and 15k variables in a config file to be configured so, do you want to do it manually or should we ask a little help, with the help of kconfig and make we are to make this exhausting hand coding process automatic with this command:
```bash
sudo make defconfig
```
Poof the beautiful config file is created, if you hit `ls -lah` there should be a `.config` file in there. Now we need to check for the following variables if they are marked with a yes and not commented:

```bash
sudo nvim(your text editor of choice) .config
```

In that config file we need to make sure the following variable are written like the following `variable=y`, here is the list of variables to check for:
```bash
CONFIG_BINFMT_ELF=y
CONFIG_EXT4_FS=y
CONFIG_BLK_DEV=y
CONFIG_SCSI=y
CONFIG_SATA_AHCI=y
CONFIG_BLK_DEV_NVME=y
CONFIG_PROC_FS=y
```
If they are not like this modify them till they look like that.

Now we can run a command to check on our computer the modules it needs to run and they are compatible with .config file we just configured:
```bash
sudo make localmodconfig 
```
If you are prompted if you need x or y module, hit yes because you will problably will

Now that we are all set we can create a .img file from our initial configuration:
```bash
sudo make -j$(nproc)
```
