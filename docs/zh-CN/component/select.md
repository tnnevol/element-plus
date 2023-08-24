---
title: Select 选择器
lang: zh-CN
---

# Select 选择器

当选项过多时，使用下拉菜单展示并选择内容。

:::tip

在 SSR 场景下，您需要将组件包裹在 `<client-only></client-only>` 之中 (如: [Nuxt](https://nuxt.com/v3)) 和 SSG (e.g: [VitePress](https://vitepress.vuejs.org/)).

:::

## 基础用法

:::demo 适用广泛的基础单选 `v-model` 的值为当前被选中的 `el-option` 的 value 属性值

select/basic-usage

:::

## 有禁用选项

:::demo 在 `el-option` 中，设定 `disabled` 值为 true，即可禁用该选项

select/disabled-option

:::

## 禁用状态

禁用整个选择器组件

:::demo 为 `el-select` 设置 `disabled`属性，则整个选择器不可用。

select/disabled

:::

## 可清空单选

您可以使用清除图标来清除选择。

:::demo 为 `el-select` 设置 `clearable` 属性，则可将选择器清空。 需要注意的是，`clearable` 属性仅适用于单选。

select/clearable

:::

## 基础多选

多选选择器使用 tag 组件来展示已选中的选项。

:::demo 为 `el-select` 设置 `multiple` 属性即可启用多选， 此时 `v-model` 的值为当前选中值所组成的数组。 默认情况下选中值会以 Tag 组件的形式展现， 你也可以设置 `collapse-tags` 属性将它们合并为一段文字。 您可以使用 `collapse-tags-tooltip` 属性来启用鼠标悬停折叠文字以显示具体所选值的行为。

select/multiple

:::

## 自定义模板

你可以自定义如何来渲染每一个选项。

:::demo 将自定义的 HTML 模板插入 `el-option` 的 slot 中即可。

select/custom-template

:::

## 将选项进行分组

你可以为选项进行分组来区分不同的选项

:::demo 使用 `el-option-group` 对备选项进行分组，它的 `label` 属性为分组名

select/grouping

:::

## 筛选选项

可以利用筛选功能快速查找选项。

:::demo 为`el-select`添加`filterable`属性即可启用搜索功能。 默认情况下，Select 会找出所有 `label` 属性包含输入值的选项。 如果希望使用其他的搜索逻辑，可以通过传入一个 `filter-method` 来实现。 `filter-method` 为一个 `Function`，它会在输入值发生变化时调用，参数为当前输入值。

select/filterable

:::

## 远程搜索

输入关键字以从远程服务器中查找数据。

:::demo 从服务器搜索数据，输入关键字进行查找。为了启用远程搜索，需要将`filterable`和`remote`设置为`true`，同时传入一个`remote-method`。 `remote-method`为一个`Function`，它会在输入值发生变化时调用，参数为当前输入值。 需要注意的是，如果 `el-option` 是通过 `v-for` 指令渲染出来的，此时需要为 `el-option` 添加 `key` 属性， 且其值需具有唯一性，比如这个例子中的 `item.value`。

select/remote-search

:::

## 创建新的选项

创建并选中未包含在初始选项中的条目。

:::demo 通过使用 `allow-create` 属性，用户可以通过输入框创建新项目。 为了使 `allow-create` 正常工作， `filterable` 的值必须为 `true`。 本例还使用了 `default-first-option` 属性， 在该属性为 `true` 的情况下，按下回车就可以选中当前选项列表中的第一个选项，无需使用鼠标或键盘方向键进行定位。

select/allow-create

:::

## 使用值键 value-key 属性

如果 Select 的绑定值为对象类型，请务必指定 `value-key` 作为它的唯一性标识。

:::demo 通过使用 `value-key` 属性，可以正确处理带有重复label的数据。 这样虽然`label` 是重复的，但任可通过 `id` 来确认唯一性。

select/value-key

:::

## Select API

### Select Attributes

| 属性名                             | 说明                                                                                                                    | 类型                                                                                                                                                                                     | Default      |
| ------------------------------- | --------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------ |
| model-value / v-model           | 选中项绑定值                                                                                                                | ^[string] / ^[number] / ^[boolean] / ^[object] / ^[array]                                                                                                                              | —            |
| multiple                        | 是否多选                                                                                                                  | ^[boolean]                                                                                                                                                                             | false        |
| disabled                        | 是否禁用                                                                                                                  | ^[boolean]                                                                                                                                                                             | false        |
| value-key                       | 作为 value 唯一标识的键名，绑定值为对象类型时必填                                                                                          | ^[string]                                                                                                                                                                              | value        |
| size                            | 输入框尺寸                                                                                                                 | ^[enum]`'' \| 'large' \| 'default' \| 'small'`                                                                                                                                      | —            |
| clearable                       | 是否可以清空选项                                                                                                              | ^[boolean]                                                                                                                                                                             | false        |
| collapse-tags                   | 多选时是否将选中值按文字的形式展示                                                                                                     | ^[boolean]                                                                                                                                                                             | false        |
| collapse-tags-tooltip ^(2.3.0)  | 当鼠标悬停于折叠标签的文本时，是否显示所有选中的标签。 要使用此属性，`collapse-tags`属性必须设定为 true                                                        | ^[boolean]                                                                                                                                                                             | false        |
| multiple-limit                  | `multiple` 属性设置为 `true` 时，代表多选场景下用户最多可以选择的项目数， 为 0 则不限制                                                               | ^[number]                                                                                                                                                                              | 0            |
| name                            | Select 输入框的原生 name 属性                                                                                                 | ^[string]                                                                                                                                                                              | —            |
| effect                          | tooltip theme, built-in theme: `dark` / `light`                                                                       | ^[enum]`'dark' \| 'light'` / ^[string]                                                                                                                                                | light        |
| autocomplete                    | Select 输入框的原生 autocomplete 属性                                                                                         | ^[string]                                                                                                                                                                              | off          |
| placeholder                     | placeholder, default is 'Select'                                                                                      | ^[string]                                                                                                                                                                              | —            |
| filterable                      | Select 组件是否可筛选                                                                                                        | ^[boolean]                                                                                                                                                                             | false        |
| allow-create                    | 是否允许用户创建新条目， 只有当 `filterable` 设置为 true 时才会生效。                                                                         | ^[boolean]                                                                                                                                                                             | false        |
| filter-method                   | 自定义筛选方法                                                                                                               | ^[Function]`() => void`                                                                                                                                                             | —            |
| remote                          | 其中的选项是否从服务器远程加载                                                                                                       | ^[boolean]                                                                                                                                                                             | false        |
| remote-method                   | 自定义远程搜索方法                                                                                                             | ^[Function]`() => void`                                                                                                                                                             | —            |
| remote-show-suffix              | 远程搜索方法显示后缀图标                                                                                                          | ^[boolean]                                                                                                                                                                             | false        |
| loading                         | 是否正在从远程获取数据                                                                                                           | ^[boolean]                                                                                                                                                                             | false        |
| loading-text                    | displayed text while loading data from server, default is 'Loading'                                                   | ^[string]                                                                                                                                                                              | —            |
| no-match-text                   | displayed text when no data matches the filtering query, you can also use slot `empty`, default is 'No matching data' | ^[string]                                                                                                                                                                              | —            |
| no-data-text                    | displayed text when there is no options, you can also use slot `empty`, default is 'No data'                          | ^[string]                                                                                                                                                                              | —            |
| popper-class                    | 选择器下拉菜单的自定义类名                                                                                                         | ^[string]                                                                                                                                                                              | ''           |
| reserve-keyword                 | 当 `multiple` 和 `filter`被设置为 true 时，是否在选中一个选项后保留当前的搜索关键词                                                               | ^[boolean]                                                                                                                                                                             | true         |
| default-first-option            | 是否在输入框按下回车时，选择第一个匹配项。 需配合 `filterable` 或 `remote` 使用                                                                  | ^[boolean]                                                                                                                                                                             | false        |
| teleported                      | whether select dropdown is teleported to the body                                                                     | ^[boolean]                                                                                                                                                                             | true         |
| persistent                      | when select dropdown is inactive and `persistent` is `false`, select dropdown will be destroyed                       | ^[boolean]                                                                                                                                                                             | true         |
| automatic-dropdown              | for non-filterable Select, this prop decides if the option menu pops up when the input is focused                     | ^[boolean]                                                                                                                                                                             | false        |
| clear-icon                      | custom clear icon component                                                                                           | ^[string] / ^[object]`Component`                                                                                                                                                       | CircleClose  |
| fit-input-width                 | whether the width of the dropdown is the same as the input                                                            | ^[boolean]                                                                                                                                                                             | false        |
| suffix-icon                     | custom suffix icon component                                                                                          | ^[string] / ^[object]`Component`                                                                                                                                                       | ArrowDown    |
| suffix-transition ^(deprecated) | animation when dropdown appears/disappears icon                                                                       | ^[boolean]                                                                                                                                                                             | true         |
| tag-type                        | tag type                                                                                                              | ^[enum]`'' \| 'success' \| 'info' \| 'warning' \| 'danger'`                                                                                                                        | info         |
| validate-event                  | whether to trigger form validation                                                                                    | ^[boolean]                                                                                                                                                                             | true         |
| placement ^(2.2.17)             | position of dropdown                                                                                                  | ^[enum]`'top' \| 'top-start' \| 'top-end' \| 'bottom' \| 'bottom-start' \| 'bottom-end' \| 'left' \| 'left-start' \| 'left-end' \| 'right' \| 'right-start' \| 'right-end'` | bottom-start |
| max-collapse-tags ^(2.3.0)      | the max tags number to be shown. To use this, `collapse-tags` must be true                                            | ^[number]                                                                                                                                                                              | 1            |
| popper-options                  | [popper.js](https://popper.js.org/docs/v2/) parameters                                                                | ^[object]refer to [popper.js](https://popper.js.org/docs/v2/) doc                                                                                                                      | {}           |

:::warning

`suffix-transition` has been **deprecated**, and **will be** removed in ^(2.4.0), please use override style scheme.

:::

### Select Events

| 事件名            | 说明                   | Type                                        |
| -------------- | -------------------- | ------------------------------------------- |
| change         | 选中值发生变化时触发           | ^[Function]`(value: any) => void`        |
| visible-change | 下拉框出现/隐藏时触发          | ^[Function]`(visible: boolean) => void`  |
| remove-tag     | 多选模式下移除tag时触发        | ^[Function]`(tagValue: any) => void`     |
| clear          | 可清空的单选模式下用户点击清空按钮时触发 | ^[Function]`() => void`                  |
| blur           | 当 input 失去焦点时触发      | ^[Function]`(event: FocusEvent) => void` |
| focus          | 当 input 获得焦点时触发      | ^[Function]`(event: FocusEvent) => void` |

### Select Slots

| 插槽名     | 说明                    | 子标签                   |
| ------- | --------------------- | --------------------- |
| default | option component list | Option Group / Option |
| prefix  | Select 组件头部内容         | —                     |
| empty   | 无选项时的列表               | —                     |

### Select Exposes

| Method | 说明                                              | 类型                         |
| ------ | ----------------------------------------------- | -------------------------- |
| focus  | focus the Input component                       | ^[Function]`() => void` |
| blur   | blur the Input component, and hide the dropdown | ^[Function]`() => void` |

## Option Group API

### Option Group Attributes

| 插槽名      | 说明                                           | Type       | Default |
| -------- | -------------------------------------------- | ---------- | ------- |
| label    | name of the group                            | ^[string]  | —       |
| disabled | whether to disable all options in this group | ^[boolean] | false   |

### Option Group Slots

| 属性名     | 说明                        | Subtags |
| ------- | ------------------------- | ------- |
| default | customize default content | Option  |

## Option API

### Option Attributes

| 插槽名      | 说明                                          | Type                                           | Default |
| -------- | ------------------------------------------- | ---------------------------------------------- | ------- |
| value    | value of option                             | ^[string] / ^[number] / ^[boolean] / ^[object] | —       |
| label    | label of option, same as `value` if omitted | ^[string] / ^[number]                          | —       |
| disabled | whether option is disabled                  | ^[boolean]                                     | false   |

### Option Slots

| Name    | 说明                        |
| ------- | ------------------------- |
| default | customize default content |
