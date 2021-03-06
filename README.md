### 该项目来自于[CarltonHere/auto-cpdaily](https://github.com/CarltonHere/auto-cpdaily)仓库，经过修改后适配了北部湾大学今日校园自动打卡。非常感谢该大佬，请小伙伴们去给他点一个STAR！

### 以下说明借用了部分该作者的原话。

### 📃免责声明

本项目为Python学习交流的开源非营利项目，仅作为程序员之间相互学习交流之用，使用需严格遵守开源许可协议。严禁用于商业用途，禁止使用本项目进行任何盈利活动。对一切非法使用所产生的后果，我们概不负责。本项目对您如有困扰请联系我们删除。

### 📗使用方法

此处只实例如何使用腾讯云函数部署，如需其他方法请移步原作者[CarltonHere/auto-cpdaily](https://github.com/CarltonHere/auto-cpdaily)仓库。

#### 📅示例 腾讯云函数平台
 - 下载此代码包，解压到本地文件夹。
 - 打开百度搜索[腾讯云函数](https://console.cloud.tencent.com/scf/index?rid=1)，注册认证后，进入控制台。
 - 点左边的函数服务，新建云函数，名称随意，运行环境选择`python3.6`，创建方式选择`自定义创建`
 - 在`高级配置`中配置`执行超时时间`100秒，在`触发器配置`中选择自定义创建，`触发周期`选择自定义触发，配置cron表达式
	
	```
	如需每日上午0点执行可使用该表达式
	0 0 0 * * * *
	如需每日上午8点30分执行可使用该表达式
	0 30 8 * * * *
	如需每日中午12点执行可使用该表达式
	0 0 12 * * * *
	```
	
 - 点击完成，不要关闭页面等待创建完成后，选择立即跳转
 - 点击`函数代码`选项卡，等待编辑器初始化完成	
 - 在编辑器左边的`src`目录下选择`config.yml`，配置你的用户签到信息，注意删除多余的示例并注意每行行首的缩进
 - 先填写自己的学号以及密码，密码就是你教务系统的密码
 - 然后[开通腾讯OCR服务](https://console.cloud.tencent.com/ocr/overview)，然后[申请腾讯云API密钥](https://console.cloud.tencent.com/cam/capi)，最后将API密钥配置到路径`config.yml`里的    `SecretId`以及`SecretKey`参数内
 - 最后，点击下方的`部署`即可完成部署(部署完成后，你可以点击`测试`按钮测试签到任务)

#### 🔐进阶使用

- 如需推送提醒服务，请在`config.yml`顶部的`notifyOption`参数中进行配置
- 建议使用QQ邮箱的SMTP的功能进行消息推送，此功能自行百度，实在不会再提交Issues
- 如需忽略必填题目，请在`form`下新增`ignore: True`字段

### 🔧常见问题

- 如果云函数报错`HTTP-418`请更换云函数其他地区节点
- 请注意`config.yml`中每行参数的缩进位置，不然会产生错误


### 📜许可证

本项目的源代码在MPL2.0协议下发布，同时附加以下条目：
* **非商业性使用** — 不得将此项目及其衍生的项目的源代码和二进制产品用于任何商业和盈利用途
