# learn_bash
Here i will put some bash tips i have discovered. These are not only related to bash, but to the terminal in general.

## shortcuts
| shortuct | action |
| ---------| -------|
| ctrl+a | start of the line |
| ctrl+e | end of the line |
| ctrl+u | cut from cursor to start |
| ctrl+y | paste what you have just cut |
| ctrl+r | search in history |
| ctrl+l | clear screen |


## command substitution
to insert the result of a command as a parameter, put the command between two ticks ``` ` ``` or ```$()```
```
touch `date`
```

## brace expansion
By putting some curly braces near an expression, you can combine the expression with the content of the braces
```
echo 1{1,2,3} {a,b,c}{a,b}
```
returns
```
11 12 13 aa ab ba bb ca cb
```

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
 
 
## fzf
this is a must have. This program is a fuzzy search utility that can be integrated with various other programs.
