### Required
- ubuntu 18.04
- go 1.13.4
- docker 19.03
- docker-compose 1.26.0
- mysql 8.0
- hyperledger fabric 1.4.6

###Ready
- Create a **github.com/fabric-app database** and import SQL
- Bring up hyperledger fabric local test net or cluster

### Config

You should modify `conf/app.ini`
Crypto-config files should be replace by you fabric network msp files
Change the network connection config file: conn-fn1.yaml 

```
[database]
Type = mysql
User = root
Password =
Host = 202.193.60.215:3306
Name = BC
TablePrefix = 
```
### Install
```
$ go get -u github.com/swaggo/swag/cmd/swag
$ git clone 
$ go mod tidy
$ go mod vendor
$ swag init
$ go run main.go
```
### Project information and existing API
```
[GIN-debug] [WARNING] Running in "debug" mode. Switch to "release" mode in production.
 - using env:	export GIN_MODE=release
 - using code:	gin.SetMode(gin.ReleaseMode)

[GIN-debug] GET    /swagger/*any             --> github.com/swaggo/gin-swagger.CustomWrapHandler.func1 (4 handlers)
[GIN-debug] POST   /api/v1/auth              --> github.com/fabric-app/controller/api/v1.Auth (4 handlers)
[GIN-debug] POST   /api/v1/reg               --> github.com/fabric-app/controller/api/v1.Reg (4 handlers)
[GIN-debug] GET    /api/v1/currentuser       --> github.com/fabric-app/controller/api/v1.CurrentUser (5 handlers)
[GIN-debug] GET    /api/v1/refreshtoken      --> github.com/fabric-app/controller/api/v1.RefreshToken (5 handlers)
[GIN-debug] POST   /api/v1/logout            --> github.com/fabric-app/controller/api/v1.Logout (5 handlers)
[GIN-debug] POST   /api/v1/password          --> github.com/fabric-app/controller/api/v1.Password (5 handlers)
[GIN-debug] POST   /api/v1/modify            --> github.com/fabric-app/controller/api/v1.ModifyUser (5 handlers)
[GIN-debug] POST   /api/v1/code              --> github.com/fabric-app/controller/api/v1.AddCode (5 handlers)
[GIN-debug] POST   /api/v1/balance           --> github.com/fabric-app/controller/api/v1.AddBanlance (5 handlers)
[GIN-debug] POST   /api/v1/cost              --> github.com/fabric-app/controller/api/v1.Cost (5 handlers)
[GIN-debug] GET    /api/v1/incomes           --> github.com/fabric-app/controller/api/v1.Incomes (5 handlers)
[GIN-debug] GET    /api/v1/costs             --> github.com/fabric-app/controller/api/v1.Costs (5 handlers)
[GIN-debug] POST   /api/v1/updatecost        --> github.com/fabric-app/controller/api/v1.UpdateCost (5 handlers)
[GIN-debug] GET    /test                     --> github.com/fabric-app/routers.InitRouter.func1 (4 handlers)
```
### Swaggo

> http://127.0.0.1:8000/swagger/index.html

## 项目结构概览
```
├── conf 配置文件
├── docs：api文档swagger
│   └── sql：sql执行语句  
├── middleware：中间件
│   └── jwt：认证中间件
├── model：引用数据库模型
├── pkg：第三方包和公共模块
│   ├── app：gin engine
│   ├── e： 错误编码和错误信息
│   ├── logging：日志模块
│   ├── setting：go-ini包
│   └── util：工具库 
└── routers：路由处理
│    └── api：controller 逻辑梳理
│        └── v1：controller逻辑处理 
└── service：逻辑处理
└── runtime：日志，文件缓存存放
└── test：单元测试
└── main.go：入口文件 
```






