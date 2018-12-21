Linkerd 1.x

## 6.4.2018

宣布成立Linkerd + GraalVM工作组。尝试使用GraalVM提高Linkerd的性能。

Linkerd的2018，是突围的一年。

作为定义Service Mesh概念的先驱，在Istio出现之后，Github热度和Google趋势都迅速超越了老前辈Linkerd，整个一年里，Linkerd仅在6月做出了一个关键决策：宣布成立Linkerd + GraalVM工作组。尝试使用GraalVM提高Linkerd的性能。

Buoyant的热点集中在2017年底诞生的Conduit上面。Conduit的目标很明确，建立一个轻量级、低难度、支持范围有限的Service Mesh组件，在6月之前，Conduit项目陆续完善了Service Mesh的各项应由功能，在2月宣布进入Alpha阶段，6月初完成了对Kubernetes所有工作负载类型的支持后，在7月6日，宣布发布最后一个版本v0.5.0，之后更名为Linkerd 2.0。这个时间点很有趣，刚好在6月Linkerd 1.x版本宣布使用GraalVM的轻量化尝试之后的一个月，个人认为这一尝试已经失败，Conduit需要接过Linkerd 1.x的重任。9月中旬，Linkerd 2宣布进入GA阶段，并得到了WePay、Hush、Studyo以及JustFootball的采用。在12月，Linkerd 2提出了Service Profile的概念，这一概念将服务网格中的各种能力以服务为中心进行了深度聚合，个人认为这是服务网格这一概念诞生之后的可能是最重要的一个新概念。Istio关了Service Mesh的门，一年摸索和碰壁之后，Linkerd2发现了Service Profile的窗，可以说是尚存希望吧。