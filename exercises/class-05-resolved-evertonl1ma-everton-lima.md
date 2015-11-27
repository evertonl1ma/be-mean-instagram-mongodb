# Exercício 5

1- Importar as collections restaurantes e pokemons

2- Distinct por 'cuisine' na restaurantes

3- Distinct por 'types' na pokemons

4- As primeiras 3 páginas com .limit() e .skip() de pokemons (5 em 5)

5- Group ou aggregate contando a quantidade dos tipos de pokemons

6- Realizar 3 counts na pokemons
   - .count()
   - TIPO FOGO
   - só de quantos tem a defesa maior que 70
   

## Exercício 1

```md
$ mongoimport --host 127.0.0.1 --db be-mean --collection pokemons --drop --file pokemons.json
2015-11-26T23:16:13.313-0200    connected to: 127.0.0.1
2015-11-26T23:16:13.354-0200    dropping: be-mean.pokemons
2015-11-26T23:16:13.896-0200    imported 610 documents


$ mongoimport --host 127.0.0.1 --db be-mean --collection restaurantes --drop --file restaurantes.json
2015-11-26T23:17:15.928-0200    connected to: 127.0.0.1
2015-11-26T23:17:15.931-0200    dropping: be-mean.restaurantes
2015-11-26T23:17:18.925-0200    [####################....] be-mean.restaurantes9.8 MB/11.4 MB (86.2%)
2015-11-26T23:17:20.634-0200    imported 25359 documents

```

## Exercício 2 

```js 

db.restaurantes.distinct("cuisine")
[
        "Hamburgers",
        "Bakery",
        "Irish",
        "American ",
        "Jewish/Kosher",
        "Delicatessen",
        "Ice Cream, Gelato, Yogurt, Ices",
        "Chinese",
        "Other",
        "Chicken",
        "Turkish",
        "Caribbean",
        "Donuts",
        "Sandwiches/Salads/Mixed Buffet",
        "Bagels/Pretzels",
        "Continental",
        "Pizza",
        "Steak",
        "Italian",
        "Polish",
        "Latin (Cuban, Dominican, Puerto Rican, South & Central American)",
        "German",
        "French",
        "Pizza/Italian",
        "Mexican",
        "Spanish",
        "Café/Coffee/Tea",
        "Tex-Mex",
        "Pancakes/Waffles",
        "Soul Food",
        "Seafood",
        "Hotdogs",
        "Greek",
        "Not Listed/Not Applicable",
        "African",
        "Japanese",
        "Indian",
        "Armenian",
        "Thai",
        "Chinese/Cuban",
        "Mediterranean",
        "Korean",
        "Bottled beverages, including water, sodas, juices, etc.",
        "Russian",
        "Eastern European",
        "Middle Eastern",
        "Asian",
        "Ethiopian",
        "Vegetarian",
        "Barbecue",
        "Egyptian",
        "English",
        "Sandwiches",
        "Portuguese",
        "Indonesian",
        "Chinese/Japanese",
        "Filipino",
        "Juice, Smoothies, Fruit Salads",
        "Brazilian",
        "Afghan",
        "Vietnamese/Cambodian/Malaysia",
        "CafÃ©/Coffee/Tea",
        "Soups & Sandwiches",
        "Tapas",
        "Moroccan",
        "Pakistani",
        "Peruvian",
        "Bangladeshi",
        "Czech",
        "Salads",
        "Creole",
        "Fruits/Vegetables",
        "Iranian",
        "Cajun",
        "Scandinavian",
        "Polynesian",
        "Soups",
        "Australian",
        "Hotdogs/Pretzels",
        "Southwestern",
        "Nuts/Confectionary",
        "Hawaiian",
        "Creole/Cajun",
        "Californian",
        "Chilean"
]

``` 
## Exercício 3 

```js 

db.pokemons.distinct("types")
[
        "normal",
        "fire",
        "water",
        "bug",
        "flying",
        "poison",
        "electric",
        "steel",
        "ghost",
        "ice",
        "fighting",
        "psychic",
        "grass",
        "ground",
        "fairy",
        "rock",
        "dark",
        "dragon"
]

```

## Exercício 4 

```js 

db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 0)
{ "name" : "Rattata" }
{ "name" : "Charmander" }
{ "name" : "Charmeleon" }
{ "name" : "Wartortle" }
{ "name" : "Blastoise" }

db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 1)
{ "name" : "Caterpie" }
{ "name" : "Metapod" }
{ "name" : "Butterfree" }
{ "name" : "Spearow" }
{ "name" : "Kakuna" }

db.pokemons.find({}, {name: 1, _id: 0}).limit(5).skip(5 * 2)
{ "name" : "Farfetchd" }
{ "name" : "Magnemite" }
{ "name" : "Magneton" }
{ "name" : "Doduo" }
{ "name" : "Seel" }

```