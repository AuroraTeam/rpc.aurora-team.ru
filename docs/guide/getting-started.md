# Использование

Стандартная реализация написана на Typescript. Так что она может использоваться в Web и Node.js приложениях написаных на Typescript и Javascript.

## Установка (Client)

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
