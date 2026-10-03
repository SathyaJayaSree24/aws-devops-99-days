# Day 01 - Linux Commands

Commands practiced during Day 01 Linux orientation.

| Command  | Purpose                                                            | Example                          |
| -------- | ------------------------------------------------------------------ | -------------------------------- |
| `pwd`    | Prints the current working directory                               | `pwd`                            |
| `ls`     | Lists files and directories                                        | `ls`                             |
| `ls -la` | Lists all files, including hidden files, with detailed information | `ls -la`                         |
| `cd`     | Changes the current directory                                      | `cd aws`                         |
| `cd ..`  | Moves to the parent directory                                      | `cd ..`                          |
| `cd ~`   | Moves to the current user's home directory                         | `cd ~`                           |
| `mkdir`  | Creates a directory                                                | `mkdir practice`                 |
| `touch`  | Creates an empty file                                              | `touch notes.txt`                |
| `cat`    | Displays the contents of a file                                    | `cat notes.txt`                  |
| `echo`   | Prints text or writes text to a file                               | `echo "Linux Day 1" > notes.txt` |
| `cp`     | Copies a file or directory                                         | `cp notes.txt practice/`         |
| `mv`     | Moves or renames a file or directory                               | `mv notes.txt linux-notes.txt`   |
| `rm`     | Removes a file                                                     | `rm linux-notes.txt`             |
| `rmdir`  | Removes an empty directory                                         | `rmdir practice`                 |
| `nano`   | Opens a terminal text editor                                       | `nano notes.txt`                 |

## Important Operators

### `>` Overwrite

Writes output to a file and replaces its existing contents.

```bash
echo "Linux Day 1" > notes.txt
```

### `>>` Append

Adds output to the end of an existing file without removing its previous contents.

```bash
echo "More Linux notes" >> notes.txt
```

## Path Symbols

```text
/    Root directory
.    Current directory
..   Parent directory
~    Current user's home directory
```

## Absolute Path

An absolute path starts from `/`.

Example:

```text
/home/sathya/day1-file-practice/devops
```

## Relative Path

A relative path is interpreted from the current working directory.

Examples:

```text
..
projects/
aws/
```

## Practical Learning

During the Day 01 mini challenge, I practiced:

1. Creating directories and files.
2. Writing and reading file contents.
3. Copying files with `cp`.
4. Renaming files with `mv`.
5. Removing files with `rm`.
6. Navigating directories using `cd`.
7. Checking the current location using `pwd`.
8. Listing directory contents using `ls`.

## Key Lesson

Linux commands are not just commands to memorize. Understanding how the filesystem, paths, files, and directories work makes it easier to work with servers, cloud infrastructure, containers, automation, and DevOps tools.
