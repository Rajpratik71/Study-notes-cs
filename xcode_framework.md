

#1-error

##reason?: compiled with older version of Swift language (2.0) than previous files (3.0) 
#solve: Build Setting / Swift Complier- Version
Use legacy Swift Language Version ---Yes


#2-error

##reason?:framework not found

#solve:
copy the abc.framework to current directory file

Build Setting /Search Path:

Framework Search Paths: /User/xxx/xxframework

### Q1 将生成的库放进去当前文件夹

### Q2 编译库，包括swift,object c 建议分开打库成framework
 注意：生成的库的object c头文件写进到库文件里面

### Q3 cocoapods
podfile.lock,podfile dirr err 
: No such file or directory
```
rm -rf all podfile 
pod init 
open podfile and import your dependency
pod install
pod setup
open xx.xcworkspace (not xxx.xcodeproj)
```

### Q4 
项目使用情况：
旧版本swift 会进行swift语言版本编译问题，设置Swift Complier --version : Yes
所有的代码，需要使用原来的代码风格，参考appdelegate.swift即可

新版本就不会

framewwork  同样会遇到这个问题


### Q5 
项目使用情况：
多模块同时进行使用，如何进行一次导入，其它的controller也可以使用


### 使用cocoapod 好处－1
swift 调用oc , 不需要头文件之类的东东

```swift
import SVProgressHUD

    SVProgressHUD.showInfoWithStatus("hello hud!")
    
```
### 使用cocoapod 好处－2
多库同时进行管理版本，具体问题c可参考Q3

### 使用cocoapod 好处－3





