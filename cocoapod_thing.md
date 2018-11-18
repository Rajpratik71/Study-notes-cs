#ques : 
如何下载和安装CocoaPods? 
在本地安装好Ruby环境

OS X系统默认可以运行Ruby,运行sudo gem update --system 升级Ruby，

移除现有Ruby默认源

$ gem sources --remove https://rubygems.org/

//等有反应之后再敲入以下命令

$ gem sources -a https://ruby.taobao.org/

验证新源是否替换成功

$gem sources -l

#cocoapods
cocoapods

这时候,你再次在终端中运行:

$ sudo gem install cocoapods

苹果系统升级OS X EL Capitan 后安装改为:

$ sudo gem install -n /usr/local/bin cocoapods

等上一会,CocoaPods就可以在你本地下载并且安装好了,不再需要其他设置。

然后$ pod setup

等上一大会，Setting up CocoaPods master repo结束，就可以使用了。。。

使用CocoaPods

使用CocoPods和安装它一样简单,也是通过一两行命令就可以搞定。

小编在这里用两种使用场景来具体说明如何使用CocoaPods。

们可以尝试搜索一个第三方类库：

pod search AFNetworking

#pod libs
(cd命令)你项目所在目录,然后在当前目录下,利用vim创建Podfile,运行:

$ vim Podfile

然后在Podfile文件中输入以下文字:

platform :ios, '7.0'

pod "AFNetworking", "~> 2.0"

-------------------------------------

```
target 'MyApp' do
  pod 'AFNetworking', '~> 3.0'
  pod 'FBSDKCoreKit', '~> 4.9'
end
```

当前AFNetworking支持的iOS最高版本是iOS 7.0,要下载的AFNetworking版本是2.0。

关于Podfile文件编辑时，第三方库版本号的各种写法：

pod ‘AFNetworking’ //不显式指定依赖库版本，表示每次都获取最新版本
pod ‘AFNetworking’,‘2.0’ //只使用2.0版本
pod ‘AFNetworking’, ‘>2.0′ //使用高于2.0的版本
pod ‘AFNetworking’, ‘>=2.0′ //使用大于或等于2.0的版本
pod ‘AFNetworking’, ‘<2.0′ //使用小于2.0的版本
pod ‘AFNetworking’, ‘<=2.0′ //使用小于或等于2.0的版本
pod ‘AFNetworking’, ‘~>0.1.2′ //使用大于等于0.1.2但小于0.2的版本，相当于>=0.1.2并且<0.2.0
pod ‘AFNetworking’, ‘~>0.1′ //使用大于等于0.1但小于1.0的版本
pod ‘AFNetworking’, ‘~>0′ //高于0的版本，写这个限制和什么都不写是一个效果，都表示使用最新版本 
然后保存退出。vim环境下,保存退出命令是:

:wq

小提示：（终端vim/vi文件 按 i 可编辑 ，esc 退出编辑，：wq 或者ZZ 可保存退出）

这时候,你会发现你的项目目录中,出现一个名字为Podfile的文件,

而且文件内容就是你刚刚输入的内容。注意,Podfile文件应该和你

的工程文件.xcodeproj在同一个目录下。

这时候,你就可以利用CocoPods下载AFNetworking类库了。还是

在终端中的当前项目目录下,运行以下命令:

$ pod install


(如果在pod install、或者pod update时，不想升级specs库，可以增加忽略参数

pod install --no-repo-update

pod update --no-repo-update)

因为是在你的项目中导入AFNetworking,这就是为什么这个命令需

要你进入你的项目所在目录中运行。

运行上述命令之后,小编的终端出现以下信息:

[i] From now on use ‘cocoaPodsDemo.xcworkspace’

注意最后一句话,意思是:以后打开项目就用CocoaPodsDemo.xcworkspace打开,而不是之前的.xcodeproj文件。

##注意
```
注意,这里有个小问题,如果刚刚你不是输入$ pod update,而是输入$ pod install,会发现类库导入不成功,并且终端出现下面

提示:

[!] Required version (UAAppReviewManager (from `../`)) notfound for `UAAppReviewManager`.

Available versions: 0.1.6这里的意思大概是Podfile文件过期,类库有升级,但是Podfile没有

更改。$ pod install只会按照Podfile的要求来请求类库,如果类

库版本号有变化,那么将获取失败。但是$ pod update会更新所有

的类库,获取最新版本的类库。而且你会发现,如果用了$ pod

update,再用$ pod install就成功了。

那你也许会问,什么时候用$ pod install,什么时候用$ pod

update呢,我又不知道类库有没有新版本。好吧,那你每次直接用$ pod update算了。或者先用$ pod install,如果不行,再用$

pod update。

终端 cocoapods 下载bug调试：

错误1：

Error fetching http://ruby.taobao.org/:

bad response Not Found 404 (http://ruby.taobao.org/specs.4.8.gz)

解决方案：把安装流程中 $gem sources -a http://ruby.taobao.org/---改为----> $gem sources -a https://ruby.taobao.org/

错误2：

ERROR: While executing gem ... (Errno::EPERM)

Operation not permitted - /usr/bin/pod

解决方案：苹果系统升级OS X EL Capitan后会出现的插件错误，将安装流程 4.安装CocoaPods 的 (1)sudo gem install cocoapods ——>改为sudo gem install -n /usr/local/bin cocoapods

错误3：

[!] Unable to satisfy the following requirements: - `AVOSCloud (~> 3.1.6.3)` required by `Podfile`

Specs satisfying the `AVOSCloud (~> 3.1.6.3)` dependency were found, but they required a higher minimum deployment target.

解决方案：安装流程：Podfile文件 中 platform:ios,‘6.0’后边的 6.0 是平台版本号 ，一定要加上

其他解决不了的

解决方案：

$ sudo rm -rf ~/.cocoapods/repos/master

$ pod setup

```

from :
http://www.th7.cn/Program/Ruby/201606/869773.shtml


# 强迫使用，暴力解决

```
$ mkdir -p $HOME/Software/ruby
$ export GEM_HOME=$HOME/Software/ruby
$ gem install cocoapods
[...]
1 gem installed
$ export PATH=$PATH:$HOME/Software/ruby/bin
$ pod --version
0.37.2
```
 


