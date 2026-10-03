# Day 01 - Linux Orientation

## 1. What is an Operating System?

An Operating System (OS) is system software that manages computer hardware and provides an environment for applications to run.

It manages resources such as:

* CPU
* Memory
* Storage
* Input/output devices
* Running processes

## 2. What is Linux?

Linux is an open-source operating system kernel developed by Linus Torvalds in 1991.

The Linux kernel acts as a bridge between applications and hardware. It manages:

* CPU resources
* Memory
* Processes
* Devices
* System resources

In everyday usage, "Linux" is also commonly used to refer to complete Linux distributions.

## 3. Linux Kernel vs Linux Distribution

The **kernel** is the core component responsible for managing hardware and system resources.

A **Linux distribution** combines the Linux kernel with system utilities, libraries, package management tools, and applications.

Examples:

* Ubuntu
* Debian
* Fedora
* Arch Linux

## 4. What is Ubuntu?

Ubuntu is an open-source Linux distribution based on Debian.

It provides a complete environment around the Linux kernel, including utilities, applications, and the `apt` package manager.

Example:

```bash
sudo apt install nginx
```

## 5. Why Linux is Important in DevOps

Linux is widely used in DevOps and cloud environments because it is:

* Open source
* Automation-friendly
* Lightweight and resource-efficient
* Highly customizable
* Widely used on servers
* Common in cloud and container environments

DevOps engineers frequently work with Linux servers, Bash scripts, SSH, containers, CI/CD systems, and cloud infrastructure.

## 6. Server vs Personal Computer

A server is a computer or virtual machine that provides services or resources to other systems over a network.

For example, an AWS EC2 instance running Ubuntu can act as a web server.

A personal computer is generally designed primarily for direct interaction with a user.

## 7. SSH

SSH stands for **Secure Shell**.

It is a protocol used to securely connect to and manage remote systems through a command-line interface.

Example:

```bash
ssh username@server_ip
```

The default SSH port is commonly **22**.

## 8. Terminal vs Shell

A **terminal** is the interface through which we interact with a command-line system.

A **shell** interprets the commands we enter and executes them.

**Bash (Bourne Again Shell)** is one of the most commonly used Linux shells and is especially useful for automation and scripting.

## 9. Linux Filesystem

Linux uses a hierarchical filesystem beginning at `/`, called the root directory.

Important directories include:

| Directory | Purpose                        |
| --------- | ------------------------------ |
| `/`       | Root of the filesystem         |
| `/home`   | Users' home directories        |
| `/etc`    | System configuration           |
| `/var`    | Variable data and logs         |
| `/usr`    | Programs and utilities         |
| `/tmp`    | Temporary files                |
| `/proc`   | Kernel and process information |
| `/dev`    | Device-related files           |
| `/root`   | Root user's home directory     |

My WSL home directory:

```text
/home/sathya
```

The shortcut `~` represents the current user's home directory.

## 10. Absolute vs Relative Paths

An **absolute path** starts from the root `/`.

Example:

```text
/home/sathya/day1-file-practice/devops
```

A **relative path** depends on the current working directory.

Examples:

```text
..
projects/
aws/
```

Special path symbols:

* `.` = current directory
* `..` = parent directory
* `~` = current user's home directory

## 11. Day 01 Hands-on Practice

Practiced:

* Navigating the Linux filesystem
* Creating directories and files
* Viewing file contents
* Writing and appending text
* Copying files
* Moving and renaming files
* Removing files and empty directories
* Working with absolute and relative paths
* Exploring hidden files and file metadata
* Using WSL Ubuntu

## 12. Mini Challenge

Created a separate practice environment and performed:

```bash
mkdir
touch
echo
cat
cp
mv
rm
cd
pwd
ls
```

The challenge involved creating files and directories, copying a file, renaming it, deleting the original, and navigating back to the home directory.

## Key Takeaways

1. Linux provides the foundation for many server and DevOps environments.
2. The kernel manages hardware and system resources, while a distribution provides the complete user environment.
3. Understanding paths and basic filesystem commands is essential before working with cloud servers, containers, and automation.
4. Bash makes Linux particularly useful for automation and scripting.
5. Hands-on practice is more valuable than memorizing commands without understanding what they do.
