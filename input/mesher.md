# 华为开源项目Mesher

Mesher脱身于华为的公有云产品CSE，CSE本身拥有java与go语言的微服务编程框架，
在17年底加入的Mesher补充完善了整个微服务解决方案。

上线后，Mesher吸纳了使用PHP， NodeJS等语言的用户，先后将Mesher应用于楼宇管理系统的SaaS化，
模型训练平台ModelArts（Model as a service）等多个项目的生产环境中，
最大规模达到600多服务实例

华为工程师田晓亮在6月份的LC3和12月的KubeCon大会讲解了商业产品CSE mesher在生产环境中的实践。

在生产中得到了验证后，
华为在8月份开源了自己的 [Service Mesh](https://github.com/go-mesh/mesher)，
以完善ServiceComb开源生态

从发展目标来看，Mesher并不只支持Kubernetes，
而是支持任意的基础设施，容器，虚拟机等
并且影响了ServiceComb Service Center的走向，使其支持异构的注册中心（目前已支持纳管
service center与kubernetes）管理，可以统一的在一个service center中发现不同基础设施，
不同数据中心的微服务，以此来更好的支持混合云场景