---
title: Segmented
lang: zh-CN
---

# Segmented 分段控制器

用于展示多个选项并允许用户选择其中单个选项。

## 基础用法

设置`v-model`为选项值。

:::demo

segmented/basic

:::

## 禁用状态

设置 `disabled` 属性来禁用一些选项。

:::demo

segmented/disabled

:::

## Block 分段选择器

设置`block`为`true`以适应父元素的宽度。

:::demo

segmented/block

:::

## 自定义内容

设置 default slot 位来渲染自定义内容。

:::demo

segmented/custom-content

:::

## 自定义样式

设置 default slot 位来渲染自定义内容。

:::demo

segmented/custom-style

:::

## API

### 属性

| 名称                                    | 说明                 | 类型                                                                                                                            | 默认值                                                    |
| ------------------------------------- | ------------------ | ----------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------ |
| model-value / v-model                 | 绑定值                | ^[string] / ^[number] | —                                                      |
| options                               | 选项的数据              | ^[array]`Option[]`                                                        | [] |
| size                                  | 组件大小               | ^[enum]`'' \\| 'large' \\| 'default' \\| 'small'`                      | ''                                                     |
| block                                 | 撑满父元素宽度            | ^[boolean]                                                                | —                                                      |
| disabled                              | 是否禁用               | ^[boolean]                                                                | false                                                  |
| validate-event                        | 是否触发表单验证           | ^[boolean]                                                                | true                                                   |
| name                                  | 原生 name 属性         | ^[string]                                                                 | —                                                      |
| id                                    | 原生 `id` 属性         | ^[string]                                                                 | —                                                      |
| aria-label ^(a11y) | 原生 `aria-label` 属性 | ^[string]                                                                 | —                                                      |

### 事件

| 名称     | 说明                  | 类型                                                                                  |
| ------ | ------------------- | ----------------------------------------------------------------------------------- |
| change | 当所选值更改时触发，参数是当前选中的值 | ^[Function]`(val: any) => void` |

### Slots

| 名称      | 说明            |
| ------- | ------------- |
| default | 自定义 Option 模板 |

## 类型声明

<details>
  <summary>Show declarations</summary>

```ts
type Option =
  | {
      label: string
      value: string | number | boolean
      disabled?: boolean
      [key: string]: any
    }
  | string
  | number
  | boolean
  | undefined
```

</details>
