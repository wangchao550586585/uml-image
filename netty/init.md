netty源码解析

# 环境配置

1. 注释所有

```
 <module>transport-native-unix-common</module>
 <module>transport-native-epoll</module>
 <module>transport-native-kqueue</module> -->
 <module>transport-rxtx</module>
 <module>transport-sctp</module>
 <module>transport-udt</module>
 <module>handler</module>
 <module>handler-proxy</module>
 <module>example</module>
 <!--<module>testsuite</module>
 <module>testsuite-autobahn</module>
 <module>testsuite-http2</module>
 <module>testsuite-osgi</module>
 <module>testsuite-shading</module>
 <module>testsuite-native</module>
 <module>testsuite-native-image</module>
 <module>testsuite-native-image-client</module>
 <module>testsuite-native-image-client-runtime-init</module>
 <module>transport-blockhound-tests</module>-->
```

注释<classifier>${tcnative.classifier}</classifier>

更改maven jdk编译版本

```
<maven.compiler.source>12</maven.compiler.source>
<maven.compiler.target>12</maven.compiler.target>
```

2：跳过运行时error



3：关闭校验

```
checkstyle.xml
```

# 2：结构

```
EventLoopGroup
```

```
EventLoop  Executor
SocketChannel   ：NioServerSocketChannel   channel
ChannelHandler
ChannelPipeline
ChannelFuture  ：因为所有操作都是异步的，所以future返回结果
ByteBuf            buffer
```

handler  n-》1  pipeline 1-》1 Channel  n - 》1  EventLoop   n - 》 1  EventLoopGroup

EventLoop    1 -》 1  Thread





策略模式

责任链模式

