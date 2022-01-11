# Bigquery and the command line

(quick notes)

Must have official bq tool installed on machine: https://cloud.google.com/bigquery/docs/bq-command-line-tool


How to use `bq query` to download data as CSV

```sh
bq query -use_legacy_sql=false 'SELECT COUNT(1) FROM bigquery-public-data.chicago_crime.crime'

bq query -use_legacy_sql=false --format csv 'SELECT * FROM bigquery-public-data.chicago_crime.crime'

```


```sh
bq query --max_rows 10000000 \
    -use_legacy_sql=false \
    --format csv 'SELECT * FROM bigquery-public-data.chicago_crime.crime' \
    > /tmp/crimes.csv
```



```sh
curl -o eu-covid.xlsx https://www.ecdc.europa.eu/sites/default/files/documents/COVID-19-geographic-disbtribution-worldwide-2020-12-14.xlsx

in2csv eu-covid.xlsx > eu-covid.csv

csvgrep -c 11 -m America eu-covid.csv > my-covid.csv


bq load --source_format=CSV \
    --autodetect \
    --replace \
    'mm-sandbox-decision-sciences:sample_places.dans_covid_data' \
    my-covid.csv


```
