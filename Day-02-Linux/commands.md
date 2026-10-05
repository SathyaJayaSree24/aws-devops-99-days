# Day 02 Linux Commands

## 1. cat

```bash
cat filename
```

Display the contents of a file.

```bash
cat -n filename
```

Display contents with line numbers, including blank lines.

```bash
cat -b filename
```

Display line numbers only for non-empty lines.

### Create/Write a File Using Redirection

```bash
cat > filename
```

Type the content and press `Ctrl+D` to finish.

### Append to a File

```bash
cat >> filename
```

Adds new content to the end of the file.

---

## 2. less

```bash
less filename
```

Open a file page by page.

### Useful Keys

```text
Space  → forward one screen
b      → backward one screen
Enter  → forward one line
k      → backward one line
g      → beginning of file
G      → end of file
q      → quit
/pattern → search forward
?pattern → search backward
n      → next match
N      → previous match
```

---

## 3. head

```bash
head filename
```

Display the first 10 lines of a file.

```bash
head -n 5 filename
```

Display the first 5 lines.

---

## 4. tail

```bash
tail filename
```

Display the last 10 lines of a file.

```bash
tail -n 5 filename
```

Display the last 5 lines.

### Follow a File in Real Time

```bash
tail -f server.log
```

Follow new lines added to a file.

Stop following with:

```text
Ctrl+C
```

---

## 5. wc

```bash
wc filename
```

Display:

```text
lines words bytes filename
```

### Count Lines

```bash
wc -l filename
```

### Count Words

```bash
wc -w filename
```

### Count Bytes

```bash
wc -c filename
```

---

## 6. sort

```bash
sort filename
```

Sort lines in ascending lexical/text order.

```bash
sort -r filename
```

Sort in reverse lexical order.

```bash
sort -n filename
```

Sort numbers numerically.

### Example

```bash
sort names.txt
sort -r names.txt
sort numbers.txt
sort -n numbers.txt
```

`sort` does not modify the original file by default.

---

## 7. uniq

```bash
uniq filename
```

Remove consecutive duplicate lines.

```bash
uniq -c filename
```

Count consecutive duplicate lines.

### Count All Duplicates

```bash
sort filename | uniq -c
```

`sort` groups identical lines together first, allowing `uniq -c` to count all occurrences.

### Example

```bash
sort duplicates.txt | uniq -c
```

---

## 8. cut

### Extract Fields

```bash
cut -d '=' -f 2 entries.txt
```

`-d` specifies the delimiter.

`-f` specifies the field.

### Extract Multiple Fields

```bash
cut -d '=' -f 1,3 entries.txt
```

### Extract Characters

```bash
cut -c 2-4 name.txt
```

`-c` extracts characters by position.

### Useful Options

```text
-d → delimiter
-f → field
-c → character
```

---

## 9. grep

```bash
grep "error" server.log
```

Search for lines containing `error`.

### Ignore Case

```bash
grep -i "error" server.log
```

### Show Line Numbers

```bash
grep -n "error" server.log
```

### Show Non-Matching Lines

```bash
grep -v "error" server.log
```

### Count Matching Lines

```bash
grep -c "error" server.log
```

### Combine Options

```bash
grep -ic "error" server.log
```

Count matching lines while ignoring case.

```bash
grep -in "error" server.log
```

Show matching lines with line numbers while ignoring case.

---

## 10. Pipes

Commands can be combined using `|`.

### Example

```bash
sort duplicates.txt | uniq -c
```

The output of `sort` becomes the input of `uniq -c`.

### General Pattern

```bash
command1 | command2
```

This allows Linux commands to be chained together for more powerful processing.

---

## Day 02 Quick Recall

```text
cat        → display file contents
less       → view file page by page
head       → beginning of file
tail       → end of file / follow logs
wc         → count lines, words, bytes
sort       → arrange lines
uniq       → remove/count adjacent duplicates
cut        → extract fields/characters
grep       → search/filter text
|          → connect commands
```

## DevOps-Relevant Commands

```bash
tail -f server.log
grep "error" server.log
grep -i "error" server.log
grep -n "error" server.log
grep -c "error" server.log
sort duplicates.txt | uniq -c
```

These commands are especially useful for inspecting and analyzing server and application logs.
