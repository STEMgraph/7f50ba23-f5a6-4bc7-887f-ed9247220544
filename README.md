<!---
{
  "id": "7f50ba23-f5a6-4bc7-887f-ed9247220544",
  "teaches": "Shell Scripts",
  "depends_on": [],
  "author": "Stephan Bökelmann",
  "first_used": "2025-04-08",
  "keywords": ["bash", "shell", "script", "shebang"]
}
--->

# Shell Scripts

## Introduction
Shell scripts are the entry-point into programmable environments and the Unix philosophy: small tools, stream processing, and the idea that everything is a file. While operating systems of the 60s and 70s varied wildly in their capabilities, Unix distinguished itself by offering a coherent **programming environment**. In this exercise, you'll write your first scripts, understand how they are run, how they can be reused, and how to pass data between them. You'll also gain a solid understanding of how the shell locates and executes scripts.

The power of Unix lies not in its monolithic design, but in its composability. Programs do one thing well and communicate through text streams, often piped from one tool to the next. Shell scripting is the glue that connects these programs. Instead of large, all-in-one applications, Unix encourages you to create pipelines — sequences of commands where the output of one becomes the input of another. This approach is reflected in many modern systems, including cloud-native microservices and the modular design of Unix-inspired tools like Git.

By learning shell scripting, you step into a tradition shaped by pioneers like Ken Thompson, Dennis Ritchie, and Brian Kernighan. You're not just learning to automate tasks — you're learning to think in terms of process composition and flow, in line with the philosophy that "software tools should interact in a predictable and understandable way."

Shell scripts are used everywhere: from embedded systems to server automation, from job scheduling in scientific computing to deployment scripts in modern DevOps pipelines. They are an essential tool in a developer's toolbox, and mastering them will make you more effective, more resourceful, and more aware of what's actually happening when you type a command and press Enter.

### Further Reading and Other Sources

## Tasks

1. Creating and Running a Script
- Open a terminal and navigate to your home directory using:
  ```bash
  cd ~
  ```
- Create a new directory to store your scripts. We'll call it `myScripts`:
  ```bash
  mkdir myScripts
  cd myScripts
  ```
- Inside this directory, create a new file called `hello`:
  ```bash
  touch hello
  ```
- Open the file using a text editor (like `nano`, `vim`, or any other):
  ```bash
  vim hello
  ```
- Add the following content:
  ```bash
  echo "Hello World!"
  ```
- Save and close the file.
- To run the script, type:
  ```bash
  bash hello
  ```
  This explicitly runs the file using the `bash` interpreter.

2. Using a Shebang and Making Scripts Executable
- The current script works, but it's not yet considered a proper standalone program. We want to make it executable directly, without explicitly calling `bash`.
- Open the `hello` file again and add the following line at the very top:
  ```bash
  #!/bin/bash
  ```
  This is called a **shebang** and tells the system which interpreter should be used to run the file.
- Save the file and close the editor.
- Now, we make the file executable by modifying its permissions:
  ```bash
  chmod +x hello
  ```
- To see the change, compare directory contents before and after:
  ```bash
  ls -la > before
  chmod +x hello
  ls -la > after
  vimdiff before after
  ```
- You can now run your script like this:
  ```bash
  ./hello
  ```
  The `./` prefix tells the shell to look for the file in the current directory.

3. Accepting Arguments in Scripts
- Shell scripts can also handle arguments passed to them from the command line.
- Create a new file called `sum`:
  ```bash
  touch sum
  vim sum
  ```
- Add the following content:
  ```bash
  #!/bin/bash
  sum=$(($1 + $2))
  echo $sum
  ```
  This script takes two numbers as input parameters (`$1` and `$2`), adds them, and prints the result.
- Make the script executable:
  ```bash
  chmod +x sum
  ```
- Run it with sample arguments:
  ```bash
  ./sum 3 5
  ```
  This should print `8`.

---

## Questions

1. Why do we need the `#!/bin/bash` line in our script?
2. What does the `chmod +x` command actually do?
4. What does `$1`, `$2`, ... mean in a shell script?

---

## Advice

To write better scripts and avoid common pitfalls, it's highly recommended to use tools like [ShellCheck](https://shellcheck.net), which can analyze your scripts for syntax issues, bad practices, or potential bugs. Additionally, if you're curious about the design and philosophy behind Unix and shell scripting, a foundational book like *The Unix Programming Environment* by Brian W. Kernighan and Rob Pike is an excellent read that explains not just the how but also the why of Unix-style programming. Finally, remember that shell scripts excel at automating tasks, creating pipelines, and gluing together tools in a Unix environment — but they are not meant to replace full-featured programming languages. Use them when they shine, and always keep readability and simplicity in mind.
