# Layer 弹层

## 示例

::: demo 
```html
<template>
    <vc-btn @click="open = !open">Open Layer - {{open}}</vc-btn>
    <vc-layer :show.sync="open" title="hello world"></vc-layer>
</template>

<script>
export default {
    data() {
        return {
            open: false
        }
    }
};
</script>
```
:::


## Poprs

| 参数 | 类型 | 说明 | 默认值 | 可选值 |
|---|---|---|:---:|:---:|
| show | `Boolean` | 是否显示弹层，支持 `.sync` 修饰符 | `false` | - |
| title | `String` | 弹层的标题 | Layer | - |
| width | `String` | 调整弹层的宽度<br>width="200px" | - | - |

## Events

| 事件名 | 说明 | 回调参数 |
| --- | --- | --- |
| close | 关闭时触发 | - |
| closed | 弹层完全关闭后触发 | - |
| open | 弹层打开时触发 | - |
| opened | 弹层完全打开后触发 | - |