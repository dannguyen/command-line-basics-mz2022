# Basics of the command line


## Key pointers


- **Tab will keep you sane**: The single best habit to learn is to use the **Tab** key to autocomplete filenames, *no matter how short they are*. Hitting the *Tab* key ensures that you won't try to open a file that doesn't exist, or delete a file that you didn't mean to.
- **Whitespace is critical**: in command-line interfaces, spaces delimit the command from its arguments and options. In other words, dealing with filenames with spaces in them can be a hassle because the typical command-line interpreter doesn't know if it's one file or multiple files. 
    + When you can, you should avoid naming things with spaces — use dashes or underscores instead
    + Quote arguments that may have spaces in them, e.g. `mkdir "funky monkey"` if you want to create a single subdirectory named `funky monkey`, whitespace and all.
        * Try and see what happens when you don't quote `funky monkey`

## Accessing the command-line

**MacOS:** Look for **Terminal** under **Applications » Utilities**

**Windows:** 
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



## Git and navigation exercise

Clone the repo for these notes with:

```sh
git clone https://github.com/dannguyen/command-line-basics-mz2022
```

- Use `dir` (or `ls` on Mac) to find out what happened, i.e. where that repo went
- Use `start` (Mac: `open`) to open the repo directory in your system's file finder
- Use `move` (Mac: `mv`) to rename the repo directory
- 



## Fun with curl

The `curl` program (use `curl.exe` on Windows) is a ubiquitous open source utility for downloading from URLs.

For example, to download the contents of the website at [example.com](http://example.com):

```sh
curl http://example.com
```

HTML is just text, but you can also download plain text files, e.g. from Project Gutenberg

```sh
curl https://www.gutenberg.org/cache/epub/1041/pg1041.txt
```



### curl's -o option flag

Many Unix/CLI-minded tools by default will output to screen (often called **stdout**, i.e. standard output). Usually, this isn't helpful because we want to capture what we've downloaded as a file.

One of the options `curl` has is to use its `-o` option flag to specify an output path:


### why minimalist curl?


I created a bitly alias for a file to make it easy to refer to: https://bit.ly/mz2022-simple

However, if you try to curl it, you might see something like this in the output:

```
<html>
<head><title>Bitly</title></head>
<body><a href="https://raw.githubusercontent.com/dannguyen/command-line-basics-mz2022/main/files/simple-data.csv">moved here</a></body>
```

That's because by default, curl doesn't follow redirects (like a webbrowser would). So you have to use the `-L` (nickname for `--location`):

```sh
curl -L https://bit.ly/mz2022-simple
```



Where does that `https://bit.ly/mz2022-simple` URL actually redirect? You don't get to see it when visiting it via a high-level tool (i.e. a web browser). Low-level tools like curl provide countless options for specific needs.

If you ever want to check the metadata of a URL (e.g. where it redirects to), but don't want to risk clicking it, use curl's `-I` flag (which is an alias for `--head`):

```sh
curl -I https://bit.ly/mz2022-simple

curl --head  https://bit.ly/mz2022-simple
```


```sh
# for windows, use curl.exe instead of just curl
curl http://example.com -o example-file.txt
```

Note, `curl` — and many other CLI programs, are designed to accept option flags in any order, including before/after the required argument. In other words, this will work too:

```sh
curl -o example-file.txt http://example.com 
```

(Keep curl in mind when going into the [Text as interface](JUSTTEXT.md) lesson)


## Fun with Python-installed tools

The following section can only be done if `python` is installed on your computer, and your shell is aware of Python, e.g. you are able to successfully run `python --version`


### youtube-dl

A tool for easily downloading videos from Youtube and many other popular video sites:

https://youtube-dl.org/

Install with Python's `pip`:

```sh
pip install youtube-dl
```

Run `youtube-dl --help` to see its huge number of options.

Try out these 3 different ways to download a movie from the same URL, and note the different results:


```sh
youtube-dl https://twitter.com/POTUS/status/1478729288895672322
```

```sh
youtube-dl --id https://twitter.com/POTUS/status/1478729288895672322
```

```sh
youtube-dl -o potus-video.mp4 https://twitter.com/POTUS/status/1478729288895672322
```








