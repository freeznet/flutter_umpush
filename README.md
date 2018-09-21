# flutter_umpush

友盟推送、友盟统计的 flutter 插件。
这个插件是从我们公司的 cordova 插件分离出来的，集成到 flutter 之后，使用公司的帐号测试可使用，安卓和 ios 都没问题。
后来，担心泄漏公司帐号，我又重新建了一个项目。目前 flutter clean && flutter build apk && flutter build ios 都没问题。只是没有使用真实帐号测试过。

目前推送平台太多了，有中间商平台的，比如百度、友盟、极光、信鸽，听说网易也在搞，感觉只要是个互联网公司都在做。这些产品已经渗透这么深了，到处都是他们的产品，想搞统一推送，太难了，难道又要程序员改程序么，而且连同服务端也一块改

考虑到这些中间商平台的推送是不能解决离线唤醒问题的，某些手机厂商就开始自己搞推送，华为、小米、魅族目前已经稳定上架了。

所以，现在的推送市场，其实就是各自为政，群魔乱舞，给程序员制造 N 多的麻烦。

手机厂商有自己的利益，这是流量入口，不可能放弃的。

中间商为了支持离线唤醒，也增加了几个手机厂商的支持，目前大多数的中间商平台都支持华为、小米、魅族。

那个 oppo 或 vivoo，目前还是测试版本(https://push.oppo.com/)，等 oppo 上线后，我估计各大中间商平台也会支持，到时我们在他们的配置一下就可以了。

所以呢，结论是啥，咱们作为程序员，肯定要选择靠谱的东西呀。

1. 友盟：已经卖个阿里了，长期维护不成问题，反正我提交工单，他们也很快回馈，在线客服也响应及时，还是值得信赖的；
2. 信鸽：腾讯的，很牛逼，绝对死不了，奈何我一开始就选择友盟了，所以你们要是感兴趣，可以封装一个 flutter 出来。腾讯 bugly+升级，还是不错的，我配合友盟一起用；
3. 百度：我感觉百度不怎么靠谱了，最近被莆田系、自动驾驶分散他们很多注意力；
4. 极光：我没用过，听说好用，你们自己评估；
5. 厂商专用通道：小米、华为、魅族。其实在友盟后台配置一下就可以使用了，不建议直接集成厂商的通道，要长远考虑，万一手机厂商没了呢

# 包括的功能

1. 友盟统计：已经集成进来了，但是各种友盟的 api 没封装，我们公司之前是 cordova 的项目，只要求统计到设备信息就可以了，没有“埋点的需求”；

2. 友盟推送：支持小米、华为、魅族的离线唤醒功能，亲测可用。从友盟后台推送的时候，需要勾选“MIUI、EMUI、Flyme 系统设备离线转为系统下发”，填写打开指定页面是：com.github.flutterumpush.UmengOtherPushActivity，100 个放心，本人反复测试过，没问题的。

3. 由于我们之前是基于 cordova 的项目，不需要 tags，我们只需要根据推送的 url 跳转到指定的界面而已，所有很多功能我没封装。

# 安卓平台需要注意一下

1. so 文件只能使用 armeabi-v7a
   ndk {
   moduleName "app"
   //设置支持的 SO 库架构
   abiFilters 'armeabi-v7a'//,'armeabi','arm64-v8a'
   }
2. 仿照 example/android/app/AndroidManifest.xml，把友盟帐号填写上去；

# ios 平台

1. 工程需要勾中 Remote notification 和 Push Notifications，这样才能支持；
2. 友盟推送需要在 adhoc 或 Distribution 环境下才可以收到推送；

## Getting Started

For help getting started with Flutter, view our online
[documentation](https://flutter.io/).

For help on editing plugin code, view the [documentation](https://flutter.io/developing-packages/#edit-plugin-package).
