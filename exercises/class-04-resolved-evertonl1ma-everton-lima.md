```md
1- Adicionar 2 ataques ao mesmo tempo para os seguintes pokemons: Pikachu, 
   Squirtle, Bulbassauro e Charmander

2- Adicionar 1 movimento em todos os pokemons: 'desvio'.

3- Adicionar o pokemons "AindaNaoExisteMon" caso ele não exista com todos os dados com o 
   valor 'null' e a descrição: "Sem maiores informações".

4- Pesquisar todos os pokemons que possuam o ataque "investida" e mais um que você adicionou, 
   escolha seu pokemon favorito.

5- Pesquisar todos os pokemons que possuam os ataques que você adicionou, escolha seu pokemon favorito.

6- Pesquisar todos que não são do tipo "elétrico".

7- Pesquisar todos os pokemons que tenham "investida" e tenham a defesa não menor ou igual a 49.

8- Remova todos os pokemons do tipo água e com attack menor que 50.

9- Explicar as diferenças entre os operadores '$ne' e '$not'.
```


## Exercício 1

```js
var query= {name: /Pikachu/i}
var mod= {$pushAll: {moves: ["Esfera elétrica", "Investida trovão"]}}
 
db.pokemons.update(query, mod)

var query= {name: /Squirtle/i}
var mod= {$pushAll: {moves: ["Raio de gelo", "Giro rápido"]}}
 
db.pokemons.update(query, mod)

var query= {name: /Bulbassauro/i}
var mod= {$pushAll: {moves: ["Raio solar", "Dança de pétalas"]}}
 
db.pokemons.update(query, mod)

var query= {name: /Charmander/i}
var mod= {$pushAll: {moves: ["Brasas", "Encarar"]}}
 
db.pokemons.update(query, mod)

```

## Exercício 2

```js
var query= {}
var mod= {$push: {moves: "Desvio"}}
var options= {multi: true}
 
db.pokemons.update(query, mod, options)

```

## Exercício 3

```js
var query= {name: /AindaNaoExisteMon/i}
var mod= {$setOnInsert:
     {
	   name: "AindaNaoExisteMon",
	   type: null,
	   attack: null,
	   defense: null,
	   height: null,
	   description: "Sem maiores informações"
	 }
}

var options= {upsert: true}

db.pokemons.update(query, mod, options)
```

## Exercício 4 

```js

var query= {moves: {$in: [/raio de gelo/i, /giro rápido/i ]}}
db.pokemons.find(query)

{ "_id" : ObjectId("564501234d99cf12bbc22dde"), "name" : "Squirtle", "Description" : "Ejeta água que o passarinho não bebe", "type" : "água", "atack" : 48, "hei                                                               ght" : 0.5, "active" : true, "moves" : [ "Investida", "Hidro bomba", "Raio de gelo", "Giro rápido", "Desvio" ] }


```

## Exercício 5 

``js

var query= {moves: {$all: [/raio solar/i, /dança de pétalas/i]}}
db.pokemons.find(query)

{ "_id" : ObjectId("5644fd6f94c4f27819da5726"), "name" : "Bulbassauro", "Description" : "Chicote de trepadeira", "type" : "grama", "atack" : 49, "height" : 0.4, "active" : true, "moves" : [ "Investida", "Folha Navalha", "Raio solar", "Dança de pétalas", "Desvio" ] }


```

## Exercício 6 

```js

var query= {type: {$not: /elétrico/i}}
db.pokemons.find(query).pretty()

{
        "_id" : ObjectId("56450ad2521495068466e39d"),
        "name" : "Caterpie",
        "Description" : "Larva lutadora",
        "type" : "inseto",
        "atack" : 30,
        "height" : 0.3,
        "defense" : 35,
        "active" : true,
        "moves" : [
                "Investida",
                "Desvio"
        ]
}
{
        "_id" : ObjectId("5644f98677799cd5d9f21749"),
        "name" : "Pikachu",
        "Description" : "Rato elétrico bem fofinho",
        "type" : "eletric",
        "atack" : 55,
        "height" : 0.4,
        "active" : true,
        "moves" : [
                "Investida",
                "Choque do Trovão",
                "Esfera elétrica",
                "Investida trovão",
                "Desvio"
        ]
}
{
        "_id" : ObjectId("564f9799607966c5bb3a1f2d"),
        "active" : true,
        "name" : "NaoExisteMon",
        "atack" : null,
        "defense" : null,
        "height" : null,
        "description" : "Sem maiores informações",
        "moves" : [
                "Investida",
                "Desvio"
        ]
}
{
        "_id" : ObjectId("564f78ad607966c5bb3a1f2c"),
        "active" : true,
        "moves" : [
                "Investida",
                "Desvio"
        ]
}
{
        "_id" : ObjectId("564501234d99cf12bbc22dde"),
        "name" : "Squirtle",
        "Description" : "Ejeta água que o passarinho não bebe",
        "type" : "água",
        "atack" : 48,
        "height" : 0.5,
        "active" : true,
        "moves" : [
                "Investida",
                "Hidro bomba",
                "Raio de gelo",
                "Giro rápido",
                "Desvio"
        ]
}
{
        "_id" : ObjectId("5644fd6f94c4f27819da5726"),
        "name" : "Bulbassauro",
        "Description" : "Chicote de trepadeira",
        "type" : "grama",
        "atack" : 49,
        "height" : 0.4,
        "active" : true,
        "moves" : [
                "Investida",
                "Folha Navalha",
                "Raio solar",
                "Dança de pétalas",
                "Desvio"
        ]
}
{
        "_id" : ObjectId("5644ff114d99cf12bbc22ddd"),
        "name" : "Charmander",
        "Description" : "É o cão chupando manga de fofinho!",
        "type" : "fogo",
        "atack" : 52,
        "height" : 0.6,
        "active" : true,
        "moves" : [
                "Investida",
                "Lança Chamas",
                "Brasas",
                "Encarar",
                "Desvio"
        ]
}
{
        "_id" : ObjectId("5656a6f89b00f08b5143f1ac"),
        "name" : "AindaNaoExisteMon",
        "type" : null,
        "attack" : null,
        "defense" : null,
        "height" : null,
        "description" : "Sem maiores informações"
}

```

## Exercício 7 

```js

var query= {$and: [{moves: {$in: ["Investida"]}}, {attack: {$not: {$lte: 49}}}]}
db.pokemons.find(query).pretty()

{
        "_id" : ObjectId("56450ad2521495068466e39d"),
        "name" : "Caterpie",
        "Description" : "Larva lutadora",
        "type" : "inseto",
        "atack" : 30,
        "height" : 0.3,
        "defense" : 35,
        "active" : true,
        "moves" : [
                "Investida",
                "Desvio"
        ]
}
{
        "_id" : ObjectId("5644f98677799cd5d9f21749"),
        "name" : "Pikachu",
        "Description" : "Rato elétrico bem fofinho",
        "type" : "eletric",
        "atack" : 55,
        "height" : 0.4,
        "active" : true,
        "moves" : [
                "Investida",
                "Choque do Trovão",
                "Esfera elétrica",
                "Investida trovão",
                "Desvio"
        ]
}
{
        "_id" : ObjectId("564f9799607966c5bb3a1f2d"),
        "active" : true,
        "name" : "NaoExisteMon",
        "atack" : null,
        "defense" : null,
        "height" : null,
        "description" : "Sem maiores informações",
        "moves" : [
                "Investida",
                "Desvio"
        ]
}
{
        "_id" : ObjectId("564f78ad607966c5bb3a1f2c"),
        "active" : true,
        "moves" : [
                "Investida",
                "Desvio"
        ]
}
{
        "_id" : ObjectId("564501234d99cf12bbc22dde"),
        "name" : "Squirtle",
        "Description" : "Ejeta água que o passarinho não bebe",
        "type" : "água",
        "atack" : 48,
        "height" : 0.5,
        "active" : true,
        "moves" : [
                "Investida",
                "Hidro bomba",
                "Raio de gelo",
                "Giro rápido",
                "Desvio"
        ]
}
{
        "_id" : ObjectId("5644fd6f94c4f27819da5726"),
        "name" : "Bulbassauro",
        "Description" : "Chicote de trepadeira",
        "type" : "grama",
        "atack" : 49,
        "height" : 0.4,
        "active" : true,
        "moves" : [
                "Investida",
                "Folha Navalha",
                "Raio solar",
                "Dança de pétalas",
                "Desvio"
        ]
}
{
        "_id" : ObjectId("5644ff114d99cf12bbc22ddd"),
        "name" : "Charmander",
        "Description" : "É o cão chupando manga de fofinho!",
        "type" : "fogo",
        "atack" : 52,
        "height" : 0.6,
        "active" : true,
        "moves" : [
                "Investida",
                "Lança Chamas",
                "Brasas",
                "Encarar",
                "Desvio"
        ]
}


```