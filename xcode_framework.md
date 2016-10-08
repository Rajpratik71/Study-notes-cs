

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

01 将生成的库放进去当前文件夹

Q2 编译库，包括swift,object c 建议分开打库成framework
 注意：生成的库的object c头文件写进到库文件里面

03 cocoapods

04 
