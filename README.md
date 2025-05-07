
# Linux Commands Reference Guide

A comprehensive guide to essential Linux commands with examples and use cases.

# [LVM and Volume Management](LVM,volume.md)
# [Network Commands](Network_Commands.md)
# [TWS Notes](TWS_notes.md)
# [awk, sed, and grep](awk,sed,grep.md)
# [User, Group, and File Management](users-groups-files.md)

## Table of Contents
1. [ls (List Directory Contents)](#1-ls-list-directory-contents)
2. [cd (Change Directory)](#2-cd-change-directory)
3. [pwd (Print Working Directory)](#3-pwd-print-working-directory)
4. [mkdir (Make Directory)](#4-mkdir-make-directory)
5. [rm and rmdir (Remove)](#5-rm-and-rmdir-remove-files-and-directories)
6. [cat and zcat (Concatenate)](#6-cat-and-zcat-concatenate-and-print-files)
7. [touch (Create/Update Files)](#7-touch-change-file-timestamps-or-create-an-empty-file)
8. [head (View File Start)](#8-head-output-the-first-part-of-files)
9. [tail (View File End)](#9-tail-output-the-last-part-of-files)
10. [less and more (File Pagers)](#10-less-and-more-file-pagers)
11. [cp (Copy)](#11-cp-copy-files-and-directories)
12. [mv (Move/Rename)](#12-mv-move-or-rename-files-and-directories)
13. [wc (Word Count)](#13-wc-word-count)
14. [vi Editor](#14-vi-editor-in-unix-and-linux)
15. [Hard and Soft Links](#15-hard-and-soft-links)
16. [cut (Extract Text)](#16-cut-remove-sections-from-each-line-of-files)
17. [tee (Split Output)](#17-tee-read-from-standard-input-and-write-to-output-and-files)
18. [sort (Sort Text)](#18-sort-sort-lines-of-text-files)
19. [clear (Clear Screen)](#19-clear-clear-the-terminal-screen)
20. [diff (Compare Files)](#20-diff-compare-files-line-by-line)
21. [ssh (Secure Shell)](#21-ssh-secure-shell)
22. [df (Disk Free)](#22-df-disk-free)
23. [du (Disk Usage)](#23-du-disk-usage)
24. [ps (Process Status)](#24-ps-process-status)
25. [top (Table of Processes)](#25-top-table-of-processes)
26. [free (Memory Usage)](#26-free-memory-usage)
27. [vmstat (Virtual Memory Statistics)](#27-vmstat-virtual-memory-statistics)
28. [fuser (File User)](#28-fuser-file-user)
29. [nohup (No Hang Up)](#29-nohup-no-hang-up)

### Linux Advnace Commands

## Table of Contents


## 1. ls (List Directory Contents)

**Use Case:** To view the files and directories within the current directory or a specified directory.

**Example:**
```bash
ls
```
This will list all the non-hidden files and directories in your current location.

**Common Options:**
* `-l`: Displays detailed information, including permissions, owner, size, and modification date.
```bash
ls -l
```
* `-a`: Shows all files and directories, including hidden ones (those starting with a `.`).
```bash
ls -a
```
* `-h`: Displays file sizes in a human-readable format (e.g., 1K, 234M, 2G). Often used with `-l`.
```bash
ls -lh
```
* `-r`: Lists files in reverse order.
```bash
ls -r
```
* `-t`: Sorts the output by modification time (newest first).
```bash
ls -lt
```

## 2. cd (Change Directory)

**Use Case:** To navigate between different directories in the file system.

**Example:**
```bash
cd Documents
```
This will change your current directory to the "Documents" directory (assuming it exists in your current location).

**Special Paths:**
* `cd ..`: Moves one directory up (to the parent directory)
* `cd ~`: Returns to your home directory
* `cd /`: Moves to the root directory of the file system
* `cd -`: Returns to the previous directory you were in

## 3. pwd (Print Working Directory)

**Use Case:** To display the full path of your current directory.

**Example:**
```bash
pwd
```
This will output something like `/home/user/Documents`.

**Options:** `pwd` generally doesn't have many common options.

## 4. mkdir (Make Directory) 

**Use Case:** To create new single directories.

**Example:**
```bash
mkdir new_folder
```
This will create a directory named "new_folder" in your current location.

**Use Case:** To create new multipal directories.

**Example:**
```bash
mkdir dev text qa
```
This will create a directory named "dev" ,"test"  "qa" in your current location.

**Common Options:**
* `-p`: Creates parent directories if they don't exist. Useful for creating nested directory structures.
```bash
mkdir -p path/to/new/folder
```
**Use Case:** To create number of multipal directories  

**Example:**
```bash
mkdir /student{1..10}
```


## 5. rm and rmdir (Remove Files and Directories)

**Use Case:** To delete files (`rm`) and empty directories (`rmdir`).

**Examples:**
```bash
rm file.txt
```
This will delete the file named "file.txt".
```bash
rmdir empty_folder
```
This will delete the directory named "empty_folder" only if it is empty.

**Common Options for `rm` (Use with caution!):**
* `-r` or `-R`: Recursively removes directories and their contents (files and subdirectories).
```bash
rm -r non_empty_folder
```
* `-f`: Forces removal without prompting for confirmation.
```bash
rm -rf very_important_file
```
**Warning:** Using `-rf` can lead to permanent data loss if you're not careful.

**Note:** For non-empty directories, you should use `rm -r`.

## 6. cat and zcat (Concatenate and Print Files)

**Use Case:** `cat` displays the content of text files. `zcat` does the same for compressed files (usually with a `.gz` extension) without needing to decompress them first.

**Examples:**
```bash
cat my_document.txt
```
This will display the content of "my_document.txt" on your terminal.
```bash
zcat compressed_file.gz
```
This will display the content of "compressed_file.gz".

**Common Options for `cat`:**
* `-n`: Numbers all output lines.
```bash
cat -n my_document.txt
```
* `-b`: Numbers non-blank output lines.
```bash
cat -b my_document.txt
```

## 7. touch (Change File Timestamps or Create an Empty File)

**Use Case:** Primarily used to update the access and modification times of a file. If the file doesn't exist, it creates an empty file.

**Use Case:** To create new single file.

**Example:**
```bash
touch notes
```
This will create a file named "new_folder" in your current location.

**Use Case:** To create new multipal file.

**Example:**
```bash
touch python java nodejs
```
This will create a file named "python" ,"java"  "nodejs" in your current location.

**Use Case:** To create number of multipal directories  

**Example:**
```bash
touch book{1..10}
```
This will create a file named "book1" to "book10" in your current location.

## 8. head (Output the First Part of Files)

**Use Case:** To display the beginning of a file (by default, the first 10 lines).

**Example:**
```bash
head large_file.txt
```
This will show the first 10 lines of "large_file.txt".

**Common Options:**
* `-n <number>`: Specifies the number of lines to display.
```bash
head -n 20 large_file.txt
```
or
```bash
head -20 large_file.txt
```

## 9. tail (Output the Last Part of Files)

**Use Case:** To display the end of a file (by default, the last 10 lines). Often used for monitoring log files in real-time.

**Example:**
```bash
tail log_file.log
```
This will show the last 10 lines of "log_file.log".

**Common Options:**
* `-n <number>`: Specifies the number of lines to display from the end.
```bash
tail -n 5 log_file.log
```
or
```bash
tail -5 log_file.log
```
* `-f`: Follow mode. Continuously displays new lines as they are added to the file. Useful for watching log files.
```bash
tail -f application.log
```

## 10. less and more (File Pagers)

**Use Case:** To view the content of files that are too long to fit on the screen. They allow you to navigate through the file. `less` is generally more feature-rich than `more`.

**Examples:**
```bash
less very_long_file.txt
```
```bash
more another_long_file.txt
```

**Common Commands within `less` (while viewing the file):**
* `Space`: Scroll down one screen
* `b`: Scroll up one screen
* `j`: Scroll down one line
* `k`: Scroll up one line
* `/pattern`: Search for the next occurrence of "pattern"
* `n`: Go to the next search result
* `N`: Go to the previous search result
* `q`: Quit

**Common Commands within `more`:** Similar to `less`, but with fewer features. `Space` usually scrolls down one screen, and `q` quits.

## 11. cp (Copy Files and Directories)

**Use Case:** To create copies of files and directories.

**Examples:**
```bash
cp file1.txt file1_copy.txt
```
This will create a copy of "file1.txt" named "file1_copy.txt" in the current directory.
```bash
cp document.pdf ~/Documents/backup.pdf
```
This will copy "document.pdf" to your "Documents" directory and name it "backup.pdf".

**Common Options:**
* `-r` or `-R`: Recursively copies directories and their contents.
```bash
cp -r source_folder destination_folder
```
* `-v`: Verbose mode, shows what files are being copied.
```bash
cp -v file.txt backup.txt
```

## 12. mv (Move or Rename Files and Directories)

**Use Case:** To move files and directories to a different location or to rename them.

**Examples (Moving):**
```bash
mv old_location/file.txt new_location/
```
This will move "file.txt" from "old_location" to "new_location".
```bash
mv report.pdf ~/Archive/
```
This will move "report.pdf" to your "Archive" directory.

**Example (Renaming):**
```bash
mv old_name.txt new_name.txt
```
This will rename "old_name.txt" to "new_name.txt" in the current directory.

## 13. wc (Word Count)

**Use Case:** To count the number of lines, words, and characters in a file.

**Example:**
```bash
wc my_essay.txt
```
This might output something like: ` 30  250 1800 my_essay.txt` (lines, words, characters, filename).

**Common Options:**
* `-l`: Only count lines.
```bash
wc -l my_essay.txt
```
* `-w`: Only count words.
```bash
wc -w my_essay.txt
```
* `-c`: Only count bytes (which is usually equivalent to characters for plain text).
```bash
wc -c my_essay.txt
```

## 14. vi Editor in Unix and Linux

`vi` (Visual Editor) is a powerful text editor available on virtually all Unix and Linux systems. It has two main modes:

* **Command Mode:** Used for navigating the file, deleting text, copying, pasting, and saving.
* **Insert Mode:** Used for typing text into the file.

To enter Insert Mode, you typically press the `i` key while in Command Mode. To return to Command Mode, you press the `Esc` key.

Basic `vi` commands include:
* `i`: Enter Insert Mode at the current cursor position
* `:w`: Save the file
* `:q`: Quit the editor (if no changes have been made)
* `:wq` or `ZZ`: Save and quit
* `:q!`: Quit without saving (discard changes)
* `h`, `j`, `k`, `l`: Move the cursor left, down, up, and right, respectively (in Command Mode)
* `x`: Delete the character at the cursor (in Command Mode)
* `dd`: Delete the current line (in Command Mode)
* `yy`: Yank (copy) the current line (in Command Mode)
* `p`: Paste the previously yanked or deleted text after the cursor (in Command Mode)
* `/pattern`: Search for the next occurrence of "pattern" (in Command Mode)

## 15. Hard and Soft Links

These are two different ways to create references to files in Linux:

**Hard Link:** A hard link is essentially another filename that points to the same underlying inode (data block) on the file system.

**Characteristics:**
* Shares the same inode number as the original file
* All hard links are treated equally; deleting the original file doesn't affect the data as long as other hard links exist
* Changes made through any hard link are reflected in all other hard links
* Cannot link across different file systems
* Cannot link to directories (usually)

**Example:**
```bash
ln original_file.txt hard_link.txt
```

**Soft Link (Symbolic Link):** A soft link is a special type of file that contains a text pointer to the path of another file or directory.

**Characteristics:**
* Has its own inode number, separate from the original file
* If the original file is deleted, the soft link becomes broken (dangling link)
* Can link across different file systems
* Can link to directories

**Example:**
```bash
ln -s original_file.txt soft_link.txt
```

## 16. cut (Remove Sections from Each Line of Files)

**Use Case:** To extract specific columns or fields from lines in a file, often based on a delimiter.

**Example (assuming a comma-separated file `data.csv`):**
```bash
cut -d',' -f1 data.csv
```
This will extract the first field (column) from each line of "data.csv", using a comma (`,`) as the delimiter.

**Common Options:**
* `-d <delimiter>`: Specifies the delimiter character
* `-f <list>`: Specifies the fields to extract. You can use single numbers (e.g., `-f 1`), a range (e.g., `-f 1-3`), or a comma-separated list (e.g., `-f 1,3,5`)

## 17. tee (Read from Standard Input and Write to Output and Files)

**Use Case:** To simultaneously display output on the terminal and save it to one or more files.

**Example:**
```bash
ls -l | tee output.txt
```
This will display the output of `ls -l` on your terminal and also save it to a file named "output.txt".

**Common Options:**
* `-a`: Appends the output to the file instead of overwriting it.
```bash
ls -l | tee -a output.txt
```

## 18. sort (Sort Lines of Text Files)

**Use Case:** To sort the lines of a text file alphabetically or numerically.

**Example:**
```bash
sort names.txt
```
This will sort the lines in "names.txt" alphabetically and display the result.

**Common Options:**
* `-n`: Sort numerically.
```bash
sort -n numbers.txt
```
* `-r`: Sort in reverse order.
```bash
sort -r names.txt
```
* `-k <field>[,<char>]`: Sort by a specific field. You can also specify a character position within the field
* `-t <delimiter>`: Specify a delimiter to use when sorting by fields

## 19. clear (Clear the Terminal Screen)

**Use Case:** To remove all previous commands and output from the terminal screen, providing a clean workspace.

**Example:**
```bash
clear
```
This command takes no arguments.

## 20. diff (Compare Files Line by Line)

**Use Case:** To show the differences between two files.

**Example:**
```bash
diff file1.txt file2.txt
```
This will output the lines that are different between "file1.txt" and "file2.txt", indicating additions, deletions, and changes.

**Common Options:**
* `-u`: Produces output in a unified format, which is often used for creating patches.
```bash
diff -u file1.txt file2.txt
```

# Linux Commands Reference Guide

## 21. ssh (Secure Shell)

**Use Case:** To establish a secure connection to a remote server or machine.

**Example:**
```bash
ssh user@remote_host
```

**Common Options:**
* `-p <port>`: Specify non-default port
```bash
ssh -p 2222 user@remote_host
```
* `-i <identity_file>`: Use private key file
```bash
ssh -i ~/.ssh/id_rsa user@remote_host
```
* `-X`: Enable X11 forwarding
```bash
ssh -X user@remote_host
```
* `-L`: Create local port forwarding
```bash
ssh -L 8080:0.0.0.0:80 user@remote_host
```

## 22. df (Disk Free)

**Use Case:** Display disk space usage information.

**Example:**
```bash
df
```

**Common Options:**
* `-h`: Human-readable format
```bash
df -h
```
* `-T`: Show filesystem type
```bash
df -Th
```
* `-i`: Display inode usage
```bash
df -i
```

## 23. du (Disk Usage)

**Use Case:** Estimate file and directory space usage.

**Example:**
```bash
du
```

**Common Options:**
* `-h`: Human-readable format
```bash
du -h
```
* `-s`: Display only totals
```bash
du -sh /home/user/Documents
```
* `-c`: Show grand total
```bash
du -ch /var/log
```

## 24. ps (Process Status)

**Use Case:** Display running processes information.

**Example:**
```bash
ps
```

**Common Options:**
* `aux`: Show all processes
```bash
ps aux
```
* `-f`: Full listing
```bash
ps -f
```
* `-u <user>`: Show user processes
```bash
ps -u root
```

## 25. top (Table of Processes)

**Use Case:** Show real-time system process activity.

**Example:**
```bash
top
```

**Interactive Commands:**
* `q`: Quit
* `M`: Sort by memory
* `P`: Sort by CPU
* `k`: Kill process

## 26. free (Memory Usage)

**Use Case:** Display system memory usage.

**Example:**
```bash
free
```

**Common Options:**
* `-h`: Human-readable format
```bash
free -h
```
* `-s`: Update continuously
```bash
free -s 5
```

## 27. vmstat (Virtual Memory Statistics)

**Use Case:** Report virtual memory statistics.

**Examples:**
```bash
vmstat        # Single report
vmstat 5      # Report every 5 seconds
vmstat 2 5    # 5 reports with 2-second delay
```

## 28. fuser (File User)

**Use Case:** Identify processes using files or sockets.

**Examples:**
```bash
fuser /path/to/file
fuser -n tcp 8080
```

**Common Options:**
* `-k`: Kill processes accessing the file
* `-u`: Show user names
* `-v`: Verbose output

## 29. nohup (No Hang Up)

**Use Case:** Run command immune to hangups.

**Example:**
```bash
nohup long_running_script.sh &
```

**Common Usage:**
```bash
nohup command > output.log 2>&1 &
```










