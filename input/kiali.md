# Kiali

单体应用使用微服务架构拆分成了许多微服务的组合。服务的数量显著增加，就对需要了解服务之间的通信模式，例如容错（通过超时、重试、断路等）以及分布式跟踪，以便能够看到服务调用的去向。服务网格可以在平台级别上提供这些服务，并使应用程序编写者从以上繁重的通信模式中解放出来。路由决策在网格级别完成。Kiali 与Istio 合作，可视化服务网格拓扑、断路器和请求率等功能。Kiali还包括 Jaeger Tracing，可以提供开箱即用的分布式跟踪功能。

访问[Kiali——Istio Service Mesh 的可观察性工具](https://jimmysong.io/posts/kiali-the-istio-service-mesh-observability-tool/)了解详情。