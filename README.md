# ERP（业务端）系统


### 项目介绍
```
1.登录
2.前台
3.测评
4.取型
5.修型车间
6.加工车间
7.质检部
8.库房管理
9.财务管理
10.回访
11.试穿
12.维修
13.体检数据库
14.大客户
15.理论数据库
16.管理员
  
```

### 软件架构
Vue.js | Router | Vuex | ElementUI | Sass | Echart | Webpack


## APIS

### 用户登录模块
|||||
|-|-|-|-|
|[用户登录](#用户登录)|[用户登出](#用户登出)|

### 支具室模块

#### 主页
||||||
|-|-|-|-|-|
[获取用户信息](#获取用户信息)||[统计模块](#统计模块)|[统计查询](#统计查询)|

#### 客户管理

||||||
|-|-|-|-|-|
|[新增客户](#新增客户)|[客户查询](#客户查询)|[客户下单](#客户下单)|[选择医院](#选择医院)|
|[获取医院科室](#获取医院科室)|[获取医院科室医生](#获取医院科室医生)|[选择产品](#选择产品)|[选择测评](#选择测评)|
|[客户信息](#客户信息)|[测评详情](#测评详情)|

#### 订单管理

|||||
|-|-|-|-|
|[订单查询](#订单查询)|[订单信息](#订单信息)|

### 项目模块

||||||
|-|-|-|-|-|
|[获取实战项目列表](#获取实战项目列表)|[获取实战项目信息](#获取实战项目信息)|[发布实战项目动态](#发布实战项目动态)|[发布实战项目动态评论](#发布实战项目动态评论)|[获取实战项目动态列表](#获取实战项目动态列表)|
|[项目动态点赞](#项目动态点赞)|[项目动态取消赞](#项目动态取消赞)|[获取实战项目动态评论列表](#获取实战项目动态评论列表)|[收藏实战项目](#收藏实战项目)|[取消收藏实战项目](#取消收藏实战项目)|
|[参与实战项目](#参与实战项目)|[取消参与实战项目](#取消参与实战项目)|[获取实战任务列表](#获取实战任务列表)|[获取实战任务信息](#获取实战任务信息)|[发布实战任务动态](#发布实战任务动态)|
|[发布实战任务动态评论](#发布实战任务动态评论)|[获取任务动态列表](#获取任务动态列表)|[获取任务动态评论列表](#获取任务动态评论列表)|||

### 自学团模块
||||||
|-|-|-|-|-|
|[获取签到列表](#获取签到列表)|[签到打卡](#签到打卡)|[点赞](#点赞)|[取消赞](#取消赞)|[评论](#评论)|
|[获取评论列表](#获取评论列表)|||||

### 队伍模块
||||||
|-|-|-|-|-|
|[获取队伍列表](#获取队伍列表)|[创建队伍](#创建队伍)|[加入队伍](#加入队伍)|[获取队伍](#获取队伍)|[首页队伍推荐](#首页队伍推荐)|
||||||


### 安装教程
```
1. git clone https://github.com/SpeedingLogan/BangDNA.git

2. npm i

3. npm start
```

### 使用说明
```
1. router.js          - 管理路由与接口
2. /controller        - 管理控制层
3. /service           - 管理服务
4. /middleware        - 管理中间件
5. app.js             - 入口文件
```

### APIS
```
host: http://47.100.161.115:80
```

### 用户模块

#### 用户登录
```
    POST /user/login
```
##### 参数说明
| 参数            | 说明     | 数据类型  |
|-----------------|----------|-----------|
| uname           | 用户名   | string |
| password        | 密码     | string |
##### 返回说明
| 参数    | 说明         |
|---------|------------|
| status  | 0 \| -1    |
| message | 登录状态消息 |
| data    | 用户信息       |
##### data
| 参数     | 说明       |
|-----------------|-------------------------------|
| userId              | 用户唯一ID                     |
| nickname        | 用户昵称                       |
| role          | 用户角色标识               |
| roleName           | 用户角色名                     |
| authority          | 用户权限|

#### 用户登出
```
  POST /user/logout
```
##### 参数说明
| 参数            | 说明     |
|-----------------|----------|
| 无              | 无      |

##### 返回说明
| 参数    | 说明         |
|---------|------------|
| status  | 0 \| -1    |
| message | 登出状态消息 |
| data    | {}       |

#### 获取用户信息
```
  POST /user/get_user_info
```
##### 参数说明
| 参数            | 说明      |  |
|-----------------|----------|
| id              | 用户ID    |
| roleName        | 用户角色 |
| authority       | 用户权限  |

##### 返回说明
| 参数    | 说明         |
|---------|------------|
| status  | 0 \| -1    |
| message | 状态消息 |
| data    | 用户数据    |


Example
```
  // 1. 登录用户
  Axios.POST('http://www.fuyinkangfu.com:80/get_user_info',{
    uname: uname,
    password: password,
  }).then((result) => {
    console.log(result)
  }).catch((result) => {
    console.log(result)
  })
```

#### 获取消息列表
```
    POST /user/get_messages
```
##### 参数说明
| 参数                 | 说明           	| 必须 	|
|---------------------|----------------	|-----:	|
| offset            	| 分页的游标        	|   是 	|
| size        	      | 每页的数量     	 |   是 	|
| message_type        | message_type: 1: 动态点赞，2：动态评论，3：系统消息     	 |   是 	|
##### 返回说明
| 参数    | 说明         |
|---------|------------|
| status  | 0 \| -1    |
| message | 消息列表    |
| data    | {}        |

#### 阅读消息
```
    POST /user/already_read
```
##### 参数说明
| 参数                 | 说明           	| 必须 	|
|---------------------|----------------	|-----:	|
| id                	| 消息ID        	|   是 	|
##### 返回说明
| 参数    | 说明         |
|---------|------------|
| status  | 0 \| -1    |
| message | 阅读状态    |
| data    | {}        |


### 支具室模块

####统计查询
```
    Post /support/homepage/query_statistic
```
#### 参数

  | 参数  | 说明  |
  |--------|---------|
  |  today  | 当前日期 |
  |  yesterday | 昨天日期  |
  |  sevenDays |  近7日 |
  |  startDay  | 开始日期  |
  |  endDay    | 结束日期  |

#### 返回说明

| 参数    | 说明         |
|---------|------------|
| status  | 0 \| -1    |
| totalOrderNumber    |  总下单数量   |
| totalSellMoney    |  总销售额   |
| totalNewClients    |  新增客户总数量   |
| totalNewOrderClients    |  新增下单客户总数量   |
| currentTime    | 当前时间段(格式 ['8', '9', '10'...])    |
| currentSeelMoney   |  当前销售额  |
| currentClientsNumber | 当前客户数量  |


#### 统计模块
```
    GET /support/homepage/statistic
```

##### 返回说明
| 参数    | 说明         |
|---------|------------|
| status  | 0 \| -1    |
| totalOrderNumber    |  总下单数量   |
| totalSellMoney    |  总销售额   |
| totalNewClients    |  新增客户总数量   |
| totalNewOrderClients    |  新增下单客户总数量   |



#### 统计图表
```
    Get /support/homepage/static_chart
```

##### 返回说明
| 参数     | 说明                                       |
|---------|-------------------------------------------|
| status  | 0 \| -1                                   |
| currentTime    | 当前时间段(格式 ['8', '9', '10'...])    |
| currentSeelMoney   |  当前销售额  |
| currentClientsNumber | 当前客户数量  |

#### 新增客户

```
    POST  /support/clientmanage/add_new_client
```
#### 参数
| 参数 | 说明                    | 是否必要 |
|----------|------------------------|---- |
| uname | 客户姓名  | yes |
| realPhone | 联系方式  | yes |
| standbyPhone | 备用联系方式 | no |
| sex | 性别 | yes |
| birthday |  出生日期  | yes |
| address  |  地址   | yes |
| clientType  |  客户类型  | no |
| clientSource  |  客户来源  | yes |
| hospital  |  医院  | yes |
| hospitalOffice | 科室 | yes |
| doctor | 医生 | no |
| recipe | 处方病情 | no | 


#### 返回说明

| 参数 | 说明  |
|------|------|
|status  |  0 \| 1 |
| data | 数据 |

#### 客户信息
```
  POST  /support/clientManage/client_info
```
|  参数  |  说明  |  数据类型  |  是否必要  |
|--------|--------|-----------|-----------|
|  userId   |  客户唯一ID  | int |  yes |

#### 返回说明

| 参数 | 说明        |   数据类型         | 是否必要 |
|----------|------------|------------|---- |
| uname | 客户姓名  | string | yes |
| realPhone | 联系方式  | string | yes |
| standbyPhone | 备用联系方式 | string | no |
| sex | 性别 | string | yes |
| age |  年龄  | string | yes |
| address  |  地址  | string  | no |
| clientType  |  客户类型 | string   | no |
| clientSource  |  客户来源  | string | yes |
| schoolName |  学校名称  | string | no|
| hospital  |  医院名称  | string | yes |
| hospitalOffice | 科室 | string | yes |
| doctor | 医生 | string | no |
| recipe | 处方病情 | string | no |
| viewIllness | 观察病情 | string | no |
| testRecord | 测评记录 | array | no |
| orderInfo | 订单信息 | array | yes |


#### 客户查询
```
    POST  /support/clientmanage/query_client
```
#### 参数
| 参数 | 说明                    | 是否必要 |
|----------|------------------------|---- |
| uname | 客户姓名  | yes |
| realPhone | 联系方式  | no |
| clientState | 客户状态 | no |
| startDate |  开始日期   | no |
| endDate |  结束日期   | no |
| birthday |  出生日期  | no |
| today  |  今日   | no |
| yesterday  |  昨日   | no |
| sevenDays  |  近7日  | no |
| visitState  |  到访状态  | no |
| isOrder  |  是否下单  | no |
| isMember | 是否会员 | no |
| clientSource | 客户来源 | no |

#### 返回说明

| 参数 | 说明  |
|------|------|
|status  |  0 \| 1 |
| data | 数据 |

##### data表及分页
| 参数 | 说明  |  数据类型 | 是否必要 |
|---------|------|------|---------|
| offset | 分页查询游标（初始为0） | int | yes |
| size | 当页显示条数 | int | yes |
| num | 序号 | int | yes |
| uname | 客户姓名 | string | yes |
| sex | 客户性别 | string | yes |
| clientState | 客户状态 | string | no |
| sex | 客户性别 | string | yes |
| visitState | 到访状态 | string | no |
| phone | 联系电话 | string | yes |
| age | 年龄 | string | no |
| clientSource | 客户来源 | string | yes |
| createTime | 创建时间 | string | yes |
| isMember | 是否会员 | bool | yes |


#### 客户下单

```
    POST  /support/clientManage/order
```

|  参数  | 说明 | 数据类型 | 是否必要  |
|--------|-------|--------|-----|
|  uname | 客户姓名 | string | yes |
|  hospital | 医院名称 | string | yes |
|  hospitalOffice | 科室名称 | string | yes |
|  doctor | 医生 | string | yes |
|  viewIllness | 观察病情 | string | yes |
|  specialRequire | 特殊要求 | string | no |
|  orderPerson | 下单人员 | string | yes |
|  orderProduct | 下单产品 | Array | yes |
|  deliveryDate | 交货日期 | string | yes |
|  payType | 付款类型 | string | yes |
|  cash | 现金实收金额 | double | yes |
|  virtualPay | 拉卡拉实收金额 | double | yes |
|  totalPay | 应收金额合计 | double | yes |

#### 选择医院

```
    Get  /support/hospital
```
##### 返回说明

|  参数  | 说明 | 数据类型 | 是否必要  |
|--------|-------|--------|-----|
| status | 0 \| 1 | int | yes |
| data | 医院数据 | array | yes |

#### 获取医院科室
```
    POST  /support/hopital/office
```

|  参数  | 说明 | 数据类型 | 是否必要  |
|--------|-------|--------|-----|
| hospitalId | 医院唯一ID | int | yes |

#### 返回说明

|  参数  | 说明 | 数据类型 | 是否必要  |
|--------|-------|--------|-----|
| status | 0 \| 1 | int | yes |
| data | 科室数据 | array | yes |

#### 获取医院科室医生
```
    POST  /support/hospital/office/doctor
```
|  参数  | 说明 | 数据类型 | 是否必要  |
|--------|-------|--------|-----|
| officeId | 科室唯一Id | int | yes |

#### 返回说明

|  参数  | 说明 | 数据类型 | 是否必要  |
|--------|-------|--------|-----|
| status | 0 \| 1 | int | yes |
| doctors| 医生表 | array | yes |

#### 选择产品
```
    POST  /support/get_product
```
|  参数  | 说明 | 数据类型 | 是否必要  |
|--------|-------|--------|-----|
| queryProduct | 模糊查询(默认为 ' ') | string | no |

#### 返回说明

|  参数  | 说明 | 数据类型 | 是否必要  |
|--------|-------|--------|-----|
| status | 0 \| 1 | int | yes |
| product | 产品目录  | Array  | yes |

#### 选择测评

```
    POST  /support/get_test_evaluate
```
|  参数  | 说明 | 数据类型 | 是否必要  |
|--------|-------|--------|-----|
| queryTest | 模糊查询(默认为 ' ') | string | no |

#### 返回说明

|  参数  | 说明 | 数据类型 | 是否必要  |
|--------|-------|--------|-----|
| status | 0 \| 1 | int | yes |
| test | 测评目录  | Array  | yes |

#### 测评详情
```
    POST  /support/get_test_information
```
|  参数  | 说明 | 数据类型 | 是否必要  |
|--------|-------|--------|-----|
| userId | 客户唯一Id | int | yes |

#### 返回说明

|  参数  | 说明 | 数据类型 | 是否必要  |
|--------|-------|--------|-----|
| uname | 客户姓名 | string | yes |
| sex  | 性别  | string  | yes |
| age  | 年龄  | string  | yes |
| phone  | 联系方式  | string  | yes |
| address  | 地址  | string  | yes |
| testData | 测评数据  | array  | yes |

##### testData 说明
|  参数  | 说明 | 数据类型 | 是否必要  |
|--------|-------|--------|-----|
| testItemId | 测评项目唯一Id | int | yes |
| testItemName | 测评项目名称 | string | yes |
| detailData |  测评详细数据    | string  | yes |
| viewIllness  | 观察病情  | string  | yes |
| testResult  | 测评结果  | string  | yes |

#### 订单查询
```
    POST  /support/ordermanage
```
|  参数  | 说明 | 数据类型 | 是否必要  |
|--------|-------|--------|-----|
| offset | 分页游标（默认为 0） | int | yes |
| size | 单页显示条数 | int  | yes |
| uname | 客户姓名 | string | no |
| phone | 联系方式 | string | no |
| orderState |  订单状态    | string  | no |
| startDate  | 开始日期  | string  | no |
| endDate  |   结束日期  | string  | no |
| today | 今日  | string  | no |
| yesterday | 昨日  | string  | no |
| sevendays | 近7日  | string  | no |
| orderType | 订单类型  | string  | no |
| payType | 付款类型  | array  | no |
| isdebt  | 是否欠款  | bool  | no |
| orderNumber | 订单编号  | string  | no |
| orderPeople |  下单人  | string  | no |

#### 返回说明

|  参数  | 说明 | 数据类型 | 是否必要  |
|--------|-------|--------|-----|
| uname | 客户姓名 | string | yes |
| phone | 联系方式 | string | yes |
| orderState |  订单状态    | string  | yes |
| createTime |  下单时间    | string  | yes |
| orderType | 订单类型  | string  | yes |
| payType | 付款类型  | array  | yes |
| isdebt  | 是否欠款  | bool  | yes |
| orderNumber | 订单编号  | string  | yes |
| orderPeople |  下单人  | string  | no |

#### 订单信息
```
    POST  /support/order_infomation
```
|  参数  | 说明 | 数据类型 | 是否必要  |
|--------|-------|--------|-----|
| userId | 客户唯一Id | int | yes |

#### 返回说明
|  参数  | 说明 | 数据类型 | 是否必要  |
|--------|-------|--------|-----|
| uname | 客户姓名 | string | yes |
| phone | 联系方式 | string | yes |
| standbyphone | 备用联系方式 | string | no |
| age | 年龄 | string | yes |
| sex | 性别 | string | yes |
| address | 地址 | string | yes |
| clientType | 客户类型 | string | yes |
| schoolName | 学校名称 | string | yes |
| hospital |  医院名称    | string  | yes |
| hospitalOffice | 医院科室 | string | yes |
| doctor | 医生 | string | yes |
| recipe | 处方病情  | string  | yes |
| viewIllness | 观察病情  | string  | yus |
| isdebt  | 是否欠款  | bool  | yes |
| orderNumber | 订单编号  | string  | yes |
| delivery | 交货时间  | string  | yes |
| orderPeople |  下单人  | string  | yes |
| refoundMoney | 退款金额  |  double  | yes |
| isUrgent | 是否加急 | bool  | yes |
| payType | 付款类型  | string  | yes |
| prepay | 预缴金额  | double  | yes |
| owingMoney | 下欠金额  | double  | yes |
| totalMoney | 应收金额合计  | double  | yes |
| refoundTime | 退款时间  | string  | yes |
| specialRequired | 特殊要求  | string  | no |



### 项目模块

#### 获取实战项目列表
```
    POST /project/list
```
##### 参数说明
| 参数       | 说明       | 必须 |
|-----------|------------|-----:|
| offset    | 分页查询的游标，最开始可以传0         |   是 |
| size    | 分页查询的每页大小，最大100         |   是 |

##### 返回说明
| 参数    | 说明         |
|---------|------------|
| status  | 0 \| -1    |
| message | 状态消息 |
| data    | 所有项目    |

#### 获取实战项目信息
```
    POST /project/item
```
##### 参数说明
| 参数         | 说明         | 必须 |
|--------------|--------------|-----:|
| project_id   | 项目ID      |   是 |

##### 返回说明
| 参数    | 说明         |
|---------|------------|
| status  | 0 \| -1    |
| message | 状态消息 |
| data    | 所有项目    |

#### 发布实战项目动态
```
    POST /project/pub_dyna
```

##### 参数说明
| 参数         | 说明         | 必须 |
|--------------|--------------|-----:|
| project_id   | 项目ID      |   是 |
| title        | 动态标题      |   是 |
| content      | 动态内容    |   是 |

##### 返回说明
| 参数    | 说明         |
|---------|------------|
| status  | 0 \| -1    |
| message | 状态消息 |
| data    | 所有项目    |

#### 发布实战项目动态评论
```
    POST /project/pub_dyna_cmt
```
##### 参数说明
| 参数         | 说明         | 必须 |
|--------------|--------------|-----:|
| dynamic_id   | 动态ID      |   是 |
| comment      | 评论标题      |   是 |

##### 返回说明
| 参数    | 说明         |
|---------|------------|
| status  | 0 \| -1    |
| message | 状态消息 |
| data    | 所有项目    |

#### 获取实战项目动态列表
```
    POST /project/dyna_list
```
##### 参数说明
| 参数         | 说明         | 必须 |
|--------------|--------------|-----:|
| dynamic_id   | 动态ID      |   是 |

##### 返回说明
| 参数    | 说明         |
|---------|------------|
| status  | 0 \| -1    |
| message | 状态消息 |
| data    | 所有项目    |

#### 项目动态点赞
```
    POST /project/dyna_star
```
##### 参数说明
| 参数                  | 说明       | 必须 |
|----------------------|------------|-----:|
| project_dynamic_id   | 动态ID      |   是 |

##### 返回说明
| 参数    | 说明         |
|---------|------------|
| status  | 0 \| -1    |
| message | 状态消息 |
| data    | 所有项目    |

#### 项目动态取消赞
```
    POST /project/dyna_unstar
```
##### 参数说明
| 参数                  | 说明       | 必须 |
|----------------------|------------|-----:|
| project_dynamic_id   | 动态ID      |   是 |

##### 返回说明
| 参数    | 说明         |
|---------|------------|
| status  | 0 \| -1    |
| message | 状态消息 |
| data    | 所有项目    |

#### 获取实战项目动态评论列表
```
    POST /project/dyna_cmt_list
```
##### 参数说明
| 参数                  | 说明       | 必须 |
|----------------------|------------|-----:|
| project_dynamic_id   | 动态ID      |   是 |

##### 返回说明
| 参数    | 说明         |
|---------|------------|
| status  | 0 \| -1    |
| message | 状态消息 |
| data    | 所有项目    |

#### 收藏实战项目
```
    POST /project/star
```
##### 参数说明
| 参数       | 说明       | 必须 |
|-----------|------------|-----:|
| project_id| 项目ID      |   是 |

##### 返回说明
| 参数    | 说明         |
|---------|------------|
| status  | 0 \| -1    |
| message | 状态消息    |
| data    | 所有项目    |

#### 取消收藏实战项目
```
    POST /project/unstar
```
##### 参数说明
| 参数       | 说明       | 必须 |
|-----------|------------|-----:|
| project_id| 项目ID      |   是 |

##### 返回说明
| 参数    | 说明         |
|---------|------------|
| status  | 0 \| -1    |
| message | 状态消息    |
| data    | 所有项目    |

#### 参与实战项目
```
    POST /project/partake
```
##### 参数说明
| 参数       | 说明       | 必须 |
|-----------|------------|-----:|
| project_id| 项目ID      |   是 |

##### 返回说明
| 参数    | 说明         |
|---------|------------|
| status  | 0 \| -1    |
| message | 状态消息    |
| data    | 所有项目    |

#### 取消参与实战项目
```
    POST /project/unpartake
```
##### 参数说明
| 参数       | 说明       | 必须 |
|-----------|------------|-----:|
| project_id| 项目ID      |   是 |

##### 返回说明
| 参数    | 说明         |
|---------|------------|
| status  | 0 \| -1    |
| message | 状态消息    |
| data    | 所有项目    |

#### 获取实战任务列表
```
    POST /project/task_list
```
##### 参数说明
| 参数       | 说明       | 必须 |
|-----------|------------|-----:|
| project_id| 项目ID      |   是 |

##### 返回说明
| 参数    | 说明         |
|---------|------------|
| status  | 0 \| -1    |
| message | 状态消息    |
| data    | 所有项目    |

#### 获取实战任务信息
```
    POST /project/task
```
##### 参数说明
| 参数       | 说明       | 必须 |
|-----------|------------|-----:|
| task_id   | 任务ID      |   是 |

##### 返回说明
| 参数    | 说明         |
|---------|------------|
| status  | 0 \| -1    |
| message | 状态消息    |
| data    | 所有项目    |

#### 发布实战任务动态
```
    POST /project/task_pub_dyna
```
##### 参数说明
| 参数       | 说明       | 必须 |
|-----------|------------|-----:|
| task_id   | 任务ID      |   是 |
| content   | 动态内容     |   是 |

##### 返回说明
| 参数    | 说明         |
|---------|------------|
| status  | 0 \| -1    |
| message | 状态消息    |
| data    | 所有项目    |

### 发布实战任务动态评论
```
  POST /project/task_pub_dyna_cmt
```
##### 参数说明
| 参数       | 说明       | 必须 |
|-----------|------------|-----:|
| dynamic_id| 任务动态ID  |   是 |
| content   | 动态内容    |   是 |


##### 返回说明
| 参数    | 说明         |
|---------|------------|
| status  | 0 \| -1    |
| message | 状态消息    |
| data    | {}         |

#### 获取任务动态列表
```
  POST /project/task_dyna_list
```

##### 参数说明
| 参数       | 说明       | 必须 |
|-----------|------------|-----:|
| task_id   | 任务ID      |   是 |


##### 返回说明
| 参数    | 说明         |
|---------|------------|
| status  | 0 \| -1    |
| message | 状态消息    |
| data    | 动态列表    |

#### 获取任务动态评论列表
```
  POST /project/task_dyna_cmt_list
```

##### 参数说明
| 参数       | 说明       | 必须 |
|-----------|------------|-----:|
| dynamic_id| 任务动态ID  |   是 |


##### 返回说明
| 参数    | 说明         |
|---------|------------|
| status  | 0 \| -1    |
| message | 状态消息    |
| data    | 评论列表    |


#### 获取签到列表
```
  POST /study/list
```

##### 参数说明
| 参数       | 说明       | 必须 |
|-----------|------------|-----:|
| offset    | 分页查询的游标，最开始可以传0         |   是 |
| size    | 分页查询的每页大小，最大100         |   是 |


##### 返回说明
| 参数    | 说明         |
|---------|------------|
| status  | 0 \| -1    |
| message | 状态消息    |
| data    | 签到列表    |


#### 签到打卡
```
  POST /study/check_in
```

##### 参数说明
| 参数       | 说明       | 必须 |
|-----------|------------|-----:|
| content   | 打卡内容    |   是 |


##### 返回说明
| 参数    | 说明         |
|---------|------------|
| status  | 0 \| -1    |
| message | 状态消息    |
| data    | {}         |


#### 点赞
```
  POST /study/star
```

##### 参数说明
| 参数          | 说明       | 必须 |
|--------------|------------|-----:|
| checkin_id   | 签到打卡ID  |   是 |


##### 返回说明
| 参数    | 说明         |
|---------|------------|
| status  | 0 \| -1    |
| message | 状态消息    |
| data    | {}         |

#### 取消赞
```
  POST /study/unstar
```

##### 参数说明
| 参数          | 说明       | 必须 |
|--------------|------------|-----:|
| checkin_id   | 签到打卡ID  |   是 |


##### 返回说明
| 参数    | 说明         |
|---------|------------|
| status  | 0 \| -1    |
| message | 状态消息    |
| data    | {}         |

#### 评论
```
  POST /study/pub_cmt
```

##### 参数说明
| 参数          | 说明       | 必须 |
|--------------|------------|-----:|
| checkin_id   | 签到打卡ID  |   是 |
| content      |评论内容     |   是 |


##### 返回说明
| 参数    | 说明         |
|---------|------------|
| status  | 0 \| -1    |
| message | 状态消息    |
| data    | {}         |

#### 获取评论列表
```
  POST /study/cmt_list
```


##### 参数说明
| 参数          | 说明       | 必须 |
|--------------|------------|-----:|
| checkin_id   | 签到打卡ID  |   是 |


##### 返回说明
| 参数    | 说明         |
|---------|------------|
| status  | 0 \| -1    |
| message | 状态消息    |
| data    | 评论列表    |


### 队伍模块

#### 获取队伍列表
```
  POST /team/list
```


##### 参数说明
| 参数       | 说明       | 必须 |
|-----------|------------|-----:|
| offset    | 分页查询的游标，最开始可以传0         |   是 |
| size    | 分页查询的每页大小，最大100         |   是 |
| project_id    | 项目ID         |   是 |


##### 返回说明
| 参数    | 说明         |
|---------|------------|
| status  | 0 \| -1    |
| message | 状态消息    |
| data    | 队伍列表    |



#### 创建队伍
```
  POST /team/create_team
```

##### 参数说明
| 参数                 | 说明          | 举例          |
|---------------------|---------------|-------------:|
| technology_stack    | 技术栈         |   VUE        |
| deadline_date       | 截止日         |   2018-08-22 |
| project_id          | 项目ID        |               |


##### 返回说明
| 参数    | 说明         |
|---------|------------|
| status  | 0 \| -1    |
| message | 状态消息    |
| data    | {}        |



#### 加入队伍
```
  POST /team/join_team
```

##### 参数说明
| 参数        | 说明          | 必须          |
|------------|---------------|-------------:|
| team_id    | 队伍ID         |   是        |


##### 返回说明
| 参数    | 说明         |
|---------|------------|
| status  | 0 \| -1    |
| message | 状态消息    |
| data    | {}         |


#### 获取队伍
```
  POST /team/get_team
```

##### 参数说明
| 参数        | 说明          | 必须          |
|------------|---------------|-------------:|
| team_id    | 队伍ID         |   是        |


##### 返回说明
| 参数    | 说明                     |
|---------|-------------------------|
| status  | 0 \| -1                 |
| message | 状态消息                 |
| data    | 队伍信息与成员列表         |

#### 首页队伍推荐
```
  POST /team/recommend
```

##### 参数说明
| 参数        | 说明          | 必须          |
|------------|---------------|-------------:|
| 无    |          |           |


##### 返回说明
| 参数    | 说明                     |
|---------|-------------------------|
| status  | 0 \| -1                 |
| message | 状态消息                 |
| data    | 推荐队伍         |



[返回顶部](#bangdna)
