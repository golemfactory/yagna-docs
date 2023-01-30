---
description: A minimal example of a functional Golem requestor agent in browser
---

# Task Example 3: Requestor in browser

{% hint style="info" %}
This example illustrates following Golem features & aspects:

* VM runtime
* Task execution from browser context
* Retrieving command output from provider's exe unit
{% endhint %}

## Prerequisites

The only difference compared to the previous examples is the launch the yagna daemon with a parameter that allows you to handle requests in REST API with CORS policy. You can do it by:

```shell
yagna service run --api-allow-origin='http://localhost:3000'
```

The origin you set depends on the place where your web application with the requestor code will be served.

## Simple web app

To create a simple web application with a single html file, we use the standard nodejs library. We create `app.js` with the content:

```javascript
const http = require("http");
const fs = require("fs");

const server = http.createServer((req, res) => {
  res.writeHead(200, { "content-type": "text/html" });
  fs.createReadStream("index.html").pipe(res);
});

server.listen(3000, () => console.log(`Server listen at http://localhost:3000`));
```

Then wen need to create main `index.html` file with minimal layout:
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Golem App</title>
</head>
<body>
    <button onclick="run()">Run</button>
    <div class="container">
        <div>
            <p>Results</p>
            <pre id="results"></pre>
        </div>
        <div>
            <p>Logs</p>
            <pre id="logs"></pre>
        </div>
    </div>
  <script></script>
</body>
</html>
```

In this layout we have three elements: 
 - run button which execute script on golem
 - results container which shows the results
 - logs container which shows api logs

## Use Yajsapi bundle library

Yajsapi is available via CDN. You should add the following script to the head section of `index.html`

```html
    <script crossorigin src="https://unpkg.com/yajsapi/yajspai.min.js"></script>
```

### Task Executor

Using the Golem network, an example script can be triggered by creating a TaskExecutor and running a command on the provider. In order for this process take place, it is necessary that certain steps are followed.
```html
<script>
    async function run() {
        const executor = await yajsapi.TaskExecutor.create({
            package: "9a3b5d67b0b27746283cb5f287c13eab1beaa12d92a9f536b747c7ae",
            yagnaOptions: { appKey: 'YOUR_YAGNA_APP_KEY' }
            logger
        });
        await executor
            .run(async (ctx) => appendResults((await ctx.run("echo 'Hello World'")).stdout))
            .catch(e => logger.error(e));
        await executor.end();
    }
</script>
```

## Getting results

We will present the end result by taking advantage of the `appendResult` function, which will put the output of our application into the designated `results` container.
```html
<script>
    function appendResults(result) {
        const results = document.getElementById('results');
        const div = document.createElement('div');
        div.appendChild(document.createTextNode(result));
        results.appendChild(div);
    }
</script>
```

## Getting logs

The TaskExecutor offers a logger parameter as optional. To accomplish this, you need to implement the Logger interface. To capture logging messages in our script for display purposes, we will develop a unique `logger` and create the `appendLog` function to add applicable records to the log storage area.
```html
<script>
    function appendLog(msg, level = 'info') {
        const logs = document.getElementById('logs');
        const div = document.createElement('div');
        div.appendChild(document.createTextNode(`[${new Date().toISOString()}] [${level}] ${msg}`));
        logs.appendChild(div);
    }
    const logger = {
        log: (msg) => appendLog(msg),
        warn: (msg) => appendLog(msg, 'warn'),
        debug: (msg) => appendLog(msg, 'debug'),
        error: (msg) => appendLog(msg, 'error'),
        info: (msg) => appendLog(msg, 'info'),
        table: (msg) => appendLog(JSON.stringify(msg, null, "\t")),
    }
</script>
```

## Run the script

Now that we have all the necessary components defined, the code should look like this

```html
<script>
    function appendResults(result) {
        const results = document.getElementById('results');
        const div = document.createElement('div');
        div.appendChild(document.createTextNode(result));
        results.appendChild(div);
    }
    function appendLog(msg, level = 'info') {
        const logs = document.getElementById('logs');
        const div = document.createElement('div');
        div.appendChild(document.createTextNode(`[${new Date().toISOString()}] [${level}] ${msg}`));
        logs.appendChild(div);
    }
    const logger = {
        log: (msg) => appendLog(msg),
        warn: (msg) => appendLog(msg, 'warn'),
        debug: (msg) => appendLog(msg, 'debug'),
        error: (msg) => appendLog(msg, 'error'),
        info: (msg) => appendLog(msg, 'info'),
        table: (msg) => appendLog(JSON.stringify(msg, null, "\t")),
    }
    async function run() {
        const executor = await yajsapi.TaskExecutor.create({
            package: "9a3b5d67b0b27746283cb5f287c13eab1beaa12d92a9f536b747c7ae",
            yagnaOptions: { apiKey: '411aa8e620954a318093687757053b8d' },
            logger
        }).catch(e => logger.error(e));
        await executor
            .run(async (ctx) => appendResults((await ctx.run("echo 'Hello World'")).stdout))
            .catch(e => logger.error(e));
        await executor.end();
    }
</script>
```

Now if we have a running yagna deamon and passed Yagna APP key correctly, after launching our application with `node app.js` we should see in the browser:

TODO screen

And if we click the run button after a while in the result container, we should get the result of the script: `Hello World`, and in the log container we should see the logs of executed commands.

TODO screen


