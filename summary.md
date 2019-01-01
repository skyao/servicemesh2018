# Servicemesh 2018 年度总结

## 前言

在2017年年底，在Service Mesh刚刚兴起之时，应InfoQ的邀请撰写过一篇名为 ["Service Mesh年度总结：群雄逐鹿烽烟起"](https://skyao.io/publication/201801-service-mesh-2017-summary/) 的文章，对2017年Service Mesh的发展做了一次年度回顾。当时正是Service Mesh技术方兴未艾，各家产品你争我夺之时，一片欣欣向荣的气象。

时隔一年，江湖风云变幻。再次有幸收到InfoQ的邀请，继续进行Service Mesh 2018年的年度总结。本次年度总结将由来自 [Servicemesher 社区](http://www.servicemesher.com/) 的多位嘉宾共襄盛举，希望能为 Service Mesh 2018年的发展做一个系统而全面的总结。

为了更有成效的完成总结，我们将以询问的方式来让下文中将出场的各个Service Mesh产品和解决方案提供自己的答案，问题很简单：**在2018年，做了什么？**

考虑到在2018年，Service Mesh在国内大热，有多家公司推出自己的Service Mesh产品和方案，因此本次内容我们将分为国际篇和国内篇。

## 国际篇

2018年，Service Mesh市场的主要竞争者还是2017年底的出场的Linkerd、Envoy、Istio、Conduit等。

### Istio

2018年对于 Istio 来说应该是蓄势待发的一年，这一年 Istio 接连发布了 0.5、0.6、0.7、0.8 和 1.0 版本。

到2018 年 7 月 31日 1.0 GA 时，Istio其实已经陆续开发了近两年。1.0 版本对 Istio 来说是一个重要的里程碑，官方宣称所有的核心功能现在都可以用于生产。1.0 版本的到来也意味着其基本架构和 API 逐渐稳定，那些锐意创新的企业可以开始试用。

我们以 GitHub 上的 Star 数量的角度来看一下 Istio 在2018年的受欢迎程度，下图显示的是 Istio 的 GitHub star 数量随时间变化曲线。可以看到在2018年，Istio 的star 数量增长了大概一万颗，目前已经接近15000颗星，其增长趋势非常平稳。

[![Stargazers over time](https://starcharts.herokuapp.com/istio/istio.svg)](https://starcharts.herokuapp.com/istio/istio)

我们来按照时间顺序回顾一下2018年 Istio 的几个重要版本的发布情况，以便对 Istio 这个目前最受关注的 Service Mesh 项目在2018年的发展有深入了解：

- 2018年1月31日，Istio发布0.5.0版本：支持Sidecar自动注入（需要 kubernets 1.9版本），加强RBAC支持，尝试修改通信规则
- 2018年3月1日，Istio发布0.6.0版本：支持发送自定义Envoy配置给Proxy，支持基于Redis的速率限制，容许为检查和报告分别设置Mixer集群，提供正式的存活以及就绪检测功能
- 2018年3月29日，Istio发布0.7.0版本：只包含问题修复和性能提升，没有新的功能。初步支持 v1alpha3 版本的流量管理功能。
- 2018年6月1日，**Istio发布0.8.0版本**：在之前三个平淡无奇的小版本发布之后，Istio 迎来了2018年第一个重大版本0.8.0，这也是 Istio 第一个LTS（长期支持）版本，这个版本带来了大量的更新，架构方面也做了很多改进，主要有：v1alpha3 版本的流量管理功能就绪；缺省使用 Envoy 的 ADS API 进行配置发送；新增 Istio Gateway 模型，不再支持 Kubernetes Ingress；支持Helm 安装；支持按需安装 Mixer 和 Citadel 模块。另外原有的 API 都经过了重构，CRD 的名字全部更改。
- 2018年7月31日，**Istio发布1.0.0版本**：这是社区期待已经的版本，也是 Istio 的重要里程碑。不过相对0.8.0版本，主要是修复错误和提高性能，新功能不多。

进入2018年下半年之后，Istio 的开发进度明显放缓，1.1版本的发布多次推迟，直到2018年结束也未能发布。在1.0版本发布之后的5个月时间，Istio只是以平均每个月一个Patch版本的方式陆续发布了1.0.1到1.0.5总共5个Patch版本，这些Patch版本都只有错误修复和性能改善，未带来新的特性。

简单总结 Istio 2018年的发布情况：Istio在上半年通过0.5.0/0.6.0/0.7.0三个小版本陆续进行了小改，在0.8.0版本中进行了唯一一次大改，然后年中发布了2018年最重要的里程碑1.0.0版本，接着是长达5个月的修整期，最后带着迟迟未能发布1.1版本的小遗憾平淡的结束2018年。

和产品演进和版本发布的平淡相比，Istio在市场和社区的接受程度方面表现非常火爆，成为2018年最热门的项目之一，也在各种技术会议上成为备受关注的技术新星。尤其在 kubernets 社区，更是被视为有望继 kubernets 成功之后成为下一个现象级产品。

目前各主流云平台也纷纷提供对 Istio 的支持：

- TODO

在市场一片红红火火之时，我们不得不指出，到2018年底，Istio 依然在几个关键领域上未能给出足够令人满意的答案，典型如性能、稳定性，Istio 的 1.0 版本并不是一个有足够生产强度的稳定版本。Istio在2018年交出的答案，对于对Istio抱有非常大期待的 Servicemesh 社区来说，是远远不够的。这直接导致 Istio 目前在生产落地上陷入尴尬境地：虽然试水 Istio 的公司非常多，但是真正大规模的实践很少。

对 Istio 的年度总结，首先回答问题：Istio 在2018年如期发布了1.0版本，顺利完成了市场布局，扩大了己方阵营，压制了所有竞争对手。不可谓不成功，但是离社区的期待依然有非常大的距离，关键在于未能真正实现大规模普及。如何打破这一叫好不叫座的僵局，将会是 Istio 2019年面临的最大挑战。

### Envoy

在2017年的总结中，我们称Envoy为"波澜不惊的Envoy"，以下这段是2017年的总结：

> 在功能方面，由于定位在数据平面，因此Envoy无需考虑太多，很多工作在Istio的控制平面完成就好，Envoy从此专心于将数据平面做好，完善各种细节。在市场方面，Envoy和Linkerd性质不同，不存在生存和发展的战略选择，也没有正面对抗生死大敌的巨大压力。Envoy在2017年有条不紊地陆续发布了1.2、1.3、1.4和1.5版本，稳步地完善自身，表现非常稳健。

在2018年，Envoy也是同样的波澜不惊，上面这段总结几乎可以一字不变的继续在2018年沿用：只要简单的将版本号变成1.6.0、1.7.0、1.8.0和1.9.0即可。

[![Stargazers over time](https://starcharts.herokuapp.com/envoyproxy/envoy.svg)](https://starcharts.herokuapp.com/istio/istio)

这是Envoy Github Star的情况。总数7800，其中2018年大致增加了5000个Star，而且增长趋势异常的平稳。

我们再来细看一下2018年Envoy的版本发布情况，这次我们换个特别的角度，关注一个细节：Envoy每次版本发布时，都会在Release Note中列出本版本包含的变更列表，非常细致，所以很长很长，每次都是三四页的样子。我们同时简单计算了一下每次发布包含的commit数量，整体情况如下：

- 2018年5月20日，Envoy发布1.6.0版本：包含392个commits，Release Note 长达四页
- 2018年6月21日，Envoy发布1.7.0版本：包含468个commits，Release Note 长达四页。这个版本是配套Istio 1.0版本作为 Production Ready的 Service mesh 解决方案。全面支持RBAC鉴权模型, TLS&JWT加密，网络通信安全性有极大提升。
- 2018年10月4日，Envoy发布1.8.0版本：包含425个commits，Release Note 长达三页
- 2018年12月21日，Envoy发布1.9.0版本：包含414个commits，Release Note 长达三页

如果有兴趣去浏览Envoy在这几次版本发布时的Release Note，就可以发现Envoy在2018年中数量惊人的各种细微改进。我们也可以简单计算一下，Envoy全年四个版本大概1800次commit，考虑到Envoy在2018年并没有大规模的架构改动和特别大的新特性支持，这些commit基本都是各种完善、改进和补充。不得不惊叹于Envoy在这种细致之处刻意打磨的精神，毕竟"细节才是魔鬼"。

Envoy的稳健和成熟，在2018年带来了丰硕成果：

- 被越来越多企业使用，不仅仅稳稳占据Istio官配Sidecar的位置，而且在网络代理、负载均衡器、网关等领域开始占据传统产品的领地，如nginx，kong。

- 被Istio之外的多个公司的Service mesh框架项目采用，如AWS的app mesh, F5的Aspen mesh, 微软的service frabric mesh，国内包括腾讯，阿里的Dubbo Mesh。Envoy逐渐有成为service mesh的数据平面标准的趋势。

- Envoy的xDS API，已经成为service mesh数据平面API的事实标准

Envoy在2018年的成功，还体现在社区开始出现基于Envoy的衍生产品：

- Ambassador：构建于envoy之上的API Gateway，紧追着envoy的新版本，支持与Istio集成，可作为service mesh架构中的ingress gateway。
- Gloo：基于Envoy的Hybrid App Gateway，可作为Kubernetes  ingress controler 和API gateway，来自 solo.io。
- Rotor: Envoy的轻量级控制平面，来自Turbine Labs（由于Turbine Labs的公司变动，这个项目已经不再维护）。
- Contour: 基于Envoy的Kubernetes Ingress Controller，来自 Heptio 公司

在2017年的总结中，我们对Envoy的评价是：

> Envoy随后收获了属于它的殊荣：
>
> - 2017年9月14日，Envoy加入CNCF，成为CNCF的第二个Service Mesh项目
>
> 可谓名至实归，水到渠成。作为一个无需承载一家公司未来的开源项目，Envoy在2017年的表现，无可挑剔。

而在2018年，Envoy继续稳健发展，一边伴随Istio一起成长，一边在各个领域开疆扩土。Envoy的成功故事在延续，并再次收获属于它的殊荣：

- 2018年11月28日，CNCF宣布Envoy毕业，成为继Kubernetes和Prometheus后，第三个孵化成熟的CNCF项目。

同样的名至实归，同样的水到渠成，Envoy在2018年的表现，同样的无可挑剔。

### Linkerd系列

### Linkerd

Linkerd的2018年，是突围的一年，作为定义Service Mesh概念的先驱，其Github Star数量在2017年底就已经被Istio超越，虽然一直有平稳增长，已经无力与Istio一较高下了。下面按照时间顺序整理一下Linkerd1.x版本在2018年之中的几个关键节点。

- 2018年5月1日，在持续了几个月对1.3.x版本的修修补补之后，发布了1.4.0版本，其中使用了最新版本的Finagle和Netty组件，尝试降低在大规模应用的情况下的内存占用，并开始在可观察性方面的持续改进；
- 2018年6月，宣布成立Linkerd + GraalVM工作组。尝试使用GraalVM提高Linkerd的性能。据笔者观察，其讨论到9月就已经再无更新，并且并未产生可发布的任何进展；
- 2018年7月14日发布的1.4.5中，提供了对[Open J9 JVM](https://www.eclipse.org/openj9/)的支持，声称可能降低40%的内存占用以及大幅降低p99延迟；
- 2018年10月3日，发布了1.5.0，其中有一项很值得注意的变更：Istio特性被标记为deprecated。事实上在[8月份的讨论](https://github.com/linkerd/linkerd/issues/2092)中，已经有人提出，在Linkerd 1.1.1版本之后，对Istio的支持并未进步，同时也没有明确迹象表明有用户对Linkerd数据面结合Istio控制面的方案感兴趣，因此Linkerd开始逐步停止对Istio的支持。

可以看到，2018年中，Linkerd的Istio Sidecar方案和GraalVM性能优化方案均已无疾而终，目前硕果仅存的是Open J9 JVM的优化版本，其测试版本还在继续发行。

而诞生于2017年底的Conduit，形势稍微乐观一点，但是根据Github star的观察，表现也仅是优于同门的Linkerd，和Istio相比，仍然不在同一数量级，其更新频度非常高，基本做到每周更新，呈现了一种小步快跑的态势。当然，这种快速更新的最重要原因应该就是其相对稚嫩的状态，和成熟的Linkerd相比，Conduit还只是刚刚起步，下面也根据Release情况看看2018年里这一项目的进展：

- 2018年2月1日，发布Conduit v0.2.0，提供了TCP和HTTP的支持；

- 2018年2月21日，发布v0.3，宣布进入Alpha阶段，为负载均衡功能提供了负载感知的能力；

- 2018年4月17日，发布v0.4.0，提供了对MySQL和SMTP的透明支持能力；

- 2018年6月5日，发布v0.4.2，支持全部Kubernetes Workload；

- 2018年7月6日，发布最后一个Conduit版本，v0.5.0，提供了Web Socket支持，加入自动TLS支持，更名为Linkerd 2.0；

- 2018年9月18日，Linkerd 2.0宣布被WePay、Hush、Studyo以及JustFootball采用，进入GA阶段；

- 2018年12月6日，Linkerd 2.1发布，推出了路由级的遥测能力。更重要的是，提出了Service Profile的概念，这一概念以服务为中心，将服务相关的大量CRD聚合成统一一个，对服务网格的管理无疑是一个强大助益。

将两个产品的时间线叠加起来，似乎可以推断，Linkerd意识到，两条产品线并行开展已经无法继续支撑，对于性能方面的优化不但难于奏效，而且也并无挽回颓势的可能；社区内也有声音提出，相对于对手Istio，控制面问题是Linkerd 1.x的关键弱点。而Linkerd 2.x版本的目标则具有很明确的针对性：提供一个轻量级、低难度、支持范围有限的Service Mesh方案，9月份宣布GA并得到客户采用，证明这一策略还是行之有效的。年底提出的Service Profile概念，虽然只是一个雏形，目前仅提供了一点监控方面的功能，但是其Roadmap中指出，日后将会把大量特性集成到Service Profile之中，笔者认为相对于Istio的Mixer适配器模型来说，这一概念能够极大的降低运维工作难度工作量，并有效的简化服务网格的管理工作。

Istio关了Service Mesh的门，一年摸索和碰壁之后，Linkerd2发现了Service Profile的窗，可以说是尚存希望吧。

### 其他产品

除了Istio、Envoy和Linkerd系列这些主要竞争者之外，Service Mesh 市场陆陆续续还有其他的一些公司参与：

- Nginmesh：来自大名鼎鼎的nginx，在2017年9月nginx对外宣布了这一产品，是一款适配 Istio 的 service mesh 方案，使用 NGINX 作为 sidecar 替换 Envoy。但nginx在Nginmesh上的态度摇摆不定：在2017年下半年发布了3个小版本之后就停止开发。2018年重新启动，接连发了几个小版本，但是在2018年7月发布0.7.1版本之后，再次停止开发。
- Consul Connet：Consul来自HashiCorp公司，主要功能是服务注册和服务发现，基于Golang和Raft协议。在2018年6月26日发布的Consul 1.2版本中，提供了新的Connect功能，能够将现有的Consul集群自动转变为Service Mesh。亮点是可以提供自动的双向TLS加密通信以及基于唯一标识的权限控制。
- kong：在2017年就有传闻说kong有意service mesh，但一直不见kong的明确动作。在2018年9月，kong宣布1.0发布之后kong将转型为服务控制平台，支持Service Mesh。关于kong到底会不会投身service mesh的悬念也就一直贯穿整个2018年度，直到12月21日，kong 1.0 GA发布时才明确给出：kong可以部署为独立的service mesh proxy，开箱即用的提供service mesh的关键功能，并集成有 Prometheus, Zipkin，支持健康检查，金丝雀发布和蓝绿部署等。
- AWS App Mesh：AWS APP Mesh 是 AWS 今年在 re:Invent 2018 大会上发布的一款新服务，旨在解决在 AWS 上运行的微服务的监控和控制问题。它主要标准化了微服务之间的通信流程，为用户提供了端到端的可视化界面，并且帮助用户应用实现高可用。App Mesh 使用开源的 Envoy 作为网络代理，这也使得它可以兼容一些开源的微服务监控工具。用户可以在 AWS ECS 和 Amazon EKS 上使用 App Mesh。从官网放出的流程图可以看出，App Mesh 是对标 Istio。目前App Mesh提供公开预览。

从社区的角度，我们希望有更多的参与者进Service Mesh市场，以推动Service Mesh的健康发展。但是实际情况是，在Istio的光辉之下，新晋产品的发展前景都不太客观，是和Istio全面对抗？还是另辟蹊径寻找适合自己的生存空间？是每个产品都要面对的问题。

### 小结



## 国内篇

### 蚂蚁金服

### 新浪微博

### 华为

### 腾讯

### 衍生产品

### 小结

## 总结