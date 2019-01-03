## Consul

2018年6月26日，发布Consul 1.2版本，新特性"Connect"支持将基于Consul的服务集群转换成为service mesh模式，亮点是可以提供自动的双向TLS加密通信以及基于唯一标识的权限控制。

Connect 是 Consul 的一个主要新功能，旨在通过自动 TLS 加密和基于鉴权的授权机制提供服务之间的安全通信。今天宣布的 Connect 的功能是完全免费并且开源的。Consul 1.2 提供 Connect 功能面向公众的发布。

Connect 在设计开发时就贯注了易于使用的想法。它可以仅仅通过一个配置参数就打开，在服务注册时额外添加一行就可以使得任何现存的应用接受基于 Connect 的连接。证书更新是自动的，因此不会导致服务停机。对于所有必须的子系统，Connect 仅仅需要一个二进制文件就可以支持。后面我们会涵盖很多其他的功能。

详情请访问[Service Mesh新成员：Consul 1.2](http://www.servicemesher.com/blog/consul-1-2-service-mesh/)。