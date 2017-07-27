# 初始化过程
----------------
获取dist文件
调用Spreadhseet函数，设置配置参数
验证配置参数，修正配置参数
？？（性能消耗）把模板代码、项目基本结构放入第三方项目中
判断，新建表还是重新打开
	如果是重新打开，
		1. 发送根据ID发送请求到后台
		2. 同步等待返回数据
		3. 待数据返回后
		4. 把返回值进行分解，
		分别填充到sheet，cell，col，row对象中，否则，就是跳过这阶段
		？？（性能消耗）

递进，循环构建过程...
	构建element的parent结构
	绑定事件
	读取collections的model数量，创建element
	把element添加到parent里
结束循环

一次性将所有的elements渲染到页面中

-------------------------

绑定工具栏事件
??(远程调用时，没有工具栏，没必要绑定，没必要render模板)

给Spreadsheet构造函数绑定属性，第三方可以通过这个属性执行操作
（绑定的方法都是内部的方法，没有参数值过滤这个过程，这个是风险）

第三方的扩展功能dataSrouce，绑定spreadsheet构造函数的属性

绑定自定义事件函数到spreadsheet构造函数属性

第三方的扩展功能highLight，绑定spreadsheet构造函数的属性

```
SpreadSheet.Point = Point;
```
？？干什么用的