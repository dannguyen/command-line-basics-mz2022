# Quick starter demo

- Open up Terminal in Mac OS
- navigate to the desktop
- `open .` to show Finder
- `ls` to list files
- `cd` to change directories
- `mkdir` to make a directory
- `mkdir -p hey/you/guys/a/b/c`


# Learn keyboard tricks:

- Up cursor to cycle through past commands
- Tab to autocomplete filenames (ESSENTIAL)
- Ctrl-A to jump to beginning of line
- Ctrl to jump to end of line



# Download the repo

```sh
git clone https://github.com/dannguyen/command-line-basics-mz2022.git
```

# Data specific commands

```sh
# bigquery querying
# https://console.cloud.google.com/bigquery?project=data-lake-production-246315&d=chicago_crime&p=bigquery-public-data&t=crime&page=table&ws=!1m5!1m4!4m3!1sbigquery-public-data!2schicago_crime!3scrime


### Downloading

bq query -use_legacy_sql=false 'SELECT COUNT(1) FROM bigquery-public-data.chicago_crime.crime'

bq query -use_legacy_sql=false --format csv 'SELECT * FROM bigquery-public-data.chicago_crime.crime'


## Uploading to bigquery
# curl stuff
curl -L https://bit.ly/mz2022-simple 

curl -L https://bit.ly/mz2022-simple  > mytable.csv



bq load --source_format=CSV --autodetect --replace \
    'mm-sandbox-decision-sciences:sample_places.dans_easy_table' \
    mytable.csv
```

# Find fun tools to use

```sh
youtube-dl https://twitter.com/POTUS/status/1478729288895672322
```



# Piping stuff


```sh
curl -L https://bit.ly/mz2022-simple | csvsort -c value

```
