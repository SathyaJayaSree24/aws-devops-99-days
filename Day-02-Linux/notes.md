# Day 02 - Linux File Inspection & Text Processing

## Overview

Day 02 focused on inspecting files, reading text efficiently, counting and sorting data, extracting fields, and searching through files.

These commands are especially useful for Linux administration, log analysis, troubleshooting, and DevOps workflows.

---

## 1. `cat`

### What it does

`cat` displays the contents of a file.

It can also concatenate multiple files and is commonly used with shell redirection to create or append text.

### Syntax

```bash
cat filename
```

### Useful options

```bash
cat -n filename
```

Numbers all lines, including blank lines.

```bash
cat -b filename
```

Numbers only non-empty lines.

### Redirection

```bash
cat > file.txt
```

Creates or overwrites a file.

```bash
cat >> file.txt
```

Appends content to an existing file.

Multiline input can be created using a heredoc:

```bash
cat > file.txt << 'EOF'
line 1
line 2
EOF
```

### Important point

`>` and `>>` are shell redirection operators. They are not features that make `cat` create files by themselves.

---

## 2. `less`

### What it does

`less` is a pager used to view large files one screen at a time.

Unlike `cat`, it does not dump the entire file into the terminal.

### Syntax

```bash
less filename
```

### Important keys

| Key        | Purpose                  |
| ---------- | ------------------------ |
| `Space`    | Move forward one screen  |
| `b`        | Move backward one screen |
| `Enter`    | Move forward one line    |
| `k`        | Move backward one line   |
| `g`        | Go to beginning          |
| `G`        | Go to end                |
| `/pattern` | Search forward           |
| `?pattern` | Search backward          |
| `n`        | Next search match        |
| `N`        | Previous search match    |
| `q`        | Quit `less`              |

### Important point

`less` is read-only viewing. It does not modify the file.

`q` exits the `less` viewer and returns to the terminal.

### `cat` vs `less`

```text
cat  → displays the file directly
less → provides an interactive, screen-by-screen viewer
```

`less` is more practical for large log files.

---

## 3. `head`

### What it does

`head` displays the beginning of a file.

By default, it displays the first 10 lines.

### Syntax

```bash
head filename
```

### Display a specific number of lines

```bash
head -n 5 filename
```

Displays the first 5 lines.

### Important point

`head` only reads and displays the file. It does not modify it.

### `head` vs `tail`

```text
head → beginning of file
tail → ending of file
```

---

## 4. `tail`

### What it does

`tail` displays the ending portion of a file.

By default, it displays the last 10 lines.

### Syntax

```bash
tail filename
```

### Display a specific number of lines

```bash
tail -n 5 filename
```

Displays the last 5 lines.

### Follow a file in real time

```bash
tail -f server.log
```

`-f` continuously watches the file and displays new lines as they are added.

This is commonly used for monitoring application and server logs.

Press:

```text
Ctrl + C
```

to stop following the file.

### DevOps relevance

`tail -f` is one of the most useful basic commands for observing live logs during troubleshooting.

---

## 5. `wc`

### What it does

`wc` stands for **word count** and can report the number of lines, words, and bytes in a file.

### Syntax

```bash
wc filename
```

Example:

```bash
wc application.log
```

Typical output format:

```text
lines words bytes filename
```

### Useful options

```bash
wc -l filename
```

Counts lines.

```bash
wc -w filename
```

Counts words.

```bash
wc -c filename
```

Counts bytes.

### DevOps relevance

`wc` is useful when quickly checking the size or amount of data in logs and command output.

---

## 6. `sort`

### What it does

`sort` arranges lines in a specified order.

By default, it performs **lexical/text-based sorting**.

### Syntax

```bash
sort filename
```

### Reverse sorting

```bash
sort -r filename
```

`-r` sorts in reverse order.

### Numeric sorting

```bash
sort -n filename
```

`-n` treats the values as numbers.

For example:

```text
1
10
2
20
30
```

Normal sorting:

```text
1
10
2
20
30
```

Numeric sorting:

```text
1
2
10
20
30
```

### Important point

`sort` does not modify the original file by default. It reads the file and displays the sorted result.

### DevOps relevance

Sorting is useful when processing command output, log data, reports, and numerical values.

---

## 7. `uniq`

### What it does

`uniq` removes or counts **consecutive duplicate lines**.

### Syntax

```bash
uniq filename
```

For example:

```text
error
error
warning
warning
info
```

becomes:

```text
error
warning
info
```

### Important rule

`uniq` only detects duplicates that are next to each other.

For example:

```text
error
warning
error
```

contains two `error` entries, but they are not adjacent, so `uniq` treats them as separate entries.

### Count consecutive duplicates

```bash
uniq -c filename
```

The `-c` option counts each consecutive group.

### Count all duplicates

To count all occurrences, sort the data first:

```bash
sort filename | uniq -c
```

The pipeline works because:

```text
sort
  ↓
groups identical lines together
  ↓
uniq -c
  ↓
counts each group
```

### DevOps relevance

This pattern is useful for identifying repeated messages or values during log analysis.

---

## 8. `cut`

### What it does

`cut` extracts specific fields or characters from each line.

It is useful when working with structured text.

For example:

```text
Sathya=Human=Engineer
```

Using `=` as the delimiter gives:

```text
Field 1 → Sathya
Field 2 → Human
Field 3 → Engineer
```

### `-d` → delimiter

A delimiter is the character that separates fields.

```bash
cut -d '=' -f 2 entries.txt
```

This means:

> Use `=` as the delimiter and extract field 2.

### `-f` → field

```bash
cut -d '=' -f 3 entries.txt
```

extracts field 3.

Multiple fields can also be selected:

```bash
cut -d '=' -f 1,3 entries.txt
```

### `-c` → characters

`cut` can also extract characters based on their positions.

```bash
cut -c 2-4 name.txt
```

For:

```text
Sathya
```

the output is:

```text
ath
```

### Important mental model

```text
-d → delimiter
-f → field
-c → character
```

### DevOps relevance

`cut` is useful for extracting specific fields from structured command output, configuration data, and log-like text.

---

## 9. `grep`

### What it does

`grep` searches for a pattern or text inside files and displays matching lines.

It is one of the most useful commands for Linux and DevOps troubleshooting.

### Syntax

```bash
grep "pattern" filename
```

Example:

```bash
grep "error" server.log
```

This displays lines containing `error`.

### `-i` → ignore case

```bash
grep -i "error" server.log
```

Matches:

```text
error
ERROR
Error
eRrOr
```

### `-n` → show line numbers

```bash
grep -n "error" server.log
```

Example:

```text
4:error database connection timeout
6:error database connectionfailed
```

### `-v` → invert the search

```bash
grep -v "error" server.log
```

Displays lines that do **not** contain `error`.

### `-c` → count matching lines

```bash
grep -c "error" server.log
```

Displays only the number of matching lines.

Important: `grep -c` counts **matching lines**, not the total number of times the word appears.

### Combining options

```bash
grep -ic "error" server.log
```

Counts matching lines while ignoring case.

```bash
grep -in "error" server.log
```

Shows matching lines with line numbers while ignoring case.

### Important options

```text
-i → ignore case
-n → show line numbers
-v → show non-matching lines
-c → count matching lines
```

### DevOps relevance

`grep` is heavily used for:

* searching application logs
* finding errors and warnings
* troubleshooting services
* filtering command output
* inspecting configuration files

---

# Important Lessons & Confusions

## 1. Lexical vs numeric sorting

`sort` normally treats values as text.

```bash
sort numbers.txt
```

can produce:

```text
1
10
2
20
30
```

Use:

```bash
sort -n numbers.txt
```

for actual numerical ordering.

---

## 2. `uniq` only sees adjacent duplicates

`uniq` does not automatically find every duplicate in a file.

Use:

```bash
sort file | uniq -c
```

when you want to group and count all duplicate entries.

---

## 3. `grep -c` vs `grep -n`

These options are easy to confuse:

```text
grep -n → matching lines + line numbers
grep -c → number of matching lines
```

---

## 4. Case sensitivity in `grep`

Normal `grep` is case-sensitive.

```bash
grep "error" file
```

does not match `ERROR`.

Use:

```bash
grep -i "error" file
```

to ignore case.

---

## 5. `cut` fields depend on the delimiter

For:

```text
Sathya=Human=Engineer
```

the delimiter is `=`.

```bash
cut -d '=' -f 2 file
```

extracts:

```text
Human
```

The delimiter must match the actual structure of the data.

---

## 6. File-name typo during `tail -f`

While practicing `tail -f`, a file-name typo occurred because `sever.log` was used instead of `server.log`.

The issue was identified by checking the filename and correcting the command.

This reinforced an important Linux debugging habit:

> When a command appears not to work, first verify the filename, path, spelling, and actual command being executed.

---

# Day 02 Command Progress

```text
cat    → display and combine file contents
less   → interactively view large files
head   → view beginning of a file
tail   → view ending / follow live logs
wc     → count lines, words, and bytes
sort   → arrange lines
uniq   → remove/count adjacent duplicates
cut    → extract fields or characters
grep   → search and filter text
```

## Day 02 Core DevOps Pattern

Many Linux commands become more powerful when combined using pipes:

```bash
command | grep "pattern"
```

or:

```bash
sort file | uniq -c
```

This introduces the idea of building **small command-line processing pipelines**, which is an important foundation for Linux and DevOps work.
