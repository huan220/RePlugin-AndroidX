# replugin-androidx
本Repo的目标是维护一个支持AndroidX的[Qihoo360 RePlugin](https://github.com/Qihoo360/RePlugin)框架分支，欢迎测试&提issue&提PR；

+ Q：为什么不在RePlugin官方提交PR？
+ A：首先，Support库和AndroidX是无法混用的，在Replugin官方上同时兼容暂时没有把握，需要的时间也太多，而很多项目迁移AndroidX已经进行或者马上会进行；另外，Replugin已经大半年没有更新，issue也无官方人员回应，PR提交上去何时能接受是个未知数。但是RePlugin已经是一个很成熟稳定的框架，经我测试切换AndroidX后的宿主和插件，在Android 10上运行也没有问题。

+ Q：如果有一天RePlugin官方复活并支持AndroidX了呢？
+ A：那当然是回归官方了。

## 当前版本0.1.0
支持的特性：宿主和插件都使用AndroidX的情况下，能顺利调起插件Activity，经测试满足几乎所有replugin已有功能。主要修改点：
1. 修改replugin-plugin-gradle中ManifestAPI，使其能够在高版本gradle api下成功获取对应manifest文件
2. 修改replugin-plugin-gradle中LoaderActivityInjector，使其能够匹配androidx下的FragmentAcvitiy和AppCompatActivity，进行替换
### 0.1.0版本接入replugin框架的方法
1. 宿主部分，按照RePlugin官方文档进行接入引入host-gradle和host-library，然后正常进行Androidx改造，需要注意的是要在app的build.gralde添加依赖:  implementation 'androidx.legacy:legacy-support-v4:1.0.0’
2. 插件部分，plugin-library仍然引用官方包，只需要参照当前sample引用本repo的plugin-gradle并apply即可；
### 0.1.1版本计划（TODO）
1. 完善sampleplugin测试各项功能兼容程度；
2. 提交plugin-gradle到远程maven仓库方便使用；