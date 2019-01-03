#  蚂蚁金服SOFAMesh和SOFAMosn介绍

## 产品介绍

蚂蚁金服的Service Mesh解决方案目前主要有两个产品组成：

- SOFAMesh项目：蚂蚁金服 Service Mesh 的控制平面，跟随社区，Fork 自 Istio，保持同步更新。在Istio体系和框架内进行功能补充/扩展/增强/改进，立足于探索并解决 Istio 生产落地，尤其是大规模落地中遇到的实际问题，在充分验证之后贡献回Istio上游。
- SOFAMosn项目：蚂蚁新型基础设施和中间件的底层网络通用解决方案，可以有多种产品形态。在蚂蚁金服 Service Mesh 中承担数据平面的角色，和 SOFAMesh 项目配合使用，兼容 Istio 体系。此外 SOFAMosn 还将用于 Ingress / API Gateway / Serverless Function Gateway 等场景。 

以下详细介绍两个产品的具体情况。

## SOFAMosn

SOFAMosn在承担Sidecar角色时，需要通过 Istio 的标准方式如 XDS API，Mixer API等协议实现与Istio 集成。此时 SOFAMosn 在功能和定位上就和 Envoy 非常相似了。尤其在实现xDS协议时，需要参考Envoy的设计思路和产品理念，所以在 SOFAMosn 的开发过程中有参考借鉴 Envoy 的一些实现方式。

[SOFAMosn](https://github.com/alipay/sofa-mosn) 在2018年7月在 github 开源。

在2018年下半年的实践和技术调研中，蚂蚁金服发现并认可 kubernetes + service mesh + serverless 的组合，同时将服务间通讯的范围从Service Mesh的东西向通讯，扩展到API Gateway的南北向通讯。为此，扩大了SOFAMosn的适用范围：

- Sidecar：类似Envoy
- API Gateway：重用SOFAMosn提供的请求转发/服务路由等能力扩展而来
- Ingress Gateway
- Function Gateway：用于 serveless/function 的gateway产品
- 未来也许还有其他的产品采用类似mesh的架构

因此，SOFAMosn 项目的定位也进行了调整，蚂蚁金服希望SOFAMosn能最终成为蚂蚁新型基础设施和中间件的底层网络通用解决方案，在网络通讯领域支撑起蚂蚁未来的架构体系。

## SOFAMesh

SOFAMesh项目坚持以下原则，以确保和社区同步：

- 持续更新：会定期拉取Istio最新的稳定代码，确保和Istio主流同步——明确的说，SOFAMesh 会是 Istio 的扩展和增强，并尽量在 Istio 的架构体系内实现，不改动核心代码
- 回馈上游：现有改动在生产验证，确认方案可行而且稳定之后，会和Istio官方沟通，如果Istio官方同意会提交回Istio。目前由于还没有足够的生产案例，蚂蚁金服的部分修改也还在不断改动中，因此这个工作进行的还不多。但是已经和Istio团队建立了联系，双方都同意进行后续的合作。
- 保持开源：SOFAMesh 也是开源项目，修改的代码都可以公开获取

目前正在开发中或者检验中的扩展功能：

- x-protocol 多协议通用解决方案：用于快速实现新通讯协议的支持
- DNS 通用寻址方案：用于兼容传统RPC应用以接口而不是服务为粒度的访问方式，还可以应用于未来的 Serverless Function 调用
- 多租户方案
- 大规模落地的最佳实践
- 超大规模服务注册/服务发现机制
- 现有应用升级Istio的平滑迁移最佳实践

目前 SOFAMesh 开发团队已经和 Istio 开发团队建立联系，一致同意在 Istio 大规模落地方面进行合作和探索，蚂蚁金服的相关实践和创新会在生产验证/代码稳定之后会贡献出来。

## 开源动机

Service Mesh是一个非常新的技术，Istio也是一个新兴的项目，在生产落地上存在很多需要了解的细节和可能遇到的各种问题。而且有些需求是有共性的，如RPC协议的支持，旧有非微服务应用的支持, 现有应用升级Istio的平滑迁移等。蚂蚁金服开源SOFSMesh和SOFAMosn，一方面是希望可以将蚂蚁金服在Service Mesh和Istio落地的知识和经验分享出去看，另一方面希望通过开源共建的方式一起来将这个两个项目做的更完善。

------

## 项目背景

为了解决多语言/类库升级等问题，在2017年底蚂蚁金服决定采用proxy模式，通过在客户端加入一个智能代理实现请求转发，从而实现将原有类库实现的功能下沉到sidecar中，这个思路刚好和2017年新出来的Service Mesh理念契合。

因此，蚂蚁金服在2017年底启动了Service Mesh项目，基于Golang，在完成前期开发之后，内部做了POC，尝试替代多语言客户端，获得成功。与此同时，蚂蚁金服还尝试了其他方案：基于NGINX扩展了sidecar poc并验证了可行性；基于ENVOY扩展HSF协议，并完成了POC。

当时除了通用的功能外，还针对蚂蚁的实际需求有特别的考虑，主要有：

- 对SOFARPC、dubbo、HSF等各种RPC协议的支持，包括未来可能的客户自定义协议的支持
- 对蚂蚁各种内部系统的集成，对蚂蚁现在部署和维护体系的适应和改造
- 对现在应用的兼容，尤其是大量未做微服务改造的应用，服务模型和访问方式都和标准的微服务体系不一致
- 升级现有应用的方式和由此带来的工作量，避免过多的业务应用改造，尽量实现平滑迁移

### 数据平面的选择

经过多轮的验证讨论，在sidecar的开发语言和产品选择中，蚂蚁金服最终选择了用Golang开发数据平面，主要原因如下：

1. Golang开发效率高，维护成本低
2. Golang适合开发云原生基础设施和中间件组件
3. 蚂蚁金服准备将原有的Java为主的语言栈，演进为Java+Golang的组合，这个选择符合在语言栈上的长期规划
4. 改造Envoy适配蚂蚁体系的工作量太大，而且很难控制进度，和上游envoy的同步也是个大问题
5. 未来对外输出，客户需要定制数据平面的功能，会非常棘手

### 控制平面的选择

为了和社区保持一致，遵循业界标准，蚂蚁金服选择跟随 Istio 社区，选择了 Istio 做为控制平面，放弃了自行开发控制平面的方案。

控制平面选择使用 Istio，但蚂蚁金服没有直接使用 Istio 的官方仓库，而是 Fork 下来，称为 [SOFAMesh](https://github.com/alipay/sofa-mesh)。主要原因有：

1. 需要将 Istio 的数据平面从默认的 Envoy 替换为 SOFAMosn，这个改动肯定是不适合提交给 Istio 官方的。因此这个替换工作不可能在 Istio 官方仓库进行，只能选择 Fork 。
2. 需要增加对SOFARPC、dubbo、HSF等各种RPC协议的支持，都需要控制平面的配合。这些工作短时间内也不可能被 Istio 官方接受
3. 需要实现和现有未做微服务改造的RPC应用的兼容和互通，为此需要改动Istio，而目前Istio没有这个方面的考虑，蚂蚁金服在方案得到生产验证之前提交给Istio也不现实。
4. 需要多租户支持，目前Istio官方没有解决方案

因此，从Istio Fork下来是不可避免的。

## 相关详细说明

如果对产品规划和技术实现细节有兴趣，可以参考下列资料：

- [大规模微服务架构下的Service Mesh探索之路](https://skyao.io/publication/201806-service-mesh-explore/): 2018-06-30，介绍蚂蚁金服Service Mesh产品(SOFAMesh)的技术选型，架构设计和开源策略。其中技术选型部分非常详细的阐述了蚂蚁金服选择开发SOFAMosn的原因。
- [Service Mesh数据平面SOFAMosn深层揭秘](http://www.servicemesher.com/blog/sofa-mosn-deep-dive/): 2018-08-02，详细介绍SOFAMosn的设计思想，核心模块和核心能力。
- [蚂蚁金服开源的 SOFAMesh 的通用协议扩展解析](http://www.servicemesher.com/blog/ant-financial-sofamesh-common-protocol-extension/)：2018-08-30，介绍SOFAMesh的通用协议扩展方式 x-protocol 的详细情况，这是 SOFAMesh 用来解决通讯协议快速开发和适配旧有RPC应用的解决方案。
- [长路漫漫踏歌而行：蚂蚁金服Service Mesh实践探索](https://skyao.io/publication/201810-ant-finance-service-mesh-practice/)：2018-10-23，演讲的第二部分，“为什么选择Golang？” 非常详尽的阐述了为什么蚂蚁金服选择用Golang开发SOFAMosn而不是直接使用Envoy的原因。演讲的第四部分，“服务间通讯范围的探索”，对服务间通讯的范围进行了探讨，可以帮助了解为什么蚂蚁金服选择扩展 SOFAMosn 的适用范围。
- [蚂蚁金服Service Mesh新型网络代理的思考与实践](http://www.servicemesher.com/blog/microservice-with-service-mesh-at-ant-financial/): 2018-11-24, 详细介绍SOFAMosn项目的整体情况和最新进展，还有各种性能优化方式。
- [蚂蚁金服Service Mesh渐进式迁移方案](https://skyao.io/publication/201811-service-mesh-step-by-step/)： 2018-11-25， 介绍蚂蚁金服Service Mesh渐进式迁移方案和实现平滑迁移的关键点，可以帮助了解蚂蚁金服在Service Mesh大规模项目落地上的思考和对策，以及SOFAMesh项目为此进行的准备工作。