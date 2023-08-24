---
title: Watermark 水印
lang: zh-CN
---

# Watermark 水印

在页面上添加文本或图片等水印信息

## 基础用法

基础用法

:::demo

watermark/basic

:::

## 多行水印

使用 "content" 设置一个字符串数组来指定多行文本水印内容

:::demo

watermark/multi-line

:::

## 图片水印

通过 'image' 指定图像地址。 为了确保图像清晰展示而不是被拉伸，请设置宽度和高度，建议使用至少两倍的宽度和高度的图片来保证显示效果。

:::demo

watermark/image

:::

## 自定义配置

配置自定义参数预览水印效果。

:::demo

watermark/custom

:::

## API

### 属性

| 属性名     | 描述                           | 类型                            | 默认值                              |
| ------- | ---------------------------- | ----------------------------- | -------------------------------- |
| width   | 水印的宽度， `content` 的默认值是它自己的宽度 | ^[number]                     | 120                              |
| height  | 水印的高度， `content` 的默认值是它自己的高度 | ^[number]                     | 64                               |
| rotate  | 水印的旋转角度, 单位 `°`              | ^[number]                     | -22                              |
| zIndex  | 水印元素的z-index值                | ^[number]                     | 9                                |
| image   | 水印图片，建议使用 2x 或 3x 图像         | ^[string]                     | —                                |
| content | 水印文本内容                       | ^[string]/^[object]`string[]` | —                                |
| font    | 文字样式                         | [Font](#font)                 | [Font](#font)                    |
| gap     | 水印之间的间距                      | ^[object]`[number, number]`   | \[100, 100\]                   |
| offset  | 水印从容器左上角的偏移 默认值为 `gap/2`     | ^[object]`[number, number]`   | \[gap\[0\]/2, gap\[1\]/2\] |

### Font

| 名称           | 详情   | 类型                                                                                        | 默认              |
| ------------ | ---- | ----------------------------------------------------------------------------------------- | --------------- |
| color        | 字体颜色 | ^[string]                                                                                 | rgba(0,0,0,.15) |
| fontSize     | 字体大小 | ^[number]                                                                                 | 16              |
| fontWeight   | 字重   | ^[enum]`'normal' \| 'light' \| 'weight' \| number`                                     | normal          |
| fontFamily   | 字体   | ^[string]                                                                                 | sans-serif      |
| fontStyle    | 字体样式 | ^[enum]`'none' \| 'normal' \| 'italic' \| 'oblique'`                                   | normal          |
| textAlign    | 文本对齐 | ^[enum]`'left' \| 'right' \| 'center'\| 'start' \| 'end'`                             | center          |
| textBaseline | 文本基线 | ^[enum]`'top' \| 'hanging' \| 'middle' \| 'alphabetic' \| 'ideographic' \| 'bottom'` | hanging         |

### Slots

| 名称 | 详情      |
| -- | ------- |
| 默认 | 添加水印的容器 |
