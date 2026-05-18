# 校园商城 (HMall)

一个基于 Spring Boot 的电商后端系统，提供商品管理、购物车、订单、支付等核心电商功能。

## 技术栈

- **Java 11**
- **Spring Boot 2.7.12**
- **MyBatis-Plus 3.4.2**
- **MySQL 8.0**
- **Redis**
- **Spring Security Crypto / JWT 认证**
- **Swagger API 文档**

## 项目结构

```
hmall/
├── hm-common/          # 公共模块（工具类、异常处理、通用配置）
│   └── src/main/java/com/hmall/common/
│       ├── advice/     # 全局异常处理
│       ├── config/     # JSON、MyBatis 配置
│       ├── domain/     # 通用 DTO（R、PageDTO、PageQuery）
│       ├── exception/  # 自定义异常
│       └── utils/      # 工具类（BeanUtils、UserContext 等）
│
├── hm-service/         # 业务服务模块
│   ├── src/main/java/com/hmall/
│   │   ├── config/       # 配置类（JWT、安全、MVC）
│   │   ├── controller/   # REST 控制器
│   │   ├── domain/       # DTO / VO / PO 实体
│   │   ├── enums/        # 枚举（支付类型、状态等）
│   │   ├── interceptor/  # 登录拦截器
│   │   ├── mapper/       # MyBatis Mapper
│   │   └── service/      # 业务逻辑
│   └── Dockerfile
└── pom.xml
```

## 核心功能模块

| 模块 | Controller | 说明 |
|------|-----------|------|
| 商品管理 | `ItemController` | 商品 CRUD、分页查询、库存扣减 |
| 购物车 | `CartController` | 添加/更新/删除购物车商品 |
| 订单管理 | `OrderController` | 创建订单、查询订单、标记支付 |
| 支付管理 | `PayController` | 支付下单、支付回调 |
| 用户管理 | `UserController` | 用户登录、注册 |
| 地址管理 | `AddressController` | 收货地址 CRUD |


## API 接口

启动后访问 Swagger 文档：`http://localhost:8080/swagger-ui.html`

### 主要接口

```
GET    /items/page          # 分页查询商品
GET    /items/{id}          # 查询商品详情
POST   /carts               # 添加购物车
GET    /carts               # 查询购物车
POST   /orders              # 创建订单
GET    /orders/{id}         # 查询订单
POST   /pay-orders          # 发起支付
```

## 认证方式

使用 JWT Token 认证，通过 `LoginInterceptor` 拦截器校验登录状态。
