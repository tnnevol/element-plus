---
title: Tour 漫游式引导
lang: zh-CN
---

# Tour 漫游式引导

用于分步引导用户了解产品功能的气泡组件。 用来引导用户并介绍产品

## 基础用法

最简单的用法。

:::demo

tour/basic

:::

## 非模态

使用`:mask="false"`可以将引导变为非模态， 同时为了强调引导本身，建议与 type="primary" 组合使用。

:::demo

tour/non-modal

:::

## 位置

改变引导相对于目标的位置，共有 12 种位置可供选择。 当 `target` 为空时引导将会展示在正中央。

:::demo

tour/placement

:::

## 自定义遮罩样式

自定义遮罩样式。

:::demo

tour/mask

:::

## 自定义指示器

自定义指示器。

:::demo

tour/indicator

:::

## 目标

可以传入目标的各种类型的参数。 自^(2.5.2)以来支持字符串和函数类型。

:::demo

tour/target

:::

## Tour API

:::tip
tour-step 组件上相同名称配置的优先级更高。
:::

### Tour 属性

| 属性                                        | 描述                               | 类型                                                                                                                                                                                                                                                    | 默认值                                                                                |
| ----------------------------------------- | -------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------- |
| show-arrow                                | 是否显示箭头                           | `boolean`                                                                                                                                                                                                                                             | true                                                                               |
| placement                                 | 引导卡片相对于目标元素的位置                   | ^[enum]`'top' \\| 'top-start' \\| 'top-end' \\| 'bottom' \\| 'bottom-start' \\| 'bottom-end' \\| 'left' \\| 'left-start' \\| 'left-end' \\| 'right' \\| 'right-start' \\| 'right-end'` | `bottom`                                                                           |
| content-style                             | 为content自定义样式                    | `CSSProperties`                                                                                                                                                                                                                                       | —                                                                                  |
| mask                                      | 是否启用遮罩，通过自定义属性改变遮罩样式以及填充的颜色      | `boolean` \\| ^[Object]`{ style?: CSSProperties; color?: string; }`                                                                                                                              | `true`                                                                             |
| type                                      | 类型，影响底色与文字颜色                     | `default` \\| `primary`                                                                                                                                                                                                                              | `default`                                                                          |
| model-value / v-model                     | 打开引导                             | `boolean`                                                                                                                                                                                                                                             | —                                                                                  |
| current / v-model:current | 当前值                              | `number`                                                                                                                                                                                                                                              | —                                                                                  |
| scroll-into-view-options                  | 是否支持当前元素滚动到视窗内，也可传入配置指定滚动视窗的相关参数 | `boolean` \\| `ScrollIntoViewOptions`                                                                                                                                                                                                                | ^[Object]`{ block: 'center' }` |
| z-index                                   | Tour 的层级                         | `number`                                                                                                                                                                                                                                              | `2001`                                                                             |
| show-close                                | 是否显示关闭按钮                         | `boolean`                                                                                                                                                                                                                                             | `true`                                                                             |
| close-icon                                | 自定义关闭图标，默认Close                  | `string` \\| `Component`                                                                                                                                                                                                                             | —                                                                                  |
| close-on-press-escape                     | 是否可以通过按下 ESC 关闭引导                | `boolean`                                                                                                                                                                                                                                             | `true`                                                                             |
| target-area-clickable                     | 启用蒙层时，target 元素区域是否可以点击。         | `boolean`                                                                                                                                                                                                                                             | `true`                                                                             |

### Tour 插槽

| 插槽名        | 说明                                     |
| ---------- | -------------------------------------- |
| default    | tourStep 组件列表                          |
| indicators | 自定义指示器, scope 参数是 `{ current, total }` |

### Tour 事件

| 事件名    | 描述         | 类型                                                                                         |
| ------ | ---------- | ------------------------------------------------------------------------------------------ |
| close  | 关闭引导时的回调函数 | ^[Function]`(current: number) => void` |
| finish | 引导完成时的回调   | ^[Function]`() => void`                |
| change | 步骤改变时的回调   | ^[Function]`(current: number) => void` |

### TourStep 属性

| 属性                       | 描述                                                                                                                                           | 类型                                                                                                                                                                                                                                                    | 默认值       |
| ------------------------ | -------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------- |
| target                   | 获取引导卡片指向的元素， 为空时居中于屏幕。 自^(2.5.2)以来支持字符串和函数类型。 字符串类型是文档.querySelector的选择器。 | `HTMLElement` \\| `string` \\| ^[Function]`() => HTMLElement`                                                                                                                                   | —         |
| show-arrow               | 是否显示箭头                                                                                                                                       | `boolean`                                                                                                                                                                                                                                             | `true`    |
| title                    | 标题                                                                                                                                           | `string`                                                                                                                                                                                                                                              | —         |
| description              | 主要描述部分                                                                                                                                       | `string`                                                                                                                                                                                                                                              | —         |
| placement                | 引导卡片相对于目标元素的位置                                                                                                                               | ^[enum]`'top' \\| 'top-start' \\| 'top-end' \\| 'bottom' \\| 'bottom-start' \\| 'bottom-end' \\| 'left' \\| 'left-start' \\| 'left-end' \\| 'right' \\| 'right-start' \\| 'right-end'` | `bottom`  |
| content-style            | 为content自定义样式                                                                                                                                | `CSSProperties`                                                                                                                                                                                                                                       | —         |
| mask                     | 是否启用蒙层，也可传入配置改变蒙层样式和填充色                                                                                                                      | `boolean` \\| ^[Object]`{ style?: CSSProperties; color?: string; }`                                                                                                                              | `true`    |
| type                     | 类型，影响底色与文字颜色                                                                                                                                 | `default` \\| `primary`                                                                                                                                                                                                                              | `default` |
| next-button-props        | “下一步”按钮的属性                                                                                                                                   | ^[Object]`{ children: VueNode \\| string; onClick: Function }`                                                                                                                                   | —         |
| prev-button-props        | “上一步”按钮的属性                                                                                                                                   | ^[Object]`{ children: VueNode \\| string; onClick: Function }`                                                                                                                                   | —         |
| scroll-into-view-options | 是否支持当前元素滚动到视窗内，也可传入配置指定滚动视窗的相关参数，默认跟随 Tour 的 `scrollIntoViewOptions` 属性                                                                      | `boolean` \\| `ScrollIntoViewOptions`                                                                                                                                                                                                                | —         |
| show-close               | 是否显示关闭按钮                                                                                                                                     | `boolean`                                                                                                                                                                                                                                             | `true`    |
| close-icon               | 自定义关闭图标，默认Close                                                                                                                              | `string` \\| `Component`                                                                                                                                                                                                                             | —         |

### TourStep 插槽

| 插槽名     | 描述     |
| ------- | ------ |
| default | 主要描述部分 |
| header  | 头部     |

### TourStep 事件

| 事件名   | 描述         | 参数                                                                          |
| ----- | ---------- | --------------------------------------------------------------------------- |
| close | 关闭引导时的回调函数 | ^[Function]`() => void` |
