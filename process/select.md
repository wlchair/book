
## 过程

- 当前状态是否为备注编辑状态，
	- 如果是，就返回
- 当前是否点击部分是否是编辑框里
	- 如果是，就返回
- `selectBox = this.getCoordinateByMouseEvent(event);`根据鼠标事件，获取对应的cell model索引和model对象
- `getCoordinateByMouseEvent`
	- 根据鼠标位置，找到当前位置应该对应的像素值
	- 根据像素值，找到对应的model索引
	- 根据索引，找到model对应alias
	- 根据alias信息，到缓存中获取对应的cell信息
	- 如果缓存中已经存在单元格，就根据单元格的信息做对应的选中处理显示，如果缓存中不存在单元格，之前的行列model对应的属性就分别是选中区域的属性
	- 返回单元格start，end的索引和存在单元格的model信息
- `adjustOperationRegion`
	- 判断是否为数据类型，如果不是选择正常的调整选择区，如果是进入选择数据方法
- `adjustSelectRegion`
	- 获取完整的选中区域(处理合并单元格情况)
	- 根据索引位置，把所以需要改变的displayName存到数组里
	- 执行，区域改变 回调函数
	- 执行，选择区域改变 回调函数
	- 改变selectRegion的model属性
	- 清除所有选中效果，设置选中区域的行列选中效果
- 执行mousedown回调函数事件，拼接传入事件对象

## 总结

没有整体感，虽然没有造成大的性能瓶颈，但是过程凌乱。阅读起来很费力

### 整体过程

点击后，
1. 判断操作类型，判断操作条件，是否可以执行

2. 根据鼠标位置，找对应的model对象
	如果存在model对象，把model信息和它所在的索引信息返回
	如果不存在，把应该对应的索引位置返回即可

3. 根据返回的结果，调整选中的区域和行列对应的效果
4. 回调函数的对象拼接，直接回调函数


### 诟病

1. 代码整体感缺失
- `headLineColModelList = headItemCols.models`，这段代码在无数地方被使用
- 代码先判断操作条件，查找坐标后，又判断操作类型，这是逻辑代码和检测性代码穿插的典型，
容易造成模块功能不清晰

2. `getCoordinateByMouseEvent`命名有问题
这段代码返回的结果，不是坐标信息，是一个对象和4个索引位置，没有注释的同时，阅读起来很费力

3. 针对一个操作来回的调用，`colDisplayNames`这个动作，在渲染时用了一次，返回结果又拼接了一次
model的结果判断也是多次，
```
options = {
		initColIndex: startColIndex,
		initRowIndex: startRowIndex,
		mouseColIndex: startColIndex,
		mouseRowIndex: startRowIndex,
	};
```
4. 返回结果的拼接，可以优化，代码也没有调用配置文件
5. 回调函数的event对象，也有问题，调用的方式应该是callback.apply(this,args)，不是excute



### 定位鼠标位置细节图

![定位单元格过程图](https://wlchair.gitbooks.io/fengniao/content/vender/mousePosiX.png)

## 改进

根据当前的操作流程，需要规划代码命名和整体流程，重写过程