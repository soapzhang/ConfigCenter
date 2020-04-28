<br>
<p align="center">
    <img src="https://images.gitee.com/uploads/images/2019/0926/165506_ab9d375b_718145.png" width="300" height="300">
    <h3 align="center">Bridge</h3>
    <h3 align="center">配置中心 · 管理系统</h3>
    <p align="center">全量/灰度下发、实例配置项订阅的实时监控、发布回滚、操作日志、配置项监听、权限控制、多环境切换</p>
        <p align="center"><a href="http://doc.u2open.com">-- 点我进入主页 --</a></p>
    <p align="center"><a href="http://bridge.u2open.com">控制台演示地址（ 账号：test  密码：test ）</a></p>
    <a align="center" href="https://www.apache.org/licenses/LICENSE-2.0">
        <img src="https://img.shields.io/badge/License-Apache--2.0-brightgreen.svg" >
    </a>
</p>


### 开发背景
>  本项目主要是为了解决分布式系统中配置杂乱，无法集中管理，和频繁修改配置项后需要重新发布服务的问题。目前提供了“全量/灰度发布、客户端实例配置项订阅情况实时监控、发布回滚、操作历史日志、配置项监听、权限控制、多环境切换（开发、测试、预发、生产）"等功能。

### 主要功能

* 秒级下发配置项，客户端系统动态更新配置项无需重新发布
* 完整的权限体系
  * 账号分为三种角色，权限依次递减：**系统管理员**、**团队管理员**、**普通用户**
  * **系统管理员**可以操作所有团队下的系统和账号
  * **团队管理员**只可以操作自己团队下的系统和团队成员的账号
  * **普通用户**只可以操作自己负责的系统
* 记录配置文件操作历史，提供版本回退，减少误操作带来的影响
* 实时监控客户端实例对配置项订阅的情况
* 提供日志监控，实时掌握客户端的配置项使用情况，让下发、客户端发布变的透明
* 只需部署一台服务即可，支持多环境切换，不需要dev、test、stable、online各部署一台
* 解决在下发配置项，用户正在读取配置项时发生的“不一致性读”的问题
* **兼容原生的Spring的@Value注解，同时支持 **注解** 和 **XML占位符** 获取配置项**
* **对Spring原生的XML占位符${}和@Value注解以及springboot的@ConfigurationProperties注解修饰的配置项提供托管，真正实现项目配置文件全托管**
* 对指定的配置项或全部的配置提供监听，方便业务扩展
* 代码侵入性低，集成、部署简单
* 友好的控制台操作页面


### 如何使用

* 可以参考demo项目[bridge-samples](https://gitee.com/Jay_git/bridge-samples)它提供了SpringBoot集成与普通Spring项目集成使用的相关示例。欢迎star  ：）。
* 或者可以通过阅读文档了解更多[点我跳转至文档](http://doc.u2open.com)。

### 使用到的一些技术

* Springboot、Mybatis、Maven
* Zookeeper
* Mysql
* Vue.js + Element + iView

### 操作界面展示

* #### 工作台<br><br>![工作台页面](https://images.gitee.com/uploads/images/2019/0912/121210_977443f1_718145.jpeg "工作台.jpg")

* #### 账号管理<br><br>![账号管理](https://images.gitee.com/uploads/images/2019/0912/165716_eaf8dd7e_718145.jpeg "账号管理.jpg")

* #### 团队管理<br><br>![团队管理](https://images.gitee.com/uploads/images/2019/0912/121401_d2123c75_718145.jpeg "团队管理.jpg")

* #### 系统管理<br><br>![系统管理](https://images.gitee.com/uploads/images/2019/0912/121424_70fca057_718145.jpeg "系统管理.jpg")

* #### 配置项管理<br><br>![配置项管理](https://images.gitee.com/uploads/images/2020/0204/170728_039d100a_718145.jpeg "20200204170607.jpg")

* #### 操作历史<br><br>![操作历史](https://images.gitee.com/uploads/images/2019/0912/165737_a0729f34_718145.jpeg "操作历史.jpg")

* #### Zookeeper<br><br>![Zookeeper](https://images.gitee.com/uploads/images/2019/1128/122802_40e3a02e_718145.jpeg "pic-zookeeper.jpg")

* #### 系统日志<br><br>![系统日志](https://images.gitee.com/uploads/images/2019/0912/121554_d1c2793f_718145.jpeg "系统日志.jpg")

### 框架原理

* 推拉模型
![推拉模型](https://images.gitee.com/uploads/images/2020/0221/172017_6a19aa71_718145.png "bridge-yl-zh-cn.png")

* 配置项加载策略
![配置项加载策略](https://images.gitee.com/uploads/images/2020/0221/181826_1e8042ee_718145.png "1112.png")


### 项目更新日志

##### 2020-03-05 v2.0.1

* 新增功能：批量同步配置项到其他环境
* 新增优化：当某个配置项被服务订阅的时候，为它提供特殊效果的展示
* 框架升级：升级Element UI 至2.13.0
* 新增优化：调整客户端在备份配置项，下载到本地时，对配置项进行排序

##### 2020-02-04 v2.0.0

* 新增功能配置项批量删除
* 优化配置项列表页面的搜索功能，优化其他页面显示、一些搜索结果展示的优化
* 在系统管理页面新增按钮"前往"
* 本次功能点优化，不升级版本

##### 2019-11-22 v2.0.0
* 新增功能配置项上传、配置项导出、一键下发
* 支持@Value注解和${}托管到配置中心
* 调整普通Spring项目的集成方式，提供XML集成和注解集成2种方式
* 调整SpringBoot的集成方式
* 新增支持在控制台不可用的时候切换为本地模式
* 新增支持在控制台恢复可用的时候，客户端自动重连
* 调整xsd文件远程路径
* 新增动态展示客户端订阅配置项的情况
* 调整注解集成的方式，不再支持"读一致性"，建议用户必要时利用ThreadLocal做线程隔离保证"读一致性"
* 修复因cglib动态代理或jdk动态代理产生的对象无法通过反射获取属性的问题
* 调整@BridgeValue注解，提供autoRefresh选项，默认为不需要动态变更配置项
* 将原来的XML占位符 **@Bridge{xxx.xx}** 调整为 **$>>T{xxx.xx}** 和 **$>>F{xxx.xx}**，其中前者为需要动态刷新
配置项，后者为不需要动态刷新， **$>>{xxx.xx}** 默认为不需要动态更新配置项。其中 **xxx.xx** 为配置项的key

##### 2019-09-11 v1.0.2
* 新增模块「系统日志」，该模块提供客户端的启动和下发以及一致性检测的实时日志，以及所有的历史日志记录。方便用户提高日志了解系统内部的配置项情况，也方便问题的定位
* 修复了在极端的显示情况下，页面部分组件显示不正常的问题
* 优化了下发、以及监听到配置项发生变更后的响应逻辑
* 修复了在客户端进行一致性检查的时候以使用的配置项为准而不是以缓存仓库的配置项为准。调整后客户端将不会注册未使用的配置项
* 调整了页面的风格

##### 2019-08-23 v1.0.1
* 通过调整webpack打包方式，优化前端访问页面的速度，由原来的1.5min提升至600ms左右
* 优化了一些代码，使其更符合阿里规约
* 更改项目logo

##### 2019-03-19 v1.0.0
* 项目开发、测试完成


### 交流讨论 QQ群

![QQ群](https://images.gitee.com/uploads/images/2019/1128/122940_c3b8f0ed_718145.jpeg "qq-1.jpg")

   

