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