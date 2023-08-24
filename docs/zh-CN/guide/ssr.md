---
title: SSR
lang: zh-CN
---

# 服务端渲染 (SSR)

当使用 Element Plus 在 SSR 场景下开发时，您需要在 SSR 期间进行特殊处理，以避免水合错误。

:::tip

对于Nuxt 用户，我们提供的 [Nuxt 模块](https://github.com/element-plus/element-plus-nuxt) 已经包含了对这些问题的处理方案。 您只需要安装它就可以了。

:::

## 提供一个ID

提供的值用于生成 ElementPlus 中的唯一ID。 因为不同的 IDs 容易发生SSR中的水合率错误， 为了确保服务器端和客户端生成相同的ID， 我们需要将 `ID_injection_key` 注入到 Vue。

```ts
// src/main.js (irrelevant code omitted)
import { createApp } from 'vue'
import { ID_INJECTION_KEY } from 'element-plus'
import App from './App.vue'

const app = createApp(App)
app.provide(ID_INJECTION_KEY, {
  prefix: 1024,
  current: 0,
})
```

## 配置 ZIndex

当您使用SSR进行开发时，您可能会遇到 `z-index` 引起的水合错误。 在这种情况下，我们建议注入一个初始值以避免这种错误。

```ts
// src/main.js (irrelevant code omitted)
import { createApp } from 'vue'
import { ZINDEX_INJECTION_KEY } from 'element-plus'
import App from './App.vue'

const app = createApp(App)
app.provide(ZINDEX_INJECTION_KEY, { current: 0 })
```

## Teleports

[Teleport](https://vuejs.org/guide/scaling-up/ssr.html#teleports) 被元素加元件中的多个组件内部使用 (例如) ElDialog, ElDrawer, ElTooltip, ElDropdown, ElSelect, ElDatePicker ...)，所以在SSR期间需要特殊处理。

### 在挂载时渲染 Teleport

一个较容易的解决办法是有条件渲染挂载上的 Teleport 。

例如，在Nuxt中使用 `ClientOnly` 这个组件。

```html
<client-only>
  <el-tooltip content="the tooltip content">
    <el-button>tooltip</el-button>
  </el-tooltip>
</client-only>
```

或

```vue
<script setup>
import { ref } from 'vue'

const isClient = ref(false)

onMounted(() => {
  isClient.value = true
})
</script>

<template>
  <el-tooltip v-if="isClient" content="the tooltip content">
    <el-button>tooltip</el-button>
  </el-tooltip>
</template>
```

### 注入 Teleport 标记

另一种方式是将传送标记注入到你的 HTML 页面末尾的正确位置。

:::warning

Teleport 可能会有一些 [SSR问题](https://github.com/vuejs/core/issues?q=is%3Aissue+is%3Aopen+ssr+teleport+)，所以你应该特别注意以下几种情况。

1. 基于 ElTooltip 的 `teleported` 的属性应该是一致的，建议使用默认值。
2. ElDialog 和 ElDrawer 的 ` append-to-body` 属性值应该是一致的，建议启用 `append-to-body`。
3. ElSubMenu组件有多层弹出窗口，建议启用 `teleported`

:::

您需要注入靠近 `<body>` 标签的传送标记。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Element Plus</title>
    <!--preload-links-->
  </head>
  <body>
    <!--app-teleports-->
    <div id="app"><!--app-html--></div>
    <script type="module" src="/src/entry-client.js"></script>
  </body>
</html>
```

:::tip

如果您修改了 [Namespace](./namespace.md) 或 `append-to` 属性，您需要调整 `#el-popper-container-` 值。

:::

```js
// src/entry-server.js (irrelevant code omitted)
import { renderToString } from 'vue/server-renderer'
import { createApp } from './main'

export async function render(url, manifest) {
  // ...
  const ctx = {}
  const html = await renderToString(app, ctx)
  const preloadLinks = renderPreloadLinks(ctx.modules, manifest)
  const teleports = renderTeleports(ctx.teleports)

  return [html, preloadLinks, teleports]
}

function renderTeleports(teleports) {
  if (!teleports) return ''
  return Object.entries(teleports).reduce((all, [key, value]) => {
    if (key.startsWith('#el-popper-container-')) {
      return `${all}<div id="${key.slice(1)}">${value}</div>`
    }
    return all
  }, teleports.body || '')
}
```

```js
// server.js or prerender.js (irrelevant code omitted)
const [appHtml, preloadLinks, teleports] = await render(url, manifest)

const html = template
  .replace('<!--preload-links-->', preloadLinks)
  .replace('<!--app-html-->', appHtml)
  .replace(/(\n|\r\n)\s*<!--app-teleports-->/, teleports)
```
