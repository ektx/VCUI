# DetailList 清单列表

## 示例

::: demo 
```html
<template>
  <vc-detail-list :format="format" :data="data" :column="column">
    <template #test="{data, value, index}">
      {{value}}
      <vc-btn @click="toggleEvt(index)">{{format[index+1].hide ? '显示':'隐藏'}}</vc-btn>
    </template>
  </vc-detail-list>
</template>

<script>
export default {
  data() {
    return {
      column: 2,
      format: [
        {
          label: '名称',
          key: 'name'
        },
        {
          label: '功能',
          key: 'features'
        },
        {
          label: 'Format',
          key: 'format',
          mark: {
            width: '100px',
            inner: '数组格式'
          }
        },
        {
          label: 'Data',
          key: 'data'
        },
        {
          label: '扩展',
          key: 'fix',
          prefix: '*',
          suffix: '*'
        },
        {
          label: 'Fun',
          key: 'event',
          fun: this.funEvt
        },
        {
          label: 'Slot',
          key: 'slot',
          slot: 'test'
        },
        {
          label: 'Hide',
          key: 'hide',
          hide: true
        }
      ],
      data: {
        name: 'DetailList',
        features: '清单列表',
        format: '展示的列表对象',
        data: '数据对象',
        fix: '--',
        slot: 'slot data',
        hide: '这是隐藏的数据'
      }
    }
  },
  methods: {
    funEvt (data, item) {
      console.log(data, item)
      return data[item.key] || '我是从事件中返回的内容'
    },

    toggleEvt (index) {
      this.format[index+1].hide = !this.format[index+1].hide
    }
  }
};
</script>
```
:::


# Props
| 参数 | 类型 | 说明 | 默认值 | 可选值 |
| --- | --- | --- | --- | --- |
| **data** | `Object` | 数据内容 | {} |  |
| **format** | `Array` | 输出内容格式规范 | [] |  |
| **width** | `String` | 设置标题的宽度 |  |  |
| **separator** | `String` | 分隔符 |  |  |
| **labelAlign** | `String` | 标题位置，参考 text-align | left |  |
| **column** | `String|Number` | 分栏设置，默认为1栏 | 1 |  |

## format
| 参数 | 类型 | 说明 | 默认值 | 可选值 |
| --- | --- | --- | --- | --- |
| **label** | `{String}` | 标题 |  |  |
| **key** | `{String}` | 引用字段 |  |  |
| **display** | `{["block"|"inherit"]}` | 是否为块状元素 |  |  |
| **mark** | `{Object}` | 提示内容 |  |  |
| **- width** | `{String}` | 设置宽度，如 => {"100px"}, |  |  |
| **- inner** | `{String}` | 需要显示内容 |  |  |
| **fun** | `{Function}` | 调用方法，返回(data, item)，接收输出字符串 |  |  |
| **prefix** | `{String}` | 标题前缀 |  |  |
| **suffix** | `{String}` | 标题后缀 |  |  |
| **hide** | `{boolean}` | 隐藏与显示 |  |  |
| **slot** | `{string}` | 插槽 |  |  |
