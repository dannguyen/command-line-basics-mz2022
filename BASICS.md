# Basics of the command line


## Key pointers
- **Tab will keep you sane**: The single best habit to learn is to use the **Tab** key to autocomplete filenames, *no matter how short they are*. Hitting the *Tab* key ensures that you won't try to open a file that doesn't exist, or delete a file that you didn't mean to.
- **Whitespace is critical**: in command-line interfaces, spaces delimit the command from its arguments and options. In other words, dealing with filenames with spaces in them can be a hassle because the typical command-line interpreter doesn't know if it's one file or multiple files. 
    + When you can, you should avoid naming things with spaces — use dashes or underscores instead
    + Quote arguments that may have spaces in them, e.g. `mkdir "funky monkey"` if you want to create a single subdirectory named `funky monkey`, whitespace and all.
        * Try and see what happens when you don't quote `funky monkey`

## Accessing the command-line

MacOS: Look for **Terminal** under **Applications » Utilities**

Windows: 
- Typically, you'll be using **Powershell** (just type in "Powershell" in the Windows searchbar), which is a modern interface to Window's command line
- The legacy Windows shell is the **Command Prompt**, aka **cmd** — there's generally no reason to be using it instead of Powershell.


## Terminology of a command

### cd example

```sh
$ cd Desktop
```

- The `$` is the typical symbol for the **prompt**. In most systems, the prompt will be the current working directory, and the full command will look something like: `C:\Users\danso> curl.exe -I http://example.com`
- `cd` is the **command/program**, in this case, the "change directory" command
- `Desktop` is the **argument**, i.e. the thing for `cd` to *act on*. In this case, it's a subdirectory I want to navigate into. 

### curl example

```sh
$ curl.exe -I http://example.com 

# or, for MacOS/Unix:
$ curl -I http://example.com
```

- The `$` is the typical symbol for the **prompt**. In most systems, the prompt will be the current working directory, e.g. `C:\Users\danso> curl.exe -I http://example.com`
- `curl.exe` — the name of the program. **curl**, a program to download from URLs, is one of the most ubiquitous 3rd-party programs, comes standard on almost every modern system.
- `-I` — an **option flag** specific to the **curl** program (tells curl to just download a file's headers)
- `http://example.com` — an **argument** to the curl.exe program. Typically, curl expects a URL to download from.




## Navigation commands

In the syntax below, the bracketed values represent *arguments*, e.g.

```sh
mkdir [directory_to_create]
```

— would translate to this actual command:

```sh
mkdir my_test_directory
```

### Windows (both powershell and cmd)

- `dir` — list the contents of the current directory
- `mkdir [directory_path_to_create]` — create a directory
- `start [directory_path/file path]` — opens the given path with the default system program
    - `start .` — opens the current directory in File Explorer
    - `start ..` — opens the parent directory in File explorer
    - `start example.html` — opens `example.html` (assuming it exists) in your default web browser
- `move [source path] [target path]`


### MacOS

- `ls` — list the contents of the current directory
- `mkdir [directory_path_to_create]` create a directory
- `open [path]` — opens the given path with the default system program
    - `open .` — opens the current directory in Finder
    - `open ..` — opens the parent directory in Finder
    - `open example.html` — opens `example.html` (assuming it exists) in your default web browser



