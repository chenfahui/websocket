HTML5 WebSocket 设计出来的目的就是要取代轮询和 Comet 技术，使客户端浏览器具备像 C/S 架构下桌面系统的实时通讯能力。 浏览器通过 JavaScript 向服务器发出建立 WebSocket 连接的请求，连接建立以后，客户端和服务器端就可以通过 TCP 连接直接交换数据。因为 WebSocket 连接本质上就是一个 TCP 连接，所以在数据传输的稳定性和数据传输量的大小方面，和轮询以及 Comet 技术比较，具有很大的性能优势。

下面是一段简单的 JavaScript 代码展示了怎样建立 WebSocket 连接和获取数据：
<pre>
 var  wsServer = 'ws://localhost:8888/Demo'; 
 var  websocket = new WebSocket(wsServer); 
 websocket.onopen = function (evt) { onOpen(evt) }; 
 websocket.onclose = function (evt) { onClose(evt) }; 
 websocket.onmessage = function (evt) { onMessage(evt) }; 
 websocket.onerror = function (evt) { onError(evt) }; 
 function onOpen(evt) { 
 console.log("Connected to WebSocket server."); 
 } 
 function onClose(evt) { 
 console.log("Disconnected"); 
 } 
 function onMessage(evt) { 
 console.log('Retrieved data from server: ' + evt.data); 
 } 
 function onError(evt) { 
 console.log('Error occured: ' + evt.data); 
 }
 </pre>
