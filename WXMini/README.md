
## 1. 注册小程序

注册小程序请单击 [微信公众平台](https://mp.weixin.qq.com) ，完成注册后，在小程序管理页面的【开发】>【基本配置】中记录下小程序 AppID 供后面使用。

>注意：
>必须以**非个人主体**类型进行注册，否则无法开通 &lt;live-pusher&gt; 和 &lt;live-player&gt; 这两个标签。

## 2. 开通标签使用权限
出于政策和合规的考虑，微信暂时没有放开所有小程序对 [&lt;live-pusher&gt;](https://developers.weixin.qq.com/miniprogram/dev/component/live-pusher.html) 和 [&lt;live-player&gt;](https://developers.weixin.qq.com/miniprogram/dev/component/live-player.html) 标签的支持：
- 目前支持这两个标签的类目如下表格所示（只有非个人主体才有以下类目）：

| 主类目 | 子类目  |小程序内容场景|
|-------|----------|----------|
| 社交| 直播 |涉及娱乐性质，如明星直播、生活趣事直播、宠物直播等。选择该类目后首次提交代码审核，需经当地互联网主管机关审核确认，预计审核时长7天左右|
| 教育| 在线视频课程 |网课、在线培训、讲座等教育类直播|
| 医疗| 互联网医院，公立医院 |问诊、大型健康讲座等直播|
| 金融| 银行、信托、基金、证券/期货、证券、期货投资咨询、保险、征信业务、新三板信息服务平台、股票信息服务平台（港股/美股）、消费金融 |金融产品视频客服理赔、金融产品推广直播等|
|汽车|	汽车预售服务|	汽车预售、推广直播|
|政府主体帐号|	-	|政府相关工作推广直播、领导讲话直播等|
|工具	|视频客服	|不涉及以上几类内容的一对一视频客服服务，如企业售后一对一视频服务等|

- 符合类目要求的小程序，需要在小程序管理后台的【开发】>【接口设置】中自助开通推拉流标签的使用权限，如下图所示：
![](https://main.qcloudimg.com/raw/cabb6b98121754b7956bd02029714616.jpg)

>说明：如果以上设置都正确，但小程序依然不能正常工作，可能是微信内部的缓存没更新，请删除小程序并重启微信后，再进行尝试。

## 3. 开通云直播服务

**3.1 申请开通视频直播服务**
进入 [云直播管理控制台](https://console.cloud.tencent.com/live) 开通云直播服务。

**3.2 添加自有域名**
- 使用云直播服务至少需要2个域名，一个作为推流域名，一个作为播放域名，推流和播放不能使用相同的域名。
- 如果您没有域名，可以登录腾讯云官网，选择【云产品】>【域名与网站】>[【域名注册】](https://buy.cloud.tencent.com/domain?from=console) 来注册购买域名。您也可以通过其他域名服务商购买域名。
- 如果您已经购买了域名，根据国家工信部规定，域名必须进行备案，您可以在腾讯云的 [域名备案](https://cloud.tencent.com/product/ba) 中进行备案。您也可以在其他域名服务商那进行备案。备案往往需要几个工作日，建议您提前进行备案。
- 如果您的域名已经备案，则需要通过云直播控制台的【域名管理】>【添加域名】来添加您的推流域名和播放域名。

例如，您的推流域名为`push.livetest.myqcloud.com`，播放域名为`play.livetest.myqcloud.com`。添加成功后，可以在域名列表中看到您的域名。
![](https://main.qcloudimg.com/raw/186a2fe7c60eeb156f4f6ef87d5e10f2.jpg)
域名列表里面有一个`数字.livepush.myqcloud.com`的推流域名，这个是我们为您提供的测试域名，可以通过这个域名进行推流测试，但强烈不建议您在正式的业务中使用这个域名作为推流域名。

**3.3 域名 CNAME**
在您添加域名成功后，您的域名需要指向腾讯云直播的云服务集群。根据域名列表中的提示，您需要在您注册的域名服务商处将域名解析地址 CNAME 到云直播控制台的域名列表中对应域名的 CNAME 地址，CNAME 添加方法请参见 [CNAME 配置](https://cloud.tencent.com/document/product/267/30560)。
>注意：
> CNAME 成功后通常需要一定时间生效，CNAME 不成功是无法使用腾讯云直播服务的。

![](https://main.qcloudimg.com/raw/47d372c5d0ac124648cb8c275b801cb3.png)
如果 CNAME 操作后，检测始终不成功，建议您向您的域名注册服务商咨询。

## 4. 开通即时通信 IM 服务

进入 [即时通信 IM 管理控制台](https://console.cloud.tencent.com/avc)，如果还没有开通服务，单击【直接开通云通信】即可。如果是新认证的腾讯云账号，则即时通信 IM 的应用列表是空的，如下图：
![](https://main.qcloudimg.com/raw/56bb27d09e17784075a5e21a2eb2a2a1/im_empty.png)

## 5. 开通房间管理服务

**5.1 创建应用**
进入云直播控制台的【直播SDK】>[【应用管理】](https://console.cloud.tencent.com/live/license/appmanage)页面，单击【创建应用】填写应用信息。完成创建后，您将会在应用列表中看到您创建的应用，记录其 SDKAppID 信息，如下图所示：
![](https://main.qcloudimg.com/raw/0f88e296acf31ce322667bf0b191ab58.jpg)
>说明：该操作的目的是创建一个即时通信 IM 应用，并将当前云直播账号和该即时通信 IM 应用绑定起来。即时通信 IM 应用能为小直播 App 提供聊天室和连麦互动的能力。

**5.2 查看并拷贝加密密钥**
如果在步骤5.1中已经成功创建了应用，就会看到【管理】入口，单击进入“应用管理”页卡，并单击【显示密钥】，即可获取加密密钥。
![](https://main.qcloudimg.com/raw/bbae69142bf9c616d3d0011f39a13e47.jpg)

**5.3 购买流量资源包**

小程序源码中的 &lt;mlvb-live-room&gt; 组件为开发者提供了腾讯云直播连麦的能力，具有低卡顿、低延时和易接入等特点。如果您希望用它来快速实现直播连麦应用，那么您需要购买直播流量资源包、移动直播 SDK License、移动直播连麦资源包和即时通信 IM 套餐包。详细计费说明请查看 [云直播计费说明](https://cloud.tencent.com/document/product/267/34174) 和 [即时通信 IM 定价](https://cloud.tencent.com/product/im/pricing)。

## 6. 下载 Demo 源码

访问 [Github](https://github.com/tencentyun/MLVBSDK/tree/master/WXMini)，获取小程序 Demo 源码。

## 7. 粘贴密钥到 Demo 工程的指定文件中


我们在各个平台的 Demo 的源码工程中都提供了一个叫做 “GenerateTestUserSig” 的文件，它可以通过 HMAC-SHA256 算法本地计算出 UserSig，用于快速跑通 Demo。

| 语言版本 |  适用平台 | GenerateTestUserSig 的源码位置 |
|:---------:|:---------:|:---------:|
| Objective-C | iOS  | [Github](https://github.com/tencentyun/MLVBSDK/tree/master/iOS/Demo/TXLiteAVDemo/LVB/LiveRoom/Debug/GenerateTestUserSig.h)|
| Java | Android  | [Github](https://github.com/tencentyun/MLVBSDK/tree/master/Android/Demo/app/src/main/java/com/tencent/liteav/demo/lvb/liveroom/debug/GenerateTestUserSig.java) |
| Javascript | 小程序 | [Github](https://github.com/tencentyun/MLVBSDK/tree/master/WXMini/pages/mlvb-live-room-demo/debug/GenerateTestUserSig.js)|

您只需要将第5步中获得的 SDKAppID 和加密密钥拷贝到文件中的指定位置即可，如下所示：
![](https://main.qcloudimg.com/raw/b4d8f63afa0f998c7da291b31f441a40.png)


>注意：
>安全警告：本地计算 UserSig 的做法虽然能够工作，但仅适合于调试 Demo 的场景，不适用于线上产品。
> 
> 这是因为客户端代码中的 SECRETKEY 很容易被反编译逆向破解，尤其是 Web 端的代码被破解的难度几乎为零。一旦您的密钥泄露，攻击者就可以计算出正确的 UserSig 来盗用您的腾讯云流量。
> 
> [安全方案](https://cloud.tencent.com/document/product/454/14548#Server)：将 UserSig 的计算代码和加密密钥放在您的业务服务器上，然后由 App 按需向您的服务器获取实时算出的 UserSig。由于攻破服务器的成本要远高于破解客户端 App，所以服务器计算的方案能够更好地保护您的加密密钥。


## 8. 编译运行

8.1 打开 [微信开发者工具](https://mp.weixin.qq.com/debug/wxadoc/dev/devtools/download.html) 后，选择【小程序】菜单栏，然后单击新建图标，选择【导入项目】。

8.2 输入小程序 AppID（注意：不是上面的 SDKAppID），单击【导入】：
![](https://main.qcloudimg.com/raw/41af7d9efc1b25ff2435d41a5e799edd.jpg)

8.3 单击【预览】，生成二维码，通过手机微信扫码二维码即可进入小程序。

>注意：
> 
>- 小程序 &lt;live-player&gt; 和 &lt;live-pusher&gt; 标签需要在手机微信上才能使用，微信开发者工具上无法使用。
>- 为了小程序能够使用腾讯云房间管理服务，您需要在手机微信上开启调试功能：手机微信扫码二维码后，单击右上角【...】>【打开调试】。
![](https://main.qcloudimg.com/raw/3241357d57baa4c3eec40bb5a791cd83.jpg)

## 9. 发布上线
关于小程序的发布流程，请参见 [发布上线](https://developers.weixin.qq.com/miniprogram/dev/framework/quickstart/release.html#%E5%8F%91%E5%B8%83%E4%B8%8A%E7%BA%BF)。

在小程序发布上线前，请务必要在微信小程序控制台的【开发】>【开发设置】>【服务器域名】中配置 “request 合法域名”，否则将无法使用腾讯云的房间管理服务。需要配置的域名包括：

| 域名 | 说明 | 
|:-------:|---------|
| https://liveroom.qcloud.com | MLVB 移动直播房间管理服务域名 | 
| https://webim.tim.qq.com | IM 域名 | 
| https://pic.tim.qq.com | IM 图片上传域名 |

![](https://main.qcloudimg.com/raw/1c55a83ce13159c4ef296511bff83dc5.jpg)

## 常见问题
### 1. 开发和运行环境要求
- 微信 App iOS 最低版本要求：6.5.21。
- 微信 App Android 最低版本要求：6.5.19。
- 小程序基础库最低版本要求：1.7.0。
- 由于微信开发者工具不支持原生组件（即 &lt;live-pusher&gt; 和 &lt;live-player&gt; 标签），需要在真机上进行运行体验。

### 2. 调试时为什么要开启调试模式？
开启调试可以跳过把这些域名加入小程序白名单的工作，否则可能会遇到登录失败，通话无法连接的问题。

