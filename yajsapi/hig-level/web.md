---
description: A minimal example of a functional Golem requestor agent in browser
---

# Task Example 3: Requestor in browser

{% hint style="info" %}
This example demonstrates the following Golem features and concepts:

* Running tasks in a VM runtime
* Executing tasks from a browser context
* Retrieving the output of a provider's executable unit

{% endhint %}

## Prerequisites

Before getting started, you need to launch the Yagna daemon with a parameter that allows you to handle REST API requests with a CORS policy. You can do this by running the following command:

```shell
yagna service run --api-allow-origin='http://localhost:3000'
```

The `--api-allow-origin` value should be set to the URL where your web application will be served.

## Simple web application

To create a simple web application, we'll use the standard Node.js library. First, we'll create a `app.js` file with the following content:

```javascript
const http = require('http');
const fs = require('fs');

const server = http.createServer((req, res) => {
  res.writeHead(200, { 'content-type': 'text/html' });
  fs.createReadStream('index.html').pipe(res);
});

server.listen(3000, () => console.log('Server listening at http://localhost:3000'));
```

Next, we'll create the main `index.html` file with a minimal layout:

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

In this layout, there are three elements:

- A "Run" button, which executes the script on Golem
- A "Results" container, which displays the results
- A "Logs" container, which displays the API logs

## Using the Yajsapi bundle library

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


