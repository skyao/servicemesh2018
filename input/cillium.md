# Cilium

Cilium是一个纯开源软件，没有哪家公司提供商业化支持，也不是由某一公司开源，该软件用于透明地保护使用Linux容器管理平台（如Docker和Kubernetes）部署的应用程序服务之间的网络连接。

Cilium的基础是一种名为BPF的新Linux内核技术，它可以在Linux本身动态插入强大的安全可见性和控制逻辑。由于BPF在Linux内核中运行，因此可以应用和更新Cilium安全策略，而无需对应用程序代码或容器配置进行任何更改。

![Cilium](https://ws4.sinaimg.cn/large/006tNbRwly1fwqi98i51ij30sc0j80zn.jpg)

基于微服务的应用程序分为小型独立服务，这些服务使用**HTTP**、**gRPC**、**Kafka**等轻量级协议通过API相互通信。但是，现有的Linux网络安全机制（例如iptables）仅在网络和传输层（即IP地址和端口）上运行，并且缺乏对微服务层的可见性。

Cilium为Linux容器框架（如[**Docker**](https://www.docker.com/)和[**Kubernetes）**](https://kubernetes.io/)带来了API感知网络安全过滤。使用名为**BPF**的新Linux内核技术，Cilium提供了一种基于容器/容器标识定义和实施网络层和应用层安全策略的简单而有效的方法。

**注**：Cilium中文意思是“纤毛“，它十分细小而又无处不在。

## Cilium 的特性

**基于身份的安全性**

Cilium可见性和安全策略基于容器编排系统的标识（例如，Kubernetes中的Label）。在编写安全策略、审计和故障排查时，再也不用担心网络子网或容器IP地址了。

**卓越的性能**

BPF利用Linux底层的强大能力，通过提供Linux内核的沙盒可编程性来实现数据路径，从而提供卓越的性能。

**API协议可见性+安全性**

传统防火墙仅根据IP地址和端口等网络标头查看和过滤数据包。Cilium也可以这样做，但也可以理解并过滤单个HTTP、gRPC和Kafka请求，这些请求将微服务拼接在一起。

**专为扩展而设计**

Cilium是为扩展而设计的，在部署新pod时不需要节点间交互，并且通过高度可扩展的键值存储进行所有协调。

## 发展历程

2018年10月23日，Cilium发布1.3版本，该版本加入了几个新特性。主要的亮点是实现了Cassandra和带有策略执行能力的Memcached协议解析器，作为[Envoy](https://github.com/envoyproxy/envoy)的Go语言扩展包，1.2到1.3版本的这段时间内社区贡献了785个commit。

2018年8月21日，Cilium发布1.2版本，该版本引入了几个新功能实现了Cilium用户和社区成员最迫切想要的功能。一个是引入基于DNS名称的安全策略，保护对集群外服务的访问。另一个最受关注的功能是加入了连接和保护多个Kubernetes集群的能力。ClusterMesh功能进入Alpha版本。它可以连接和保护多个Kubernetes集群中运行的pod。Kube-router与Cilium的集成同等重要。DigitalOcean团队的努力使kube-router提供BGP网络与Cilium提供的基于BPF的安全性和负载均衡相结合。整个Cilium开发者社区贡献者总数已增加到85个，在1.1到1.2版本内贡献了579个PR。

## 参考

- [Cilium——具备API感知的网络和安全性管理的开源软件](http://www.servicemesher.com/blog/cilium-intro/)

- [Cilium 1.3：支持Envoy、Cassandra和Memcached的Go语言扩展](http://www.servicemesher.com/blog/cilium-13-go-extensions-for-envoy-cassandra-memcached-support/)

- [Cilium 1.2发布—DNS安全性策略、EKS支持、ClusterMesh、kube-router集成等](http://www.servicemesher.com/blog/cilium1.2-dns-security-policies-eks-support-clustermesh-kube-router-integration/)

- [使用Cilium增强Istio—通过Socket感知BPF程序](http://www.servicemesher.com/blog/how-cilium-enhances-istio-with-socket-aware-bpf-programs/)