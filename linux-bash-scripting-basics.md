# Linux Bash Scripting Basics

---

# What is a Bash Script?

A Bash script is a text file containing a sequence of Linux commands that are executed automatically by the Bash shell.

Benefits:
- Automate repetitive tasks
- Save time
- Reduce human error
- Simplify system administration

---

# Creating a Script

Create a new script:

```bash
vi script.sh
```

Every Bash script should begin with the shebang:

```bash
#!/bin/bash
```

This tells the operating system to execute the script using the Bash interpreter.

---

# Example 1 — Basic Commands

```bash
#!/bin/bash

echo "Hello, World!"
date
ls ~/
```

This script:
- Prints a message
- Displays the current date
- Lists the files in the user's home directory

---

# Variables

```bash
#!/bin/bash

VAR="Hello, World!"

echo $VAR
echo $PWD
```

Special variable:

- `$PWD` → Current working directory

---

# Script Parameters

```bash
#!/bin/bash

echo "Number of parameters: $#"
echo "All parameters: $*"

echo "First parameter: $1"
echo "Second parameter: $2"
echo "Third parameter: $3"

date

echo "Script PID: $$"

echo "Exit status of previous command: $?"
```

Special variables:

| Variable | Description |
|----------|-------------|
| `$#` | Number of arguments |
| `$*` | All arguments |
| `$1` | First argument |
| `$2` | Second argument |
| `$3` | Third argument |
| `$$` | Process ID of the script |
| `$?` | Exit status of the previous command |

---

# User Input

```bash
#!/bin/bash

echo -n "Do you like Linux? "
read ANSWER

if [ "$ANSWER" == "yes" ]; then
    echo "Great!"
fi
```

---

# if / elif / else

```bash
#!/bin/bash

echo -n "Do you like Linux? "
read ANSWER

if [ "$ANSWER" == "yes" ]; then
    echo "Great!"

elif [ "$ANSWER" == "no" ]; then
    echo "Maybe you'll like it later."

else
    echo "Invalid answer."
fi
```

---

# Numeric Comparison

```bash
#!/bin/bash

echo -n "How old are you? "
read AGE

if [ "$AGE" -lt 18 ]; then
    echo "You are under 18."

elif [ "$AGE" -lt 35 ]; then
    echo "You are between 18 and 34."

else
    echo "You are 35 or older."
fi
```

Comparison operators:

| Operator | Meaning |
|----------|---------|
| `-eq` | Equal |
| `-ne` | Not equal |
| `-lt` | Less than |
| `-le` | Less than or equal |
| `-gt` | Greater than |
| `-ge` | Greater than or equal |

---

# while Loop

```bash
#!/bin/bash

LEAVE="no"

while [ "$LEAVE" != "yes" ]; do

    echo -n "How old are you? "
    read AGE

    if [ "$AGE" -lt 18 ]; then
        echo "You are under 18."

    elif [ "$AGE" -lt 35 ]; then
        echo "You are between 18 and 34."

    else
        echo "You are 35 or older."
    fi

    echo -n "Exit script? (yes/no): "
    read LEAVE

done
```

The loop continues until the user enters `yes`.

---

# for Loop

```bash
#!/bin/bash

for i in $(seq 1 10); do
    echo $i
done
```

Output:

```text
1
2
3
4
5
6
7
8
9
10
```

---

# while Counter Loop

```bash
#!/bin/bash

i=1

while [ "$i" -le 10 ]; do
    echo $i
    i=$((i + 1))
done
```

This loop prints the numbers from **1** to **10**.

---

## 🧠 Summary

Bash scripting enables Linux users to automate tasks by combining commands, variables, conditions, loops, and user input into executable scripts. It is an essential skill for Linux administration, DevOps, automation, and cybersecurity.
           
 


