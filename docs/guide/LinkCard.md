---
title: 链接卡片
---

## 引入组件

```ts
import DefaultTheme from 'vitepress/theme'

import { DocBox, DocLinks, DocBoxCube } from '@theojs/lumen'// [!code ++]
export default {
  extends: DefaultTheme,
  enhanceApp: ({ app }) => {// [!code ++]
    app.component('Box', DocBox)// [!code ++]
    app.component('Links', DocLinks)// [!code ++]
    app.component('BoxCube', DocBoxCube)// [!code ++]
  }// [!code ++]
  ...//其他代码
}

```

## Box

### 示例

**输入**

```vue-html
<Box
  :items="[
    //使用FontAwesome图标 + 颜色
    { name: 'Vue.js', link: '', icon: 'fab fa-vuejs', color: '#4FC08D' },
    //使用FontAwesome图标 + 标签
    { name: 'GitHub', link: '', icon: 'fab fa-github', tag: 'Github' },
    //使用FontAwesome图标 + 标签 + 颜色
    { name: '支付宝', link: 'https://i.theojs.cn/docs/202405201752089.jpg', icon: 'fab fa-alipay', color: '#00a1e9', tag: '打赏' },
    { name: '微信', link: 'https://i.theojs.cn/docs/202405201752087.jpg', icon: 'fab fa-weixin', color: '#2ca83c', tag: '打赏' },
    //使用自定义图标 + 标签
    { name: 'GitHub', link: '', icon: 'https://i.theojs.cn/logo/github.svg', tag: 'Github' },
    //使用自定义图标 + 深浅模式 + 标签
    { name: 'GitHub', link: '', light: 'https://i.theojs.cn/logo/github.svg', dark: 'https://i.theojs.cn/logo/github-dark.svg', tag: 'Github' }
  ]"
/>
```

**输出**
<Box
  :items="[
    //使用FontAwesome图标 + 颜色
    { name: 'Vue.js', link: '', icon: 'fab fa-vuejs', color: '#4FC08D' },
    //使用FontAwesome图标 + 标签
    { name: 'GitHub', link: '', icon: 'fab fa-github', tag: 'Github' },
    //使用FontAwesome图标 + 标签 + 颜色
    {
      name: '支付宝',
      link: 'https://i.theojs.cn/docs/202405201752089.jpg',
      icon: 'fab fa-alipay',
      color: '#00a1e9',
      tag: '打赏'
    },
    {
      name: '微信',
      link: 'https://i.theojs.cn/docs/202405201752087.jpg',
      icon: 'fab fa-weixin',
      color: '#2ca83c',
      tag: '打赏'
    },
    //使用自定义图标 + 标签
    {
      name: 'GitHub',
      link: '',
      icon: 'https://i.theojs.cn/logo/github.svg',
      tag: 'Github'
    },
    //使用自定义图标 + 深浅模式 + 标签
    {
      name: 'GitHub',
      link: '',
      light: 'https://i.theojs.cn/logo/github.svg',
      dark: 'https://i.theojs.cn/logo/github-dark.svg',
      tag: 'Github'
    }
  ]"
/>

### 参数说明

```ts
items: Array<{
  link: string /* 链接项的链接地址。 */
  icon: string /* 链接项的图标地址或类名。 */
  name: string /* 链接项的名称。 */
  tag?: string /* 链接项的标签（可选）。 */
  light?: string /* 浅色模式下的图标 URL（可选）。 */
  dark?: string /* 深色模式下的图标 URL（可选）。 */
  color?: string /* 图标的颜色（可选）。 */
}>
```

## Links

### 示例

**输入**

```vue-html
<Links
  :items="[
    { name: '支付宝', link: 'https://www.alipay.com', icon: 'fab fa-alipay', color: '#00a1e9' },
    { name: '微信支付', link: 'https://pay.weixin.qq.com', icon: 'fab fa-weixin', color: '#2ca83c' },
    { name: '支付宝', link: 'https://www.alipay.com', icon: 'https://i.theojs.cn/logo/github.svg' },
    { name: '支付宝', link: 'https://www.alipay.com', light: 'https://i.theojs.cn/logo/github.svg', dark: 'https://i.theojs.cn/logo/github-dark.svg' },
    { name: '支付宝', link: 'https://www.alipay.com' }
  ]"
/>
```

**输出**
<Links
  :items="[
    {
      name: '支付宝',
      link: '',
      icon: 'fab fa-alipay',
      color: '#00a1e9'
    },
    {
      name: '微信支付',
      link: 'https://pay.weixin.qq.com',
      icon: 'fab fa-weixin',
      color: '#2ca83c'
    },
    {
      name: '支付宝',
      link: '',
      icon: 'https://i.theojs.cn/logo/github.svg'
    },
    {
      name: '支付宝',
      link: 'https://www.alipay.com',
      light: 'https://i.theojs.cn/logo/github.svg',
      dark: 'https://i.theojs.cn/logo/github-dark.svg'
    },
    { name: '支付宝', link: 'https://www.alipay.com' }
  ]"
/>

### 参数说明

```ts
items: Array<{
  name: string /* 链接项的名称。 */
  link: string /* 链接项的 URL。 */
  color?: string /*  图标的颜色（可选）。 */
  icon?: string /* 图标的 URL 或类名（可选）。 */
  light?: string /* 浅色模式下的图标 URL（可选）。 */
  dark?: string /* 深色模式下的图标 URL（可选）。 */
}>
```

## BoxCube

### 示例

**输入**

```vue-html
<BoxCube
  :items="[
    //使用FontAwesome图标
    { name: 'Github', link: '', icon: 'fab fa-github' },
    //使用FontAwesome图标 + 副标题
    { name: 'Vue.js', link: '', icon: 'fab fa-vuejs', desc: 'v3.4.31' },
    //使用自定义图标+副标题
    { name: 'Node.js', link: '', icon: 'https://i.theojs.cn/logo/nodejs.svg', desc: 'v20.15.0' },
    //使用自定义图标+深浅模式+副标题
    { name: 'Github', link: '', light: 'https://i.theojs.cn/logo/github.svg', dark: 'https://i.theojs.cn/logo/github-dark.svg', desc: 'v20.15.0' }
  ]"
/>
```

**输出**
<BoxCube
  :items="[
    //使用FontAwesome图标
    { name: 'Github', link: '', icon: 'fab fa-github' },
    //使用FontAwesome图标 + 副标题
    { name: 'Vue.js', link: '', icon: 'fab fa-vuejs', desc: 'v3.4.31' },
    //使用自定义图标+副标题
    {
      name: 'Node.js',
      link: '',
      icon: 'https://i.theojs.cn/logo/nodejs.svg',
      desc: 'v20.15.0'
    },
    //使用自定义图标+深浅模式+副标题
    {
      name: 'Github',
      link: '',
      light: 'https://i.theojs.cn/logo/github.svg',
      dark: 'https://i.theojs.cn/logo/github-dark.svg',
      desc: 'v20.15.0'
    }
  ]"
/>

## 参数说明

```ts
items: Array<{
  icon: string /*图标的 URL 或类名。  */
  name: string /* 项目的名称。 */
  link: string /* 项目的链接。 */
  desc?: string /* 项目的描述（可选）。 */
  color?: string /* 图标的颜色（可选）。 */
  light?: string /* 浅色模式下的图标 URL（可选）。 */
  dark?: string /* 深色模式下的图标 URL（可选）。 */
}>
```
