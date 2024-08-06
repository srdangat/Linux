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

## Consider the below text file as an input.

```sh
cat sample.txt
```

```sh
unix is great os. unix is opensource. unix is free os.
learn operating system.
unix linux which one you choose.
unix is easy to learn.unix is a multiuser os.Learn unix .unix is a powerful.
```

# Replacing or substituting string :

- Sed command is mostly used to replace the text in a file.
- The below simple sed command replaces the word “unix” with “linux” in the file.
- By default, the sed command replaces the first occurrence of the pattern in each line and it won’t replace the second, third…occurrence in the line

```sh
$ sed 's/unix/linux/' sample.txt
```

# Output

```sh
linux is great os. unix is opensource. unix is free os.
learn operating system.
linux linux which one you choose.
linux is easy to learn.unix is a multiuser os.Learn unix .unix is a powerful.
```

# Replacing the nth occurrence of a pattern in a line :

- Use the /1, /2 etc flags to replace the first,second occurrence of a pattern in a line.
- The below command replaces the second occurrence of the word “unix” with “linux” in a line.

```sh
$ sed 's/unix/linux/2' sample.txt
```

# Output

```sh
unix is great os. linux is opensource. unix is free os.
learn operating system.
unix linux which one you choose.
unix is easy to learn.linux is a multiuser os.Learn unix .unix is a powerful.
```

