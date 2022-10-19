# Использование

Стандартная реализация написана на Typescript. Так что она может использоваться в Web и Node.js приложениях написаных на Typescript и Javascript.

## Установка (Client)

`npm i aurora-rpc-client`

### Использование

```ts
import { Client } from "aurora-rpc-client";

// --- Connect ---

const client = new Client("ws://localhost:8080");
client.connect();

// or

const client = new Client();
client.connect("ws://localhost:8080");

// ---

const result = await client.send("hello");
console.log(result); // "Hello Aurora RPC!"
```

## Установка (Server)

`npm i aurora-rpc-server`

### Использование

```ts
import { Server } from 'aurora-rpc-server';

const debug = false; // Установите значение true, чтобы включить вывод отладки

const server = new Server({
    // параметры сервера websocket (из библиотеки ws)
    port: 8080,
}, debug);

// --- Создайте обработчик запроса ---

import { AbstractRequest, ResponseResult } from 'aurora-rpc-server';

class HelloRequest extends AbstractRequest {
    method = "hello"

    invoke(): ResponseResult {
        return "Hello Aurora RPC!";
    }
}

// --- Зарегистрируйте обработчики запросов ---

server.registerRequest(new HelloRequest());
server.registerRequest(new AnotherRequest());
...
```
