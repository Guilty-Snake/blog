---
title: "Linux Shells"
date: 2026-03-23
tags: ["THM", "Linux"]
image: "images/linuxshells.png"
---
## Intro
Shells provide great features for the commands written in the CLI(Command Line Interface). Using the CLI instead of the GUI(Graphical User Interface) is similar to going into the kitchen of a restaurent to make your own dish instead of ordering one.

Though a lot of shells exist for Linux the default and as well as the most popular one is bash (Bourne-again Shell). 

The file /etc/shells contains all the installed shells on a Linux system. To switch between shells, their name can be typed in the terminal.
To permanently change a default shell, the command:
 chsh -s /usr/bin/zsh
can be used.

## Types of Linux shells
| Feature              | Bash | Fish | Zsh |
|:---------------------|:-----|:-----|:----|
| Fullname             | Bourne Again Shell | Friendly Interactive Shell | Z shell |
| Scripting            | It offers widely compatible scripting with extensive documentation available. | It has limited scripting features as compared to the other two shells. | It offers an excellent level of scripting, combining the traditional capabilities of Bash shell with some extra features. |
| Tab Completion       | It has basic tab completion feature | Gives suggestions based on previous commands | Can be extended heavily with plugins. |
| Customization        | Basic level of customization | It offers some good customization through interactive tools. | Advanced customization through oh-my-zsh framework. |
| User friendliness    | Least user friendly | Most user friendly | Highly user friendly with proper customization | 
| Syntax highlighting  | Not available | Built into the shell | Available through plugins |

## Shell scripting on Linux
A shell script is simply a set of commands that can be performed on a shell. It is utilized to automate repatitive commands that may need to be executed, so intead of executing the commands one by one we only need to execute the script once.

Scripts can be written in any programming language however in this post it is done through the text editor nano where a file with the extension .sh(default extension for bash scripts) needs to be created.

Every script should be started with #! a.k.a. shebang written in the first line of a script followed by the name of the interpretor to use while executing the script, which in case of this post is bash so it would look like this:
```bash
#!/bin/bash
```
### Variables syntax
echo is used to display string, read is used to read user input and "$" is used to call the value of a variable.
Note: A script can only be executed after giving it the relevent permission.
```bash
chmod +x first_script.sh
```
Script
```sh
# Defining the Interpreter 
#!/bin/bash
echo "Hey, what’s your name?"
read name
echo "Welcome, $name"
```

### Loops syntax
```sh
# Defining the Interpreter 
#!/bin/bash
# Defining the Loop
for i in {1..10};
do
echo $i
# done indicated the end
done
```

### Conditional statements syntax
```sh
# Defining the Interpreter 
#!/bin/bash
echo "Please enter your name first:"
read name
if [ "$name" = "Stewart" ]; then
        echo "Welcome Stewart! Here is the secret: You are adopted."
else #elif is used for multiple conditions
        echo "Sorry! You are not authorized to access the secret."
# fi is used to end the condition        
fi
```
