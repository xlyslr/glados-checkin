# glados-checkin
![glados-checkin](https://github.com/hbstarjason/glados-checkin/workflows/glados-checkin/badge.svg)

#### 注册地址：

1、打开 https://github.com/glados-network/GLaDOS ，找到[<u>***Register***</u>]，打开链接，填写邮箱进行登录。

2、输入激活码`4IUEE-RV2OW-8F8Q1-L5WVO`，进行激活，获得3天试用。

3、每天手动进行checkin一次，能增加一天。



#### 脚本功能：

1、通过Github Action自动定时运行[checkin.py](https://github.com/hbstarjason/glados-checkin/blob/master/checkin.py)脚本。

2、通过cookies自动登录（[https://glados.rocks/console/checkin](https://glados.rocks/console/checkin))，脚本会自动进行checkin。

3、然后通过“Server酱”（[http://sc.ftqq.com/3.version](http://sc.ftqq.com/3.version))，自动发通知到微信上。



#### 食用姿势：

1. 先“Fork”本仓库。（不需要修改任何文件！）

2. 注册GLaDOS，方法见上。

3. 登录GLaDOS后获取cookies。（简单获取方法：浏览器快捷键F12，打开调试窗口，点击“network”获取）获取方法：

+ 首先使用 Chrome 浏览器登录 GLaDOS
+ 然后打开开发者工具, `win` 系统 快捷键 `F12` ，`mac` 快捷键 `option + command + i`
+ 打开开发者工具中的 `Network` 选项卡，刷新页面，然后选第一个 `console`，然后找到右侧的 `Cookie` 字段，复制出来。

如图操作：

![](https://cdn.jsdelivr.net/gh/yangchuansheng/imghosting/img/20200802090832.png)

4. 在自己的仓库“Settings”里创建3个“Secrets”，分别是：（不开启通知，只需要创建一个COOKIE即可）

   - COOKIE（**必填**）
   - SERVE（server酱开关，默认是off，填on的话，会同时开启cookie失效通知和签到成功通知）
   - SCKEY（填写server酱sckey，不开启server酱则不用填）

5. 以上设置完毕后，每天下午3点会自动触发，并会执行自动checkin，如果开启server酱，会自动发通知到微信上。如果想调整执行时间，可以修改[checkin.yml](.github/workflows/checkin.yml)，如下：
   ```yaml
   on:
     push:
       branches: [ master ]
     pull_request:
       branches: [ master ]
     schedule:
     # 修改cron表达式，注意是按UTC时间执行的。比如下面表示每天7点执行，实际是东八区的15点执行
       - cron:  0 7 * * * 
   ...
   ```

6. **如果以上都不会的话，注册GLaDOS后，每天勤奋点记得登录后手动进行checkin即可。**

   [*<u>如果是Edu邮箱，可免费升级为360天。</u>*]
