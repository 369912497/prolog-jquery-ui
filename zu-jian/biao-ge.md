### 表格组件

> 组件名称

```
PlgGrid
```

> 快速使用

```js
<link rel="stylesheet" type="text/css" href="../../../modules/dhtmlx/grid/codebase/dhtmlxgrid.css"/>
<link rel="stylesheet" type="text/css" href="../../../modules/dhtmlx/grid/skins/web/dhtmlxgrid.css"/>
<link rel="stylesheet" type="text/css" href="../../../modules/layui-master/dist/css/layui.css"/>

<script src="../../../modules/jquery/jquery.js" type="text/javascript" charset="utf-8"></script>
<script src="../../../modules/layer/layer.js" type="text/javascript" charset="utf-8"></script>
<script src="../../../modules/layui-master/dist/layui.js" type="text/javascript" charset="utf-8"></script>
<script src="../../../modules/dhtmlx/grid/codebase/dhtmlxgrid.js" type="text/javascript" charset="utf-8"></script>
<script src="../../../core/plgcore.js" type="text/javascript" charset="utf-8"></script>


<link rel="stylesheet" type="text/css" href="../codebase/PlgGrid.css"/>
<script src="../codebase/PlgGrid.js" type="text/javascript" charset="utf-8"></script>

layui.use(['laypage'], function(){
   var opts = {
    skin:"terrace",
    //renderer:"grid",
    columns:[
        {id:"id",name:"id",type:'txt',width:200,hidden:true},
        {id:"platformId",name:"平台",type:'ro',render:function(v){if(v=='test001') return '测试平台1';}},
        {id:"enable",name:"是否可用",type:'ch'},
        {id:"createTime",name:"创建时间",type:'ro'},
        {id:"creatorId",name:"创建人",type:'ro'}
        ],
    multiselect:false,
    url:"data.json",//数据接口
    type:"get",//数据提交方式，默认为get
    params:{},//查询提交参数，分页参数默认为pageNum,pageSize
    page:true, //是否启用分页
    totalCount:"totalCount" //总记录数字段，默认totalCount
　　};
    //分页参数 pageSize pageNum
    console.log(opts);
    var grid = new PlgGrid(opts);    
    grid.renderTo("grid");
    grid.loadData();
})
```

![](/assets/table1.png)

> 构造方法

```
方法一：
var grid = new PlgGrid(opts);

方法二：
var grid = $("div1").initPlgGrid(opts);
```

> 配置

| 配置项 | 说明 |
| :--- | :--- |
| skin | 皮肤样式 |
| renderer | 渲染节点 |
| columns | 列数组配置，如：\[{id:"platformId",name:"平台",type:'ro'},{id:"enable",name:"是否可用",type:'ch'}\]，配置项：id - 数据索引,name - 显示名称,type - 类型（ro/rotxt/ron/txt/txttxt/ra/ch/co/img/...）,sort - 排序方式（int/date/str/na）,align - 对齐方式（left/center/right）,width - 宽度,hidden - 是否隐藏（true/false,默认false\),render - function\(v\){return v;} |
| multiselect | 是否支持多选，默认false |
| url | 数据接口 |
| params | 数据接口提交参数 |
| page | 是否开启分页，默认true，分页参数默认为pageNum和pageSize |
| totalCount | 设定总页数字段，默认为“totalCount” |
| filters | 头部过滤器，有如下类型：\#text\_filter,\#select\_filter,\#combo\_filter,\#text\_search,\#numeric\_filter\(包含'='、'&gt;'、'&lt;'、'?'、'&gt;='、'n1..n2'\) |

> 方法

| 方法 | 说明 |
| :--- | :--- |
| renderTo\(id\) | 项目目标节点进行渲染 |
| loadData\(\) | 加载数据 |
| reload\(\) | 刷新数据 |
| getElement\(\) | 获取组件dom节点 |
| getGrid\(\) | 获取grid组件 |
| getParams\(\) | 获取接口参数 |
| getSelectedRowId\(\) | 获取选择行id |
| getSelectedCellIndex\(\) | 获取选择单元格索引，值为-1时，表示为选择 |
| getRowId\(rowIndex\) | 根据行索引（从0开始）获取row id |
| getRowIndex\(rowId\) | 根据row id获取行索引 |
| getCellObject\(rowId,colIndex\) | 获取单元格对象 |
| getCellVaule\(rowId,colIndex\) | 获取单元格值 |
| getCellObject2\(rowIndex,colIndex\) | 获取单元格对象 |
| getCellVaule2\(rowIndex,colIndex\) | 获取单元格值 |
| getColumnsNum\(\) | 获取纵列数，包括隐藏列 |
| setColWidth\(colIndex,width\) | 设置指定列的宽度 |

> 事件

```
使用：grid.on("eventName",function(e){});
```

| 事件 | 说明 |
| :--- | :--- |
| onRowSelect\(id,ind\) | 选择行事件。id - 选择行的id，ind - 列索引 |
| onRightClick\(id,ind,obj\) | 右键事件。id - 单击行id ，ind - 列索引，obj-事件对象 |
| onHeaderClick\(ind,obj\) | 表头单击事件。ind - 列索引，obj - 事件对象 |



