# java-websocket-reverse-proxy

Java implementation of a websocket reverse proxy. A similar method to the one described in 
[https://www.nginx.com/blog/websocket-nginx/](https://www.nginx.com/blog/websocket-nginx/),
but implemented in Java. This should be useful in Java application servers, e.g. Spring Boot.

There are a few nodejs scripts at the root level that can be used to mimic some of the 
surrounding functionality required to verify the proxy server.

The common mock here is the [websocketserver.js](./websocketserver.js) script, which listens 
on port 9999 and just echos back any input after uppercasing it. To test the echoing behaviour 
establish a direct connection to a websocket server, run 
[test_websocketserver_direct.sh](./test_websocketserver_direct.sh) 

*(requires node & npm to be installed)*

There is also a very simple [websocketproxy.js](./websocketproxy.js) script which will proxy
the websocketserver running on port 9999. It listens on port 8888 and can be tested by running
[test_websocketserver_nodeproxy.sh](./test_websocketserver_nodeproxy.sh)

A simple java implementation to match this proxying behaviour is contained in the classes defined
in the src folder. It is based on [Spring Boot](https://projects.spring.io/spring-boot/).
You can build the implementation using [Gradle](https://gradle.org/) and run it up manually
or use the [test_websocketserver_javaproxy.sh](./test_websocketserver_javaproxy.sh) script.

*(developed on macOS, ymmv on other platforms)*

