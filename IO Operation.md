### Linux I/O Redirection

Redirection can be defined as changing the way from where commands read input to where commands send output. You can redirect input and output of a command. The bash shell has three standard streams in I/O redirection:

1. **Standard Input (stdin)**: The stdin stream is numbered as stdin (0). The bash shell takes input from stdin. By default, the keyboard is used as input.
2. **Standard Output (stdout)**: The stdout stream is numbered as stdout (1). The bash shell sends output to stdout. Output goes to the display.
3. **Standard Error (stderr)**: The stderr stream is numbered as stderr (2). The bash shell sends error messages to stderr. Error messages go to the display.

#### Redirecting Output to a File

- Use the greater than symbol `>` to redirect text to a file. This will overwrite the file if it already exists.

    ```sh
    echo "this is a sample text" > temp.txt
    ```

    This stores the echo text in `temp.txt`. If `temp.txt` already exists, the single greater than symbol will delete any previous content.

- Use the double greater than symbol `>>` to append text to a file.

    ```sh
    echo "This is sample text2" >> temp.txt
    ```

#### Error Messages and Exit Status

- A message is printed to the stderr stream when a command generates an error message.

```sh
ls 120
```

```sh
ls : cannot access '120': No such file or directory													
Here 120 is an invalid agrument for ls command and hence an error is returned
```

#### Sucessful command example			

```sh
$ ls			
# (lists the files and directories)			
$ echo $?			
0
```

#### Unsucessful command example			

```sh
$ ls nonexistentfile					
ls: cannot access 'nonexistentfile': No such file or directory					
$ echo $?					
2
```

#### Redirecting stderr to a File

To redirect stderr to err.txt:

```sh
ls + 2> err.txt
```

#### Redirecting stdout to a File

To redirect stdout to out.txt:

```sh
ls > out.txt
```

#### Combining stdout & stderr

To redirect both stdout and stderr to output.txt:

```sh
$ ls /nonexistentdirectory &> output.txt
$ cat output.txt
ls: cannot access '/nonexistentdirectory': No such file or directory
```