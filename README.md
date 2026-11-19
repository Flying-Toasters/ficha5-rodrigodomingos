Como executar a aplicação

Entre no Visual Studio Code e abra dois Terminais (Terminal -> New Terminal OU Ctrl+Shift+ç)

Nos dois terminais, clique o botão de + e selecione Git Bash

Corra os seguintes comandos no primeiro terminal:

cd server

npm install

node --watch server.js

Corra os seguintes comandos no segundo terminal:

cd client

npm install

npm run dev

API:
GET /api/cartas, recebe nada, responde 200 e um array com todas as cartas
GET /api/cartas/aleatoria, não recebe nada e responde 200 com uma cartas escolhida ao acaso
POST /api/cartas, recebe name e type e responde 201 com uma carta criada e o seu id

Questão 3:
O primeiro request é um OPTIONS, mandado pelo próprio browser. A razão pela qual o console.log não aparecia no terminal antes do pacote cors é por que o servidor não conseguia responder com os headers de autorização do cors, por isso o browser cancelava o POST antes de enviar; se o POST nunca chegasse, naturalmente, o console.log da rota nunca correria.

Questão 4:
setCards: a carta nova vivia na memória do browser. Era apagado quando desse refresh no browser (F5).
POST sem ficheiro: a carta nova vivia no array cards do servidor. Agora sobrevivia ao refresh, mas era apagada ao reiniciar o servidor.
POST com cartas.json: a carta nova vivia no ficheiro cartas.json, ou seja, no disco. Agora, nem refresh nem reiniciar o servidor deletava-a; apenas com o método DELETE ou edição manual do ficheiro. 