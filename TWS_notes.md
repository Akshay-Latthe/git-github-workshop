Alright, let's break down these system-level and user/group management commands with examples, use cases, and common options, incorporating the commands from your images:

**User Management Commands**

1.  **`useradd <username>` (Create user account)**
    * **Use Case:** To add a new user to the system.
    * **Example:**
        ```bash
        sudo useradd shub
        ```
    * **Explanation:** This command creates a new user account named `shub` with default settings. You'll likely need to set a password using the `passwd` command.

2.  **Checking User Account Properties**
    * **Command:** `grep <username> /etc/passwd`
    * **Use Case:** To display basic information about a user account stored in the `/etc/passwd` file.
    * **Example:**
        ```bash
        grep shub /etc/passwd
        ```
    * **Output Example:** `shub:1001:1001::/home/shub:/bin/bash`
    * **Explanation:** This output shows the username, user ID (UID), group ID (GID), GECOS field (usually empty), home directory, and login shell for the user `shub`.

3.  **`passwd <username>` (Create/change user account password)**
    * **Use Case:** To set or change the password for a user account.
    * **Example (setting password for `shub`):**
        ```bash
        sudo passwd shub
        ```
    * **Explanation:** You will be prompted to enter the new password for the user `shub`.

4.  **Checking User Password Properties**
    * **Command:** `grep <username> /etc/shadow`
    * **Use Case:** To view password-related information for a user stored in the `/etc/shadow` file (requires root privileges).
    * **Example:**
        ```bash
        sudo grep shub /etc/shadow
        ```
    * **Output Example:** `shub:$6$Lbc25fR...:19002:0:99999:7:::`
    * **Explanation:** This output contains the encrypted password, last password change date, minimum password age, maximum password age, warning period, inactivity period, and account expiration date for the user `shub`. The actual encrypted password will be a long string.

5.  **`su <username>` (Switch user account)**
    * **Use Case:** To switch to another user account.
    * **Example (switch to `shub`):**
        ```bash
        su shub
        ```
    * **Explanation:** You will be prompted for the password of the `shub` user. If you are already root, you might not need a password. Using `su - <username>` loads the target user's environment variables.

6.  **`exit` or `Ctrl+D` (Logout from user account)**
    * **Use Case:** To log out from the current user account and return to the previous one.
    * **Examples:**
        ```bash
        exit
        ```
        or press `Ctrl+D`.

7.  **`userdel <username>` (Delete user account)**
    * **Use Case:** To remove a user account from the system.
    * **Example:**
        ```bash
        sudo userdel shub
        ```
    * **Explanation:** This command deletes the `shub` user account but leaves their home directory and files intact. Use `sudo userdel -r shub` to also remove the home directory and mail spool.

8.  **`usermod -l <new_username> <old_username>` (Change user login name)**
    * **Use Case:** To modify an existing user account, specifically to change the username.
    * **Example:**
        ```bash
        sudo usermod -l devops_shub shub
        ```
    * **Explanation:** This command changes the username from `shub` to `devops_shub`.

**Group Management Commands**

1.  **`groupadd <groupname>` (Add Group account)**
    * **Use Case:** To create a new group on the system.
    * **Example:**
        ```bash
        sudo groupadd developers
        ```
    * **Explanation:** This command creates a new group named `developers`.

2.  **Checking Group Account Properties**
    * **Command:** `grep <groupname> /etc/group`
    * **Use Case:** To display information about a group from the `/etc/group` file.
    * **Example:**
        ```bash
        grep developers /etc/group
        ```
    * **Output Example:** `developers:1002::` or `developers:1002:ravi,ajay,vineet`
    * **Explanation:** This output shows the group name, group ID (GID), password field (usually empty), and a comma-separated list of group members.

3.  **Checking Group Admin Property**
    * **Command:** `grep <groupname> /etc/gshadow`
    * **Use Case:** To view shadow group information, including group administrators (requires root privileges).
    * **Example:**
        ```bash
        sudo grep developers /etc/gshadow
        ```
    * **Output Example:** `developers:*::` or `developers:admin1,admin2::`
    * **Explanation:** This file contains information about group passwords and administrators. The example shows that `admin1` and `admin2` are administrators for the `developers` group.

4.  **`groupdel <groupname>` (Delete Group Account)**
    * **Use Case:** To remove a group from the system.
    * **Example:**
        ```bash
        sudo groupdel old_developers
        ```
    * **Explanation:** This command deletes the `old_developers` group. You cannot delete a group that is the primary group of any user.

5.  **`gpasswd -a <username> <groupname>` (Add single member in group)**
    * **Use Case:** To add a user to a supplementary group.
    * **Example:**
        ```bash
        sudo gpasswd -a ajay developers
        ```
    * **Explanation:** This command adds the user `ajay` to the `developers` group.

6.  **`gpasswd -M <user1>,<user2>,... <groupname>` (Add multiple members in group)**
    * **Use Case:** To add multiple users to a supplementary group at once.
    * **Example:**
        ```bash
        sudo gpasswd -M rahul,viral,nikit developers
        ```
    * **Explanation:** This command adds the users `rahul`, `viral`, and `nikit` to the `developers` group.

7.  **`gpasswd -d <username> <groupname>` (Remove group member)**
    * **Use Case:** To remove a user from a supplementary group.
    * **Example:**
        ```bash
        sudo gpasswd -d vinit developers
        ```
    * **Explanation:** This command removes the user `vinit` from the `developers` group.

8.  **`gpasswd -A <username> <groupname>` (Make group admin)**
    * **Use Case:** To designate a user as an administrator of a group. This allows them to manage group membership.
    * **Example:**
        ```bash
        sudo gpasswd -A sachin developers
        ```
    * **Explanation:** This command makes the user `sachin` an administrator of the `developers` group.

**Access Control List (ACL) - `grep` Command**

The image section on ACL actually focuses on the `grep` command, which is a powerful tool for searching for patterns in files. While not strictly an ACL management command itself, `grep` can be used to inspect file permissions and ownership, which are related to access control.

* **Regular Expressions:** The image correctly points out that `grep` uses regular expressions for pattern matching. These are special characters that help define search patterns.
* **`grep` (Global Regular Expression Print):** This command searches for lines in input that match a given pattern and prints the matching lines.

Here are the `grep` examples from your image:

1.  **Search a word (string) in a file:**
    ```bash
    grep root /etc/passwd
    ```
    * **Use Case:** To find all lines in the `/etc/passwd` file that contain the word "root".

2.  **Search a string in multiple files:**
    ```bash
    grep "shub" /etc/passwd /etc/shadow
    ```
    * **Use Case:** To find all lines containing "shub" in both the `/etc/passwd` and `/etc/shadow` files.

3.  **Search a string insensitive in title:**
    ```bash
    grep -i "root" /etc/passwd
    ```
    * **Use Case:** To find all lines containing "root", regardless of case (e.g., "Root", "ROOT"), in the `/etc/passwd` file. The "-i" option makes the search case-insensitive.

4.  **Search a string in all files recursively:**
    ```bash
    grep -r "shub" /
    ```
    * **Use Case:** To search for the string "shub" in all files under the root directory (`/`) and its subdirectories. The "-r" option enables recursive searching.

5.  **Inverting the string match:**
    ```bash
    grep -v "nologin" /etc/passwd
    ```
    * **Use Case:** To display all lines in `/etc/passwd` that *do not* contain the string "nologin". The "-v" option inverts the match.

6.  **Displaying the string match total line no:**
    ```bash
    grep -c "shub" /etc/passwd
    ```
    * **Use Case:** To count the number of lines in `/etc/passwd` that contain the string "shub". The "-c" option outputs only the count.

7.  **Display the file names that match the string:**
    ```bash
    grep -l "shub" /etc/passwd /etc/shadow
    ```
    * **Use Case:** To list only the names of the files that contain the string "shub". The "-l" option outputs the filenames.

8.  **Display the file names that do not contain the string:**
    ```bash
    grep -L "shub" /etc/passwd /etc/shadow
    ```
    * **Use Case:** To list only the names of the files that do *not* contain the string "shub". The "-L" option outputs the filenames of non-matching files.

9.  **Display the string match line with number:**
    ```bash
    grep -n "shub" /etc/passwd
    ```
    * **Use Case:** To display the lines containing "shub" in `/etc/passwd`, along with their line numbers. The "-n" option prefixes the output with line numbers.

10. **Display the lines that start with a string:**
    ```bash
    grep "^root" /etc/passwd
    ```
    * **Use Case:** To find all lines in `/etc/passwd` that begin with the string "root". The "^" anchor matches the beginning of a line.

11. **Display the lines that end with a string:**
    ```bash
    grep "bash$" /etc/passwd
    ```
    * **Use Case:** To find all lines in `/etc/passwd` that end with the string "bash". The "$" anchor matches the end of a line.

12. **Search and redirect output to a new file:**
    ```bash
    grep "shub" /etc/passwd > found_shub.txt
    ```
    * **Use Case:** To find all lines containing "shub" in `/etc/passwd` and redirect the output to a new file named `found_shub.txt`, overwriting it if it exists. Use `>>` to append to the file instead.

**`find` Command**

The `find` command is a powerful utility for searching for files and directories based on various criteria.

* **Use Case:** The image correctly states that `find` is used to search and locate lists of files and directories based on conditions you specify.

Here are the `find` examples from your image:

1.  **Find files under the home directory:**
    ```bash
    find /home -name shub.txt
    ```
    * **Use Case:** To find files named `shub.txt` within the `/home` directory and its subdirectories. The `-name` option searches for files with a specific name.

2.  **Find files with suid permission:**
    ```bash
    find / -perm /4000
    ```
    * **Use Case:** To find files with the Set User ID (SUID) permission bit set. The `-perm /mode` searches for files with any of the bits in `mode` set. 4000 represents the SUID bit.

3.  **Find files with guid permission:**
    ```bash
    find / -perm /2000
    ```
    * **Use Case:** To find files with the Set Group ID (SGID) permission bit set. 2000 represents the SGID bit.

4.  **Find files with sticky bit permission:**
    ```bash
    find / -perm /1000
    ```
    * **Use Case:** To find directories with the sticky bit set. 1000 represents the sticky bit.

5.  **Using find command based on users:**
    ```bash
    find / -user shub
    ```
    * **Use Case:** To find all files and directories owned by the user `shub` under the root directory (`/`). The `-user` option filters by owner.

6.  **Using find command based on groups:**
    ```bash
    find / -group developers
    ```
    * **Use Case:** To find all files and directories belonging to the group `developers` under the root directory (`/`). The `-group` option filters by group.

7.  **Search the file with less than 10MB in a folder:**
    ```bash
    find /data -type f -size -10M
    ```
    * **Use Case:** To find regular files (`-type f`) in the `/data` directory and its subdirectories that are smaller than 10 megabytes (`-size -10M`).

8.  **Search the file with more than 10MB in a folder:**
    ```bash
    find /data -type f -size +10M
    ```
    * **Use Case:** To find regular files (`-type f`) in the `/data` directory and its subdirectories that are larger than 10 megabytes (`-size +10M`).

Remember to consult the man pages for each command (`man <command>`) to explore the full range of options and their specific behavior on your system. These commands are essential tools for managing users, groups, and files in a Linux environment.
