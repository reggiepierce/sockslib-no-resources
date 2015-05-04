# Fucksocks

**Fucksocks** a Java library of **SOCKS5** protocol.

See [Javadoc](http://fengyouchao.github.io/fucksocks/apidocs/index.html)

#### References

* [SOCKS Protocol Version 5](http://www.ietf.org/rfc/rfc1928.txt)
* [Username/Password Authentication for SOCKS V5](http://www.ietf.org/rfc/rfc1929.txt)

## Featrues

### Client

* TCP proxy
* UDP proxy
* Bind
* Anonymouse authenticaion
* USERNAME/PASSWORD authencation
* Proxy chain.

### Server

* TCP proxy
* UDP proxy
* Bind
* Anonymouse authenticaion
* USERNAME/PASSWORD authencation
* Black or white IP lists for clients.

## Quick start

#### Dependency

You should put following libraries in your project's *CLASSPATH*:

* log4j-1.2.17.jar
* slf4j-log4j12-1.7.5.jar
* slf4j-api-1.7.5.jar
* guava-18.0-rc2.jar

### SCOKS5 Client

#### CONNECT

```java
    SocksProxy proxy = new Socks5(new InetSocketAddress("localhost",1080));
    Socket socket = new SocksSocket(proxy, new InetSocketAddress("whois.internic.net",43));
```

#### BIND

```java
    SocksServerSocket serverSocket = new SocksServerSocket(proxy, inetAddress,8080);
    InetAddress bindAddress = serverSocket.getBindAddress();
    int bindPort  = serverSocket.getBindPort();
    Socket socket = serverSocket.accept();
```

#### UDP ASSOCIATE

```java
   DatagramSocket socket = new Socks5DatagramSocket(proxy);
```

### SOCKS5 Server

```java
     SocksProxyServer proxyServer = SocksProxyServerFactory.newNoAuthenticaionServer();
     proxyServer.start();// Creat a SOCKS5 server bind at port 1080
```
