
1	ASM

华为云应用网格服务ASM(Application Service Mesh)基于Istio构建。提供高性能、高可靠性、高可维护性的企业级网格服务平台。

2018年8月28日,华为云中国行上成都站上,宣布作为国内首家推出了Istio服务网格产品对外发布,并正式公测。

（TODO图 ASM）

AMS深度集成华为云容器服务CCE(Cloud Container Engine)，一键开启即可提供非侵入的智能流量治理解决方案。包括负载均衡、熔端、限流等多种治理能力。内置金丝雀、蓝绿等多种灰度发布流程，提供一站式自动化的发布管理。基于无侵入的监控数据采集，深度整合华为云APM能力，提供实时流量拓扑、调用链等服务性能监控和运行诊断，构建全景的服务运行视图。

截止2018-12-24，华为云Istio团队在Istio社区累计Pull Requests (PRs)贡献 270条，厂商贡献排名全球第3。现有Istio社区Approver 3席，Member 6席，Contributor 若干。

（TODO图 HuaweiCloud Istio contribution）

2	Azure Service Fabric Mesh 

Azure Service Fabric Mesh 于2018年7月开放公测。是一个完全托管的服务，开发者可部署微服务应用程序，而无需管理虚拟机、存储或网络。开发人员察觉不到所有的群集操作。 只需上传代码，并指定所需的资源、可用性要求和资源限制即可。其中使用Envoy做智能路由管理。

![](https://blog.tomkerkhove.be/content/images/2018/07/Traffic-Routing.png)

3	Google

2018年7月 google Next上提出了Cloud Services Platform。与Istio相关的包括：

Managed Istio 提供服务发现和智能流量管理、安全、监控。也是对Istio官方提出的功能定位的概况。当然强调了和自身云服务的结合，如可观察性上强调和StackDriver的集成。在Kubernetes集群上安装了Istio，可以通过命令行工具配置DestinationRule、VirtualService等Istio规则可以通过StackDriver看服务的metric、调用链、拓扑。

![](https://3.bp.blogspot.com/-0PF8lTgs2mc/W1ZeqBT0wAI/AAAAAAAAGHo/SirNgEV8SAQuepeZjrhRtdqi3t7abzyxgCLcBGAs/s1600/The%2BCloud%2BServices%2BPlatform%2Bfamily.png)

Apigee API Management for Istio。通过Apigee定义控制策略，基于Istio的Mixer的策略执行对每请求的控制，如Quota、Oath等。

使用 Istio 管理混合云负载。安全地控制流经任何 Kubernetes 环境或微服务环境的流量且确保操作的可扩展性，最佳的方法是在 Google Kubernetes Engine 上使用 Istio。借助 Istio连接内部负载和云端负载，并全盘管理所有负载，而这一切均无需对应用软件做任何更改。
