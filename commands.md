# Linux Commands Cheat Sheet

## File and Directory Operations

- **`du -sh`**: Display size of file & directory.
- **`ls`**: Lists files and directories in the current directory.
- **`ls -l`**: List files and directories with details.
- **`ls -la`**: List hidden files and directories.
- **`cd`**: Change working directory.
- **`cd ..`**: Change to the parent directory.
- **`cp`**: Allows you to copy files and directories.
  - **`cp -r`**: Copy recursively.
  - **`cp -rv`**: Copy with details, `-v` flag for verbose mode.
- **`mv`**: Allows you to move files and directories.
  - **`mv -v`**: Move with details.
- **`rm`**: Allows you to remove (delete) files and directories.
  - **`rm -r`**: Remove directories and their contents.
  - **`rm -v`**: Remove with details.
  - **`rm -rf`**: Remove without confirmation.
- **`pwd`**: Print working directory.
- **`mkdir`**: Create new directory.
  - **`mkdir dir1`**: Create a single directory.
  - **`mkdir dir2 dir3`**: Create multiple directories.
  - **`mkdir dir2/dir3`**: Create nested directories.
  - **`mkdir -p /dir4/dir5`**: Create multiple nested directories with parent directories.

## File Viewing and Manipulation

- **`cat`**: Print the content of the file.
- **`head`**: Print the top contents of the file.
  - **`head -n1`**: Specify the number of lines to display.
  - **`head -c1`**: Specify the number of bytes to display.
- **`tail`**: Print the last contents of the file.
  - **`tail -n`**: Specify the number of lines to display.
  - **`tail -c1`**: Specify the number of bytes to display.
- **`diff`**: Compare the contents of files.
  - **`diff file1 file2`**: Compare two files.
  - **`diff -r ~/Desktop ~/Code`**: Compare entire directories recursively.
- **`touch`**: Create a new, empty file.

## User and Group Management

- **`whoami`**: Display your current user identity.
- **`id`**: Display user and group information.
- **`chown`**: Change the ownership of a file.
  - **`sudo chown root:root example.txt`**: Change owner and group.
  - **`sudo chown -R root:root new-dir`**: Change ownership recursively.
- **`chmod`**: Change the permissions of a file & directory.
  - **`sudo chmod 700 example.txt`**: Change permissions to `rwx------`.
  - **`chmod -R 755 ~/Desktop`**: Change permissions recursively.
  - **`chmod +x script.sh`**: Give execute permission to the script.
- **`chgrp`**: Change the group ownership of a file & directories.
- **`useradd`**, **`adduser`**: Create a new user.
- **`passwd`**: Change the password of a user.
- **`userdel`**: Delete a user.
- **`usermod`**: Modify a user.
  - **`sudo usermod -c "This is test user" test_user`**: Add a comment.
  - **`sudo usermod -d /home/manav test_user`**: Change home directory.
  - **`sudo usermod -e 2025-05-29 test_user`**: Change expiry date.
  - **`sudo usermod -g manav test_user`**: Change group.
  - **`sudo usermod -l test_account test_user`**: Change login name.
  - **`sudo usermod -L test_user`**: Lock a user.
  - **`sudo usermod -U test_user`**: Unlock a user.
  - **`sudo usermod -p test_password test_user`**: Set an unencrypted password.
  - **`sudo usermod -s /bin/sh test_user`**: Create a shell for the user.
  - **`sudo usermod -u 1234 test_user`**: Change user ID.
- **`groupadd`**: Create group.
- **`gpasswd`**: Add user into group.
  - **`gpasswd -a user_name group_name`**: Add single user.
  - **`gpasswd -M "user1 user2"`**: Add multiple users.
- **`groupdel`**: Delete group.
- **`deluser`**: Remove user from group.
- **`sudo`**: Execute a command as another user.
- **`su`**: Switch user.

## Archive and Compression

- **`tar`**: Used to combine multiple files into one.
  - **`tar -cvf dirx.tar dirx`**: Create archive.
  - **`tar -xvf dir.tar`**: Extract archive.
  - **`tar -xvf dir.tar -C /opt/`**: Extract to specified location.
  - Options:
    - `-c`: Create an archive.
    - `-f`: File name (compulsory).
    - `-v`: Verbose.
    - `-t`: List contents.
    - `-x`: Extract contents.
    - `-P`: Preserve permissions.
    - `-C`: Change to directory.
- **`gzip`**: Reduce the size of a file.
  - **`tar -czvf dir.tar.gz /opt/`**: Create gzip compressed archive.
- **`bzip2`**: Provides better compression ratio.
  - **`tar -cjvf dir.tar.bz2 /opt/`**: Create bzip2 compressed archive.
- **`xz`**: Uses LZMA algorithm for impressive compression ratio.
  - **`tar -cJvf dir.tar.xz /opt/`**: Create xz compressed archive.
- **`gunzip`**: Decompress files.

## Network and File Transfer

- **`scp`**: Secure Copy, transfer local to server.
  - **`scp -i "/path/private_key" Source user@hostname:destination_file`**: Transfer single file.
  - **`scp -i "/path/private_key" -r Directory_name user@hostname:destination_file`**: Transfer directory.

## Shell and Environment

- **`chsh`**: Change the shell for user.
  - **`chsh -s /bin/sh bob`**: Change shell to `/bin/sh` for user `bob`.
- **`export`**: Create environment variable.
  - **`export PROJECT=MERCURY`**: Set environment variable.
  - **`echo 'export PROJECT=MERCURY' >> /home/user_name/.profile`**: Make persistent.

## Search and Find

- **`find`**: Allows you to search for files.
  - **`find /etc -name host.conf`**: Search by name.
  - **`find / -perm 600`**: Search by permission.
  - **`find /home/bob -empty`**: Search for empty files/directories.
  - **`find /home/bob -empty -delete`**: Delete empty files/directories.
  - **`find /home/bob/ -type f -name "*.txt" -exec wc -l {} \;`**: Find and execute command.
  - **`find / -size +10M -size -20M`**: Search files by size range.

## Process Management

- **`ps`**: Display information about running processes.
  - **`ps -aux`**: Detailed information of all processes.
  - **`ps -ef`**: Full-format listing.
  - **`ps -u username`**: Processes owned by specific user.
  - **`ps -p PID`**: Information about a specific process.
  - **`ps -l`**: Long listing format.
  - **`ps axjf`**: Display a process tree.
- **`kill`**: Terminate processes.
  - **`kill -9 PID`**: Forcefully terminate a process.
- **`top`**: Provides real-time, dynamic view of system's performance.
- **`uptime`**: Displays current time, system's uptime, number of users, and load average.

## Job Control

- **`sleep`**: Delay execution.
  - **`sleep 30s`**: Sleep for 30 seconds.
  - **`sleep 30s&`**: Run in background.
- **`jobs`**: List currently running jobs.
  - **`fg %<job number>`**: Bring job to foreground.
  - **`bg %<job number>`**: Resume job in background.
  - **`kill %<job number>`**: Terminate job.
