# Bußgeldkataloge „Corona-Pandemie“: Datenerzeugung

1. Suchanfrage
```
   https://www.verkuendung-bayern.de/baymbl/?offset=1&title=Bu%C3%9Fgeldkatalog&from=2020-03-01&to=2022-03-01
   https://www.verkuendung-bayern.de/baymbl/?offset=16&title=Bu%C3%9Fgeldkatalog&from=2020-03-01&to=2022-03-01
```
2. Extraktion Referenzen
suche nach Referenzen mit regex `baymbl\/\d*-\d*`
Ergebnis:
```
baymbl/2021-828
baymbl/2021-789
baymbl/2021-735
baymbl/2021-617
baymbl/2021-556
baymbl/2021-441
baymbl/2021-206
baymbl/2021-193
baymbl/2020-768
baymbl/2020-617
baymbl/2020-563
baymbl/2020-481
baymbl/2020-480
baymbl/2020-445
baymbl/2020-349
baymbl/2020-307
baymbl/2020-252
baymbl/2020-223
baymbl/2020-193
baymbl/2020-173
baymbl/2020-159
```
3. Download der Quellen
Erstellen der Dateiliste nach URL-Schema in `urls.txt`
```
https://www.verkuendung-bayern.de/baymbl/2021-828
https://www.verkuendung-bayern.de/baymbl/2021-789
https://www.verkuendung-bayern.de/baymbl/2021-735
https://www.verkuendung-bayern.de/baymbl/2021-617
https://www.verkuendung-bayern.de/baymbl/2021-556
https://www.verkuendung-bayern.de/baymbl/2021-441
https://www.verkuendung-bayern.de/baymbl/2021-206
https://www.verkuendung-bayern.de/baymbl/2021-193
https://www.verkuendung-bayern.de/baymbl/2020-768
https://www.verkuendung-bayern.de/baymbl/2020-617
https://www.verkuendung-bayern.de/baymbl/2020-563
https://www.verkuendung-bayern.de/baymbl/2020-481
https://www.verkuendung-bayern.de/baymbl/2020-480
https://www.verkuendung-bayern.de/baymbl/2020-445
https://www.verkuendung-bayern.de/baymbl/2020-349
https://www.verkuendung-bayern.de/baymbl/2020-307
https://www.verkuendung-bayern.de/baymbl/2020-252
https://www.verkuendung-bayern.de/baymbl/2020-223
https://www.verkuendung-bayern.de/baymbl/2020-193
https://www.verkuendung-bayern.de/baymbl/2020-173
https://www.verkuendung-bayern.de/baymbl/2020-159
```
Download mit `curl`
```
#!/bin/bash -e

for i in $(cat urls.txt); do
	curl -JLO $i
done
```
4. Extraktion der Tabellen
rename to html
  - Verkettung der Dateien mit `cat`
  - Extraktion mit Regex `<table .*?>.*?<\/table>`
  - import in Libre Office

 