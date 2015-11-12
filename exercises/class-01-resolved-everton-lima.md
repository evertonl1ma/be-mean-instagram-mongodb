# MongoDB - Aula 01 - Exercício
autor: Everton Lima

## Importando os restaurantes

```
mongoimport --db be-mean --collection restaurantes --drop --file restaurantes.json
2015-11-12T03:32:55.933-0200    connected to: localhost
2015-11-12T03:32:55.961-0200    dropping: be-mean.restaurantes
2015-11-12T03:32:58.760-0200    [##############..........] be-mean.restaurantes7.1 MB/11.4 MB (62.3%)
2015-11-12T03:32:59.691-0200    imported 25359 documents
```

## Contando os restaurantes

```
db.restaurantes.find({}).count()
25359

```

