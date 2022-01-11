# Text is a universal interface, i.e. The Unix philosophy


> [This is the Unix philosophy](
https://homepage.cs.uri.edu/~thenry/resources/unix_art/ch01s06.html): Write programs that do one thing and do it well. Write programs to work together. Write programs to handle text streams, because that is a universal interface.


## Pre-req: installing csvkit

https://csvkit.readthedocs.io/en/latest/

[csvkit](https://csvkit.readthedocs.io/en/latest/) is a suite of CLI tools for handling CSV data, including converting from and to different formats. Install it with python's **pip**:

```sh
pip install csvkit
```


## The redirection operator `>`

> **Warning:** the redirection operator will automatically wipe out whatever path you point it to. There is no "Recycle Bin" in the command-line world

In the [BASICS.md](BASICS.md) lesson, we covered how to use `curl` and its `-o` option flag to specify the file path for saving the downloaded content:


```sh
curl -o my-example.html http://example.com

curl -o nic-cage.jpg https://upload.wikimedia.org/wikipedia/commons/c/c0/Nicolas_Cage_Deauville_2013.jpg
```

The `curl` program was designed to have that `-o` flag...but not all programs have that same flag or even the option to specify an output file. However, many/most CLI-friendly tools (including curl) will by default print to **stdout** — i.e. splurge text onto the screen. Luckily, there's a "standard" way of dealing with this interface — **redirect** the output to a file path:

```sh
curl http://example.com  >  myexample.html
``` 


## The pipe operator `|`

Not only can we redirect a program's stdout output to a file, we can redirect it into other programs using the **pipe operator**: `|` 

Note: not all programs are designed to accept **standard input** (aka **stdin**).

`curl` and `youtube-dl` and `mkdir` are examples of programs that **do not** accept stdin. However, most of the [csvkit](https://csvkit.readthedocs.io/en/latest/) tools *are* designed for stdin.


Try this out:

```sh
curl -L https://bit.ly/mz2022-simple 
```

And then:

```sh
curl -L https://bit.ly/mz2022-simple | csvsort -c value
```

And then:

```sh
curl -L https://bit.ly/mz2022-simple | csvsort -c value | csvcut -c value,id,name > my-simple-data.csv
```

Which, when you get used to writing scripts, is more readable as:

```sh
curl -L https://bit.ly/mz2022-simple \
    | csvsort -c value \
    | csvcut -c value,id,name \
    > my-simple-data.csv
```




## Real-world data exercise

The [European Centre for Disease Prevention and Control](https://www.ecdc.europa.eu/en/publications-data/download-todays-data-geographic-distribution-covid-19-cases-worldwide) has historical Covid data in CSV format:

https://opendata.ecdc.europa.eu/covid19/casedistribution/csv/data.csv

- Download it with curl
- Inspect its headers with `csvcut -n`
- Create a subset of the data by continent, sorted by cases




