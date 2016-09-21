---
author: admin
comments: false
date: 2013-06-14 07:01:00+00:00
layout: post
link: https://witr.net/quotation/?p=53
slug: simple-nodejs-http-server
title: simple nodejs http server
wordpress_id: 53
categories:
- javascript
---


  
================================================= 14/06/2013  
simple nodejs http server:  
- install nodejs  
- create file server.js with following content:  
var url = require("url");  
  
function handleHttpRequest(request, response){  
 response.writeHead(200, {"Content-Type": "text/html"});  
 response.write("pathname:"+url.parse(request.url).pathname);  
 response.write("  
");  
 response.write("query:"+url.parse(request.url).query);  
 response.end();  
}  
  
var http = require("http");  
http.createServer(handleHttpRequest).listen(8888);  
- in command line: node /path/to/server.js  
- go to http://localhost:8888  
- go to http://localhost:8888/sevice?user=nour&age;=42  


  




