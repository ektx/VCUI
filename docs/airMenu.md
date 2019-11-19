# AirMenu 悬浮菜单

## 示例

::: demo 
```html
<template>
  <div 
    style="width: 100px; height: 100px; background: #09f"
    @mouseover="show = true"
  >鼠标移入</div>

  <vc-air-menu :list="list" :parent="parent" :show.sync="show" @click="callback"/>
</template>

<script>
export default {
  data() {
    return {
      show: false,
      parent: {},
      list: [
        {
          label: 'menu-1',
          children: [
            {
              label: 'menu2-1',
              children: [
                {
                  label: 'menu3-1',
                  to: '/'
                },
              ]
            },
            {
              label: 'menu2-2',
              children: [
                {
                  label: 'menu4-1',
                  children: [
                    {
                      label: 'menu5-1',
                      children: [
                        {
                          label: 'menu6-1',
                          to: '/'
                        },
                        {
                          label: 'menu6-2',
                          to: '/'
                        }
                      ]
                    }
                  ]
                }
              ]
            }
          ]
        }, {
            label: 'menu-2',
            children: [
              {
                label: 'menu6-1',
                children: [
                  {
                    label: 'menu7-1',
                    to: '/'
                  },
                        
                ]
              },
            ]
          }
        ]
      }
    },
  mounted () {
    this.parent = this.$el.querySelector('div')
  },
  methods: {
    callback (data) {
      alert(data.label)
    }
  }
};
</script>

<style>
/* css 内容 */
</style>
```
:::


## Poprs

| 参数 | 类型 | 说明 | 默认值 | 可选值 |
|---|---|---|:---:|:---:|
| list | `Array` | 菜单数据 | [] | - |
| parent | `DOM` | 触发的对象 | - | - |
| show | `Boolean` | 是否显示 | false | - |
| autoClose | `Boolean` | 是否自动关闭<br/>默认为点击页面时关闭菜单 | false | - |

## Events

| 事件名 | 说明 | 回调参数 |
| --- | --- | --- |
| click | 菜单内部被点击时 | 返回点击的菜单信息 Object 对象 |