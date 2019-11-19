# makeSeal 印章制作

::: demo
```html
<template>
    <vc-make-seal 
        :url="url"
        :locked="locked"
        :options="options"
        @submit="submitEvt"
        @selected="selectedEvt"
    />
</template>

<script>
export default {
    data () {
        return {
            url: './logo.png',
            locked: false,
            options: {
                local: true
            }
        }
    },
    methods: {
        submitEvt (data) {
            this.locked = true
            console.log(data)
            // 实现截取图片上传
            let formData = new FormData()
            formData.append('name', data.blob)

            // 模拟2s后，我们上传的图像，返回了制章的效果
            setTimeout(() => {
                this.locked = false
            }, 2000)
        },
        selectedEvt ({index, width, height, image}) {
            console.log(`选择了第 ${index +1} 印章`)
            console.log(`宽:${width}px 高:${height}px`)
            console.log(`图片信息是: ${image}`)
        }
    }
}
</script>
```
:::


## Poprs

| 参数 | 类型 | 说明 | 默认值 | 可选值 |
|---|---|---|---|:---:|
| url | `String|Object` | 裁切的图片地址 | - | - |
| list | `Array` | 用于展示印章处理的选择列表<br/>如果使用浏览器生成的，可以忽略此项 | [] | - |
| locked | `Boolean` | 控制是否可以触发查看印章效果 | - | - |
| options | `Object` | 对生成印章的属性设置 | 见下面 options | - |
| cropperOpts | `Object` | 印章的设置 | 见下面 cropperOpts | - |

### list

| 参数 | 类型 | 说明 | 默认值 | 可选值 |
|---|---|---|---|:---:|
| threshold | `Number` | 当前图片处理的阈值 | - | - |
| checked | `Boolean` | 是否选中 | - | - |
| url | `Image URL or Base64` | 展示的图片地址 | - | - |


### options

| 参数 | 类型 | 说明 | 默认值 | 可选值 |
|---|---|---|---|:---:|
| defaultColor | `Color` | 默认印章颜色 | #F5222D | - |
| colors | `Array` | 印章可用颜色<br/>默认提供了 红 黑 蓝 | ['#F5222D', '#307BF6', '#333333'] | - |
| threshold | `Array` | 阈值<br/>默认生成40，60，80与10的阈值印章 | [40, 60, 80, 10] | - |
| local | `Boolean` | 是否使用本地处理印章 | false | - |
| scale | `Number` | 背景图片缩放 | 1 | - |
| angle | `Number` | 旋转方向 | 0 | - |


### cropperOpts

| 参数 | 类型 | 说明 | 默认值 | 可选值 |
|---|---|---|---|:---:|
| aspectRatio | `Number` | 设置印章缩放比例<br/>NaN 为自由模式 | NaN | - |
| dragMode | `String` | 设置印章选区拖动模式 | `move` | - |
| cropBoxMovable | `Boolean` | 选区是否禁用，默认禁用 | `false` | - |
| toggleDragModeOnDblclick | `Boolean` | 切换拖动区功能，默认禁用 | `false` | - |
| cropBoxResizable | `Boolean` | 选区大小，默认禁用 | `false` | - |
| minCropBoxWidth | `Number` | 默认选区宽 | `200` | - |
| minCropBoxHeight | `Number` | 默认选区高 | `200` | - |

> 通常，不用配制 `cropperOpts`

## Events

| 事件名 | 说明 | 回调参数 |
| --- | --- | --- |
| fileChange | 更换图片时触发，你可以触来触发文件上传<br/>如果不设置时，则使用本地文件读取显示(IE 10+) | files 文件信息 |
| error | 错误时回调，返回信息信息 | - |
| submit | 查看制章效果事件 | 返回截取后的图像相关信息，包括blob color image(png;base64) sealHeight(印章高度) sealWidth(印章宽度) threshold type(submit)|
| selected | 当前选择的印章 | - |

```js
// submit 返回数据
{
    blob: Blob,
    image: 'data:image/png;base64,abcd...',
    color: '#f5222d', // 印章的印章
    sealHeight: 45,
    sealWdith: 45,
    // 触发对象 
    // submit - 查看印章效果
    // color  - 更换印章颜色
    type: 'submit' 
}

```