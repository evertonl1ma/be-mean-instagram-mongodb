# MongoDB - Aula 03 - Exercício

## Estrutura

```md
# MongoDB - Aula 03 - Exercício
autor: **Everton Lima**

## Liste todos Pokemons com a altura **menor que** 0.5

var query= {height: {$lt: 0.5}}

db.pokemons.find(query)
{ "_id" : ObjectId("5644f98677799cd5d9f21749"), "name" : "Pikachu", "Description" : "Rato elétrico bem fofinho", "type" : "eletric", "atack" : 55, "height" : 0.4}
{ "_id" : ObjectId("5644fd6f94c4f27819da5726"), "name" : "Bulbassauro", "Description" : "Chicote de trepadeira", "type" : "grama", "atack" : 49, "height" : 0.4}
{ "_id" : ObjectId("56450ad2521495068466e39d"), "name" : "Caterpie", "Description" : "Larva lutadora", "type" : "inseto", "atack" : 30, "height" : 0.3, "defense" : 35 }


## Liste todos Pokemons com a altura **maior ou igual que** 0.5 **E** do tipo grama

var query= {height: {$gte: 0.5}}
db.pokemons.find(query);
{ "_id" : ObjectId("5644ff114d99cf12bbc22ddd"), "name" : "Charmander", "Description" : "Esse é o cão chupando manga fofinho\u001b[D\u001b[D\u001b[D\u001b[D\u001b[D\u001b[D\u001b[Dde \u001b[C\u001b[C\u001b fofinho", "type" : "fogo", "atack": 52, "height" : 0.6 }
{ "_id" : ObjectId("564501234d99cf12bbc22dde"), "name" : "Squirtle", "Description" : "Ejeta água que o passarinho não bebe", "type" : "água", "atack" : 48, "height" : 0.5 }

## Liste todos Pokemons com a altura **menor ou igual que** 0.5 **E** do tipo grama

var query= {$and: [{height: {$lte: 0.5}}, {type: /grama/}]}
db.pokemons.find(query)
{ "_id" : ObjectId("5644fd6f94c4f27819da5726"), "name" : "Bulbassauro", "Description" : "Chicote de trepadeira", "type" : "grama", "atack" : 49, "height" : 0.4 }



## Liste todos os Pokemons com o name 'Pikachu' **OU** com attack **menor** ou igual que** 0.5

var query= {$or: [{atack: {$lte: 50}}, {name: /pikachu/i}]}
db.pokemons.find(query)
{ "_id" : ObjectId("5644f98677799cd5d9f21749"), "name" : "Pikachu", "Description" : "Rato elétrico bem fofinho", "type" : "eletric", "atack" : 55, "height" : 0.4 }
{ "_id" : ObjectId("5644fd6f94c4f27819da5726"), "name" : "Bulbassauro", "Description" : "Chicote de trepadeira", "type" : "grama", "atack" : 49, "height" : 0.4 }
{ "_id" : ObjectId("564501234d99cf12bbc22dde"), "name" : "Squirtle", "Description" : "Ejeta água que o passarinho não bebe", "type" : "água", "atack" : 48, "height" : 0.5 }
{ "_id" : ObjectId("56450ad2521495068466e39d"), "name" : "Caterpie", "Description" : "Larva lutadora", "type" : "inseto", "atack" : 30, "height" : 0.3, "defense" : 35 }


## Liste todos os Pokemons com o attack **Maior Ou igual que** 48 **E** com height **menor ou igual que** 0.5

var query= {$and: [{atack: {$gte: 48}}, {height: {$lte: 0.5}}]}
db.pokemons.find(query)
{ "_id" : ObjectId("5644f98677799cd5d9f21749"), "name" : "Pikachu", "Description" : "Rato elétrico bem fofinho", "type" : "eletric", "atack" : 55, "height" : 0.4}
{ "_id" : ObjectId("5644fd6f94c4f27819da5726"), "name" : "Bulbassauro", "Description" : "Chicote de trepadeira", "type" : "grama", "atack" : 49, "height" : 0.4}
{ "_id" : ObjectId("564501234d99cf12bbc22dde"), "name" : "Squirtle", "Description" : "Ejeta água que o passarinho não bebe", "type" : "água", "atack" : 48, "height" : 0.5}
