📡 Projeto RealtimeDB 2025A
Este projeto demonstra a integração do Firebase Realtime Database com aplicações desenvolvidas em Flutter e Vuejs. Ele permite a sincronização de dados em tempo real entre diferentes plataformas.

📁 Estrutura do Projeto
app/: Aplicativo Flutter.

site/: Aplicação Vuejs

🚀 Pré-requisitos
Antes de começar, certifique-se de ter as seguintes ferramentas instaladas:

Flutter SDK

Node.js (versão 20.x ou superior)

Firebase CLI

Conta no Firebase

🔧 Configuração do Firebase
Acesse o Console do Firebase e crie um novo projeto.

No menu lateral, vá em Build > Realtime Database e clique em Criar banco de dados.

Escolha a localização do banco de dados e selecione o modo de segurança apropriado:

Modo de teste: Permite leitura e escrita sem autenticação (não recomendado para produção).

Modo bloqueado: Requer autenticação para acesso.

📱 Configuração Firebase no Flutter (app/)
Inicialize o Firebase no projeto Flutter
No terminal, dentro do diretório app/, execute:

```shell
dart pub global activate flutterfire_cli
flutterfire configure
```
Siga as instruções para selecionar o projeto Firebase e as plataformas desejadas. Isso gerará o arquivo lib/firebase_options.dart.
Qualquer duvida pode acessar <a>https://firebase.google.com/docs/database/flutter/start?hl=pt-br</a>

🌐 Configuração Firebase no Vuejs (site/)
Inicialize o Firebase no código
Crie um arquivo Firebase.js com conteúdo disponibilizado no console da firebase:
Exemplo:
```shell
import { initializeApp } from 'firebase/app';
import { getDatabase } from 'firebase/database';

const firebaseConfig = {
  apiKey: "SUA_API_KEY",
  authDomain: "seu-projeto.firebaseapp.com",
  databaseURL: "https://seu-projeto.firebaseio.com",
  projectId: "seu-projeto",
  storageBucket: "seu-projeto.appspot.com",
  messagingSenderId: "SEU_SENDER_ID",
  appId: "SEU_APP_ID"
};

const app = initializeApp(firebaseConfig);
const database = getDatabase(app);

export { database };
```
Substitua os valores acima pelas informações do seu projeto Firebase, disponíveis no console do Firebase.
