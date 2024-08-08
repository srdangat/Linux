# Grep - Global Regular Expression Print

- `grep` command search for a particular string/keyword from a file and print a lines matching pattern.
- It check line by line and print lines matching given pattern.
- We can use grep anywhere like with files,searching for files,directories

**Synatx**
```sh
grep [options] pattern [file...]
```

**Search Keyword**
```sh
grep Jimmy users.csv
```

**To ignore the upper and lower case while searching**
```sh
grep -i "keyword" file 
```
- -i: ignore

```sh
grep -i jimmy users.csv 
```

**To search everything except given pattern/keyword**
```sh
grep -v "keyword" file
```
- -v:Invert the match; select non-matching lines.

```sh
grep -v Hester users.csv
```

**To print how many times (count) given keyword present in file**
```sh
grep -c "keyword" file
```
- -c:Count the number of lines that match the pattern.

```sh
grep -c UK users.csv
```

**To search for exact match of given keyword in a file**
```sh
grep -w "keyword" file
```
- -w:Match whole words only

```sh
grep -w Beth users.csv
```

**To print the line no. of matches of given keyword in a file**
```sh
grep -n "keyword" file
```
- -n:Prefix each line of output with the line number where it was found

```sh
 grep -n Rollins users.csv
```

**To search a given keyword in multiple files**
```sh
grep "keyword" file1 file2...
```

```sh
Note: By default result of multiple files shows file name in output
```

```sh
grep -i Rollins users.csv emp.csv
```