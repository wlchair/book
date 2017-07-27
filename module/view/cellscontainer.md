
## cellscontainer模块

## 模块功能：
- 作为容器包含选中区，行列容器
- 监听鼠标点击、拖住动作，做出相关的选中区域调整（包含数据源等其他区域）

## 开放全局的方法：
- adaptWidth
    - 自动调整宽度，对列发生宽度变化时触发（删除/插入/调整宽度）
- adaptHeight
    - 同上
- getCoordinateDisplayName
    - 用于处理第三方调用，将相对于浏览器页面的横纵坐标，转换为表格视
图的行列坐标
- bindDragSelect
    - 绑定鼠标的移动事件，扩大选中区域（由于冻结情况下含有多个cellscontainer对象，需要进行同时绑定和解绑，所以，开放为全局方法）
- unBindDragSelect
    - 同上

## 主要执行流程说明：

### 单击
- 判断是否为编辑状态，编辑状态不进行定位，直接退出执行
- 调用getCoordinate，将点击事件的点击位置转换为表格视图中的行列索引
    - 将传入坐标转换为表格内容区域的相对坐标
    - 判断选中点在当前视图内（避免第三方调用，传入点不在当前视图中）
    - 通过二分查询，查找行列索引
- 判断选中位置是否包含单元格
    - 若包含单元格，根据单元格扩充选中区域的大小
- 判断当前选中区域的状态，根绝不同状态，对不同的selectRegionModel进行设置
    - 设置selectRegionModel视图 initColIndex、initRowIndex、mouseColIndex、mouseRowIndex
- selectRegion视图监听相关属性变化
    - 调整选中区域位置以及宽高
    - 调整行列相关效果
- 触发自定义mousedown事件
- 触发监听mousemove事件

### 拖动
- mousemove事件触发dragSelect方法
    - 调用getCoordinate，将mousemove事件的位置转换为表格视图中的行列索引
    - 判断鼠标位置是否行列之间进行了移动
        - 未移动退出当前逻辑
        - 发生移动，设置selectRegionModel视图
        - selectRegion视图监听相关属性变化，做出相应调整
            - 判断整个选中区域内单元格是否已经包含完整，如果含有未包含全单元格，进行选中区域扩大，直至包含单元格完成
            - 调整选中区域位置以及宽高
- bodyContainer 监听mouseup事件，当事件发生取消对mouseover事件的监听，拖动动作停止


