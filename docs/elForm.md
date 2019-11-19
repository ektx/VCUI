# ElForm 表单

> 这里是对 element-ui 的 From 进行的整合调整。

## 示例

基础效果演示，内部组件按照element-ui表单组件来使用就可以了。

::: demo 
```html
<template>
  <vc-el-form 
    :data="formData" 
    :list="formList" 
    column="2" 
    label-width="100px" 
    layout="right"
    @submit="submit"
  />
</template>

<script>
export default {
  data() {
    return {
      formData: {
        name: '',
        status: 0,
        daterange: ''
      },
      formList: [
        {
          type: 'input',
          key: 'name',
          label: '应用名称',
          placeholder: '请输入应用名称'
        },
        {
          type: 'select',
          key: 'status',
          label: '状态',
          options: [
            {
              label: '全部',
              value: 0
            },
            {
              label: '启用',
              value: 1
            },
            {
              label: '停用',
              value: 2
            }
          ]
        },
        {
          type: 'daterange',
          rangeSeparator: '至',
          key: 'daterange',
          label: '最近修改时间'
        },
      ]
    }
  },
  methods: {
    submit () {
      console.log(JSON.stringify(this.formData, '', '  '))
    }
  }
}
</script>
```
:::

**带有验证功能**

::: demo 
```html
<template>
  <vc-el-form 
    :data="formData" 
    :list="formList" 
    :rules="rules"
    :buttons="buttons"
    column="2" 
    label-width="100px" 
    @submit="submit"
  />
</template>

<script>
export default {
  data() {
    return {
      formData: {
        name: '',
        status: '',
        sex: '',
        birthday: ''
      },
      rules: {
        name: [
          {
            required: true,
            message: '姓名不能为空',
            trigger: 'blur'
          },
          {
            max: 5,
            message: '长度不能超过5个字符',
            trigger: ['change', 'blur']
          }
        ],
        status: [
          {
            required: true,
            message: '请选择状态',
            trigger: 'change'
          },
        ],
        sex: [
          {
            required: true,
            message: '请选择性别',
            trigger: 'change'
          }
        ],
        birthday: [
          {
            required: true,
            message: '请选择生日',
            trigger: 'change'
          }
        ]
      },
      buttons: [
        {
          label: 'Save',
          type: 'submit',
          props: {
            color: 'warn'
          },
          event () {
            console.log(this.formData)
          }
        },
        {
          label: 'Reset',
          type: 'reset'
        }
      ],
      formList: [
        {
          type: 'input',
          key: 'name',
          label: '姓名',
          maxlength: 5,
          placeholder: '请输入姓名'
        },
        {
          type: 'select',
          key: 'status',
          label: '状态',
          options: [
            {
              label: '全部',
              value: 0
            },
            {
              label: '启用',
              value: 1
            },
            {
              label: '停用',
              value: 2
            }
          ]
        },
        {
          type: 'radio',
          key: 'sex',
          label: '性别',
          list: [
            {
              label: '👧🏻女',
              value: 0
            },
            {
              label: '👶🏻男',
              value: 1
            },
            {
              label: '👀其它',
              value: -1
            }
          ]
        },
        {
          type: 'date',
          rangeSeparator: '至',
          key: 'birthday',
          label: '生日'
        },
      ]
    }
  },
  methods: {
    submit () {
      console.log(JSON.stringify(this.formData, '', '  '))
    }
  }
}
</script>
```
:::