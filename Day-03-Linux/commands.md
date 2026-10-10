# Day 03 - Linux Permissions Commands

Commands practiced during Day 03 Linux permissions.

| Command  | Purpose                                                                      | Example                 |
| -------- | ---------------------------------------------------------------------------- | ----------------------- |
| `id`     | Displays the current user's ID, group ID, and group memberships              | `id`                    |
| `ls -l`  | Displays file details, including permissions, owner, group, and size         | `ls -l report.txt`      |
| `ls -ld` | Displays detailed information about a directory itself                       | `ls -ld practice/`      |
| `ls -li` | Displays file details along with inode numbers                               | `ls -li report.txt`     |
| `chmod`  | Changes file or directory permissions                                        | `chmod 644 report.txt`  |
| `chown`  | Changes file or directory ownership                                          | `chown alex report.txt` |
| `umask`  | Displays or sets the permission mask for newly created files and directories | `umask`                 |
| `touch`  | Creates an empty file if it does not exist                                   | `touch umask-test.txt`  |
| `mkdir`  | Creates a directory                                                          | `mkdir umask-test-dir`  |

## Symbolic Permission Commands

Symbolic mode uses permission categories, operators, and permission letters.

### Permission Categories

```text
u    Owner/user
g    Group
o    Others
a    All categories
```

### Operators

```text
+    Add permissions
-    Remove permissions
=    Set permissions exactly
```

### Examples Practiced

```bash
chmod u+x rwx-practice.txt
chmod u-w rwx-practice.txt
chmod u+w rwx-practice.txt
chmod u=o rwx-practice.txt
chmod u=rw rwx-practice.txt
chmod g+w rwx-practice.txt
chmod o+x rwx-practice.txt
chmod a-x rwx-practice.txt
chmod o=rx rwx-practice.txt
chmod ug-w rwx-practice.txt
chmod u=rwx,g=rx,o=--- rwx-practice.txt
```

## Numeric Permission Commands

Numeric permissions use these values:

```text
r = 4
w = 2
x = 1
- = 0
```

### Common Examples

```bash
chmod 644 rwx-practice.txt
chmod 640 rwx-practice.txt
chmod 700 rwx-practice.txt
chmod 755 rwx-practice.txt
```

| Mode  | Owner | Group | Others |
| ----- | ----- | ----- | ------ |
| `644` | `rw-` | `r--` | `r--`  |
| `640` | `rw-` | `r--` | `---`  |
| `700` | `rwx` | `---` | `---`  |
| `755` | `rwx` | `r-x` | `r-x`  |

## Ownership Commands

```bash
chown alex report.txt
chown alex:developers report.txt
ls -l report.txt
```

* `chown alex report.txt` changes the owner to `alex` and leaves the existing group unchanged.
* `chown alex:developers report.txt` explicitly sets the owner to `alex` and the group to `developers`.
* Changing ownership may require administrator privileges.

## `umask` Commands

```bash
umask
touch umask-test.txt
ls -l umask-test.txt
mkdir umask-test-dir
ls -ld umask-test-dir
```

My WSL environment displayed `0022` for `umask`.

With this mask, the observed default permissions were:

```text
New file:      644  (-rw-r--r--)
New directory: 755  (drwxr-xr-x)
```

## Practical Learning

During Day 03, I practiced:

1. Inspecting file permissions and ownership with `ls -l`.
2. Reading directory permissions with `ls -ld`.
3. Changing permissions using symbolic mode.
4. Changing permissions using numeric mode.
5. Understanding the difference between `chmod` and `chown`.
6. Checking the default permission mask with `umask`.
7. Verifying the permissions of newly created files and directories in Ubuntu WSL.

## Key Lesson

Linux permissions control access to files and directories. `chmod` changes permissions, `chown` changes ownership, and `umask` influences the default permissions assigned when new files and directories are created.
