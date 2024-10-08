---
title: 页脚配置
---

![首页页脚 - 效果图](https://i.theojs.cn/docs/202408081933196.png)

## 创建数据

在`.vitepress`目录下新建`data/fooertData.ts`文件，并添加以下内容：

```ts
// .vitepress/data/footerData.ts

export const Footer_Data = {
  beian: { icp: '备案号', police: '公网安备号' },
  author: { name: 'Theo', link: 'https://' },
  group: [
    {
      title: '外部链接',
      icon: 'fas fa-link', // Font Awesome 图标类名 具体查看:https://fontawesome.com/
      style: 'color: rgba(255, 87, 51, 1)',
      links: [
        { name: '示例1', href: 'https://' },
        { name: '示例2', href: 'https://' }
      ]
    },
    {
      title: '内部链接',
      internal: true, // `internal`默认为 false , 为 true 时不显示外部链接图标
      icon: 'fas fa-link',
      style: 'color: rgba(255, 87, 51, 1)',
      links: [
        { name: '示例1', icon: 'fas fa-book', href: '/docs' },
        { name: '示例2', href: '/page' }
      ]
    }
  ]
}
```

## 引入组件

::: tip
`.. /data/footerData` 可替换为存放数据的路径
:::

```ts
//.vitepress/theme/index.ts
import DefaultTheme from 'vitepress/theme'
import { h } from 'vue'// [!code ++]

import { HomeFooter } from '@theojs/lumen'// [!code ++]
import { Footer_Data } from '../data/footerData'// [!code ++]

export default {
  extends: DefaultTheme,
  Layout() {// [!code ++]
    return h(DefaultTheme.Layout, null, {// [!code ++]
      'layout-bottom': () => h(HomeFooter, { Footer_Data }) // [!code ++]
    }) // [!code ++]
  }// [!code ++]
  ...
}
```

## 数据接口说明

```ts
Footer_Data: {
  group: Array<{
    icon?: string /* 图标（可选）。 */
    style?: string /* 图标样式（可选）。 */
    title: string /* 分组标题。 */
    internal?: boolean /* 该组是否为内部链接，默认为 `false`（可选）。 */
    links: Array<{
      icon?: string /* 链接图标（可选）。 */
      style?: string /* 链接样式（可选）。 */
      name: string /* 链接名称。 */
      href: string /* 链接地址。 */
      internal?: boolean /* 是否为内部链接，默认为 `false`（可选）。 */
    }>
  }>
  beian?: {
    icp?: string /* ICP 备案号（可选）。 */
    police?: string /* 公安备案号（可选）。 */
  }
  author?: {
    name?: string /* 作者姓名（可选）。 */
    link?: string /* 作者链接（可选）。 */
  }
}
```
