# Istio

2018 年对于 Istio 来说应该是蓄势待发的一年，这一年 Istio 发布了 0.5、0.6、0.7、0.8 和 1.0 版本，GitHub 上的 Star 数增长近一万颗。笔者从  2017 年 Istio 还是 0.3.0 版本起开始关注该项目，1.0 版本的到来意味着其基本架构和 API 逐渐稳定，那些锐意创新的企业可以开始试用了，2018 年 7 月 31日 1.0 GA 时其实已经开发了近两年，1.0 版本对 Istio 来说是一个重要的里程碑，官方宣称所有的[核心功能](https://preliminary.istio.io/zh/about/feature-stages/)现在都可以用于生产。

下图显示的 Istio 的 GitHub star 数量随时间变化曲线。

[![Stargazers over time](https://starcharts.herokuapp.com/istio/istio.svg)](https://starcharts.herokuapp.com/istio/istio)

下文仅针对 Istio 的几个重要版本加以说明，关于 Istio 每本版本的详细情况请参考[发布说明](https://preliminary.istio.io/zh/about/notes/)。

## 1.0 GA

1.0 版本对是一个重要的里程碑，意味着所有的[核心功能](https://preliminary.istio.io/zh/about/feature-stages/)现在都可以用于生产。请参考 [1.0 发布说明](https://preliminary.istio.io/zh/about/notes/1.0/)。

## 0.8 重构与掌握发布节奏

[0.8 版本](https://preliminary.istio.io/zh/about/notes/0.8/)是 Istio 达到 1.0 之前最重要的一次发布，除了通常的问题修复和性能增强之外，其中包含了很多新功能，架构方面也做出了很多改进。原有的 API 都经过了重构，以前的 CRD 的名字全部更改了，并且不再支持 Kubernetes ingress 做边缘路由，而是使用  自定义的 Gateway 资源对象。

另外经过该版本发布后 Istio 团队稳定了[构建 & 发布节奏](https://preliminary.istio.io/zh/about/release-cadence/)。Istio 每天都有新的构建和发布，大约每个月会将其中一个日常构建版本通过一系列额外的质量测试后，将其构建标记为 Snapshot 版本。大约每个季度左右，会选择其中一个 Snapshot 版本运行更多测试并将构建标记为长期支持（LTS）版本。最后，如果发现 LTS 版本有问题，Istio 会发布补丁。

## 0.6 探索中

可以说在 Istio 0.6 版本以前还有支持非 Kubernetes 平台的打算，可是到了 2018 年，各大云厂商纷纷投资 Kubernetes，随着 Kubernetes 平台的普及速度加快，Istio 团队已经逐步放弃对非 Kubernetes 平台的支持。