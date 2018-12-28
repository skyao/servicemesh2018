# Service Mesh2018年度总结

应InfoQ的邀请，再次撰写Service Mesh2018年度总结。

此次，邀请了Service Mesh社区的一众好友共襄盛举，希望能为Service Mesh2018年的发展做一个系统而全面的总结。特此鸣谢！

参与者名单：

- 敖小剑
- 崔秀龙
- 单家骏
- 宋净超
- 田晓亮
- 徐蓓
- 张超盟

## 资料整理

资料按照国内国外分为两大块。

国外部分，目前主要的service mesh产品：

- [Istio](input/istio.md)：来自Google/IBM/Lyft，目前最主流的Service Mesh项目
- [Istioi平台支持](input/istio-platform.md)：对Istio提供支持的各主流云平台介绍
- [Envoy](input/envoy.md)：来自Lyft的数据平面，也是Istio默认的数据平面
- [Conduit](input/conduit.md)：来自Buoyant，已经转为Linkerd2
- [Linkerd](input/linkerd.md)：来自Buoyant，业界第一个Service Mesh项目
- [Linkerd2](input/linkerd2.md)：来自Buoyant

各家Network厂商也开始尝试Service Mesh：

- [Consul Connect](input/consul.md)：来自Consul
- [Kong](input/kong.md)：Kong到底想不想做Service Mesh？
- [Nginmesh](input/nginmesh.md)：来自Nginx的Service Mesh项目
- [Aspen Mesh](input/aspenmesh.md): F5 出品的Istio商业版本，未开源
- [AWS App Mesh](input/aws.md): 来自Amazon AWS，未开源

国外的Service Mesh的衍生产品，底层支撑，或者外围支持：

- [Cillium](input/cillium.md)：可以和Istio/Envoy一起使用的网络解决方案
- [Kiali](input/kiali.md)：Istio的控制台UI

Envoy的衍生产品：

- [Rotor](input/rotor.md): Envoy的轻量级控制平面，来自Turbine Labs，已经不再维护
- [Ambassador](input/ambassador.md)：基于Envoy的API Gateway
- [Gloo](input/gloo.md)：基于Envoy的API Gateway
- [Contour](input/contour.md): 基于Envoy的Kubernetes Ingress Controller

国内的Service Mesh产品：

- [SOFAMosn](input/sofamosn.md)：蚂蚁金服的数据平面
- [SOFAMesh](input/sofamesh.md)：蚂蚁金服的控制平面，基于Istio
- [Motan Mesh](input/motanmesh.md)：新浪微博的ServiceMesh产品
- [Dubbo Mesh](input/dubbomesh.md)：阿里Dubbo的Service Mesh方案
- [Mesher](input/mesher.md)：华为CSE Mesher的开源产品
- [AMS/Application Service Mesh ](input/asm.md): 华为云应用服务网格
- [Tencent Service Mesh](input/tencent.md): 腾讯Service Mesh产品

国内的Service Mesh的衍生产品，底层支撑，或者外围支持：

- [Naftis](input/naftis.md)：来自小米的Isito管理面板
- [Istio-ui](input/istio-ui.md)：Istio的简易UI

