# MongoDB - Aula 02 - Exercício
autor: Everton Lima

## Listagem das databases (Passo 2)

```
use be-mean-pokemons
switched to db be-mean-pokemons

ballon             0.078GB
be-mean            0.078GB
be-mean-instagram  0.078GB
languages          0.078GB
local              0.078GB
```

## Listagem das coleções (Passo 3)

show collections
pokemons
system.indexes


## Cadastro de Pokemons (Passo 4)

db.pokemons.insert(pokemons)
BulkWriteResult({
        "writeErrors" : [ ],
        "writeConcernErrors" : [ ],
        "nInserted" : 5,
        "nUpserted" : 0,
        "nMatched" : 0,
        "nModified" : 0,
        "nRemoved" : 0,
        "upserted" : [ ]
})

## Listagens dos pokemons (Passo 5)

db.pokemons.find()
{ "_id" : ObjectId("564668c07371891bdd4ce953"), "name" : "Raichu", "description" : "Evolução do Pikachu", "type" : "Eletric", "attack" : 50, "defense" : 30, "height" : 0.8 }
{ "_id" : ObjectId("564668c07371891bdd4ce954"), "name" : "Sandshrew", "description" : "Pokemon de pedra", "type" : "ground", "attack" : 40, "defense" : 40, "height" : 0.6 }
{ "_id" : ObjectId("564668c07371891bdd4ce955"), "name" : "Nidoran", "description" : "Pokemon rato", "type" : "Poison", "attack" : 30, "defense" : 20, "height" : 0.4 }
{ "_id" : ObjectId("564668c07371891bdd4ce956"), "name" : "Clefairy", "description" : "Pokemon fada", "type" : "Fairy", "attack" : 20, "defense" : 20, "height" : 0.6 }
{ "_id" : ObjectId("564668c07371891bdd4ce957"), "name" : "Vulpix", "description" : "Pokemon raposa", "type" : "Fire", "attack" : 20, "defense" : 20, "height" : 0.6 }


## Armazendo um pokemon numa varíavel (Passo 6)

var querie= {name: "Raichu"}
var poke= db.pokemons.findOne(querie)
poke
{
        "_id" : ObjectId("564668c07371891bdd4ce953"),
        "name" : "Raichu",
        "description" : "Evolução do Pikachu",
        "type" : "Eletric",
        "attack" : 50,
        "defense" : 30,
        "height" : 0.8
}

## Atualizando a descrição e salvando (Passo 7)

poke.description
Evolução do Pikachu
poke.description= "Evolução e muito mais legal do que o Pikachu"
Evolução e muito mais legal do que o Pikachu

db.pokemons.save(poke)
WriteResult({ "nMatched" : 1, "nUpserted" : 0, "nModified" : 1 })
db.pokemons.findOne()
{
        "_id" : ObjectId("564668c07371891bdd4ce953"),
        "name" : "Raichu",
        "description" : "Evolução e muito mais legal do que o Pikachu",
        "type" : "Eletric",
        "attack" : 50,
        "defense" : 30,
        "height" : 0.8
}


db.pokemons.find()
{ "_id" : ObjectId("564668c07371891bdd4ce953"), "name" : "Raichu", "description"                                                                : "Evolução e muito mais legal do que o Pikachu", "type" : "Eletric", "attack"                                                                : 50, "defense" : 30, "height" : 0.8 }
{ "_id" : ObjectId("564668c07371891bdd4ce954"), "name" : "Sandshrew", "descripti                                                               on" : "Pokemon de pedra", "type" : "ground", "attack" : 40, "defense" : 40, "hei                                                               ght" : 0.6 }
{ "_id" : ObjectId("564668c07371891bdd4ce955"), "name" : "Nidoran", "description                                                               " : "Pokemon rato", "type" : "Poison", "attack" : 30, "defense" : 20, "height" :                                                                0.4 }
{ "_id" : ObjectId("564668c07371891bdd4ce956"), "name" : "Clefairy", "descriptio                                                               n" : "Pokemon fada", "type" : "Fairy", "attack" : 20, "defense" : 20, "height" :                                                                0.6 }
{ "_id" : ObjectId("564668c07371891bdd4ce957"), "name" : "Vulpix", "description"                                                                : "Pokemon raposa", "type" : "Fire", "attack" : 20, "defense" : 20, "height" :                                                                0.6 }

