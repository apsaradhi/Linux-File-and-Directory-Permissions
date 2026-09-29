# Linux-File-and-Directory-Permissions

# Linux File and Directory Permissions

## Objective

Configure and manage Linux file and directory access using standard permissions, ownership, ACLs, and special permissions.

---

## Step 1: Check File Permissions

```bash
ls -l
```

Example:

```text
-rw-r--r--  user1 developers file.txt
```

### Permission Structure

```text
-rw-r--r--
 │││ │││ └── Others
 │││ └────── Group
 ││└──────── Owner
 └────────── File type
```

Permissions:

* `r` → Read
* `w` → Write
* `x` → Execute

---

## Step 2: Change File Permissions with chmod

```bash
chmod 755 script.sh
```

### What it does

Sets:

```text
Owner  → rwx
Group  → r-x
Others → r-x
```

Another example:

```bash
chmod 644 file.txt
```

Sets:

```text
Owner  → rw-
Group  → r--
Others → r--
```

---

## Step 3: Change File Ownership

```bash
chown user1 file.txt
```

### What it does

Changes the owner of `file.txt` to `user1`.

Change owner and group together:

```bash
chown user1:developers file.txt
```

---

## Step 4: Change Group Ownership

```bash
chgrp developers file.txt
```

### What it does

Changes the group ownership of `file.txt` to `developers`.

---

## Step 5: Configure ACL

Check existing ACL:

```bash
getfacl file.txt
```

Grant a specific user permissions:

```bash
setfacl -m u:user1:rw file.txt
```

### What it does

Gives `user1` read and write permissions without changing the normal owner/group permissions.

Verify:

```bash
getfacl file.txt
```

---

## Step 6: Configure Special Permissions

### SUID

```bash
chmod 4755 file
```

SUID allows an executable to run with the permissions of its owner.

### SGID

```bash
chmod 2755 directory
```

SGID on a directory causes newly created files to inherit the directory's group.

### Sticky Bit

```bash
chmod 1777 directory
```

Sticky bit restricts deletion of files in a shared directory to the file owner, directory owner, or root.

---

## Step 7: Verify Permissions

```bash
ls -l file.txt
```

For ACL:

```bash
getfacl file.txt
```

For ownership:

```bash
ls -l
```

---

## Permission Management Workflow

```text
Create File/Directory
        ↓
Check Permissions
        ↓
chmod → Configure Permissions
        ↓
chown → Change Owner
        ↓
chgrp → Change Group
        ↓
setfacl → Configure ACL
        ↓
Special Permissions
        ↓
Verify with ls -l / getfacl
```

## Result

Successfully practiced Linux file and directory permission management using `chmod`, `chown`, `chgrp`, ACLs, SUID, SGID, and Sticky Bit.
