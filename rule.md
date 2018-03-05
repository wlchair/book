# 命名规范

- 所有文件、文件夹都是用小写形式命名
- 如果名字过长，用 “-” 连接
- 名字全部使用英文及缩写形式表示、不能出现拼音

## 分类

### 模块
- `topbar`，`toolbar`
- `book`，`sheet`，`col`，`row`，`cell`，`line`
- `tab`
- `operate`

### 类型
- `head`

### 职能
- `panel`（结构）
- `group`（容器）
- `item`（内容）

### 功能
- `confrim`，`edit`

# 命名组成

## 视图

`view`: `模块 - [? 类型] - [? 职能]` , `功能`

### 示例

- `toolbar-box`
- `toolbar-panel`
- `toolbar-list`
- `col-head-box`
- `table`、`toolbar`，`col`

## 组件

`component`: `职能 - [? 模块] || 功能`

### 示例

- `box-col`
- `box-row`
- `sidebar`（信息显示框）、`colorpanel`（颜色版），`edit`（编辑框）

----

# template 规范

### 属性优先级

- `HTML`属性 > 不带`：`的语法 > 有`：`的语法

### 示例

```
<div class="one" v-for="item in list" 
:class="{{key | capitalize}}" :style="{
	color: red,
	width: 50px
}"
```
