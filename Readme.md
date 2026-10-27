# Linux Administration Complete Laboratory Manual & Practical Guide

A comprehensive, beginner-friendly handbook covering Red Hat Enterprise Linux 8 (RHEL 8) system administration, user management, file systems, process control, networking, firewall configuration, Apache web hosting, and automation scripting.

---

## 📌 Standard 5-Part Layout Convention

Every practical exercise in this manual adheres strictly to the following 5-part layout:

1. **Direct & Encouraging Overview:** A quick, plain-language summary of what we are doing, what Linux concept is involved, and why it is essential.
2. **Step-by-Step Instructions:** Bulleted, numbered sequential steps for setting up files, tools, and environments.
3. **Fully Written Command & Script Blocks:** Clean, formatted, commented commands, scripts, and syntax breakdowns with expected terminal outputs.
4. **File Paths & Locations Included:** Explicit directory paths indicating where to run commands, where files are stored, and where configuration settings live.
5. **Next Steps / Follow-up:** A clear next action, guiding question, or practical exercise to reinforce learning.

---

## 🖥️ System Architecture & Prerequisites

* **Operating System:** Red Hat Enterprise Linux 8.10 (x86_64)
* **Hypervisor:** Oracle VM VirtualBox 7.x / VMware Workstation 16+
* **Virtual Machine Specifications:** 2 GB RAM, 2 vCPUs, 50 GB Virtual Disk (VDI/VMDK)
* **Default Shell:** GNU Bash (`/bin/bash`)
* **Package Management:** RPM (`rpm`) and DNF (`dnf`)
* **Service & Boot Management:** Systemd (`systemctl`)

---

## 📑 Table of Contents

1. [Practical 1: Installation & Graphical Environment](#practical-1-installation--graphical-environment)
   * [1.a: Installing Red Hat Enterprise Linux 8](#1a-installing-red-hat-enterprise-linux-8-virtualbox--vmware)
   * [1.b: Linux Graphical Environment, Desktop Environments & File Systems](#1b-linux-graphical-environment-desktop-environments--file-systems)
2. [Practical 2: Basic System Commands & Text Analysis](#practical-2-basic-system-commands--text-analysis)
   * [2.a: Input-Output Redirection & Piping](#2a-input-output-redirection--piping)
   * [2.b: Text Analysis Using grep and Regular Expressions](#2b-text-analysis-using-grep-and-regular-expressions)
   * [2.c: Log In and Switch Users in Multi-User Targets](#2c-log-in-and-switch-users-in-multi-user-targets)
   * [2.d: Working with Text Files (cat, cut, sort, wc, less, head, tail, awk)](#2d-working-with-text-files-cat-cut-sort-wc-less-head-tail-awk)
3. [Practical 3: Essential File Management Tools](#practical-3-essential-file-management-tools)
   * [3.a & 3.e: Managing Files Using Hard and Soft Links](#3a--3e-managing-files-using-hard-and-soft-symbolic-links)
   * [3.b & 3.d: Archiving and Compression (tar, star, gzip, bzip2)](#3b--3d-archiving-and-compression-tar-star-gzip-bzip2)
   * [3.c: Create, Delete, Copy, Move, and Rename Files & Directories](#3c-create-delete-copy-move-and-rename-files-and-directories)
4. [Practical 4: Users, Groups, and Permissions](#practical-4-users-groups-and-permissions)
   * [4.a: Creating and Managing Users](#4a-creating-and-managing-users)
   * [4.b: Creating and Managing Groups](#4b-creating-and-managing-groups)
   * [4.d: Passwords and Password Aging Policies](#4d-passwords-and-password-aging-policies)
   * [4.e: Superuser Access (su, sudo, wheel, and visudo)](#4e-superuser-access-su-sudo-wheel-and-visudo)
5. [Practical 5: Managing Software](#practical-5-managing-software)
   * [5.c: Managing Software Packages with RPM](#5c-managing-software-packages-with-rpm)
6. [Practical 6: Managing Processes](#practical-6-managing-processes)
   * [6.a: Introduction to Process Management](#6a-introduction-to-process-management)
   * [6.b & 6.c: Managing Shell Jobs & Process Priorities](#6b--6c-managing-shell-jobs--process-priorities)
   * [6.f: Identify Intensive Processes and Kill Processes](#6f-identify-intensive-processes-and-kill-processes)
7. [Practical 7: Configuring Firewalls](#practical-7-configuring-firewalls)
   * [7.a: Linux Firewall with iptables](#7a-linux-firewall-with-iptables)
   * [7.b: Working with firewalld](#7b-working-with-firewalld)
8. [Practical 8: Configuring Apache Web Server](#practical-8-configuring-apache-web-server)
   * [8.a & 8.b: Basic Apache Server & Configuration Architecture](#8a--8b-basic-apache-server--configuration-architecture)
   * [8.c: Configuring Apache Virtual Hosts](#8c-configuring-apache-virtual-hosts)
9. [Practical 9: Creating Shell Scripts](#practical-9-creating-shell-scripts)
   * [9.a: Automate and Monitor Tasks & Processes](#9a-automate-and-monitor-tasks--processes)
   * [9.b: Getting and Setting System Information](#9b-getting-and-setting-system-information)
10. [Practical 10: Scheduling Tasks](#practical-10-scheduling-tasks)
    * [10.a: Configuring Cron to Automate Recurring Tasks](#10a-configuring-cron-to-automate-recurring-tasks)
    * [10.b & 10.c: Scheduling Future Tasks with At](#10b--10c-scheduling-future-tasks-with-at)

---

# Practical 1: Installation & Graphical Environment

## 1.a: Installing Red Hat Enterprise Linux 8 (VirtualBox / VMware)

### 1. Direct & Encouraging Overview
Setting up Red Hat Enterprise Linux 8 in a virtual machine gives you an isolated, enterprise-grade environment to practice system administration safely. Virtualization lets you create, snapshot, reconfigure, and reboot Linux servers without altering your host operating system.

### 2. Step-by-Step Instructions
1. Open Oracle VM VirtualBox and click the **New** button.
2. Enter the VM name (`RHEL8`), choose VM folder location, select the `rhel-8.10-x86_64-dvd.iso` image, and set Type to **Linux** and Version to **Red Hat (64-bit)**.
3. Allocate virtual hardware: set Base Memory to **2048 MB (2 GB)**, Processor to **2 CPUs**, and Virtual Disk Size to **50 GB**. Click **Finish**.
4. Select the `RHEL8` VM and click **Start**.
5. At the boot menu, select **Install Red Hat Enterprise Linux 8.10**.
6. Select **English (United States)** as the installation language and click **Continue**.
7. In **Installation Summary**:
   * Click **Installation Destination**, select the 50 GB disk, and click **Done**.
   * Click **Time & Date**, choose your regional timezone (e.g., `Asia/Kolkata`), and click **Done**.
   * (Optional) Configure **Network & Host Name** and enable the Ethernet connection.
   * Under User Settings, set a secure **Root Password**.
   * Click **User Creation**, enter full name and username (e.g., `rmishra`), check *Make this user administrator*, and set a user password.
8. Click **Begin Installation**. Wait until packages are installed, then click **Reboot System**.
9. Complete the **Initial Setup**: accept the License Agreement, click **Finish Configuration**, log in, and complete the welcome wizard.

### 3. Fully Written Command & Script Blocks
```bash
# Post-installation verification commands run in terminal:

# 1. Check OS and kernel version
uname -r
cat /etc/redhat-release
# Expected Output: Red Hat Enterprise Linux release 8.10 (Ootpa)

# 2. Verify allocated memory
free -h

# 3. Verify partitioned storage
lsblk
```

### 4. File Paths & Working Locations
* **Virtual Machine Storage:** `C:\Users\<username>\VirtualBox VMs\RHEL8\`
* **RHEL ISO Image Path:** `D:\Linux\ISO\rhel-8.10-x86_64-dvd.iso`
* **OS Release Details:** `/etc/redhat-release` and `/etc/os-release`

### 5. Next Steps / Follow-up
Open GNOME Terminal from **Activities > Terminal** and run `whoami` to verify that your administrative user is active.

---

## 1.b: Linux Graphical Environment, Desktop Environments & File Systems

### 1. Direct & Encouraging Overview
Linux separates the operating system core from its visual presentation. A **Display Manager** handles user authentication upon boot, while a **Desktop Environment (DE)** provides the graphical desktop, window manager, and menus. Understanding the unified hierarchical directory tree (`/`) and filesystem formats is the key to managing data storage.

### 2. Step-by-Step Instructions
1. Log in through the Display Manager graphical greeting screen.
2. Explore the GNOME Desktop Environment interface (top bar, system tray, Activities overview, and application dock).
3. Open the terminal to navigate the top-level root directory (`/`).
4. Inspect the core system directories using `ls -l /`.
5. Review the characteristics of common Linux file systems (XFS, EXT4, Btrfs).

### 3. Fully Written Command & Script Blocks

```bash
# Navigate to the root directory
cd /

# List all top-level system directories with details
ls -l /
```

#### Core Linux Directories Reference
| Directory | Purpose |
| :--- | :--- |
| `/` | **Root directory;** the top-level parent of the entire Linux filesystem hierarchy. |
| `/bin` | Essential user command binaries (symlink to `/usr/bin`) like `ls`, `cp`, `cat`. |
| `/boot` | Static bootloader files, initramfs images, and the Linux kernel. |
| `/dev` | Device files representing physical and virtual hardware (disks, terminals). |
| `/etc` | System-wide configuration files and startup scripts. |
| `/home` | Personal home directories for standard non-root users. |
| `/lib` | Shared libraries essential for system binaries (symlink to `/usr/lib`). |
| `/media` | Automatic mount point for removable media (USB drives, CD-ROMs). |
| `/mnt` | Temporary mount point for manually mounted filesystems. |
| `/opt` | Add-on, optional, or proprietary third-party software packages. |
| `/proc` | Virtual pseudo-filesystem exposing real-time kernel and process information. |
| `/root` | Home directory of the root superuser. |
| `/sbin` | Essential system administration binaries (symlink to `/usr/sbin`). |
| `/tmp` | Temporary scratch directory cleared automatically upon system reboot. |
| `/usr` | Multi-user applications, libraries, documentation, and source code. |
| `/var` | Variable dynamic data such as system logs (`/var/log`), mail, and spool files. |

#### Common Linux File Systems Reference
| File System | Key Characteristics |
| :--- | :--- |
| **XFS** | Default in RHEL 8; high-performance 64-bit journaling file system engineered for enterprise storage and large files. |
| **EXT4** | Fourth Extended File System; widely compatible, dependable, and standard across Debian/Ubuntu distributions. |
| **Btrfs** | Copy-on-write advanced file system offering built-in snapshots, multi-device spanning, and data scrubbing. |
| **FAT32** | Universal cross-platform compatibility with Windows, Mac, and Linux; limited to 4 GB maximum file size. |
| **NTFS** | Windows NT file system supported in Linux via the `ntfs-3g` user-space driver. |

### 4. File Paths & Working Locations
* **Root Directory:** `/`
* **User Personal Directory:** `/home/<username>/` (abbreviated as `~`)
* **Superuser Home Directory:** `/root/`

### 5. Next Steps / Follow-up
Run `df -T` in your terminal: what filesystem type is mounted on your root partition (`/`) in RHEL 8?

---

# Practical 2: Basic System Commands & Text Analysis

## 2.a: Input-Output Redirection & Piping

### 1. Direct & Encouraging Overview
Every Linux program automatically connects to three standard I/O data streams: **Standard Input (`stdin`)** for receiving data, **Standard Output (`stdout`)** for regular output, and **Standard Error (`stderr`)** for error diagnostics. Redirection lets you store command output directly into files or daisy-chain commands together using pipes (`|`).

### 2. Step-by-Step Instructions
1. Open the terminal and navigate to your home directory.
2. Create sample data files using text redirection (`<` and `<<`).
3. Reroute command output into a new file using overwrite redirection (`>`).
4. Append additional listings to the same file using append redirection (`>>`).
5. Isolate and save error messages using error redirection (`2>` and `2>>`).
6. Connect the output of one command into the input of another using a pipe (`|`).

### 3. Fully Written Command & Script Blocks

```bash
# --- Standard Input (stdin: File Descriptor 0) ---
# Create sample data
cat << 'EOF' > file1.txt
ID  Name
1   Ram
2   Ajay
3   Anjali
4   Supriya
EOF

# Read file contents via standard input redirection
cat < file1.txt

# --- Standard Output (stdout: File Descriptor 1) ---
# Overwrite (>): write system hostname into host.txt
hostname > host.txt

# Append (>>): append directory listing to host.txt without deleting existing text
ls >> host.txt

# Verify host.txt contents
cat host.txt

# --- Standard Error (stderr: File Descriptor 2) ---
# Redirect error message (2>) into error.txt
cd /root/ 2> error.txt
cat error.txt
# Output: bash: cd: /root/: Permission denied

# Append error message (2>>) into error.txt
cd Ram/ 2>> error.txt
cat error.txt

# --- Pipe Operator (|) ---
# Connect the output of ls directly into grep with line numbers (-n)
ls | grep -n "file"
```

### 4. File Paths & Working Locations
* **Working Directory:** `/home/<username>/`
* **Generated Files:** `~/file1.txt`, `~/host.txt`, `~/error.txt`

### 5. Next Steps / Follow-up
Run `ls NonExistentFolder > output.txt 2>&1`: observe how `2>&1` redirects standard error into the same channel as standard output.

---

## 2.b: Text Analysis Using `grep` and Regular Expressions

### 1. Direct & Encouraging Overview
The `grep` (*Global Regular Expression Print*) utility searches text files and command outputs for specific keywords or patterns. By combining `grep` with regular expression anchors (`^` for line beginnings and `$` for line endings), you can rapidly filter large log files, system dumps, and datasets.

### 2. Step-by-Step Instructions
1. Navigate to your terminal and prepare sample text files (`file1.txt`, `abc.txt`, `def.txt`, `sample.txt`).
2. Run case-insensitive searches with the `-i` flag.
3. Invert match to exclude specific keywords using `-v`.
4. Count the frequency of matching lines using `-c`.
5. Match exact whole words using `-w` and print line numbers with `-n`.
6. Search across multiple files simultaneously and list matching filenames using `-l`.
7. Apply regex anchors (`^` and `$`) to target pattern boundaries.

### 3. Fully Written Command & Script Blocks

```bash
# Case 1: Case-insensitive search (ignores upper and lower case)
ls | grep -i "File"

# Case 2: Invert search (prints everything EXCEPT lines containing 'Ram')
grep -v "Ram" file1.txt

# Case 3: Count total matching lines (-c)
grep -c "new" sample.txt

# Case 4: Search for exact whole word match (-w prevents matching 'name1' or 'surname')
grep -w "name" new4.txt

# Case 5: Print matching lines along with their line numbers (-n)
grep -n "name" new4.txt

# Case 6: Search across multiple files simultaneously
grep "name" abc.txt def.txt

# Case 7: Search for multiple distinct patterns (-e)
grep -e "id" -e "sita" abc.txt

# Case 8: Print only the filenames containing the match (-l)
grep -l "name" abc.txt def.txt

# Case 9: Read search patterns from a file (-f)
grep -f file1.txt abc.txt def.txt

# Case 10: Match lines STARTING with the specified pattern (^ anchor)
grep "^began" sample.txt

# Case 11: Match lines ENDING with the specified pattern ($ anchor)
grep "source$" sample.txt
```

### 4. File Paths & Working Locations
* **Working Directory:** `/home/<username>/`
* **Target Files:** `~/file1.txt`, `~/abc.txt`, `~/def.txt`, `~/sample.txt`

### 5. Next Steps / Follow-up
What regex pattern would you pass to `grep` to find lines that contain only digits from start to end? *(Hint: combine `^`, `[0-9]*`, and `$`)*.

---

## 2.c: Log In and Switch Users in Multi-User Targets

### 1. Direct & Encouraging Overview
RHEL uses `systemd` targets to control whether the machine boots into a graphical desktop (`graphical.target`) or a lightweight text console (`multi-user.target`). Switching between targets and mastering session switching with `su -` are foundational skills for managing headless Linux servers.

### 2. Step-by-Step Instructions
1. Inspect the system's current default boot target using `systemctl`.
2. Reconfigure the default boot target to `multi-user.target`.
3. Reboot into command-line mode and log in with your standard user account.
4. Verify your current identity with `whoami`.
5. Escalate to the superuser (`root`) using `su -`.
6. Exit the root session and restore `graphical.target` as default.
7. Reboot the system to return to the graphical desktop.

### 3. Fully Written Command & Script Blocks

```bash
# Step 1: Check current default boot target
systemctl get-default
# Output: graphical.target

# Step 2: Set Multi-User Target (CLI mode) as default
systemctl set-default multi-user.target
# Output: Created symlink /etc/systemd/system/default.target -> /usr/lib/systemd/system/multi-user.target

# Step 3: Reboot into text mode
reboot

# Step 4: Log in at the text prompt:
# tyit-rhel8 login: rmishra
# Password: <your_password>

# Step 5: Verify the active logged-in user
whoami
# Output: rmishra

# Step 6: Switch to root user session (the '-' loads root's environment and profile)
su -
# Enter root password when prompted

# Step 7: Verify root session
whoami
# Output: root

# Step 8: Exit root session
exit
# Output: logout

# Step 9: Restore Graphical Target as default
systemctl set-default graphical.target

# Step 10: Reboot back into the graphical desktop
reboot
```

### 4. File Paths & Working Locations
* **Default Target Symlink:** `/etc/systemd/system/default.target`
* **System Target Definitions:** `/usr/lib/systemd/system/multi-user.target` and `/usr/lib/systemd/system/graphical.target`

### 5. Next Steps / Follow-up
What is the difference between switching users with `su username` versus `su - username`?

---

## 2.d: Working with Text Files (`cat`, `cut`, `sort`, `wc`, `less`, `head`, `tail`, `awk`)

### 1. Direct & Encouraging Overview
Linux administrators rely on a suite of stream-processing utilities to inspect, slice, sort, and reformat plain-text datasets and configuration files without opening interactive editors.

### 2. Step-by-Step Instructions
1. View and inspect file contents with line numbers and hidden formatting using `cat`.
2. Extract specific character positions and delimited columns using `cut`.
3. Sort records alphabetically, numerically, or in human-readable units using `sort`.
4. Count lines, words, and characters with `wc`.
5. Page through large files interactively using `less`.
6. Preview the first and last lines of files using `head` and `tail`, including live log streaming (`tail -f`).
7. Extract columns and filter records conditionally using `awk`.

### 3. Fully Written Command & Script Blocks

```bash
# --- 1. Cat Command ---
cat abc.txt                         # View entire file contents
cat abc.txt def.txt                 # View multiple files sequentially
cat -n abc.txt                      # Display line numbers
cat -s TYIT2627.txt                 # Squeeze multiple consecutive blank lines into one
cat -A TYIT2627.txt                 # Show hidden characters (tabs as ^I, line ends as $)
cat -T -E TYIT2627.txt              # Explicitly display tabs (-T) and line endings (-E)

# --- 2. Cut Command ---
cut -c 1-4 sample.txt               # Extract characters 1 through 4 from each line
cut -c 1 sample.txt                 # Extract the first character from each line
echo "2026-07-07 SYSTEM_ERR: Database timeout" | cut -c 12-21
cut -d ':' -f1 /etc/passwd          # Extract field 1 (usernames) with colon (:) delimiter

# --- 3. Sort Command ---
sort abc.txt                        # Sort lines alphabetically
sort -n abc.txt                     # Sort numerically in ascending order
sort -u abc.txt                     # Remove duplicate lines while sorting
sort -h abc.txt                     # Sort human-readable numbers (2K, 4M, 1G)
sort -o abc_sorted.txt abc.txt      # Save sorted output directly to a target file

# --- 4. Wc Command ---
wc sample.txt                       # Display lines, words, and byte counts
wc -l sample.txt                    # Display line count only
wc -w sample.txt                    # Display word count only
wc -c sample.txt                    # Display byte count only
wc -m sample.txt                    # Display character count only
wc -L sample.txt                    # Display length of the longest line

# --- 5. Less Command ---
less myFile0.csv
# Key bindings inside less:
#   Space or 'f': move forward one full page
#   'b': move backward one full page
#   Enter or Down Arrow: move forward one line
#   Up Arrow: move backward one line
#   'g' / 'G': jump to beginning / end of file
#   /pattern: search forward for pattern
#   ?pattern: search backward for pattern
#   'n' / 'N': repeat search next / previous
#   'q': quit less

# --- 6. Head & Tail Commands ---
head fruits.txt                     # Display first 10 lines (default)
head -n 5 fruits.txt                # Display first 5 lines
head -c 20 sample.txt               # Display first 20 characters
head -q sample.txt fruits.txt       # Suppress file headers when inspecting multiple files
tail fruits.txt                     # Display last 10 lines (default)
tail -n 5 fruits.txt                # Display last 5 lines from end
tail -c 20 sample.txt               # Display last 20 characters from end
tail -f error.log                   # Monitor file updates in real time (press Ctrl+C to stop)

# --- 7. Awk Command ---
cat myFile1.txt                     # Display original file structure
awk '{print $1, $3}' myFile1.txt    # Print column 1 and column 3
awk -F: '{print $1}' /etc/passwd    # Extract column 1 with custom colon delimiter
awk '/test/ {print $0}' /etc/passwd # Print records matching pattern 'test'
awk '{print NR, $0}' myFile1.txt    # Print record numbers (NR) alongside content
awk '$1==100 {print $2}' myFile1.txt # Print column 2 only where column 1 equals 100
```

### 4. File Paths & Working Locations
* **Working Directory:** `/home/<username>/`
* **System Database:** `/etc/passwd`
* **Sample Data Files:** `~/abc.txt`, `~/fruits.txt`, `~/myFile1.txt`, `~/error.log`

### 5. Next Steps / Follow-up
Combine `awk` and `sort`: how would you extract the login shell (field 7) from `/etc/passwd`, count occurrences of each shell, and sort them in numerical order?

---

# Practical 3: Essential File Management Tools

## 3.a & 3.e: Managing Files Using Hard and Soft (Symbolic) Links

### 1. Direct & Encouraging Overview
Links are pointers to files. A **hard link** points directly to the underlying disk index node (**inode**), sharing data blocks; if the original filename is deleted, the data remains intact. A **soft (symbolic) link** acts like a shortcut storing the file's pathname; if the target file is removed, the symbolic link breaks.

### 2. Step-by-Step Instructions
1. Create a dedicated practice directory named `Soft_Hard_Link`.
2. Create initial data files (`abc.txt` and `def.txt`).
3. Create a hard link with `ln` and compare inode numbers using `ls -li`.
4. Delete the original file and verify that data is preserved through the hard link.
5. Create a symbolic link with `ln -s` pointing to a file and another pointing to a directory.
6. Verify that soft links possess unique inode numbers and relative path pointers.
7. Delete the target file and confirm that the soft link becomes broken.

### 3. Fully Written Command & Script Blocks

```bash
# Setup working directory
mkdir Soft_Hard_Link && cd Soft_Hard_Link

# Prepare test data
echo -e "ram\nshyam\nsita\ngita" > abc.txt
echo -e "vijay\najay\nanjali\nshivani" > def.txt

# --- Hard Links ---
# Create hard link: ln [target_file] [link_name]
ln abc.txt abc_h.txt

# Verify with inode listings (-i)
ls -li
# Observe: both abc.txt and abc_h.txt share the exact same inode number and link count = 2

# Compare file contents
cat abc.txt
cat abc_h.txt

# Delete original file
rm abc.txt

# Verify data remains accessible through the hard link
cat abc_h.txt

# Note: Hard links cannot normally be created for directories:
# ln my_folder my_folder_h -> "ln: hard link not allowed for directory"

# --- Soft (Symbolic) Links ---
# Create symbolic link to a file: ln -s [target_file] [link_name]
ln -s def.txt def_s.txt

# Create symbolic link to a directory
mkdir hard_link
ln -s hard_link hard_link_s

# Verify with inode listings
ls -li
# Observe: def.txt and def_s.txt have different inode numbers; def_s.txt shows 'l' permissions

# Read file through symlink
cat def_s.txt

# Delete original target file
rm def.txt

# Verify that the symbolic link is now broken
cat def_s.txt
# Output: cat: def_s.txt: No such file or directory
```

### 4. File Paths & Working Locations
* **Working Directory:** `/home/<username>/Soft_Hard_Link/`
* **Hard Linked Files:** `abc_h.txt`
* **Symbolic Pointers:** `def_s.txt -> def.txt`, `hard_link_s -> hard_link`

### 5. Next Steps / Follow-up
Why can symbolic links point across different disk partitions or network filesystems while hard links are strictly restricted to a single filesystem?

---

## 3.b & 3.d: Archiving and Compression (`tar`, `star`, `gzip`, `bzip2`)

### 1. Direct & Encouraging Overview
**Archiving** combines multiple files and directories into a single container archive (`.tar` or `.star`) while preserving file attributes and permissions. **Compression** (`gzip` and `bzip2`) reduces the storage size of archives by removing redundant binary data.

### 2. Step-by-Step Instructions
1. Archive files using the traditional `tar` command with options `-cvf`.
2. Inspect archive contents without unpacking using `tar -tvf`.
3. Extract archive contents into current and target directories using `tar -xvf -C <path>`.
4. Install and create tape archives using `star`.
5. Compress files using `gzip` and `bzip2` and compare storage savings using `ls -lh`.
6. Decompress archives using the `-d` option.

### 3. Fully Written Command & Script Blocks

```bash
# Set up practice environment
mkdir -p ~/Archiving_Compression && cd ~/Archiving_Compression
touch fruits.txt myFile0.csv

# --- 1. TAR Archiving ---
# Create archive (-c = create, -v = verbose, -f = filename; always place -f last)
tar -cvf Practical3_b_d.tar fruits.txt myFile0.csv

# List archive table of contents without extracting (-t)
tar -tvf Practical3_b_d.tar

# Extract archive into the current directory (-x)
tar -xvf Practical3_b_d.tar

# Extract archive into a specific target directory (-C)
mkdir ArchivedFiles
tar -xvf Practical3_b_d.tar -C ~/Archiving_Compression/ArchivedFiles/

# --- 2. STAR Archiving Utility ---
# Install star package using dnf
sudo dnf install star -y

# Create star archive (star requires 'f=' instead of '-f')
star -c -v f=Practical3_b_d.star fruits.txt myFile0.csv

# List star archive contents
star -t -v f=Practical3_b_d.star

# Extract star archive to target directory
star -x -v f=Practical3_b_d.star -C ~/Archiving_Compression/ArchivedFiles/

# --- 3. GZIP Compression ---
# Check file size before compression
ls -lh Practical3_b_d.star

# Compress file (replaces original with .gz)
gzip Practical3_b_d.star

# Compress while keeping the original uncompressed file (-k)
gzip -k Practical3_b_d.tar

# Compress all files in a folder recursively (-r)
mkdir CompressesFiles && cp fruits.txt CompressesFiles/
gzip -r CompressesFiles/

# Force overwrite existing compressed file without prompting (-f)
gzip -kf Practical3_b_d.tar

# Decompress a gzip file (-d)
gzip -d Practical3_b_d.star.gz

# --- 4. BZIP2 Compression ---
# Compress file using bzip2 (higher compression ratio, creates .bz2)
bzip2 -k Practical3_b_d.tar

# Compare file sizes between uncompressed, gzip, and bzip2
ls -lh Practical3_b_d.tar*

# Decompress bzip2 file (-d)
bzip2 -d Practical3_b_d.tar.bz2
```

### 4. File Paths & Working Locations
* **Working Directory:** `/home/<username>/Archiving_Compression/`
* **Destination Folder:** `/home/<username>/Archiving_Compression/ArchivedFiles/`
* **Archive Files:** `Practical3_b_d.tar`, `Practical3_b_d.star`
* **Compressed Bundles:** `Practical3_b_d.tar.gz`, `Practical3_b_d.tar.bz2`

### 5. Next Steps / Follow-up
Compare compression performance: how does `tar -czvf archive.tar.gz` (gzip) compare to `tar -cjvf archive.tar.bz2` (bzip2) in terms of speed and resulting file size?

---

## 3.c: Create, Delete, Copy, Move, and Rename Files & Directories

### 1. Direct & Encouraging Overview
File and directory manipulation is the bedrock of system administration. Mastering basic command-line operations—creating files via `touch`, `echo`, `cat`, and text editors, building nested directories, recursively copying directory trees, moving resources, and safely deleting obsolete data—is required for all workflows.

### 2. Step-by-Step Instructions
1. Create empty files using `touch`, populated files using `echo` and `cat`, and formatted files using `vi` and `nano`.
2. Create single, multiple, and nested directories using `mkdir -p`.
3. Copy individual files and recursively copy entire directories with `cp -r`.
4. Move and rename files and directories using `mv`.
5. Remove individual files, empty directories with `rmdir`, and nested trees using `rm -r`.

### 3. Fully Written Command & Script Blocks

```bash
# --- 1. Creating Files ---
touch file1.txt                     # Create empty file or update timestamp
echo "Hello World" > file2.txt      # Create file and populate with echo

# Create file using cat (type text, then press Enter and Ctrl+D to exit)
cat > file3.txt
Hello World, my name is Chitti.

# Create and edit using vi (:wq to save and quit)
vi file4.txt

# Create and edit using nano (Ctrl+O to save, Enter to confirm, Ctrl+X to exit)
nano file5.txt

# --- 2. Creating Directories ---
mkdir TYIT-A                        # Create single directory
mkdir TYIT-B TYIT-C                 # Create multiple sibling directories
mkdir -p TYIT-A/A_division_dir      # Create nested parent and child directories
mkdir /home/rmishra/Practical3_c/RHEL # Create directory using absolute path

# --- 3. Copying Files & Directories ---
cp file1.txt file2.txt RHEL/        # Copy multiple files into target directory
cp -r RHEL/ TYIT-A/                 # Recursively copy an entire directory (-r is mandatory)

# --- 4. Moving & Renaming ---
mv file3.txt file4.txt TYIT-B/      # Move files into a directory
mv TYIT-B/ TYIT-C/                  # Move a directory inside another directory
mv file5.txt file6.txt              # Rename a file
mv RHEL/ RHEL_NEW/                  # Rename a directory

# --- 5. Deleting Files & Directories ---
rm file1.txt                        # Delete a single file
rm file2.txt file6.txt              # Delete multiple files
rm -d A_division_dir/               # Delete an empty directory (or use rmdir)
rmdir RHEL/                         # Remove empty directory
rm -r RHEL_NEW/                     # Recursively remove a non-empty directory and all contents
```

### 4. File Paths & Working Locations
* **Working Directory:** `/home/<username>/Practical3_c/`
* **Directory Trees:** `TYIT-A/`, `TYIT-B/`, `TYIT-C/`, `RHEL/`, `RHEL_NEW/`

### 5. Next Steps / Follow-up
Why does `rmdir` fail on a folder containing hidden configuration files (like `.bashrc`), and what safety flag can you add to `rm -r` to prompt for confirmation before deleting each file?

---

# Practical 4: Users, Groups, and Permissions

## 4.a: Creating and Managing Users

### 1. Direct & Encouraging Overview
Linux is a multi-user operating system where every process and file belongs to an identified user account. Creating user accounts with explicit settings (home directories, customized login shells, and descriptive comments) and modifying user properties using `usermod` are primary security administration tasks.

### 2. Step-by-Step Instructions
1. Create a basic user account using `useradd`.
2. Create an enterprise user account with customized primary group, login shell, description, and custom home directory path.
3. Verify user details, User ID (UID), and Group ID (GID) using `id`.
4. Inspect the system account database in `/etc/passwd`.
5. Modify user attributes (comment, shell, home directory) using `usermod`.
6. Set and test user authentication passwords with `passwd`.

### 3. Fully Written Command & Script Blocks

```bash
# 1. Create a basic user account
sudo useradd Sandeep

# Verify account UID, GID, and assigned group
id Sandeep
# Output: uid=1001(Sandeep) gid=1001(Sandeep) groups=1001(Sandeep)

# 2. Create a user account with explicit parameters:
# -g : Primary group
# -s : Default login shell
# -c : Description comment
# -m -d : Create and specify custom home directory
sudo useradd -g TYIT -s /bin/bash -c "Om Sinha" -m -d /home/osinha osinha

# 3. Verify user account entry in /etc/passwd
grep "osinha" /etc/passwd
# Format: username:x:UID:GID:comment:home_directory:login_shell
# Output: osinha:x:1002:1002:Om Sinha:/home/osinha:/bin/bash

# 4. Modify user settings using usermod:
sudo usermod -c "Om Sinha TYIT" osinha          # Update user comment
sudo usermod -s /sbin/nologin osinha            # Set shell to nologin (disables interactive login)
sudo usermod -s /bin/bash osinha                # Restore bash shell

# 5. Move user home directory to a new location (-m moves existing files)
sudo usermod -m -d /home/newfolder/ osinha

# 6. Set or reset a user password
sudo passwd osinha
```

### 4. File Paths & Working Locations
* **User Accounts Database:** `/etc/passwd`
* **Default User Shells:** `/bin/bash`, `/sbin/nologin`
* **Home Directories:** `/home/<username>/`

### 5. Next Steps / Follow-up
What security risk does giving a system service account (such as `apache` or `ftp`) a valid login shell like `/bin/bash` introduce?

---

## 4.b: Creating and Managing Groups

### 1. Direct & Encouraging Overview
Groups allow administrators to manage access permissions for teams of users simultaneously rather than configuring permissions individually. Users belong to one **primary group** (assigned at creation) and can belong to multiple **supplementary (secondary) groups**.

### 2. Step-by-Step Instructions
1. Create a new system group using `groupadd`.
2. Add a user to a supplementary group using `usermod -aG`.
3. Verify group memberships using `id <username>`.
4. Remove a user from a group using `gpasswd -d`.
5. Assign multiple supplementary groups simultaneously.
6. Inspect group definitions in `/etc/group`.

### 3. Fully Written Command & Script Blocks

```bash
# 1. Create a new group
sudo groupadd TYIT

# 2. Add a user to a supplementary group (-a = append, -G = supplementary group)
# CRITICAL: Always use -a with -G to avoid overwriting existing group memberships
sudo usermod -aG TYIT Sandeep

# 3. Verify group memberships
id Sandeep
# Output: uid=1001(Sandeep) gid=1001(Sandeep) groups=1001(Sandeep),1004(TYIT)

# 4. Remove a user from a group
sudo gpasswd -d Sandeep TYIT
# Output: Removing user Sandeep from group TYIT

# 5. Assign multiple groups simultaneously (-G group1,group2)
sudo groupadd Developers
sudo groupadd Testers
sudo usermod -aG Developers,Testers Sandeep

# 6. View the group database file
grep "Developers" /etc/group
# Format: group_name:password:GID:user_list
```

### 4. File Paths & Working Locations
* **Group Database:** `/etc/group`
* **Encrypted Group Passwords:** `/etc/gshadow`

### 5. Next Steps / Follow-up
Why will a user currently logged into a terminal not see newly added group permissions until they log out and log back in (or run `newgrp`)?

---

## 4.d: Passwords and Password Aging Policies

### 1. Direct & Encouraging Overview
Enforcing password aging policies ensures accounts are protected against credential theft by requiring regular password rotations, minimum change intervals, warning periods, and automatic account expiration. The `chage` utility controls these settings on local Linux systems.

### 2. Step-by-Step Instructions
1. Inspect current password aging parameters for a user using `chage -l`.
2. Set minimum password age (`-m`) to prevent immediate consecutive changes.
3. Set maximum password age (`-M`) to force password renewal after 90 days.
4. Set password warning period (`-W`) to alert users 10 days before expiration.
5. Set inactivity grace period (`-I`) to disable accounts if passwords are not renewed.
6. Force an immediate password change upon next login using `chage -d 0`.
7. Verify parameters in `/etc/shadow` and review default policies in `/etc/login.defs`.

### 3. Fully Written Command & Script Blocks

```bash
# 1. View current password aging parameters
sudo chage -l osinha

# 2. Set minimum days between password changes (-m: must wait 7 days to change again)
sudo chage -m 7 osinha

# 3. Set maximum password validity (-M: password expires after 90 days)
sudo chage -M 90 osinha

# 4. Set expiration warning days (-W: warn 10 days before expiration)
sudo chage -W 10 osinha

# 5. Set inactive grace period (-I: locks account 10 days after password expires)
sudo chage -I 10 osinha

# 6. Force password change at next login (-d 0 sets last change date to 0)
sudo chage -d 0 osinha

# 7. Verify resulting record in /etc/shadow
sudo grep "osinha" /etc/shadow
# Format: username:password:lastchg:min:max:warn:inactive:expire:reserved
# Sample Output: osinha:$6$WUQJ1IK2...:0:7:90:10:10:::

# 8. Modify system-wide defaults for future accounts in /etc/login.defs:
# PASS_MAX_DAYS   90
# PASS_MIN_DAYS   7
# PASS_MIN_LEN    8
# PASS_WARN_AGE   10
```

### 4. File Paths & Working Locations
* **Encrypted Passwords & Aging Settings:** `/etc/shadow`
* **Default System Account Policies:** `/etc/login.defs`

### 5. Next Steps / Follow-up
In `/etc/shadow`, what does a password hash starting with `$6$` indicate regarding the cryptographic hashing algorithm used?

---

## 4.e: Superuser Access (`su`, `sudo`, `wheel`, and `visudo`)

### 1. Direct & Encouraging Overview
Root privileges allow unrestricted administrative control. Logging in directly as root is discouraged for security reasons. Best practice is to log in as a standard user and elevate privileges either via `su -` or by delegating commands with `sudo` and the `wheel` administrative group.

### 2. Step-by-Step Instructions
1. Switch between user accounts using `su` and `su -`.
2. Exit elevated sessions safely using `exit`.
3. Grant full sudo access to an account by adding them to the `wheel` group.
4. Safely open `/etc/sudoers` using the `visudo` editor.
5. Delegate specific, limited commands to a user without granting full root access.
6. Test delegated permissions using `sudo`.

### 3. Fully Written Command & Script Blocks

```bash
# --- 1. Switching Users with su ---
su Sandeep       # Switches user while preserving current working directory/environment
exit

su - Sandeep      # Switches user and initializes complete login environment (home, path)
exit

# --- 2. Granting Full Sudo Access via the Wheel Group ---
# In RHEL 8, members of the 'wheel' group have full administrative sudo rights
sudo usermod -aG wheel Sandeep

# Test sudo access as user Sandeep
su - Sandeep
sudo systemctl restart httpd
exit

# --- 3. Delegating Limited Sudo Access via visudo ---
# Remove Sandeep from wheel to restrict access
sudo gpasswd -d Sandeep wheel

# Open sudoers file safely (visudo validates syntax on save)
sudo visudo

# Add the following command alias and user permission inside the file:
# Cmnd_Alias DELEGATING = /bin/chown, /bin/chmod, /bin/chgrp
# Sandeep ALL=(ALL) DELEGATING

# Test delegated command as user Sandeep
su - Sandeep
sudo chown Sandeep /abc.txt      # Succeeds (allowed in DELEGATING alias)
sudo systemctl restart httpd    # Fails (not permitted)
exit
```

### 4. File Paths & Working Locations
* **Sudoers Privilege Rules:** `/etc/sudoers` (must only be edited using `visudo`)
* **Modular Sudo Rules Directory:** `/etc/sudoers.d/`

### 5. Next Steps / Follow-up
Why must the `/etc/sudoers` file never be edited directly with standard text editors like `vi` or `nano`?

---

# Practical 5: Managing Software

## 5.c: Managing Software Packages with RPM

### 1. Direct & Encouraging Overview
The **RPM** (*Red Hat Package Manager*) is the low-level package manager for enterprise Linux distributions. While higher-level tools like `dnf` automatically fetch packages from remote repositories and resolve dependencies, `rpm` is essential for installing local `.rpm` binaries, verifying package integrity, and querying configuration files.

### 2. Step-by-Step Instructions
1. Locate or download a local `.rpm` package (e.g., `vsftpd-3.0.3-36.el8.x86_64.rpm`).
2. Install the package with verbose output and progress hashes using `rpm -ivh`.
3. Upgrade an existing package using `rpm -Uvh`.
4. Query all installed packages on the system using `rpm -qa`.
5. Search for specific installed packages by piping `rpm -qa` into `grep`.
6. Inspect package metadata and descriptions using `rpm -qi`.
7. Identify configuration files installed by the package using `rpm -qc`.
8. Erase (uninstall) the package using `rpm -evh`.

### 3. Fully Written Command & Script Blocks

```bash
# 1. Install an RPM package file (-i = install, -v = verbose, -h = hash progress marks)
sudo rpm -ivh vsftpd-3.0.3-36.el8.x86_64.rpm

# 2. Upgrade an existing package or install if not present (-U = upgrade)
sudo rpm -Uvh vsftpd-3.0.3-36.el8.x86_64.rpm

# 3. Query all installed packages on the operating system
rpm -qa

# 4. Search for a specific installed package using grep
rpm -qa | grep "httpd"
rpm -qa | grep "vsftpd"

# 5. Display comprehensive package information and description (-qi)
rpm -qi vsftpd

# 6. List all configuration files deployed by the package (-qc)
rpm -qc vsftpd
# Expected Output:
# /etc/logrotate.d/vsftpd
# /etc/pam.d/vsftpd
# /etc/vsftpd/ftpusers
# /etc/vsftpd/user_list
# /etc/vsftpd/vsftpd.conf

# 7. Erase (uninstall) the package (-e)
sudo rpm -evh vsftpd
```

### 4. File Paths & Working Locations
* **RPM Local Database:** `/var/lib/rpm/`
* **Package Configuration Directory:** `/etc/vsftpd/`

### 5. Next Steps / Follow-up
What error occurs if you attempt to install a package using `rpm -ivh` that requires missing library dependencies, and how does `sudo dnf install` solve this problem?

---

# Practical 6: Managing Processes

## 6.a: Introduction to Process Management

### 1. Direct & Encouraging Overview
In Linux, every program in execution is assigned a unique **Process ID (PID)** and a **Parent Process ID (PPID)**. Process management enables administrators to monitor running programs, trace parent-child process relationships, and manage system resources efficiently.

### 2. Step-by-Step Instructions
1. Run a program in the background using the ampersand operator (`&`).
2. View shell processes using `ps`.
3. Display complete process information across all users using `ps -ef` and `ps aux`.
4. Trace process hierarchies using `pstree`.
5. Filter processes belonging to specific users or groups.

### 3. Fully Written Command & Script Blocks

```bash
# 1. Start a command in the background (&)
firefox &
# Output: [1] 3260  (Job 1, PID 3260)

# 2. View processes running in the current shell
ps

# 3. View all running processes with full details (standard UNIX syntax)
ps -ef

# 4. View all processes in BSD syntax with CPU/Memory utilization
ps aux

# 5. Display the tree of processes showing parent-child relationships
pstree

# 6. Filter running processes by username
ps -u rmishra

# 7. Filter running processes by group name
ps -G rmishra

# 8. Trace a specific application process
ps -ef | grep "firefox"
```

### 4. File Paths & Working Locations
* **Kernel Process Filesystem:** `/proc/` (live kernel representations under `/proc/<PID>/`)

### 5. Next Steps / Follow-up
In the output of `ps -ef`, what process always holds PID 1, and what is its role on a Linux system?

---

## 6.b & 6.c: Managing Shell Jobs & Process Priorities

### 1. Direct & Encouraging Overview
Job control allows you to pause active terminal programs, resume them in the background, or bring them back to the foreground. Process priority (**niceness**) allows you to assign CPU preference to important workloads, while `nohup` keeps long-running tasks alive even if the terminal disconnects.

### 2. Step-by-Step Instructions
1. Run a foreground task and pause it using `Ctrl + Z`.
2. Inspect suspended tasks using the `jobs` command.
3. Bring a task back to the interactive foreground using `fg`.
4. Resume a task in the background using `bg`.
5. Launch a process with a custom priority using `nice -n`.
6. Inspect the nice value (`NI` column) of a process using `ps -l`.
7. Launch an immune background process using `nohup`.

### 3. Fully Written Command & Script Blocks

```bash
# --- 1. Shell Job Control ---
# Start a script in foreground
./jobs.sh
# Press Ctrl+Z to suspend process
# Output: [1]+ Stopped ./jobs.sh

# List all active and suspended jobs in current shell
jobs
# Note: '+' indicates the current default job; '-' indicates previous job

# Resume job 1 in foreground
fg %1
# Press Ctrl+Z again to pause

# Resume job 1 in background
bg %1
# Output: [1]+ ./jobs.sh &

# --- 2. Process Niceness (Priority) ---
# Niceness scale ranges from -20 (highest priority) to 19 (lowest priority). Default is 0.

# Start a script with lower priority (nice value = 4)
nice -n 4 ./jobs.sh &

# Find PID of the script
ps -ef | grep "jobs.sh"

# Inspect the NI column to verify nice value
ps -l <PID>

# --- 3. Nohup (No Hang Up) ---
# Launch a background script immune to terminal hangups
nohup ./jobs.sh &
# Output: nohup: ignoring input and appending output to 'nohup.out'

# Verify the process is still running from another terminal
ps -ef | grep "jobs.sh"

# Close the terminal session; process continues executing in the background
```

### 4. File Paths & Working Locations
* **Default Output Log:** `./nohup.out`

### 5. Next Steps / Follow-up
Can a regular non-root user assign a negative nice value (such as `-5`) to give their process higher CPU priority? Why or why not?

---

## 6.f: Identify Intensive Processes and Kill Processes

### 1. Direct & Encouraging Overview
When a system becomes sluggish, administrators must quickly identify runaway processes consuming excessive CPU cycles or RAM and terminate them cleanly. Signals allow you to shut down programs gracefully (`SIGTERM` / 15) or force immediate termination (`SIGKILL` / 9).

### 2. Step-by-Step Instructions
1. Display the top CPU-consuming processes sorted in descending order.
2. Display the top memory-consuming processes sorted in descending order.
3. Identify the target process ID (PID).
4. Terminate the process gracefully using `kill PID`.
5. Terminate unresponsive processes forcefully using `kill -9 PID`.
6. Verify that the process has released system memory.

### 3. Fully Written Command & Script Blocks

```bash
# 1. Identify the top 10 CPU-consuming processes (descending order)
ps aux --sort=-%cpu | head -n 11

# 2. Identify the top 10 Memory-consuming processes (descending order)
ps aux --sort=-%mem | head -n 11

# 3. Graceful termination (SIGTERM - Signal 15: allows process to save state and clean up)
# Example: Firefox process running with PID 12272
kill 12272

# 4. Verify process has closed
ps aux --sort=-%mem | head -n 11

# 5. Forceful termination (SIGKILL - Signal 9: immediate kernel-level termination)
kill -9 12272
```

### 4. File Paths & Working Locations
* **System Process Data:** `/proc/<PID>/status`

### 5. Next Steps / Follow-up
Why should you always try `kill <PID>` before using `kill -9 <PID>` on a database server like MySQL or PostgreSQL?

---

# Practical 7: Configuring Firewalls

## 7.a: Linux Firewall with `iptables`

### 1. Direct & Encouraging Overview
The `iptables` tool controls packet filtering directly in the Linux kernel via three core elements: **Tables** (such as the default `filter` table), **Chains** (`INPUT`, `OUTPUT`, and `FORWARD`), and **Targets** (`ACCEPT`, `DROP`, `REJECT`). Configuring explicit allow rules while establishing a default drop policy forms a secure perimeter.

### 2. Step-by-Step Instructions
1. Flush existing firewall rules to avoid rule conflicts.
2. Set default policies to `DROP` for incoming traffic and `ACCEPT` for outgoing traffic.
3. Allow local loopback traffic (`lo`) and established sessions.
4. Allow essential network ports: SSH (22), HTTP (80), HTTPS (443), and ICMP (Ping).
5. Verify your host IP using `ifconfig` and test network connectivity from a client machine.
6. Block outbound ICMP traffic to test rule enforcement.
7. Inspect active rules with line numbers and delete rules by index.

### 3. Fully Written Command & Script Blocks

```bash
# 1. Flush (delete) all existing rules
sudo iptables -F

# 2. Set default chain policies
sudo iptables -P INPUT DROP
sudo iptables -P FORWARD DROP
sudo iptables -P OUTPUT ACCEPT

# 3. Allow internal loopback communication
sudo iptables -A INPUT -i lo -j ACCEPT

# 4. Allow packets belonging to established or related connections
sudo iptables -A INPUT -m state --state ESTABLISHED,RELATED -j ACCEPT

# 5. Allow incoming traffic for specific services:
sudo iptables -A INPUT -p tcp --dport 22 -j ACCEPT   # SSH
sudo iptables -A INPUT -p tcp --dport 80 -j ACCEPT   # HTTP
sudo iptables -A INPUT -p tcp --dport 443 -j ACCEPT  # HTTPS
sudo iptables -A INPUT -p icmp -j ACCEPT             # ICMP Ping

# 6. Check host IP address
ifconfig

# 7. Block outgoing ICMP traffic
sudo iptables -A OUTPUT -p icmp -j DROP

# 8. List all active firewall rules
sudo iptables -L

# 9. List rules with line numbers and numeric port/IP representations
sudo iptables -L --line-numbers -n
sudo iptables -L INPUT --line-numbers -n
sudo iptables -L OUTPUT --line-numbers -n

# 10. Delete a specific rule by index (e.g., delete rule #1 in INPUT chain)
sudo iptables -D INPUT 1
```

### 4. File Paths & Working Locations
* **Saved Rules File (Persistent):** `/etc/sysconfig/iptables`

### 5. Next Steps / Follow-up
What is the difference between the `DROP` target (silently discarding packets) and the `REJECT` target (sending an ICMP port-unreachable error back to the sender)?

---

## 7.b: Working with `firewalld`

### 1. Direct & Encouraging Overview
`firewalld` is the default dynamic firewall management tool in RHEL. It organizes network traffic into security **zones** (such as `public`, `home`, and `trusted`) and allows administrators to apply changes on the fly without dropping existing active connections.

### 2. Step-by-Step Instructions
1. Ensure the `firewalld` service is running and enabled.
2. Permanently allow SSH, HTTP, and HTTPS services.
3. Reload `firewalld` to apply changes into memory.
4. Verify active rules using `firewall-cmd --list-all`.
5. Test service availability from a remote client machine.
6. Remove services to verify that traffic is blocked as expected.

### 3. Fully Written Command & Script Blocks

```bash
# 1. Start firewalld daemon
sudo systemctl start firewalld

# 2. Allow services permanently across system reboots
sudo firewall-cmd --permanent --add-service=ssh
sudo firewall-cmd --permanent --add-service=http
sudo firewall-cmd --permanent --add-service=https

# 3. Reload firewall to load permanent configurations into active memory
sudo firewall-cmd --reload

# 4. Inspect active zone settings and allowed services
sudo firewall-cmd --list-all
# Output:
# public (active)
#   services: cockpit dhcpv6-client http https ssh

# --- Testing Connectivity from Client Machine ---
# In Windows Command Prompt:
# ping <rhel_ip_address>
# ssh rmishra@<rhel_ip_address>
# Browse to: http://<rhel_ip_address>

# --- Blocking / Removing Services ---
# Remove HTTP and HTTPS access
sudo firewall-cmd --permanent --remove-service=http
sudo firewall-cmd --permanent --remove-service=https
sudo firewall-cmd --reload

# Remove SSH access
sudo firewall-cmd --permanent --remove-service=ssh
sudo firewall-cmd --reload

# Verify that PuTTY connection fails with "Connection timed out"
```

### 4. File Paths & Working Locations
* **Active Zone Definitions:** `/etc/firewalld/zones/public.xml`
* **Predefined System Service Profiles:** `/usr/lib/firewalld/services/`

### 5. Next Steps / Follow-up
What is the difference between running `firewall-cmd --add-service=http` (runtime only) versus `firewall-cmd --permanent --add-service=http`?

---

# Practical 8: Configuring Apache Web Server

## 8.a & 8.b: Basic Apache Server & Configuration Architecture

### 1. Direct & Encouraging Overview
The Apache HTTP Server (`httpd` in RHEL) is an enterprise web server responsible for delivering web pages over HTTP and HTTPS. Installing Apache and understanding its modular configuration hierarchy gives you full control over web hosting, virtual domains, and diagnostic access logging.

### 2. Step-by-Step Instructions
1. Install the `httpd` package using `dnf`.
2. Start and enable the service on system boot.
3. Open HTTP traffic in `firewalld`.
4. Deploy a custom `index.html` file to the default document root (`/var/www/html/`).
5. Verify web delivery from a client browser.
6. Review the primary configuration files and log locations.

### 3. Fully Written Command & Script Blocks

```bash
# 1. Install Apache HTTP Server
sudo dnf install httpd -y

# 2. Start and enable Apache service
sudo systemctl start httpd
sudo systemctl enable httpd

# 3. Verify service status
sudo systemctl status httpd

# 4. Allow HTTP and HTTPS traffic through the firewall
sudo firewall-cmd --permanent --add-service=http
sudo firewall-cmd --permanent --add-service=https
sudo firewall-cmd --reload

# 5. Create a test web page
cd /var/www/html
cat << 'EOF' | sudo tee index.html
<!DOCTYPE html>
<html>
<head><title>Apache Web Server</title></head>
<body>
  <h1>Welcome to Apache Web Server</h1>
  <p>This is a test web page.</p>
  <p>HTTP and HTTPS traffic are working successfully.</p>
</body>
</html>
EOF

# Ensure appropriate read permissions
sudo chmod 644 /var/www/html/index.html

# 6. Restart Apache service
sudo systemctl restart httpd
```

#### Apache Core Configuration Files Reference
| File / Directory Path | Role & Purpose |
| :--- | :--- |
| `/etc/httpd/conf/httpd.conf` | **Main configuration file;** controls listening ports (`Listen 80`), server admin, and global security. |
| `/etc/httpd/conf.d/` | **Modular configuration directory;** loads all `.conf` files (VirtualHosts, SSL) automatically at boot. |
| `/var/www/html/` | **Default DocumentRoot;** default filesystem location for web files. |
| `/var/log/httpd/access_log` | **Access Log;** logs incoming client HTTP requests, IPs, timestamps, and HTTP response codes. |
| `/var/log/httpd/error_log` | **Error Log;** logs server warnings, syntax errors, permission problems, and startup issues. |

### 4. File Paths & Working Locations
* **Main Configuration:** `/etc/httpd/conf/httpd.conf`
* **Document Root:** `/var/www/html/index.html`
* **Log Files:** `/var/log/httpd/access_log`, `/var/log/httpd/error_log`

### 5. Next Steps / Follow-up
Open a browser on your client host and visit `http://<rhel_ip_address>` to confirm your web server is live.

---

## 8.c: Configuring Apache Virtual Hosts

### 1. Direct & Encouraging Overview
An Apache **Virtual Host** allows a single physical web server to host multiple independent domain names (such as `site1.local` and `site2.local`) on a single IP address. Apache inspects the incoming HTTP `Host:` header to route requests to the correct document root.

### 2. Step-by-Step Instructions
1. Create separate document root directories for `site1` and `site2`.
2. Create dedicated `index.html` files for each site.
3. Write `<VirtualHost>` configuration files inside `/etc/httpd/conf.d/`.
4. Validate configuration syntax using `httpd -t`.
5. Restart the Apache daemon.
6. Configure local DNS resolution in `/etc/hosts` and test both websites in a browser.

### 3. Fully Written Command & Script Blocks

```bash
# 1. Create document root directories
sudo mkdir -p /var/www/site1
sudo mkdir -p /var/www/site2

# 2. Create test page for Site 1
cat << 'EOF' | sudo tee /var/www/site1/index.html
<html>
<head><title>Site 1</title></head>
<body>
  <h1>Welcome to Site 1</h1>
  <p>Virtual Host 1 is active and serving content correctly.</p>
</body>
</html>
EOF

# 3. Create test page for Site 2
cat << 'EOF' | sudo tee /var/www/site2/index.html
<html>
<head><title>Site 2</title></head>
<body>
  <h1>Welcome to Site 2</h1>
  <p>Virtual Host 2 is active and serving content correctly.</p>
</body>
</html>
EOF

# 4. Create VirtualHost configuration for Site 1
cat << 'EOF' | sudo tee /etc/httpd/conf.d/site1.conf
<VirtualHost *:80>
    ServerName site1.local
    DocumentRoot /var/www/site1
</VirtualHost>
EOF

# 5. Create VirtualHost configuration for Site 2
cat << 'EOF' | sudo tee /etc/httpd/conf.d/site2.conf
<VirtualHost *:80>
    ServerName site2.local
    DocumentRoot /var/www/site2
</VirtualHost>
EOF

# 6. Test Apache configuration for syntax errors
sudo httpd -t
# Expected Output: Syntax OK

# 7. Restart Apache
sudo systemctl restart httpd

# 8. Add local hostname mappings in /etc/hosts (replace IP with your server IP)
cat << 'EOF' | sudo tee -a /etc/hosts
192.168.174.178 site1.local
192.168.174.178 site2.local
EOF

# 9. Test in browser or via curl:
curl http://site1.local
curl http://site2.local
```

### 4. File Paths & Working Locations
* **Site 1 Root:** `/var/www/site1/index.html`
* **Site 2 Root:** `/var/www/site2/index.html`
* **Virtual Host Configs:** `/etc/httpd/conf.d/site1.conf` and `/etc/httpd/conf.d/site2.conf`
* **Local Host Resolution:** `/etc/hosts`

### 5. Next Steps / Follow-up
How would you configure a custom error log specifically for `site1.local` inside its `<VirtualHost>` block?

---

# Practical 9: Creating Shell Scripts

## 9.a: Automate and Monitor Tasks & Processes

### 1. Direct & Encouraging Overview
Shell scripts allow administrators to bundle repetitive diagnostic commands into executable files. Automating monitoring checks for disk capacity, top running processes, and available RAM ensures proactive system maintenance.

### 2. Step-by-Step Instructions
1. Write a disk usage monitoring script (`disk_usage.sh`).
2. Write a top running process monitoring script (`runn_process.sh`).
3. Write a memory monitoring script (`mem_usage.sh`).
4. Grant execution permissions to the scripts using `chmod +x`.
5. Execute the scripts and analyze memory buffers versus cache.

### 3. Fully Written Command & Script Blocks

```bash
mkdir -p ~/Practical_9.a && cd ~/Practical_9.a

# --- Script 1: Disk Usage (disk_usage.sh) ---
cat << 'EOF' > disk_usage.sh
#!/bin/bash
echo "=== Disk Usage Report ==="
df -h
EOF

# --- Script 2: Top Processes (runn_process.sh) ---
cat << 'EOF' > runn_process.sh
#!/bin/bash
echo "=== Top Running Processes ==="
ps -ef | head -n 11
EOF

# --- Script 3: Memory Usage (mem_usage.sh) ---
cat << 'EOF' > mem_usage.sh
#!/bin/bash
echo "=== Memory Usage ==="
free -h
EOF

# Grant execution rights
chmod +x disk_usage.sh runn_process.sh mem_usage.sh

# Run scripts
./disk_usage.sh
./runn_process.sh
./mem_usage.sh
```

#### Memory Concepts: Buffers vs. Cache
* **Buffer:** Temporary memory reserved for raw disk block I/O operations (speeds up block reading and writing).
* **Cache:** Memory storing recently accessed files in RAM so repeated reads bypass the hard drive.

### 4. File Paths & Working Locations
* **Working Directory:** `/home/<username>/Practical_9.a/`
* **Script Files:** `~/Practical_9.a/disk_usage.sh`, `runn_process.sh`, `mem_usage.sh`

### 5. Next Steps / Follow-up
How can you modify `disk_usage.sh` to send an alert if any partition exceeds 80% usage?

---

## 9.b: Getting and Setting System Information

### 1. Direct & Encouraging Overview
Retrieving server telemetry (kernel version, OS release, uptime, and load averages) provides a snapshot of system health. Setting configuration properties—such as changing the system hostname using `hostnamectl`—ensures unambiguous identity across network infrastructure.

### 2. Step-by-Step Instructions
1. Create an inventory script (`system_info.sh`) collecting hostname, kernel version, OS release, user, and uptime.
2. Make the script executable and interpret the 1-minute, 5-minute, and 15-minute load averages.
3. Create a configuration script (`hostname.sh`) to modify the system hostname using `hostnamectl`.
4. Refresh the shell environment with `exec bash` to verify prompt updates.

### 3. Fully Written Command & Script Blocks

```bash
mkdir -p ~/Practical_9.b && cd ~/Practical_9.b

# --- Script 1: System Information (system_info.sh) ---
cat << 'EOF' > system_info.sh
#!/bin/bash
echo "Hostname:       $(hostname)"
echo "Kernel Version: $(uname -r)"
echo -n "Operating System: "
grep "PRETTY_NAME" /etc/os-release | cut -d '=' -f2 | tr -d '"'
echo "Current User:   $(whoami)"
echo "System Uptime:  $(uptime)"
EOF

# --- Script 2: Change Hostname (hostname.sh) ---
cat << 'EOF' > hostname.sh
#!/bin/bash
hostnamectl set-hostname server01
echo "Hostname changed successfully."
EOF

# Grant execution permissions
chmod +x system_info.sh hostname.sh

# Run system info script
./system_info.sh

# Change hostname
sudo ./hostname.sh

# Refresh active shell to update terminal prompt
exec bash
# Prompt updates to: [rmishra@server01 Practical_9.b]$
```

#### Load Average Interpretation
In the output of `uptime` (e.g., `load average: 0.50, 0.28, 0.25`):
* **0.50:** Average CPU load over the last **1 minute**.
* **0.28:** Average CPU load over the last **5 minutes**.
* **0.25:** Average CPU load over the last **15 minutes**.
* *Values below the total number of CPU cores indicate a light, healthy workload.*

### 4. File Paths & Working Locations
* **OS Details:** `/etc/os-release`
* **Static Hostname File:** `/etc/hostname`

### 5. Next Steps / Follow-up
Run `hostnamectl status` to view your system's Chassis type, Machine ID, and Virtualization hypervisor.

---

# Practical 10: Scheduling Tasks

## 10.a: Configuring Cron to Automate Recurring Tasks

### 1. Direct & Encouraging Overview
A **cron job** is a task scheduled to run repeatedly at specified calendar intervals (e.g., every minute, hourly, daily, or on specific days). The background service `crond` checks the user's `crontab` table every minute and executes scheduled commands without manual intervention.

### 2. Step-by-Step Instructions
1. Verify that the `crond` service is running using `systemctl status crond`.
2. Write an automation script (`create_file.sh`) that increments a counter and generates timestamped test files.
3. Grant execute permissions using `chmod +x`.
4. Open the user crontab editor using `crontab -e`.
5. Enter a cron rule to execute the script every minute (`* * * * *`).
6. Verify active cron schedules using `crontab -l`.
7. Wait 2 minutes and inspect created files using `ls` and `cat`.
8. Remove the cron schedule using `crontab -r`.

### 3. Fully Written Command & Script Blocks

```bash
# 1. Verify cron daemon status
sudo systemctl status crond

# 2. Create the practice automation script
mkdir -p ~/Practical_10.a && cd ~/Practical_10.a

cat << 'EOF' > create_file.sh
#!/bin/bash
PATH1="/home/rmishra/Practical_10.a"
COUNTFILE="$PATH1/count.txt"

# Initialize counter if absent
[ ! -f "$COUNTFILE" ] && echo 0 > "$COUNTFILE"

# Increment count
count=$(cat "$COUNTFILE")
count=$((count + 1))
echo "$count" > "$COUNTFILE"

# Generate numbered test file
/usr/bin/touch "$PATH1/testfile$count"
/usr/bin/echo "This file is created using Cron" > "$PATH1/testfile$count"
EOF

# Make script executable
chmod +x create_file.sh

# 3. Configure crontab entry
crontab -e
```
*Add the following entry in the editor (`:wq` to save):*
```text
# ┌───────────── Minute (0 - 59)
# │ ┌─────────── Hour (0 - 23)
# │ │ ┌───────── Day of Month (1 - 31)
# │ │ │ ┌─────── Month (1 - 12)
# │ │ │ │ ┌───── Day of Week (0 - 6, Sunday=0)
# │ │ │ │ │
  * * * * * /home/rmishra/Practical_10.a/create_file.sh
```

```bash
# 4. View active cron schedules
crontab -l

# 5. Wait 2 minutes, then verify automatic file generation
ls -l
# Output: count.txt, create_file.sh, testfile1, testfile2

# View content of generated file
cat testfile1

# 6. Delete all user cron jobs
crontab -r

# Verify removal
crontab -l
# Output: no crontab for rmishra
```

### 4. File Paths & Working Locations
* **Script Location:** `/home/<username>/Practical_10.a/create_file.sh`
* **User Crontabs:** `/var/spool/cron/<username>`
* **System Crontab:** `/etc/crontab`

### 5. Next Steps / Follow-up
How would you configure a crontab entry to run a script every Sunday at midnight (`0 0 * * 0`)?

---

## 10.b & 10.c: Scheduling Future Tasks with At

### 1. Direct & Encouraging Overview
Unlike `cron`, which executes tasks repeatedly, the **`at`** command schedules a command or script to execute **exactly once** at a specified future date and time. It is driven by the background daemon `atd` and is ideal for deferred maintenance or one-off operations.

### 2. Step-by-Step Instructions
1. Verify that the `atd` service is running using `systemctl status atd`.
2. Schedule a one-time job for a specific upcoming minute using `at <time>`.
3. Type the commands at the interactive `at>` prompt, then press **Ctrl + D** to submit.
4. View pending jobs in the queue with `atq`.
5. Check system time with `date` until the scheduled time arrives.
6. Verify output with `ls` and `cat`.
7. Remove a queued job before it runs using `atrm <job_id>`.

### 3. Fully Written Command & Script Blocks

```bash
# 1. Verify at daemon status
sudo systemctl status atd

mkdir -p ~/Practical_10.b && cd ~/Practical_10.b

# 2. Schedule a task for a specific time (e.g., 9:54 am)
at 9:54 am

# At the at> prompt, enter your command:
# at> touch at_testfile && echo "This file is created using at" > at_testfile
# at> <EOT>  (press Ctrl + D to save and submit)
# Output: job 21 at Sun Oct 11 09:54:00 2026

# 3. View scheduled jobs in the queue
atq
# Output: 21  Sun Oct 11 09:54:00 2026 a rmishra

# 4. Check system clock
date

# 5. After the scheduled time has passed, verify file creation
ls -l at_testfile
cat at_testfile
# Output: This file is created using at

# 6. Removing a scheduled job before it executes:
# Schedule another job:
at 10:30 am
# at> cal > cal.txt
# at> <EOT> (Ctrl + D) -> job 23

atq
# Output: 23  Sun Oct 11 10:30:00 2026 a rmishra

# Delete job 23
atrm 23

# Verify removal
atq
# (Job 23 no longer appears)
```

#### Comparison: `cron` vs. `at`
| Feature | `cron` (`crond`) | `at` (`atd`) |
| :--- | :--- | :--- |
| **Execution Frequency** | Repeated recurring intervals (e.g. daily, hourly) | One-time execution |
| **Configuration Tool** | `crontab -e` / `crontab -l` / `crontab -r` | `at <time>` / `atq` / `atrm <id>` |
| **Storage Location** | `/var/spool/cron/<username>` | `/var/spool/at/` |
| **Best Used For** | Automated backups, log rotation, status reports | Delayed reboots, off-hours batch runs, reminders |

### 4. File Paths & Working Locations
* **Working Directory:** `/home/<username>/Practical_10.b/`
* **Job Spool Queue:** `/var/spool/at/`

### 5. Next Steps / Follow-up
You can specify natural language time formats with `at`, such as `at now + 15 minutes` or `at teatime` (4:00 PM). Try scheduling a job using relative time!
