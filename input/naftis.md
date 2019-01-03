# Naftis

用[Istio](https://istio.io/zh)治理服务时须通过istioctl或kubectl，这种方式可能存在一些问题。因此小米武汉研发中心推出Naftis，帮助用户更轻松地管理Istio。

近年来服务网格（Service Mesh）已成为各大公司关注重点，各大公司纷纷开始调研Service Mesh相关架构。作为Service Mesh中的佼佼者，Istio诞生之初就已吸引众多目光。

作为基础设施层，Istio有优秀的服务治理能力。但使用Istio进行服务治理时，开发者需通过istioctl或kubectl工具在终端中进行操作，这种方式目前存在一些问题，举例如下：

1. Istio要求用户熟练掌握istioctl工具的数百种指令，有较高的学习成本。
2. Istio进行服务治理时需要的yaml配置文件的数量非常庞大，如何配置和管理这些配置文件，也是个难题。
3. Istio的istioctl工具没有用户权限的约束，存在一定安全隐患，无法适应大公司严格的权限管理需求。
4. Istio的istioctl工具不支持任务回滚等需求，在执行任务出错的情况下，无法快速回滚到上一个正确版本。

为了解决这些问题，小米信息部武汉研发中心为Istio研发出了一套友好易用的Dashboard - Naftis。

Naftis意为水手，和Istio（帆船）意境契合。作为dashboard，Naftis能使用户像水手一样熟练掌控和管理Istio。

<https://github.com/XiaoMi/naftis>

Naftis通过任务模板的方式来帮助用户更轻松地执行Istio任务。用户可以在 Naftis中定义自己的任务模板，并通过填充变量来构造单个或多个任务实例，从而完成各种服务治理功能。

Naftis提供了如下特性：

- 集成了一些常用的监控指标，包括40X、50X错误趋势等。
- 提供了可定制的任务模板的支持。
- 支持回滚指定某一任务。
- 提供了Istio状态诊断功能，可实时查看Istio的Services和Pod状态。
- 开箱即用，通过kubectl指令一键部署。

## 参考

- [小米正式开源Istio管理面板Naftis](http://www.servicemesher.com/blog/naftis-istio-dashboard-xiaomi/)