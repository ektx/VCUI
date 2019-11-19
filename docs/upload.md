# Upload 上传

## 示例

基础效果演示

::: demo 
```html
<template>
  <vc-upload action="https://jsonplaceholder.typicode.com/posts/" multiple></vc-upload>
</template>
```
:::


自动上传效果演示

::: demo 
```html
<template>
  <vc-upload 
    action="https://jsonplaceholder.typicode.com/posts/" 
    multiple 
    autoUpload 
    :files="files"
    @success="success"
  ></vc-upload>
</template>

<script>
export default {
  data () {
    return {
      files: [
        {
          name: 'abc',
          url: 'https://cn.bing.com/th?id=OIP.uHgMWxkyFP_RIqEwHeTJwQHaFF&pid=Api&rs=1'
        }
      ]
    }
  },
  methods: {
    success (data, file, list) {
      this.files.push({
        name: file.name,
        url: ''
      })

      console.log(this.files)
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
