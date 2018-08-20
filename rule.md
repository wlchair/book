# 组件及文件 - 命名规范

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

# template - 规范

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

# 代码 - 命名规范
- getters函数名按照Camel-Case命名法，首单词全部小写，其余单词首字母大写
- getters函数中不带get前缀
- actions/mutations函数名全部大写
- actions行为缺省表示change
- 名字全部使用英文及缩写形式表示、不能出现拼音

## 分类

### mutations
- `create`（新增）
- `insert`（插入）
- `delete`（删除）
- `update`（更新）

### actions
- `add`（新增）
- `infix`（插入）
- `remove`（删除）
- `change`（更新）默认缺省

# 命名组成

## getters

`获取数据`: `[? 形容词] 数据名称 [? By条件] [? In获取范围]`
`判断`: `is || has [? 形容词] 数据名称 [? By条件] [? In获取范围]`

### 示例

- `editState`
- `colIdxByAliasInVisible`
- `isMerge`

## mutations

`mutations`: `M_模块名_操作_[? 操作对象属性]`

### 示例

- `M_CELLS_UPDATE_EDITSTYLE`
- `M_ROWS_INSERT`

## actions

`actions`: `A_模块名_操作 || 操作对象属性`

### 示例

- `A_CELLS_MERGE`
- `A_ROWS_ADD`
- `A_COLS_REDUCE`

