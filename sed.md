# Stream Editor - Replacing a String

`sed` is a powerful text stream editor.Can do insertion, deletion, search and replace(substitution).

## Basic Syntax for Replacing a String

```sh
sed 's/old_string/new_string/' input_file
```
- `s` stands for substitute.
- `old_string` is the string you want to replace.
- `new_string` is the string you want to replace it with.
- `input_file` is the file in which you want to make the replacement.

**Consider the below text file as an input**

```sh
cat sample.txt
```

```sh
unix is great os. unix is opensource. unix is free os.
learn operating system.
unix linux which one you choose.
unix is easy to learn.unix is a multiuser os.Learn unix .unix is a powerful.
```

**Replacing or substituting string**

- Sed command is mostly used to replace the text in a file.
- The below simple sed command replaces the word “unix” with “linux” in the file.
- By default, the sed command replaces the first occurrence of the pattern in each line and it won’t replace the second, third…occurrence in the line

```sh
$ sed 's/unix/linux/' sample.txt
```

**Output**

```sh
linux is great os. unix is opensource. unix is free os.
learn operating system.
linux linux which one you choose.
linux is easy to learn.unix is a multiuser os.Learn unix .unix is a powerful.
```

**Replacing the nth occurrence of a pattern in a line**

- Use the /1, /2 etc flags to replace the first,second occurrence of a pattern in a line.
- The below command replaces the second occurrence of the word “unix” with “linux” in a line.

```sh
$ sed 's/unix/linux/2' sample.txt
```

**Output**

```sh
unix is great os. linux is opensource. unix is free os.
learn operating system.
unix linux which one you choose.
unix is easy to learn.linux is a multiuser os.Learn unix .unix is a powerful.
```

**Replacing all the occurrence of the pattern in a line**
- The substitute flag /g (global replacement) specifies the sed command to replace all the occurrences of the string in the line.

```sh
$ sed 's/unix/linux/g' sample.txt
```

**Output**

```sh
linux is great os. linux is opensource. linux is free os.
learn operating system.
linux linux which one you choose.
linux is easy to learn.linux is a multiuser os.Learn linux .linux is a powerful.
```

**Replacing string on a specific line number**
- Replace the string on a specific line number.Below command replaces the string only on the third line.

```sh
$ sed '3 s/unix/linux/' sample.txt
```

**Output**

```sh
unix is great os. unix is opensource. unix is free os.
learn operating system.
linux linux which one you choose.
unix is easy to learn.unix is a multiuser os.Learn unix .unix is a powerful.
```

**Replacing from nth occurrence to all occurrences in a line**
- Use the combination of /1, /2 ,/3 and /g to replace all the patterns from the nth occurrence of a pattern in a line. 
- The following sed command replaces the third, fourth, fifth… “unix” word with “linux” word in a line.

```sh
$ sed 's/unix/linux/3g' sample.txt
```

**Output**

```sh
unix is great os. unix is opensource. linux is free os.
learn operating system.
unix linux which one you choose.
unix is easy to learn.unix is a multiuser os.Learn linux .linux is a powerful.
```

**Replacing string on a range of lines**
- You can specify a range of line numbers to the sed command for replacing a string.
- The following sed command replaces the lines with range from 1 to 3.

```sh
$ sed '1,3 s/unix/linux/' sample.txt
```

**Output**

```sh
linux is great os. unix is opensource. unix is free os.
learn operating system.
linux linux which one you choose.
unix is easy to learn.unix is a multiuser os.Learn unix .unix is a powerful.
```
**Another example ,Here $ indicates the last line in the file. So the sed command replaces the text from second line to last line in the file**

```sh
$ sed '2,$ s/unix/linux/' sample.txt
```

**Output**

```sh
unix is great os. unix is opensource. unix is free os.
learn operating system.
linux linux which one you choose.
linux is easy to learn.unix is a multiuser os.Learn unix .unix is a powerful
```

**Deleting lines from a particular file**

**Syntax**

```sh
$ sed 'nd' filename.txt
```

**Example1**
- To Delete a particular line

```sh
$ sed '4d' sample.txt
```

**Example2**
- To Delete a last line

```sh
$ sed '$d' sample.txt
```

**Example3**
- To Delete line from range x to y

```sh
$ sed '1,3d' sample.txt
```

**Example4**
-  To Delete from nth to last line

```sh
$ sed '2,$d' sample.txt
```

**Example5**
- To Delete pattern matching line

```sh
$ sed '/linux/d' sample.txt
```

**Insert one blank line after each line**

```sh
$ sed G sample.txt
```

**Viewing a file from x to y range**

```sh
$ sed -n '2,4p' sample.txt
```
**View the entire file except the given range**

```sh
$ sed '2,4d' sammple.txt
```
**Print nth line of the file**

```sh
$ sed -n '3'p sample.txt
```

**Number each line of a file (left alignment). **=** is used to number the line. \t is used for tab between number and sentence**

```sh
$ sed = sample.txt | sed 'N;s/\n/\t/'
```