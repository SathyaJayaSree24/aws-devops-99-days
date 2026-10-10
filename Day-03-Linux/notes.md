# Day 03: Linux Permissions

## 1. Why Linux Permissions Exist

Linux permissions control who can access files and directories and what actions they can perform. They help protect data and prevent unauthorized modifications.

## 2. Users, Groups, Owner, and Others

Linux permissions are divided into three categories:

* **User (`u`):** The owner of the file.
* **Group (`g`):** Users belonging to the file's group.
* **Others (`o`):** Everyone else.

Check the current user and group information using:

```bash
id
```

## 3. Understanding `rwx`

* `r` = Read
* `w` = Write
* `x` = Execute

### File permissions

* Read: View file contents.
* Write: Modify file contents.
* Execute: Run an executable file or script.

### Directory permissions

* Read: List directory entries.
* Write: Create, remove, or rename entries, subject to permission checks.
* Execute: Traverse the directory and access entries by name.

## 4. Reading `ls -l`

Example:

```text
-rw-r--r-- 1 sathya sathya 0 Oct 10 14:48 umask-test.txt
```

The output contains:

1. File type and permissions.
2. Hard-link count.
3. Owner.
4. Group.
5. Size in bytes.
6. Last modification date and time.
7. Filename.

Useful commands:

```bash
ls -l filename
ls -ld directory_name
ls -li filename
```

* `ls -l` displays detailed file information.
* `ls -ld` displays information about the directory itself.
* `ls -li` displays inode numbers.

## 5. Changing Permissions with `chmod` Symbolic Mode

`chmod` means change mode. It changes file or directory permissions.

### Permission categories

* `u` = Owner
* `g` = Group
* `o` = Others
* `a` = All

### Operators

* `+` = Add permissions
* `-` = Remove permissions
* `=` = Set permissions exactly

Examples:

```bash
chmod u+x file.txt
chmod u-w file.txt
chmod g+w file.txt
chmod o+x file.txt
chmod a-x file.txt
chmod o=rx file.txt
chmod ug-w file.txt
chmod u=rwx,g=rx,o=--- file.txt
```

## 6. Numeric Permissions

Each permission has a numeric value:

* Read (`r`) = 4
* Write (`w`) = 2
* Execute (`x`) = 1
* No permission = 0

Add the values for each category.

| Number | Permissions |
| ------ | ----------- |
| 7      | `rwx`       |
| 6      | `rw-`       |
| 5      | `r-x`       |
| 4      | `r--`       |
| 3      | `-wx`       |
| 2      | `-w-`       |
| 1      | `--x`       |
| 0      | `---`       |

Common permission modes:

* `644` = `rw-r--r--`
* `640` = `rw-r-----`
* `700` = `rwx------`
* `755` = `rwxr-xr-x`

Examples:

```bash
chmod 644 file.txt
chmod 640 file.txt
chmod 700 file.txt
chmod 755 file.txt
```

The three digits represent owner, group, and others, respectively.

## 7. Changing Ownership with `chown`

`chown` means change owner. It changes file or directory ownership.

Examples:

```bash
chown alex file.txt
chown alex:developers file.txt
ls -l file.txt
```

* `chown alex file.txt` changes the owner to `alex`, leaving the existing group unchanged.
* `chown alex:developers file.txt` explicitly sets the owner to `alex` and the group to `developers`.

Changing ownership may require administrator privileges using `sudo`.

**Remember:** `chmod` changes permissions; `chown` changes ownership.

## 8. Understanding `umask`

`umask` controls which permissions are removed from the default permissions of newly created files and directories.

Check the current mask:

```bash
umask
```

Observed output in WSL:

```text
0022
```

With `umask 022`:

* Ordinary files start with base permissions `666`. The resulting permissions are `644` (`rw-r--r--`).
* Directories start with base permissions `777`. The resulting permissions are `755` (`rwxr-xr-x`).

Examples:

```bash
touch umask-test.txt
ls -l umask-test.txt

mkdir umask-test-dir
ls -ld umask-test-dir
```

The results were verified in Ubuntu WSL.

**Important:** `umask` removes permissions from the base permissions requested by the creating application. It does not grant permissions. The application and system defaults also affect the final result.

## Day 03 Summary

Topics completed:

* Why Linux permissions exist.
* Users, groups, owner, and others.
* Read, write, and execute permissions.
* Reading `ls -l` output.
* Symbolic permissions using `chmod`.
* Numeric permissions using `chmod`.
* Changing ownership using `chown`.
* Default permissions using `umask`.
