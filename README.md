# Introduction

This program transfers all files outside of folders to the specific folders to which they belong.

# Download & Build

First download the program from GitHub and go to the File-Sorter-Core folder.

```
% git clone https://github.com/rounnus/File-Sorter-Core.git
% cd File-Sorter-Core/
```

After installation the program must be built. In order to build the program, the following instructions must be
followed.<br>

```
% mkdir build
% cd build/
% cmake ../
% make
% sudo make install
```

After this the program will be installed and ready to run.

# Config

The program gets the information it needs from a config file, which is like the following

```
[basic_config]
check_interval 3000
parse_interval 5000
debug_log 0
default_dir_path /home/username/default_sorter_path/

[check]

[done_check]

[targets]

[done_targets]
```

The information is as follows.<br>

Field |  Description
---------|--------------
`check_interval` | The time between checks (for new files etc).
`parse_interval` | The time to read the config file again for any changes.
`debug_log` | For debugging. To enter debug mode, the value of the debugLog field must be changed to 1.
`default_dir_path` | If a file is found outside of a folder and no specific location has been specified to which it should be moved, then it will go to default_dir_path.
`[check]` | This field includes all locations where the program will look for files. Each location that enters this field must be entered before `[done_check]`.
`[targets]` | This field contains all the file extensions and all the locations that these files should be sent to. Each line in this field consists of two elements that are separated by a space. The first element is the extension of the file and the second is the location where this file should be sent. Also each new line must be entered before `[done_targets]`.

An example of `[check]`:<br>

```
[check]
/home/username/
/home/username/Desktop/
...
[done_check]
```

An example of `[targets]`:<br>

```
[targets]
.py /home/username/Documents/py/
.cpp /home/username/Documents/cpp/
...
[done_targets]
```

In the example above the first part consists of the extensions `.py` and `.cpp` and the second part of the
locations `/home/username/ Documents/py/` and `/home/username/Documents/cpp/`.

# Service

The program can be run using `systemd`. To start the program from `systemd` the following must be performed.<br>
``` systemctl --user start file-sorter```
