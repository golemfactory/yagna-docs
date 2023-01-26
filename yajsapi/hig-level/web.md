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
const http = require('http');
const fs = require('fs');

const server = http.createServer((req, res) => {
  res.writeHead(200, { 'content-type': 'text/html' });
  fs.createReadStream('index.html').pipe(res);
});

server.listen(3000, () => console.log('Server listening at http://localhost:3000'));
```

Then wen need to create main `index.html` file with minimal layout:
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Golem App</title>
    <style>
      .container {
        display: flex;
        width: 100%;
      }
      .results, .logs {
          width: 50%;
      }
    </style>
</head>
<body>
  <button onclick="run()">Run</button>
  <div class="container">
    <div class="results">
        <p>Results</p>
    </div>
    <div class="logs">
        <p>Logs</p>
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

TODO: from cdn or yarn build:web

### Task Executor
```html
<script>
    //TODO:
</script>
```

## Getting results
```html
<script>
    //TODO:
</script>
```

## Getting logs
```html
<script>
    //TODO:
</script>
```


