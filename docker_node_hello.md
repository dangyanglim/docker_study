# index.js
```
var express = require('express')
var app = express()

app.get('/', function (req, res) {
 res.send('Hello World!')
})

var server = app.listen(4001, function () {

 var host = server.address().address
 var port = server.address().port

 console.log('Example app listening at http://%s:%s', host, port)

})
```
# package.json
```

{
 "name": "docker-node-hello",
 "private": true,
 "version": "0.0.1",
 "description": "Node.js Hello world app on Ubuntu using docker",
 "dependencies": {
   "express": "4.x.x"
 }
}
```
# Dockerfile
```

FROM node:8.9.0
RUN mkdir -p /src/hello
COPY . /src/hello
RUN ls /src/hello
WORKDIR /src/hello
RUN npm install
EXPOSE 4001
CMD ["node","/src/hello/index"]

```
# centos6.8步骤
```bash
yum -y install docker-io
docker build --rm -t node-hello .
docker run -d -p 4001:4001 --name nodejs1 node-hello
```
