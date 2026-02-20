# 登录

## 登录方式

Pixiv-MultiPlatform提供了两种登录方式：

- [使用嵌入式浏览器登录](#使用嵌入式浏览器登录)
- [使用会话token登录(自1.6.0起)](#使用登录token登录)



## 使用嵌入式浏览器登录

:::warning

为保证软件在各个平台上的UI逻辑统一性，我们使用了嵌入式浏览器。

在**v1.8.4 前**，桌面端首次使用软件时需要初始化嵌入式浏览器，它会下载**大约400MB**的浏览器内核并解压缩。
自**v1.8.4 起**，桌面端已移除 `kcef` 依赖，首次使用嵌入式浏览器时将**不再需要下载**约300MB的Chromium内核。

而在安卓端则可以直接登录。

:::

### 1. 登录前的准备

- 魔法上网工具。因为Pixiv使用oauth进行登录，而网页中存在的验证码使得模拟调用登录接口的方法不现实，因此只能通过魔法上网的方式打开嵌入式浏览器并抓取登录token。

  ::: tip

  登录及后续的访问可以不用魔法上网，我们有对应的措施来绕过不可抗力造成的封锁。
  :::

- 一个Pixiv账号，若没有的话请[点击此链接](https://accounts.pixiv.net/signup)进行注册。

### 2. 登录步骤

1. 在登录向导中点击`以嵌入式浏览器登录`

   ![image-20250208110605818](./login.assets/image-20250208110605818.png)

2. 等待浏览器加载并弹出pixiv登录网页。（如果您使用v1.8.4，则这个步骤会很快。如果卡在了这个页面，请携带日志前往Issue页面。）

   ![image-20250208110709549](./login.assets/image-20250208110709549.png)

3. 输入账号密码后，点击`Login In`。如果登录成功，则程序会弹出下面的提示后三秒，进入主页面

   ![image-20250208110811007](./login.assets/image-20250208110811007.png)

### 3. 登录的常见问题

#### 3.1 - 无法使用谷歌账号登录

谷歌在2023年9月禁止了在嵌入式浏览器中进行登录的途径。针对此种情况请使用账号密码的方式进行登录。

#### 3.2 - 白屏

请检查魔法上网软件是否成功开启。

#### 3.3 - 无法初始化嵌入式浏览器(自V1.6.4起)

目前仅出现了[一例](https://github.com/magic-cucumber/Pixiv-MultiPlatform/issues/16)无法初始化浏览器内核的情况。而在最新版本中则会弹出如下的提示：

![image-20250307230117872](./login.assets/image-20250307230117872.png)

如果您也出现了这个问题，请按如下步骤进行排查：

1. 是否开启防火墙。
   如有开启，请关闭。
   或者放行`Pixiv-MultiPlatform`应用(具体如何放行请百度。)
2. 该url是否可以正常访问：[https://d2xrhe97vsfxuc.cloudfront.net/jbr_jcef-21.0.6-windows-x64-b895.97.tar.gz](https://d2xrhe97vsfxuc.cloudfront.net/jbr_jcef-21.0.6-windows-x64-b895.97.tar.gz)。
   如无法访问，请在魔法上网环境下初始化嵌入式浏览器。
3. 下载步骤`2`中提到的链接，然后点击`选择压缩包路径`按钮，选择您刚刚下载的`.tar.gz`文件后重试
4. 若仍然失败，请点击`点击此文本以查看详细信息`的链接，将对话框内的内容截图并打开[Issue页面](https://github.com/magic-cucumber/Pixiv-MultiPlatform/issues/new?template=功能故障.md)进行反馈。

#### 3.4 - 浏览器登录成功，解析用户配置时失败并返回到登录页面

这种情况一般发生在 **嵌入式浏览器的流量走系统代理，但是JVM的流量没走系统代理** 的情况下。

针对此种情况，我们推荐您使用`Mihomo`的**TUN**模式。



## 使用登录Token登录

::: tip

请检查您下载的Pixiv-MultiPlatform版本是否为`1.6.0`及以上。低于此版本则无法使用此类方式进行登录。

:::



### 1. 登录前的准备

- 如果您所在的地区无法访问Pixiv，则请回忆您是否在欢迎向导中启用了`SNI Bypass`功能。
  如果您开启了，则不需要魔法上网。若未开启，则需要开启魔法上网。
- 没有登录token但是登录了其他第三方pixiv客户端？请参考[我该如何导出登录Token](#3-我该如何导出登录token)



### 2. 登录步骤

1. 点击：`使用Token登录`

   ![image-20250208110605818](./login.assets/image-20250208110605818.png)

2. 在接下来的对话框中粘贴您的Token：

   ![image-20250208111530930](./login.assets/image-20250208111530930.png)

3. 如果您输入的Token正确。在等待一会后，会出现如下提示。三秒后进入主页面。

   ![image-20250208110811007](./login.assets/image-20250208110811007.png)

### 3. 我该如何导出登录Token？

1. 如果您要从Pixiv-MultiPlatform导出token，请前往程序设置，找到`导出登录会话`后点击：

   ![image-20250208111717114](./login.assets/image-20250208111717114.png)

2. 如果您使用其他客户端。在找到客户端导出的会话信息后，需要重点关注诸如`refresh_token`的字段，其中的值便是Pixiv-MultiPlatform需要的登录token。
   

   ::: danger 温馨提示

   请不要将网页端的Cookie直接粘入聊天框！PMF只接受移动端的登录凭证！

   > #### 什么是网页端的Cookie？
   >
   > 是指您在开发者工具里复制的类似这样的字符串：
   >
   > ```
   > p_ab_id=2; p_ab_id_2=8; p_ab_d_id=...; yuid_b=...; login_ever=yes; PHPSESSID=....; c_type=...; privacy_policy_notification=0; a_type=0; b_type=0; privacy_policy_agreement=7; __cf_bm=...; privacy_policy_agreement=7; cf_clearance=...
   > ```
   >
   > **尤其注意不要将PHPSESSID的内容填入对话框！**

   :::
