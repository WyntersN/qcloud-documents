
基于 Spring Cloud Greenwich 版本 SDK，支持 spring boot 2.1.6。

## 1.22.1-Greenwich-RELEASE（2020-05-06）

### 优化

优化 TSF MSGW scg 使用，用户无需显示配置全局路由。

### 版本建议

支持向后兼容，建议全量升级。

## 1.22.0-Greenwich-RELEASE（2020-04-29）

### 新特性

- 支持 SpringCloud Gateway 链路追踪和调用监控。
- TSF MSGW scg 版本发布。
- TSF MSGW zuul1 版本发布。

### Bug 修复

- 修复在使用 redis，自定义多个 LettuceConnectionFactory 时，不能链路追踪所有请求的问题。
- 修复调用监控禁用场景内存泄露问题。
- 修复 Spring Cloud Gateway 无法使用 TSF 服务注册和发现的问题。

### 优化

优化默认日志配置支持容器部署场景。

## 1.21.1-Greenwich-RELEASE（2020-04-29）

### Bug 修复

修复泳道 ID 在非泳道起始应用中传递丢失的问题。

### 优化

- 修复调用链生成文件名称问题。
- 任务调度组件优化任务生成器逻辑，兼容 BeanName 和 BeanType 方式获取工厂。

## 1.21.0-Greenwich-RELEASE（2020-04-17）

### 新特性

- 全链路灰度发布。
- 增加熔断状态变更事件上报。

### Bug 修复

- 修复 Feign 无法使用绝对 URL 请求的问题
- 修复 spring-cloud-tsf-swagger 包中 @ApiParam 注解 Example 属性解析异常问题。

### 优化

支持 swagger 自动扫描包多路径特性。

## 1.20.0-Greenwich-RELEASE（2020-03-02）

### 新特性

- 新增`分布式任务调度`功能。
- spring-cloud-tsf-sleuth 支持`kafka`和`rocketmq`链路追踪功能。

### Bug 修复

处理 tomcat 组件开源漏洞风险。
  - 升级 org.apache.tomcat.embed.tomcat-embed-core 到9.0.31版本。
  - 升级 org.apache.tomcat.embed.tomcat-embed-el 到9.0.31版本。
  - 升级 org.apache.tomcat.embed.tomcat-embed-websocket 到9.0.31版本。

## 1.19.0-Greenwich-RELEASE（2020-01-16）

### 新特性

新增`服务熔断`功能。

### 版本建议

支持向后兼容，建议全量升级。

## 1.18.1-Greenwich-RELEASE（2020-01-14）

### Bug 修复

- spring-cloud-tsf-route 修复路由权重不准的问题。
- spring-cloud-tsf-consul-discovery 修复服务发现线程池上限的问题。
- spring-cloud-tsf-sleuth 修复 druid 连接池事务兼容问题。
- spring-cloud-tsf-sleuth 修复同时依赖多个数据库连接池问题。
- spring-cloud-tsf-core 修复 Custom Metadata 设置接口不兼容。

### 优化

支持通过 `tsf.discovery.watch.enabled` 关闭服务发现时的 watch 监听。

### 版本建议

支持向后兼容，建议全量升级。

## 1.18.0-Greenwich-RELEASE（2019-12-25）

### Bug 修复

- spring-cloud-tsf-sleuth 修复 JdbcDataSourceBeanPostProcessor NPE bug 问题。
- spring-cloud-tsf-consul-discovery 修复 ConsulProperties 中同时使用 @Value 和  @ConfigurationProperties 方式进行属性注入，先后顺序导致的 bug 问题。
- spring-cloud-tsf-sleuth 修复监控日志可能出现的 NPE bug 问题。

### 新特性

- 服务治理支持全局命名空间。
- 新增自定义日志配置需要的 Converter 和 Layout 类，支持用户使用自定义 logback\log4j\log4j2 日志配置。

### 优化

spring-cloud-tsf-sleuth 优化 TraceStatementProxyHandler  JDBC 代理过程内部异常处理逻辑：非代理异常、非 SDK 产生的异常，直接抛出；代理异常或 SDK 产生的异常，直接调用服务不经过调用链逻辑。

### 版本建议

支持向后兼容，建议全量升级。

## 1.16.2-Greenwich-RELEASE（2020-03-02）

### Bug 修复

- spring-cloud-tsf-sleuth bug fixed：
  - 处理 Custom Metadata 设置接口不兼容。
  - 调用链输出用户自定义 Tag 和 Metadata。
  - 修复druid连接池事务兼容问题。
  - 修复同时依赖多个数据库连接池问题。

## 1.16.1-Greenwich-RELEASE（2019-12-3）

### Bug 修复

API 注册兼容从环境变量和启动参数中读取 TSF 参数信息。

## 1.16.0-Greenwich-RELEASE（2019-11-5）

### 新特性

#### 服务限流（spring-cloud-tsf-rate-limit）

- 支持针对所有请求、单个服务的请求进行流量控制。
- 支持服务下单个 API 请求级别的限流。

#### 服务路由（spring-cloud-tsf-route）

- 支持基于部署组、系统标签、自定义标签的路由设置。
- 支持服务下单个 API 请求级别的路由。
- 支持自动重注册，服务鉴权/路由/限流策略本地缓存。
- 服务路由支持基于可用区和地域就近访问策略。

#### 服务鉴权

支持基于服务名和标签的鉴权设置。

#### 链路跟踪（spring-cloud-tsf-sleuth）

- 支持微服务调用全链路跟踪。
- 支持 MySQL JDBC、Redis、MongoDB、CMQ 组件调用链。
- 支持在调用链上设置标签和自定义 Metada。

#### 分布式配置（spring-cloud-tsf-config）

- 支持分布式配置功能。
- 配置回调。
- 配置加密 spring-cloud-tsf-encrypt。

#### API注册（spring-cloud-tsf-swagger）

- API 注册：支持服务下 API 信息自动注册，查看 API 出入参请求结构。
- 集成 spring-cloud-tsf-swagger 包，支持本地使用 swagger-ui 进行调试。
