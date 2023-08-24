---
title: Virtualized Table 虚拟化表格
lang: zh-CN
---

# Virtualized Table 虚拟化表格 ^(beta)

Along with evolutionary web development, table component has always been the most popular component in our web apps especially for dashboards, data analysis. For [Table V1](./table.md), with even just 1000 records of data, it can be very annoying when using it, because of the poor performance.

通过虚拟化表格组件，超大数据渲染将不再是一个头疼的问题。

:::tip

该组件**仍在测试中**，生产环境使用可能有风险。 If you find any bugs or issues, please report them at [GitHub](https://github.com/element-plus/element-plus/issues) for us to fix. Also there were some APIs which are not mentioned in this documentation, some of them were not fully developed yet, which is why they are not mentioned here.

**Even though** Virtualized Table is efficient, when the data load is too large, your **network** and **memory size** can become the bottleneck of your app. So keep in mind that Virtualized Table is never the ultimate solution for everything, consider paginating your data, adding filters etc.

:::

:::tip

在 SSR 场景下，您需要将组件包裹在 `<client-only></client-only>` 之中 (如: [Nuxt](https://nuxt.com/v3)) 和 SSG (例如: [VitePress](https://vitepress.vuejs.org/)).

:::

## 基础用法

Let's demonstrate the performance of the Virtualized Table by rendering a basic example with 10 columns and 1000 rows.

:::demo

table-v2/basic

:::

## 自动调整大小

When you do not want to manually pass the `width` and `height` properties to the table, you can wrap the table component with the AutoResizer. This will automatically update the width and height for you.

尝试调整您的浏览器大小来看看它是如何工作的。

:::tip

由于 `AutoResizer` 组件的默认高度是 100%，所以请确保该组件的父元素**拥有固定的高度值**。 或者，您可以通过将 `style` 属性传递到 `AutoResizer` 来定义它。

:::

:::demo

table-v2/auto-resizer

:::

## 自定义单元格渲染器{#customize-cell-renderer}

当然，您可以根据您的需要呈现表格单元格。 这是如何自定义您的单元格的简单例子。

:::demo

table-v2/cell-templating

:::

## 带有选择的表格

使用自定义的单元格渲染来给表格组件添加选择的能力。

:::demo

table-v2/selection

:::

## 可编辑单元格

类似上面添加筛选框的方法，我们可以用同样的方法实现可编辑单元格。

:::demo

table-v2/inline-editing

:::

## 带状态的表格

可将表格内容 highlight 显示，方便区分「成功、信息、警告、危险」等内容。

要自定义行的外观，请使用 `row-class-name` 属性。 For example, every 10th row is highlighted using the `bg-blue-200` class, and every 5th row with the `bg-red-100` class.

:::demo

table-v2/row-class

:::

## 表格行的粘性布局

You can make some rows stick to the top of the table, and that can be very easily achieved by using the `fixed-data` attribute.

You can dynamically set the sticky row based on scroll events, as shown in this example.

:::demo

table-v2/sticky-rows

:::

## 固定列表格

If you want to have columns stick to the left or right for some reason, you can achieve this by adding special attributes to the table.

您可以设置该行的` fixed` 属性为 `true` （代表`FixedDir.LEFT`）、`FixedDir.LEFT` 或 `FixedDir.RIGHT`

:::demo

table-v2/fixed-columns

:::

## 表头分组

By customizing your header renderer, you can group your header as shown in this example.

:::tip

In this case we used `JSX` feature which is not supported in the playground. You may try them out in your local environment or on online IDEs such as `codesandbox`.

建议您使用 JSX 使用您的表格组件，因为它包含 VNode 操作。

:::

:::demo

table-v2/grouping-header

:::

## 过滤器

Virtualized Table provides custom header renderers for creating customized headers. We can then utilize these to render filters.

:::demo

table-v2/filter

:::

## 可排序表格

您可以使用排序状态来对表格进行排序。

:::demo

table-v2/sort

:::

## 受控的排序

You can define multiple sortable columns as needed. Keep in mind that if you define multiple sortable columns, the UI may appear confusing to your users, as it becomes unclear which column is currently being sorted.

:::demo

table-v2/controlled-sort

:::

## 高亮显示鼠标悬停单元格

When dealing with a large list, it's easy to lose track of the current row and column you are visiting. In such cases, using this feature can be very helpful.

:::demo

table-v2/cross-hovering

:::

## 横跨列

The virtualized table doesn't use the built-in `table` element, so `colspan` and `rowspan` behave a bit differently compared to [TableV1](./table.md). However, with a customized row renderer, these features can still be implemented. In this section, we'll demonstrate how to achieve this.

:::demo

table-v2/colspan

:::

## 纵跨行

Since we have covered [Colspan](#colspan), it's worth noting that we also have row span. It's a little bit different from colspan but the idea is basically the same.

:::demo

table-v2/rowspan

:::

## 同时跨行和跨列

我们当然可以同时使用横跨列与纵跨行来满足您的业务需求！

:::demo

table-v2/spans

:::

## 树形数据

Virtual Table can also render data in a tree-like structure. By clicking the arrow icon, you can expand or collapse the tree nodes.

:::demo

table-v2/tree-data

:::

## 动态高度行

Virtual Table is capable of rendering rows with dynamic heights. If you're working with data and are uncertain about the content size, this feature is ideal for rendering rows that adjust to the content's height. To enable this, pass down the `estimated-row-height` attribute. The closer the estimated height matches the actual content, the smoother the rendering experience.

:::tip

Each row's height is dynamically measured during rendering the rows. As a result, if you're trying to display a large amount of data, the UI **might be** bouncing.

:::

:::demo

table-v2/dynamic-height

:::

## 可展开的附加信息

Using dynamic height rendering, you can also display a detailed view within the table.

:::demo

table-v2/detailed-view

:::

## 自定义页脚

Render a customized footer when you want to show a concluding message or information.

:::demo

table-v2/footer

:::

## 自定义空元素渲染器

Render a customized empty element.

:::demo

table-v2/empty

:::

## 浮动遮罩层

Render an overlay on top of the table when you want to show a loading indicator or something else.

:::demo

table-v2/overlay

:::

## 手动滚动

Use the methods provided by Table V2 to scroll manually/programmatically with desired offset/rows.

:::tip

`scrollToRow` 的第二个参数代表滚动策略，计算了要滚动的位置，其默认值是 `auto`。 If you wish to scroll to a specific position, you can define the strategy yourself. 可用的选项是 `"auto" | "center" | "end" | "start" | "smart"`

`smart` 和`auto` 之间的区别是， `auto` 是 `smart` 滚动策略的子集。

:::

:::demo

table-v2/manual-scroll

:::

## TableV2 属性

| 属性名                       | 描述说明                                                                                                       | 类型                                                     | 默认值       |
| ------------------------- | ---------------------------------------------------------------------------------------------------------- | ------------------------------------------------------ | --------- |
| cache                     | Number of rows rendered in advance to boost the performance                                                | Number                                                 | 2         |
| estimated-row-height      | 渲染动态的单元格的预估高度                                                                                              | Number                                                 | -         |
| header-class              | header 部分的自定义 class 名                                                                                      | String/Function\<[HeaderClassGetter](#typings)\>     | -         |
| header-props              | header 部分的自定义 props 名                                                                                      | Object/Function\<[HeaderPropsGetter](#typings)\>     | -         |
| header-cell-props         | header cell 部分的自定义 props 名                                                                                 | Object/Function\<[HeaderCellPropsGetter](#typings)\> | -         |
| header-height             | The height of the header is set by `height`. If given an array, it renders header rows equal to its length | Number/Array\<Number\>                               | 50        |
| footer-height             | The height of the footer element, when provided, will be part to the calculation of the table's height.    | Number                                                 | 0         |
| row-class                 | row wrapper 部分的自定义 class 名                                                                                 | String/Function\<[RowClassGetter](#typings)\>        | -         |
| row-key                   | The key of each row, if not provided, will be the index of the row                                         | String/Symbol/Number                                   | id        |
| row-props                 | row component 部分的自定义 class 名                                                                               | Object/Function\<[RowPropsGetter](#typings)\>        | -         |
| row-height                | 每行的高度, 用于计算表的总高度                                                                                           | Number                                                 | 50        |
| cell-props                | 每个单元格 cell 的自定义 props (除了 header cell 以外)                                                                  | Object/Function\<[CellPropsGetter](#typings)\>       | -         |
| columns                   | 列 column 的配置数组                                                                                             | Array\<[Column](#column-attribute)\>                 | -         |
| data                      | 要在表中渲染的数据数组                                                                                                | Array\<[Data](#typings)\>                            | []        |
| data-getter               | A method to customize data fetch from the data source.                                                     | Function                                               | -         |
| fixed-data                | 渲染行在表格主内容上方和 header 下方区域的数据                                                                                | Array\<[Data](#typings)\>                            | -         |
| expand-column-key         | 列的 key 来标记哪个行可以被展开                                                                                         | String                                                 | -         |
| expanded-row-keys         | 存放行展开状态的 key 的数组，可以和  `v-model` 搭配使用                                                                       | Array\<[KeyType](#typings)\>                         | -         |
| default-expanded-row-keys | 默认展开的行的 key 的数组, **这个数据不是响应式的**                                                                            | Array\<[KeyType](#typings)\>                         | -         |
| class                     | Class name for the virtual table, will be applied to all three tables (left, right, main)                  | String/Array/Object                                    | -         |
| fixed                     | Flag indicates the table column's width to be fixed or flexible.                                           | Boolean                                                | false     |
| width ^(required)         | 表格的宽度                                                                                                      | Number                                                 | -         |
| height ^(required)        | 表格的高度                                                                                                      | Number                                                 | -         |
| max-height                | 表格的最大高度                                                                                                    | Number                                                 | -         |
| h-scrollbar-size          | 配置表格的水平滚动条大小，防止水平和垂直滚动条重叠。                                                                                 | Number                                                 | 6         |
| v-scrollbar-size          | 配置表格的垂直滚动条大小，防止水平和垂直滚动条重叠。                                                                                 | Number                                                 | 6         |
| scrollbar-always-on       | 如果开启，滚动条将一直显示，反之只会在鼠标经过时显示。                                                                                | Boolean                                                | false     |
| sort-by                   | 排序方式                                                                                                       | Object\<[SortBy](#typings)\>                         | {}        |
| sort-state                | 多个排序                                                                                                       | Object\<[SortState](#typings)\>                      | undefined |

## TableV2 插槽

| 插槽名         | 参数                              |
| ----------- | ------------------------------- |
| cell        | [CellSlotProps](#typings)       |
| header      | [HeaderSlotProps](#typings)     |
| header-cell | [HeaderCellSlotProps](#typings) |
| row         | [RowSlotProps](#typings)        |
| footer      | -                               |
| empty       | -                               |
| overlay     | -                               |

## TableV2 事件

| 事件名                  | 描述                      | 参数                                         |
| -------------------- | ----------------------- | ------------------------------------------ |
| column-sort          | 列排序时调用                  | Object\<ColumnSortParam\>                |
| expanded-rows-change | 行展开状态改变时触发              | `Array<KeyType>`                     |
| end-reached          | 到达表格末尾时触发               | -                                          |
| scroll               | Invoked after scrolling | Object\<[ScrollParams](#typings)\>       |
| rows-rendered        | 当行被渲染后触发                | Object\<[RowsRenderedParams](#typings)\> |
| row-expand           | 点击箭头图标展开/折叠树节点时触发       | Object\<[RowExpandParams](#typings)\>    |
| row-event-handlers   | 当每行添加了一系列事件处理器时触发       | Object\<[RowEventHandlers](#typings)\>   |

## TableV2 方法

| 事件名          | 描述              | 参数                                                                             |
| ------------ | --------------- | ------------------------------------------------------------------------------ |
| scrollTo     | 滚动到给定位置         | `{ scrollLeft?: number, scrollTop?: number}`                                   |
| scrollToLeft | 滚动到给定的水平位置      | `scrollLeft: number`                                                           |
| scrollToTop  | 滚动到给定的垂直位置      | `scrollTop: number`                                                            |
| scrollToRow  | 使用给定的滚动策略滚动至指定行 | `row: number, strategy?: "auto" \|"center" \| "end" \| "start" \| "smart"` |

:::tip

Note that these are `JavaScript` Objects, so you **CANNOT USE** kebab-case for these attributes

:::

## Column 属性

| 属性名                | 描述                                                                    | 类型                                                                                                                                                               | 默认值   |
| ------------------ | --------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----- |
| align              | 表格单元格内容对齐方式                                                           | [Alignment](https://github.com/element-plus/element-plus/blob/b92b22932758f0ddea98810ae248f6ca62f77e25/packages/components/table-v2/src/constants.ts#L6)         | left  |
| class              | 列的类名                                                                  | String                                                                                                                                                           | -     |
| fixed              | 固定列位置                                                                 | Boolean/[FixedDir](https://github.com/element-plus/element-plus/blob/b92b22932758f0ddea98810ae248f6ca62f77e25/packages/components/table-v2/src/constants.ts#L11) | false |
| flexGrow           | CSSProperties flex grow, Only useful when this is not a fixed table   | Number                                                                                                                                                           | 0     |
| flexShrink         | CSSProperties flex shrink, Only useful when this is not a fixed table | Number                                                                                                                                                           | 1     |
| headerClass        | 自定义 header 头部类名                                                       | String                                                                                                                                                           | -     |
| hidden             | 此列是否不可见                                                               | Boolean                                                                                                                                                          | -     |
| style              | 自定义列单元格的类名，将会与 gird 单元格合并                                             | CSSProperties                                                                                                                                                    | -     |
| sortable           | 设置列是否可排序                                                              | Boolean                                                                                                                                                          | -     |
| title              | Header 头部单元格中的默认文本                                                    | String                                                                                                                                                           | -     |
| maxWidth           | 列的最大宽度                                                                | String                                                                                                                                                           | -     |
| minWidth           | 列的最小宽度                                                                | String                                                                                                                                                           | -     |
| width ^(required)  | 列宽度                                                                   | Number                                                                                                                                                           | -     |
| cellRenderer       | 自定义单元格渲染器                                                             | VueComponent/(props: [CellRenderProps](#typings)) => VNode                                                                                                       | -     |
| headerCellRenderer | 自定义头部渲染器                                                              | VueComponent/(props: [HeaderRenderProps](#typings)) => VNode                                                                                                     | -     |

## Typings{#typings}

<details>
<summary>显示类型声明</summary>

```ts
type HeaderClassGetter = (param: {
  columns: Column<any>[]
  headerIndex: number
}) => string

type HeaderPropsGetter = (param: {
  columns: Column<any>[]
  headerIndex: number
}) => Record<string, any>

type HeaderCellPropsGetter = (param: {
  columns: Column<any>[]
  column: Column<any>
  columnIndex: number
  headerIndex: number
  style: CSSProperties
}) => Record<string, any>

type RowClassGetter = (param: {
  columns: Column<any>[]
  rowData: any
  rowIndex: number
}) => string

type RowPropsGetter = (param: {
  columns: Column<any>[]
  rowData: any
  rowIndex: number
}) => Record<string, any>

type CellPropsGetter = (param: {
  column: Column<any>
  columns: Column<any>[]
  columnIndex: number
  cellData: any
  rowData: any
  rowIndex: number
}) => void

type CellRenderProps<T> = {
  cellData: T
  column: Column<T>
  columns: Column<T>[]
  columnIndex: number
  rowData: any
  rowIndex: number
}

type HeaderRenderProps<T> = {
  column: Column<T>
  columns: Column<T>[]
  columnIndex: number
  headerIndex: number
}

type ScrollParams = {
  xAxisScrollDir: 'forward' | 'backward'
  scrollLeft: number
  yAxisScrollDir: 'forward' | 'backward'
  scrollTop: number
}

type CellSlotProps<T> = {
  column: Column<T>
  columns: Column<T>[]
  columnIndex: number
  depth: number
  style: CSSProperties
  rowData: any
  rowIndex: number
  isScrolling: boolean
  expandIconProps?:
    | {
        rowData: any
        rowIndex: number
        onExpand: (expand: boolean) => void
      }
    | undefined
}

type HeaderSlotProps = {
  cells: VNode[]
  columns: Column<any>[]
  headerIndex: number
}

type HeaderCellSlotProps = {
  class: string
  columns: Column<any>[]
  column: Column<any>
  columnIndex: number
  headerIndex: number
  style: CSSProperties
  headerCellProps?: any
  sortBy: SortBy
  sortState?: SortState | undefined
  onColumnSorted: (e: MouseEvent) => void
}

type RowCommonParams = {
  rowData: any
  rowIndex: number
}

type RowEventHandlerParams = {
  rowKey: KeyType
  event: Event
} & RowCommonParams

type RowEventHandler = (params: RowEventHandlerParams) => void
type RowEventHandlers = {
  onClick?: RowEventHandler
  onContextmenu?: RowEventHandler
  onDblclick?: RowEventHandler
  onMouseenter?: RowEventHandler
  onMouseleave?: RowEventHandler
}

type RowsRenderedParams = {
  rowCacheStart: number
  rowCacheEnd: number
  rowVisibleStart: number
  rowVisibleEnd: number
}

type RowSlotProps = {
  columnIndex: number
  rowIndex: number
  data: any
  key: number | string
  isScrolling?: boolean | undefined
  style: CSSProperties
}

type RowExpandParams = {
  expanded: boolean
  rowKey: KeyType
} & RowCommonParams

type Data = {
  [key: KeyType]: any
  children?: Array<any>
}

type FixedData = Data

type KeyType = string | number | symbol

type ColumnSortParam<T> = { column: Column<T>; key: KeyType; order: SortOrder }

enum SortOrder {
  ASC = 'asc',
  DESC = 'desc',
}

type SortBy = { key: KeyType; Order: SortOrder }
type SortState = Record<KeyType, SortOrder>
```

</details>

## 常见问题

#### How do I render a list with a checkbox in the first column?

Since you are allowed to define your own cell renderer, you can do what the example [Customize Cell Renderer](#customize-cell-renderer) did to render `checkbox` yourself, and maintain the state by yourself.

#### 为什么虚拟化表提供的功能较 [TableV1](./table.md) 少？

For virtualized table, we intend to provide less feature and let our users implement their own features as needed. 整合过多的功能会让组件的代码变得难以维护，且对于大多数用户来说，基础功能就已足够。 一些主要的功能尚未开发。 我们很希望听从您的意见。 进入 [Discord](https://discord.com/invite/gXK9XNzW3X) 持续关注.
