# VirtualList 虚拟列表

## 示例

基础效果演示

::: demo 
```html
<template>
  <div style="height: 400px; width: 280px; border: 1px solid #ddd">
    <vc-virtual-list :itemHeight="100" :list-data="data">
      <template v-slot:default="item">
        <div :style="{height: item.height+'px', backgroundColor: item.color}">{{item}}</div>
      </template>
    </vc-virtual-list>
  </div>
  <vc-btn @click="createData">生成数据</vc-btn>
</template>

<script>
export default {
  data () {
    return {
      data: []
    }
  },
  methods: {
    // 创建数据
    createData () {
      for (let i = 0; i < 1000; i++) {
        this.data.push({
          id: i,
          value: i,
          height: Math.random() * 100 + 100,
          color: '#'+(Math.random()*0xffffff<<0).toString(16)
        })
      }
    }
  }
}
</script>
```
:::


## Poprs

| 参数 | 类型 | 说明 | 默认值 | 可选值 |
|---|---|---|:---:|:---:|
| listData | Array | 渲染数据 | [] | - |
| itemHeight | Number | 单个元素的高度，一个初始值，如果是高度不定，可以不填写 | 50 | - |
| cache | Number | 防止滚动出现空白时设置的列缓存 | 1 | - |

## Events

| 事件名 | 说明 | 回调参数 |
| --- | --- | --- |
