

## Table of Contents

## User Management Commands 🌐
1. [useradd (Create User Account)](#1-useradd-create-user-account)
2. [usermod (Modify User Account)](#2-usermod-modify-user-account)
3. [userdel (Delete User Account)](#3-userdel-delete-user-account)
4. [passwd (Manage User Password)](#4-passwd-manage-user-password)
5. [chage (Change User Password Expiry)](#5-chage-change-user-password-expiry)

## Group Management Commands 🌐

1. [groupadd (Add Group)](#1-groupadd-add-group)  
2. [groupmod (Modify Group)](#2-groupmod-modify-group)  
3. [groupdel (Delete Group)](#3-groupdel-delete-group)  
4. [gpasswd (Group Password Administration)](#4-gpasswd-group-password-administration)  
5. [usermod (Add User to Group)](#5-usermod-add-user-to-group)  
6. [groups (Check Group Membership)](#6-groups-check-group-membership)

## File Permissions 🌐

1. [File Permissions](#file-permissions)


## User Management Commands 🌐

## 1. useradd (Create User Account)

**Use Case:** Create a new user account.

**Example:**
```bash
useradd newuser
```

**Common Options:**
* `-m`: Create home directory
```bash
useradd -m newuser
```
* `-g <group>`: Specify primary group
```bash
useradd -g users newuser
```
* `-u <uid>`: Specify user ID
```bash
useradd -u 1001 newuser
```

## 2. usermod (Modify User Account)

**Use Case:** Modify an existing user account.

**Example:**
```bash
usermod -l newusername oldusername
```

**Common Options:**
* `-l <new_username>`: Change username
* `-g <group>`: Change primary group
* `-a -G <group>`: Add to supplementary group
* `-d <new_homedir>`: Change home directory


## 3. userdel (Delete User Account)

**Use Case:** Delete a user account.

**Example:**
```bash
userdel newuser
```

**Common Options:**
* `-r`: Remove home directory
```bash
userdel -r newuser
```


## 4. passwd (Manage User Password)

**Use Case:** Manage user passwords.

**Example:**
```bash
passwd newuser
```


## 5. chage (Change User Password Expiry)

**Use Case:** Change user password expiry settings.

**Example:**
```bash
chage -d 0 newuser  # Set password to expire immediately
```

**Common Options:**
* `-d <date>`: Set last password change date
* `-m <min>`: Set minimum days before password change
* `-M <max>`: Set maximum days before password change
* `-W <warn>`: Set warning days before password expiry


## Group Management Commands 🌐

### 1. groupadd (Add Group)
**Use Case:** Create a new group.

**Example:**
```bash
groupadd newgroup
```

### 2. groupmod (Modify Group)
**Use Case:** Modify an existing group's properties.

**Example:**
```bash
groupmod -n newgroupname oldgroupname
```

### 3. groupdel (Delete Group)
**Use Case:** Remove an existing group.

**Example:**
```bash
groupdel groupname
```

### 4. gpasswd (Group Password Administration)
**Use Case:** Administer /etc/group and /etc/gshadow.

**Examples:**
```bash
# Add a user to group
gpasswd -a username groupname

# Remove a user from group
gpasswd -d username groupname

# Set group administrators
gpasswd -A admin1,admin2 groupname
```

### 5. usermod (Add User to Group)
**Use Case:** Add a single member to group.

**Example:**
```bash
usermod -aG groupname username
```

### 6. groups (Check Group Membership)
**Use Case:** Display group memberships for a user.

**Example:**
```bash
groups username
```

## File Permissions 

# `chmod` (Change Mode)
**Description:** Controls file and directory permissions in Linux

#### Permission Types
Each file/directory has three permission groups:
```
Owner (u) │ Group (g) │ Others (o)
    rwx   │    rwx    │    rwx
```

#### Permission Symbols
- `r` (Read) = 4
- `w` (Write) = 2
- `x` (Execute) = 1

#### Permission Examples
```
Permission  Binary  Decimal
---         000     0
--x         001     1
-w-         010     2
-wx         011     3
r--         100     4
r-x         101     5
rw-         110     6
rwx         111     7
```

#### Common Usage Patterns
```bash
# Numeric (Octal) Mode
chmod 755 file.txt    # rwxr-xr-x
chmod 644 file.txt    # rw-r--r--
chmod 777 file.txt    # rwxrwxrwx (careful!)

# Symbolic Mode
chmod u+x file.txt    # Add execute for owner
chmod g-w file.txt    # Remove write for group
chmod o=r file.txt    # Set others to read-only
chmod a+x file.txt    # Add execute for all
```

#### Special Permissions
```bash
chmod 4755 file    # Set SUID (4000)
chmod 2755 file    # Set SGID (2000)
chmod 1755 file    # Set sticky bit (1000)
```

#### Common Permission Patterns
- `755` (-rwxr-xr-x): Standard for executable programs
- `644` (-rw-r--r--): Standard for regular files
- `777` (-rwxrwxrwx): Full permissions (use with caution!)
- `700` (-rwx------): Private files
- `600` (-rw-------): Private files (no execute)

#### Examples with Explanations
```bash
# Make a script executable
chmod u+x script.sh   # Owner can execute

# Set full read/write for owner, read-only for others
chmod 644 config.txt  # -rw-r--r--

# Give full permissions to owner, none to others
chmod 700 private/    # -rwx------

# Add write permission for group
chmod g+w shared.txt  # Allow group writing
```

#### Directory Permissions
For directories:
- `r`: List contents (ls)
- `w`: Create/delete files
- `x`: Access/traverse directory

```bash
# Make directory accessible
chmod 755 directory/  # rwxr-xr-x

# Recursive change for directory and contents
chmod -R 755 directory/
```
