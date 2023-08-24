---
title: Anchor 锚点
lang: zh-CN
---

# Anchor 锚点

通过锚点，您可以很快找到当前页面上信息内容的位置。

## 基础用法

最简单的用法。

:::demo

anchor/basic

:::

## 水平模式

水平排列的锚点

:::tip

水平模式不支持`sub-link`槽位

:::

:::demo

anchor/horizontal

:::

## 滚动的容器

自定义滚动区域，使用 `offset` props 可以设置锚点滚动偏移。 监听`link-click`事件并阻止浏览器的默认行为，然后它不会改变历史。

:::demo

anchor/scroll

:::

## 锚点链接变化

监听锚点链接变化

:::demo

anchor/change

:::

## 下划线类型

设置\`type="underline"更改为下划线类型

:::demo

anchor/underline

:::

## 固定模式

使用 affix 组件来固定住页面中的锚点。

:::demo

anchor/affix

:::

## Anchor API

### Anchor Attributes

| 属性        | 说明                | 类型                                                                                        | 默认值        |
| --------- | ----------------- | ----------------------------------------------------------------------------------------- | ---------- |
| container | 滚动的容器             | `string` \\| `HTMLElement` \\| `Window `                                                | —          |
| offset    | 设置锚点滚动的偏移量        | `number`                                                                                  | 0          |
| bound     | 触发锚点的元素的位置偏移量     | `number`                                                                                  | 15         |
| duration  | 设置容器滚动持续时间，单位为毫秒。 | `number`                                                                                  | 300        |
| marker    | 是否显示标记            | ^[boolean]                            | true       |
| type      | 设置锚点类型            | ^[enum]`'default' \\| 'underline'`   | `default`  |
| direction | 设置锚点方向            | ^[enum]`'vertical' \\| 'horizontal'` | `vertical` |

### Anchor Events

| 事件名    | 说明          | 类型                                                                                                      |
| ------ | ----------- | ------------------------------------------------------------------------------------------------------- |
| change | step 改变时的回调 | ^[Function]`(href: string) => void`                 |
| click  | 当用户点击链接时触发  | ^[Function]`(e: MouseEvent, href?: string) => void` |

### Anchor Methods

| 名称       | 说明         | 类型                                                                                      |
| -------- | ---------- | --------------------------------------------------------------------------------------- |
| scrollTo | 手动滚动到特定位置。 | ^[Function]`(href: string) => void` |

### Anchor Slots

| 名称      | 说明              |
| ------- | --------------- |
| default | AnchorLink 组件列表 |

### AnchorLink Attributes

| 属性    | 说明       | 类型       | 默认值 |
| ----- | -------- | -------- | --- |
| title | 链接的文本内容。 | `string` | —   |
| href  | 链接的地址。   | `string` | —   |

### AnchorLink Slots

| 名称       | 说明      |
| -------- | ------- |
| default  | 链接的内容   |
| sub-link | 子链接的槽位。 |
