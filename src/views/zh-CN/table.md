# Table 表格

函数式的对 el-table 二次封装, 不需要将 columns 属性写在 el-table 中，而是抽离出来写成一个 columns.js 进行管理

### 基础用法

**图例**

![avatar](https://raw.githubusercontent.com/devin-huang/devin-huang.github.io/master/img/pubilc/vue-template-markdown/fun-table.png)

**在线查看**

[ -------------- codesandbox：查看在线 Demo --------------](https://codesandbox.io/s/fun-table-uv9m6)

**在线下载**

链接：[https://share.weiyun.com/rM9m2Cq2](https://share.weiyun.com/Cl8QbHLP) 密码：stwkvj

```html
<fun-table
  :columns="
	{
		align: 'center',
		label: '名称',
		prop: 'name',
		width: '220px',
	},
	{
		align: 'center',
		label: '版本',
		prop: 'version',
	}
	"
  :data="[{name: 'Vue', version: '2.0'}, {name: 'React', version: '12.0'}]"
  :page="page"
  @pageChange="onPageChange"
/>
```

### Table Attributes

| 参数                   | 说明                                        | 类型    | 可选值 | 默认值                                                                  |
| ---------------------- | ------------------------------------------- | ------- | ------ | ----------------------------------------------------------------------- |
| selection              | 是否使用多选框                              | Boolean | —      | false                                                                   |
| multipleSelection.sync | 仅在 selection 为 true 时使用，获取已选对象 | Array   | —      | []                                                                      |
| columns                | 列组，详细看 <b>columns Attributes</b> 说明 | Array   | —      | []                                                                      |
| data                   | 数据源                                      | Array   | —      | []                                                                      |
| page                   | 分页                                        | Object  | —      | { currentPage: 1, pageSize: 10, total:0, pageSizes: [10, 20, 50, 100] } |

### Table Events

| 参数       | 说明                 | 回调参数                                                    |
| ---------- | -------------------- | ----------------------------------------------------------- |
| pageChange | 分页组件被触发时回调 | (value: Object) { currentPage, pageSize, pageSizes, total } |

### columns Attributes

| 参数    | 说明                     | 类型     | 可选值 | 默认值 |
| ------- | ------------------------ | -------- | ------ | ------ |
| showPop | 内容溢出是否显示提示框   | Boolean  | —      | false  |
| header  | 是否使用 HTML 定义列头部 | Function | —      | —      |
| slot    | 是否使用 HTML 定义行内容 | Function | —      | —      |
| hidden  | 是否隐藏                 | Boolean  | —      | false  |

:::tip
columns.js 中 `this` 指向是当前 `el-table` 对象，想获取对应当前组件 this 则是 `this.$parent`
:::

:::tip
fun-table 是基于 el-table 进行二次封装，所以 Columns 可定义 el-table 列已有属性，也可另自定义属性进行特别处理
:::
