# Pagination 分页

## 示例

基础效果演示

::: demo 
```html
<template>
  <vc-pagination :index.sync="index" :total="total"/>
  <vc-pagination :index.sync="index2" :total="total2" :size="15"/>
</template>

<script>
export default {
  data () {
    return {
      index: 1,
      total: 40,
      index2: 3,
      total2: 1000
    }
  },
  watch: {
    index (i) {
      console.log(i)
    }
  }
}
</script>
```
:::


## Poprs

| 参数 | 类型 | 说明 | 默认值 | 可选值 |
|---|---|---|:---:|:---:|
| index | `Number` | 当前页数 | 1 | - |
| total | `Number` | 总数 | 0 | - |
| size | `Number` | 每页数量 | 10 | - |

## Events

| 事件名 | 说明 | 回调参数 |
| --- | --- | --- |
| indexChange | 页码发生变化 | 返回变化后的页数 |
| prevChange | 上一页事件 | 返回变化后的页数 |
| nextChange | 下一页事件 | 返回变化后的页数 |