# Linux How To 
Guide for how to do certain things on a linux os

## How to Compress a Folder into a `.zip`

### Installing `zip`

If `zip` is not installed on your system, install it using:

**Ubuntu/Debian:**
```bash
sudo apt-get install zip
```

**Fedora/RHEL:**
```bash
sudo dnf install zip
```

### Using the `zip` Command Inside Folder to be Compressed (Recommended)

Compress all files and subdirectories within the current working directory into a `.zip` called `my_folder_compressed.zip`. `my_folder` is the current working directory

```bash
name@name:~/my_folder$ zip -r my_folder_compressed.zip .
```

#### Structure of `.zip` File from Example Above
```
my_folder_compressed/
└── contents in my_folder
```

### Using the `zip` Command Outside Folder to be Compressed

Compress all files and subdirectories within a folder named `my_folder` into a `.zip` called `my_folder_compressed.zip`. `my_folder` is in the currently working directory

```bash
name@name:~$ zip -r my_folder_compressed.zip my_folder
```

Compress all files and subdirectories within a folder named `my_folder` into a `.zip` called `my_folder_compressed.zip`, excluding all files in `folder1`, the text file `file1.txt`, and all files with `.tmp` extensions in `folder2`:

```bash
name@name:~$ zip -r my_folder_compressed.zip my_folder/ -x "my_folder/folder1/*" "file1.txt" "folder2/*.tmp"
```

#### Structure of `.zip` File from Example Above
```
my_folder_compressed/
└── my_folder
    └──contents in my_folder
```

## Options
- `-r` (recursive): Compress all files and subdirectories within the folder
- `-x` (exclude): Exclude specific files 

