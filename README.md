# learn_bash
Here i will put some bash tips i have discovered.

## tar
- To create a tar archive:
```
  tar -cf destination from_folder
```
- To create a tar archive from stdin:
```
  random_program | tar -cf destination --null -T -
```
random_program should return a file list separated by null characters, to support names with \n or other escape sequences.
after tar, the flag --null enables reading that list of files. The option -T is used to describe where to get the list from. - is the stdin.

## netcat
- to start listening for tcp connections on a port:
```
  nc -l port_number
```
- to connect to a remote server which is listening for tcp connections:
```
  nc ip port
```
After establishing a connection between two machines, everything you type in that terminal session,
is sent to the other device.
- send file to other device:
  on the sender device:
  ```nc -l port < file_path```
  on the receiver:
  ```nc ip port > file_path```
 
 - show progress on the receiver
 ```nc ip port | pv > file_path```
 where pv is a utility used to analyze a pipe, it shows the current speed and the bytes transfered.
 
 ## gpg
 - basic file encryption:
  ```gpg -c file```
  outputs the file as file.gpg, encrypted.
 - basic file decryption:
 ```gpg -d file > dest```
