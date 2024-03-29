# Payload2Super

```
OPTION 1: pay2sup.sh [-rw|--read-write] [-r|--resize] payload.bin|rom.zip
OPTION 2: pay2sup.sh [-rw|--read-write] [-r|--resize] --remake super.zip|.img or /path/to/superblock
OPTION 3: pay2sup.sh [-rw|--read-write] [-r|--resize] [-c|--continue]

-rw  | --read-write          = Grants write access to all the partitions.

-r   | --resize	             = Resizes partitions based on user input. User input will be asked during the program.

-dfe | --disable-encryption  = Disables Android's file encryption. This parameter requires read&write partitions.

-t   | --thread	             = Certain parts of the program are multitaskable. If you wish to make the program faster, you can specify a number here.

-c   | --continue            = Continues the process if the program had to quit early. Do not specify a payload file with this option. NOTE: This option could be risky depending on which part of the process the program exited. Use only if you know what you're doing.

-s   | --remake	             = Additional feature to repack super flashable images. It can also extract super from /dev/block/by-name/super on Android.

-h   | --help                = Prints out this help message.

Note that --remake, --continue or payload.zip|.bin flag has to come after all other flags otherwise other flags will be ignored. You should not use --remake <super_flashable.zip> and payload.zip|.bin or --continue flags mixed with together. They are mutually exclusive.
```

This tool has only been tested on POCO F3 device, and is compatible with devices that have the same type of super partition scheme. You are free to test it on your device and give feedbacks.

It basically converts any payload flashable ROMs into super flashables to make flashing easier and faster. You can also repack super flashables to grant them read&write access and increase/decrease partition sizes or disable Android's file encryption.

## FEATURES
 - Can convert payload flashables to super flashables
 - Can repack super flashables from zips or /dev/block/by-name/super partition
 - Can grant partitions read and write access
 - Can increase/shrink partitions
 - Can disable Android's file encryption
 - Can use multi-threads to make process faster
 - Can continue if the program has exited in the middle of a process.

```
git clone https://github.com/elfametesar/Payload2Super
cd Payload2Super
```
# Example Usage

```
sh pay2sup -rw -r -dfe -t $(nproc --all) <path-to-your-rom-file>
```

This is a multi-platform tool, meaning it can work on both x64 Linux distros and arm64 Android devices. To use it on Linux distros, you need ADB access once to your device in order to get the super block size.

Warning: Some shells may not be compatible, so make sure to use it on BASH,ZSH or a newer version of SHELL. Android SHELL is compatible.
