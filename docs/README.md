<!--
 * @Author: Devin Wang
 * @Date: 2019-08-20 10:50:58
 * @LastEditors: Devin Wang
 * @LastEditTime: 2019-10-21 11:21:14
 -->
## Welcome

## 注意点
```
1. WeChat DevTool 里面的调试面板是在模拟器调试的时候用的，真机调试有单独的调试工具


```

# 知识点
版本控制：开发板，体验版，审核版，线上版（特定某个人提交体验版）

## 尺寸单位
rpx（responsive pixel）: 可以根据屏幕宽度进行自适应。规定屏幕宽为750rpx。如在 iPhone6 上，屏幕宽度为375px，共有750个物理像素，则750rpx = 375px = 750物理像素，1rpx = 0.5px = 1物理像素。
```
设备	            rpx换算px (屏幕宽度/750)	   px换算rpx (750/屏幕宽度)
iPhone5	        1rpx = 0.42px	            1px = 2.34rpx
iPhone6	        1rpx = 0.5px	            1px = 2rpx
iPhone6 Plus	1rpx = 0.552px	            1px = 1.81rpx
```
建议： 开发微信小程序时设计师可以用 iPhone6 作为视觉稿的标准。
注意： 在较小的屏幕上不可避免的会有一些毛刺，请在开发时尽量避免这种情况。

## 样式
style：静态的样式统一写到 class 中。style 接收动态的样式，在运行时会进行解析，请尽量避免将静态的样式写进 style 中，以免影响渲染速度。

## API
各个API都有版本，技术调研的时候要注意，说明从哪个版本开始支持，不同版本有相应的设备占有率

很多行为都有时间限制，技术评估和使用的时候要注意，如：
即使不配置为 homePage ，小程序如果退出过久（当前默认一天时间，可以使用退出状态来调整），下次冷启动时也将不再遵循 restartStrategy 的配置，而是直接从首页冷启动。

## 分包
打包原则

1. 声明 subpackages 后，将按 subpackages 配置路径进行打包，subpackages 配置路径外的目录将被打包到 app（主包） 中
2. app（主包）也可以有自己的 pages（即最外层的 pages 字段）
3. subpackage 的根目录不能是另外一个 subpackage 内的子目录
4. tabBar 页面必须在 app（主包）内

引用原则

1. packageA 无法 require packageB JS 文件，但可以 require app、自己 package 内的 JS 文件
2. packageA 无法 import packageB 的 template，但可以 require app、自己 package 内的 template
3. packageA 无法使用 packageB 的资源，但可以使用 app、自己 package 内的资源

## 云开发数据库
云开发提供了一个 JSON 数据库，顾名思义，数据库中的每条记录都是一个 JSON 格式的对象。一个数据库可以有多个集合（相当于关系型数据中的表），集合可看做一个 JSON 数组，数组中的每个对象就是一条记录，记录的格式是 JSON 对象。
```
关系型              文档型
表 table	    集合 collection
行 row	        记录 record / doc
列 column	    字段 field
```

## 云函数
云函数，更改后要上传才生效！！！！！！！！！！