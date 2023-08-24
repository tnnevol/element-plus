---
title: Virtualized Select 虚拟化选择器
lang: zh-CN
---

# Virtualized Select 虚拟化选择器

:::tip

这个组件目前在测试当中，如果在使用中发现任何漏洞和问题，请在 [GitHub](https://github.com/element-plus/element-plus/issues) 中提交 issue 以便我们进行处理。

:::

:::tip

在 SSR 场景下，您需要将组件包裹在 `<client-only></client-only>` 之中 (如: [Nuxt](https://nuxt.com/v3)) 和 SSG (例如: [VitePress](https://vitepress.vuejs.org/)).

:::

## 背景

在某些使用情况下，单个选择器可能最终加载数万行数据。 将这么多的数据渲染至 DOM 中可能会给浏览器带来负担，从而造成性能问题。 为了更好的用户和开发者体验，我们决定添加此组件。

## 基础用法

适用广泛的基础选择器

:::demo

select-v2/basic-usage

:::

## 多选

最基础的多选选择器

:::demo

select-v2/multiple

:::

## 隐藏多余标签的多选

默认情况下选中值会以 Tag 的形式展现，你也可以设置`collapse-tags`属性将它们合并为一段文字。 您可以使用 `collapse-tags-tooltip` 属性来启用鼠标悬停折叠文字以显示具体所选值的行为。

:::demo

select-v2/hide-extra-tags

:::

## 可过滤的多选

当选项太多时，你可以使用 `filterable` 选项来启用过滤功能来找到所需的选项。

:::demo

select-v2/filterable

:::

## 禁用选择器本身或选项

您可以选择禁用 Select 或者 Select 中的某个选项。

:::demo

select-v2/disabled

:::

## 给选项进行分组

只要数据格式满足特定要求，我们就可以按照自己的意愿为选项进行分组。

:::demo

select-v2/grouping

:::

## 一键清除

我们可以同时清除所有选定的选项。此设定也适用于单选。

:::demo

select-v2/clearable

:::

## 自定义选项的渲染模板

我们也可以通过自定义模板来渲染自己想要的选项内容。

:::demo

select-v2/customized-option

:::

## 自定义下拉菜单的头部 ^(2.5.2)

您可以自定义下拉菜单的头部。

::: demo 使用slot 自定义内容

select-v2/custom-header

:::

## 自定义下拉菜单的底部 ^(2.5.2)

您可以自定义下拉菜单的底部。

::: demo 使用slot 自定义内容

select-v2/custom-footer

:::

## 创建临时选项

创建并选中未包含在初始选项中的条目。

通过使用 `allow-create` 属性，用户可以通过输入框创建新项目。 为了使 `allow-create` 正常工作， `filterable` 的值必须为 `true`。

:::tip

最好在使用 `allow-create` 属性的同时设置 `:reserve-keyword="false"`。

:::

:::demo

select-v2/allow-create

:::

## 远程搜索

输入关键字以从远程服务器中查找数据。

:::demo 从服务器搜索数据，输入关键字进行查找。为了启用远程搜索，需要将`filterable`和`remote`设置为`true`，同时传入一个`remote-method`。 `remote-method`为一个`Function`，它会在输入值发生变化时调用，参数为当前输入值。

select-v2/remote-search

:::

## 使用 value-key 键属性

当 `options.value` 是一个对象时，您应该为它设置一个唯一的标识名称

::: tip

在 ^(2.4.0) 之前，`value-key`既用作所选对象的唯一值，也用作`options`中表示值的对应 key。 现在 `value-key` 仅作为所选对象的唯一值使用，选项中值的 key 是 `props.value`.

:::

:::demo

select-v2/use-valueKey

:::

## 自定义选项 ^(2.4.2)

当您的 `options` 格式不同于默认格式 您可以通过 `props` 属性自定义 `options`

:::demo

select-v2/props

:::

## 自定义标签 ^(2.5.0)

您可以自定义标签。

:::demo 将自定义的标签插入 `el-select` 的 slot 中即可。 `collapse-tags`, `collapse-tags-tooltip`, `max-collapse-tags` 在此模式下不生效.

select-v2/custom-tag

:::

## 自定义加载 ^(2.5.2)

修改加载区域内容

:::demo

select-v2/custom-loading

:::

## 空值配置^(2.7.0)

若想配置如空字符串为有效值而不是空值，可以配置 `empty-values` 为 `[null, undefined]`.

如果您想要将清空值更改为 `null`, 请设置 `value-on-clear` 为 `null`

:::demo

select-v2/empty-values

:::

## 自定义标签 ^(2.7.4)

您可以自定义标签

:::demo

select-v2/custom-label

:::

## API

### Attributes

| 属性名                                 | 说明                                                                                                         | 类型                                                                                                                                                                                     | 默认值                                            |
| ----------------------------------- | ---------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ---------------------------------------------- |
| model-value / v-model               | 选中项绑定值                                                                                                     | ^[string] / ^[number] / ^[boolean] / ^[object] / ^[array]                                                                                                                              | —                                              |
| options                             | 选项的数据源， `value` 的 key 和 `label` 可以通过 `props`自定义.                                                           | ^[array]                                                                                                                                                                               | —                                              |
| props ^(2.4.2)                      | 配置选项，具体看下表                                                                                                 | ^[object]                                                                                                                                                                              | —                                              |
| multiple                            | 是否多选                                                                                                       | ^[boolean]                                                                                                                                                                             | false                                          |
| disabled                            | 是否禁用                                                                                                       | ^[boolean]                                                                                                                                                                             | false                                          |
| value-key                           | 作为 value 唯一标识的键名，绑定值为对象类型时必填                                                                               | ^[string]                                                                                                                                                                              | value                                          |
| size                                | 组件大小                                                                                                       | ^[enum]`'' \| 'large' \| 'default' \| 'small'`                                                                                                                                      | ''                                             |
| clearable                           | 是否可以清空选项                                                                                                   | ^[boolean]                                                                                                                                                                             | false                                          |
| clear-icon                          | 自定义清除图标                                                                                                    | ^[string] / ^[object]`Component`                                                                                                                                                       | CircleClose                                    |
| collapse-tags                       | 多选时是否将选中值按文字的形式展示                                                                                          | ^[boolean]                                                                                                                                                                             | false                                          |
| multiple-limit                      | 多选时可被选择的最大数目。 当被设置为0时，可被选择的数目不设限。                                                                          | ^[number]                                                                                                                                                                              | 0                                              |
| name                                | 选择器的原生name属性                                                                                               | ^[string]                                                                                                                                                                              | —                                              |
| effect                              | tooltip 主题，内置了 `dark` / `light` 两种                                                                         | ^[enum]`'dark' \| 'light'` / ^[string]                                                                                                                                                | light                                          |
| autocomplete                        | 自动完成选择输入                                                                                                   | ^[string]                                                                                                                                                                              | off                                            |
| placeholder                         | 占位文字                                                                                                       | ^[string]                                                                                                                                                                              | Please select                                  |
| filterable                          | 是否可筛选                                                                                                      | ^[boolean]                                                                                                                                                                             | false                                          |
| allow-create                        | 是否允许创建新条目， 当使用该属性时，`filterable`必须设置为`true`                                                                 | ^[boolean]                                                                                                                                                                             | false                                          |
| filter-method                       | 自定义筛选方法                                                                                                    | ^[Function]`() => void`                                                                                                                                                             | —                                              |
| loading                             | 是否从远程加载数据                                                                                                  | ^[boolean]                                                                                                                                                                             | false                                          |
| loading-text                        | 从服务器加载数据时显示的文本，默认为“Loading”                                                                                | ^[string]                                                                                                                                                                              | —                                              |
| reserve-keyword                     | 筛选时，是否在选择选项后保留关键字                                                                                          | ^[boolean]                                                                                                                                                                             | true                                           |
| no-match-text                       | 搜索条件无匹配时显示的文字，也可以使用 `empty` 插槽设置，默认是 “No matching data'”                                                   | ^[string]                                                                                                                                                                              | —                                              |
| no-data-text                        | 当在没有数据时显示的文字，你同时可以使用empty插槽进行设置。                                                                           | ^[string]                                                                                                                                                                              | No Data                                        |
| popper-class                        | 选择器下拉菜单的自定义类名                                                                                              | ^[string]                                                                                                                                                                              | ''                                             |
| popper-append-to-body ^(deprecated) | 是否将弹出框插入至 body 元素 当弹出框的位置出现问题时，你可以尝试将该属性设置为false。                                                          | ^[boolean]                                                                                                                                                                             | false                                          |
| teleported                          | 是否将下拉列表元素插入 append-to 指向的元素下                                                                               | ^[boolean]                                                                                                                                                                             | true                                           |
| persistent                          | 当下拉选择器未被激活并且`persistent`设置为`false`，选择器会被删除。                                                                | ^[boolean]                                                                                                                                                                             | true                                           |
| popper-options                      | [popper.js](https://popper.js.org/docs/v2/) parameters                                                     | ^[object]refer to [popper.js](https://popper.js.org/docs/v2/) doc                                                                                                                      | {}                                             |
| automatic-dropdown                  | 对于不可搜索的 Select，是否在输入框获得焦点后自动弹出选项菜单                                                                         | ^[boolean]                                                                                                                                                                             | false                                          |
| height                              | 下拉菜单的高度，每一个选项为34px                                                                                         | ^[number]                                                                                                                                                                              | 274                                            |
| item-height                         | 下拉项的高度                                                                                                     | ^[number]                                                                                                                                                                              | 34                                             |
| scrollbar-always-on                 | 是否总是展示滚动条                                                                                                  | ^[boolean]                                                                                                                                                                             | false                                          |
| remote                              | 是否从服务器获取数据                                                                                                 | ^[boolean]                                                                                                                                                                             | false                                          |
| remote-method                       | 当输入值发生变化时触发的函数。 它的参数就是当前的输入值。 当`filterable`设置为 true 时才会生效                                                  | ^[Function]`(keyword: string) => void`                                                                                                                                              | —                                              |
| validate-event                      | 是否触发表单验证                                                                                                   | ^[boolean]                                                                                                                                                                             | true                                           |
| placement                           | 下拉框出现的位置                                                                                                   | ^[enum]`'top' \| 'top-start' \| 'top-end' \| 'bottom' \| 'bottom-start' \| 'bottom-end' \| 'left' \| 'left-start' \| 'left-end' \| 'right' \| 'right-start' \| 'right-end'` | bottom-start                                   |
| fallback-placements ^(2.5.6)        | dropdown 可用的 positions 请查看[popper.js 文档](https://popper.js.org/docs/v2/modifiers/flip/#fallbackplacements) | ^[array]`Placement[]`                                                                                                                                                                  | ['bottom-start', 'top-start', 'right', 'left'] |
| collapse-tags-tooltip ^(2.3.0)      | 当鼠标悬停于折叠标签的文本时，是否显示所有选中的标签。 只有当 `collapse-tags` 设置为 true 时才会生效。                                            | ^[boolean]                                                                                                                                                                             | false                                          |
| max-collapse-tags ^(2.3.0)          | 需要显示的 Tag 的最大数量。 只有当 `collapse-tags` 设置为 true 时才会生效。                                                       | ^[number]                                                                                                                                                                              | 1                                              |
| tag-type ^(2.5.0)                   | 标签类型                                                                                                       | ^[enum]`'' \| 'success' \| 'info' \| 'warning' \| 'danger'`                                                                                                                        | info                                           |
| aria-label ^(a11y) ^(2.5.0)         | 等价于原生 input `aria-label` 属性                                                                                | ^[string]                                                                                                                                                                              | —                                              |
| empty-values ^(2.7.0)               | 组件的空值配置 [参考config-provider](/en-US/component/config-provider#empty-values-configurations)                  | ^[array]                                                                                                                                                                               | —                                              |
| value-on-clear ^(2.7.0)             | 清空选项的值 [参考 config-provider](/en-US/component/config-provider#empty-values-configurations)                  | ^[string] / ^[number] / ^[boolean] / ^[Function]                                                                                                                                       | —                                              |

### props

| Attribute | 说明                  | Type      | Default  |
| --------- | ------------------- | --------- | -------- |
| value     | 指定选项的值为选项对象的某个属性值   | ^[string] | value    |
| label     | 指定节点标签为节点对象的某个属性值   | ^[string] | label    |
| options   | 指定选项的子选项为选项对象的某个属性值 | ^[string] | options  |
| disabled  | 指定选项的禁用为选项对象的某个属性值  | ^[string] | disabled |

### 事件

| 插槽名            | 说明                                               | 类型                                          |
| -------------- | ------------------------------------------------ | ------------------------------------------- |
| change         | 当所选值更改时触发，参数是当前选中的值                              | ^[Function]`(val: any) => void`          |
| visible-change | 当下拉菜单出现/消失时触发器, 当它出现时, 参数将是 `true`, 否则将是 `false` | ^[Function]`(visible: boolean) => void`  |
| remove-tag     | 当一个标签在多个模式下被移除时触发，参数将被移除标签值                      | ^[Function]`(tagValue: any) => void`     |
| clear          | 可清空的单选模式下用户点击清空按钮时触发                             | ^[Function]`() => void`                  |
| blur           | 当选择器的输入框失去焦点时触发                                  | ^[Function]`(event: FocusEvent) => void` |
| focus          | 当选择器的输入框获得焦点时触发                                  | ^[Function]`(event: FocusEvent) => void` |

### Slots

| 名称               | 详情                     |
| ---------------- | ---------------------- |
| default          | 自定义 Option 模板          |
| header ^(2.5.2)  | 下拉列表顶部的内容              |
| footer ^(2.5.2)  | 下拉列表底部的内容              |
| empty            | 自定义当选项为空时的内容           |
| prefix           | 输入框的前缀                 |
| tag ^(2.5.0)     | select 组件自定义标签内容       |
| loading ^(2.5.2) | select 组件自定义 loading内容 |
| label ^(2.7.4)   | select 组件自定义标签内容       |

### Exposes

| 方法    | 描述                  | 类型                         |
| ----- | ------------------- | -------------------------- |
| focus | 使选择器的输入框获取焦点        | ^[Function]`() => void` |
| blur  | 使选择器的输入框失去焦点，并隐藏下拉框 | ^[Function]`() => void` |
