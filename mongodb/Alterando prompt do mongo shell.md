#Alterando o prompt do mongo shell

O prompt do mongo shell apresenta por padr�o tr�s informa��es 

 1. host onde esta em execu��o
 2. vers�o do mongodb em use, e
 3. banco de dados corrente

As duas primeiras informa��es s�o irrelevantes se a sua execu��o � local ou em servidor conhecido, al�m de atrapalhar a leitura do terminal. 

Veja abaixo alguns exemplos para diferentes sistemas operacionais, sendo o pior caso a instala��o windows que apresenta ainda o drive e pasta onde o execut�vel esta instalado:

 - MacBook-Pro-de-xxxxxxxxxx(mongod-3.0.7) be-mean-pokemons>
 - linux(mongod-2.6.10) be-mean-pokemons>
 - xxxxxxxxx-debian(mongod-3.0.7) be-mean-pokemons>
 - Mac-mini-de-xxxxxxxx(mongod-3.0.7) be-mean-pokemons>
 - 5e14de9d5d4e(mongod-3.0.7) be-mean-pokemons>
 - Ubuntu-pc(mongod-3.0.7) be-mean-pokemons>
 - RNEQHOME(D:\mongodb\bin\mongod.exe-3.0.7)be-mean-pokemons>

Para alterar esse padr�o, mostrando apenas o baco de dados em use digite o seguinte comando ap�s iniciar o mongo client:
```
var prompt = function() {return db + "> ";}
```

fonte: https://docs.mongodb.org/manual/