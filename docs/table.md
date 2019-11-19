# Table 表格

## 示例

基础效果演示

::: demo 
```html
<template>
  <vc-table :data="data" :header="header"/>
</template>

<script>
export default {
  data () {
    return {
      header: [
        {
          label: '姓名',
          key: 'name',
          width: '100px'
        },
        {
          label: '时间',
          key: 'date',
          width: '100px'
        },
        {
          label: '地址',
          key: 'address',
        }
      ],
      data: [
        {
          date: "2016-05-02",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1518 弄"
        },
        {
          date: "2016-05-04",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1517 弄"
        },
        {
          date: "2016-05-01",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1519 弄"
        },
        {
          date: "2016-05-03",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1516 弄"
        }
      ]
    }
  }
}
</script>
```
:::

添加操作

::: demo 
```html
<template>
  <vc-table :header="header" :data="data" :index.sync="index" :total="data.length">
    <template v-slot:setting="{item, index}">
      <vc-btn @click="showDetail(item, index)">详情</vc-btn>
    </template>
  </vc-table>
  <vc-btn @click="add">添加数据</vc-btn>
</template>

<script>
export default {
  data() {
    return {
      header: [
        {
          label: '姓名',
          key: 'name',
          width: '100px'
        },
        {
          label: '时间',
          key: 'date',
          width: '100px'
        },
        {
          label: '地址',
          key: 'address',
        },
        {
          label: '设置',
          slot: 'setting',
          width: '100px'
        },
      ],
      data: [],
      index: 1
    }
  },
  methods: {
    showDetail (item, index) {
      console.log(item, index)
      item.name = 'zwl'
    },
    add () {
      this.data = [
        {
          date: "2016-05-02",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1518 弄"
        },
        {
          date: "2016-05-04",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1517 弄"
        },
        {
          date: "2016-05-01",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1519 弄"
        },
        {
          date: "2016-05-03",
          name: "王小虎",
          address: "上海市普陀区金沙江路 1516 弄"
        }
      ]
    }
  }
}
</script>
```
:::


# Props
| 参数 | 类型 | 说明 | 默认值 | 可选值 |
| --- | --- | --- | --- | --- |
| **data** | `Array` |  | [] |  |
| **header** | `Array` |  | [] |  |
| **total** | `Number` |  |  |  |
| **index** | `Number` |  | 1 |  |
