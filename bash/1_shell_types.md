# Bash

## What is a Shell? ##

<dl>
  <dt>tty / Console
    <dd> Lowest level interface with the operating system with no GUI<br>
    Access one in Ubuntu with <code>ctrl-alt-F3</code>
  <dt>Terminal Emulator
    <dd> A window in the GUI to access the tty / Console
  <dt>Shell Interpreter
    <dd> The program that interprets the commands in the terminal (Bash, Zsh)
  <dt>Shell language
    <dd> The syntax and control structures provided for scripting. (bash, zsh)</dd>
</dl>


> Bash is a terminal emulator and a terminal language


---

## (Non)Interactive & (Non)Login ##


### Which am I in? ###

- Command returns "**-bash**" = Non-Login
- Command returns "**bash**" = Login

```bash
    iain@home:~/Code/cheatsheets$ echo $0
    -bash
    iain@home:~/Code/cheatsheets$ bash
    iain@home:~/Code/cheatsheets$ echo $0
    bash
    iain@home:~/Code/cheatsheets$ exit
    iain@home:~/Code/cheatsheets$ echo $0
    -bash
    iain@home:~/Code/cheatsheets$ bash --login
    iain@home:~/Code/cheatsheets$ echo $0
    bash
```

### Login shell ###

Purpose is to load initializing code in the `.profile` or `.bash_profile` files

1. Computer starts
2. ssh to computer
3. Change user `su otheruser`
4. Run:
    - `bash --login`
    - `su -`
    - `su -l`
    - `su --login`
    - `su USERNAME -`
    - `su -l USERNAME`
    - `su --login USERNAME`
    - `sudo -i`

### Non-Login shell ###
1. One script calls another
2. Subshell ``` `ls` ``` or `(ls)`
3. Run `bash`

When you just want to run a command without the initialization. A new nonlogin shell is created anytime a script calls another script or the `bash` command is run.


### Interactive ###

1. New tty / console
2. Open a terminal emulator like Terminal, Alacritty, Terminator etc.
3. ssh into computer

This is basically a shell you type into. Any subshell from an interactive shell is also an interactive shell.

To test this you can 

### Non-Interactive ###

1. One script calls another

[Next => 'Files'](2_files.md)

