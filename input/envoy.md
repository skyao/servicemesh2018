# Envoy

2018年对Envoy来说，属于大规模落地的一年。随着功能的逐步完善和成熟，以及作为service mesh控制面的头牌项目--istio的官配sidecar，被越来越多企业的service mesh框架项目所采用并落地（包括aws的app mesh, F5的aspen mesh, 微软的service frabric mesh，国内的如腾讯、阿里等），Envoy逐渐有成为service mesh的数据面标准的趋势。

下面针对envoy的关键版本和关键事件做说明，关于envoy各版本详细的变更参考[变更说明](https://www.envoyproxy.io/docs/envoy/v1.9.0/intro/version_history)。

## 2018.6.21

发布1.7.0版本，配套istio 1.0版本作为production ready的service mesh解决方案。全面支持RBAC鉴权模型, TLS&JWT加密，网络通信安全性有极大提升。

## 2018.11.28

云原生基金会宣布Envoy从CNCF毕业，成为继Kubernetes和Prometheus后，第三个孵化成熟的项目。

