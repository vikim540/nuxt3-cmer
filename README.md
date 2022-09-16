# Nuxt 3  CMER 前端起始模板
具有许多有用功能的 Nuxt 3 入门模板或样板。集成 TailwindCSS 3 。

_该模板旨在让使用 Nuxt 3 创建 Web 项目使工作变得更加容易。因此结合了许多插件及 ui 组件_

> **警告** \
> Nuxt 3 现在是 RC 版本（测试版）[但此模板使用 Nuxt 3.x edge*（最新版本）]
> 等出正式版会进行不定期更新.  
> * 可以在此处找到重大更改 [here](https://github.com/nuxt/framework/discussions/2883)  
> * 说明文档及路线图可以在这里找到 [here](https://v3.nuxtjs.org/community/roadmap)

## 特征
- [x] 💨 [Tailwind CSS v3](https://tailwindcss.com/) 带有 [Windicss](https://windicss.org/)
- [x] ✨ [Headless UI](https://headlessui.dev/)
- [x] 🔔 [一个公共的字体图标库 Icon Pack Component (unplugin-icons)](https://icones.js.org/)
- [x] 🛹 [状态及商店管理 State & Store Management (Pinia)](https://pinia.vuejs.org/)
- [x] 🚩 [本地化的翻译工具 Localization (i18n) by @intlify](https://github.com/intlify/nuxt3) & Auto Generate Locales
- [x] 📦 [Vue内容的集合 Composition Collection (Vueuse)](https://vueuse.org/)
- [x] 📚 [Nuxt的内容管理器 在content/post 目录可以见到基于md文件即可产生对应文章页  Content Management System (Nuxt Content)](https://content.nuxtjs.org/) [SSR]
- [x] 🌙 更符合现状发展的护眼及夜间模式 (light, dark, system, realtime)
- [x] 💬 语言切换器
- [x] 🔳 内置组件和布局
- [x] 👨‍💻 代码美化及规则Eslint & Prettier 
- [x] 🚠 检查提交描述Husky & Commitlint 
- [x] 🛎️ 自定义工作区片段 Custom Workspace Snippets

## 计划
- [ ] 完善企业模板
- [ ] Adding HTTP Client
- [ ] 主题外观配置颜色选项
- [ ] 配置headless CMS 
- [ ] 一键托管
- [ ] 尽可能使修改变得容易
  - [x] 默认的颜色选项
  - [x] 字体及字号

## 预览
 [链接地址](https://nuxt3.cmer.qcdz.vip/) 
 
## 目录
- [Nuxt 3 cmer](#nuxt-3-CMER)
  - [特征](#特征)
  - [计划](#计划)
  - [预览](#预览)
  - [目录](#目录)
  - [快速启动](#快速启动)
    - [Start with this template](#start-with-this-template)
    - [Deploy as Static Site](#deploy-as-static-site)
  - [内置组件](#内置组件)
  - [笔记](#笔记)
    - [Nuxt Content](#nuxt-content)
    - [自定义工作区片段](#自定义工作区片段)
    - [Styles](#styles)
    - [Theme (Dark Mode)](#theme-dark-mode)
    - [Localization](#localization)
    - [Generate Locales](#generate-locales)
    - [Icons](#icons)
    - [Precommit and Postmerge](#precommit-and-postmerge)
  - [License](#license)



## 快速启动

从这个模板开始
*这个项目使用“yarn”作为包管理器。
*将此项目克隆到您的计算机' git Clone https://github.com/vikim540/nuxt3-cmer '
*安装依赖' yarn Install '
*运行' yarn dev '启动开发服务器，并在浏览器中打开' http://localhost:3000 '

作为静态站点部署
*运行“yarn generate”来构建项目
*服务“dist/”文件夹
[部署文档](https://v3.nuxtjs.org/docs/deployment)。


## 内置组件
- [x] Footer
- [x] Button
- [x] Anchor (link)
- [x] Alert
- [x] Card
- [x] Action Sheet
- [x] Theme Toggle / Switcher
- [x] Navbar
  - [x] Navbar Builder
  - [x] Drawer (on mobile)
  - [x] Options (on mobile)
- [x] Page Layout
  - [x] Wrapper
  - [x] Header
    - [x] Title
  - [x] Body
    - [x] Section
      - [x] Section Wrapper
      - [x] Section Title
- [x] Dashboard Layout
    - [x] Sidebar
- [ ] Modal

## 笔记
### Nuxt 内容
使用 Nuxt Content，您可以在 `content` 文件夹内创建 .md 文件（推荐）。
但这仅适用于 SSR（服务器端渲染）模式。静态模式还是不行，可以看问题[nuxt/content#1202](https://github.com/nuxt/content/issues/1202)  现在可以关注

### 自定义工作区片段
此工作区包括 VSCode 的自定义片段。
- **n3:content**  
  content template with markdown
- **n3:page**  
  page template

### 风格
由 windicss 管理的 Tailwindcss 导入。您可以在以下位置添加自定义样式：

```
/path/to/assets/sass/app.scss
```
### 主题（夜晚模式）
ThemeManager 是一个允许您在主题之间切换的插件。这个库在：
```
/path/to/utils/theme.ts
```
`Thememanager` 在挂载之前是一个函数类构造 `AppSetup()` 里面的主题构造 `/path/to/app.vue` :
```vue
<!-- /path/to/app.vue -->
<script lang="ts" setup>
import { AppSetup } from '~/utils/app';
// app setup
AppSetup()
</script>
```
要更改主题，您可以直接从 state 设置主题`theme.setting`，例如：
```vue
<script lang="ts" setup>
import { IThemeSettingOptions } from '~/utils/theme'
const themeSetting = useState<IThemeSettingOptions>('theme.setting')
themeSetting.value = 'dark'
</script>
```
当你改变状态`theme.setting`时，它会自动改变主题。

主题设置有 4 个选项：
- `light`
- `dark`
- `system` (操作系统主题)
- `realtime` (实时主题，如果05:00-17:00，将变为浅色主题，否则为深色)

我们有状态`theme.current`，这个状态返回`light`或`dark`主题。基本上是从`theme.setting`. 不要用这种状态改变主题。
### 本地化语言
本地化是一个允许您在语言之间切换的插件。这个库在：
```
/path/to/utils/lang.ts
```
`LanguageManager` 在挂载之前是一个函数类构造。这个库依赖于内部的  [@intlify/nuxt3](https://github.com/intlify/nuxt3)
lang 构造： `AppSetup()` in `/path/to/app.vue` :
<!-- /path/to/app.vue -->
<script lang="ts" setup>
import { AppSetup } from '~/utils/app';
// app setup
AppSetup()
</script>
要更改语言，您可以直接从 state 设置语言 `lang.setting`, example :
```vue
<script lang="ts" setup>
const langSetting = useState<string>('locale.setting')
langSetting.value = 'en'
</script>
```
当你改变 state `locale.setting`时，它​​会自动改变语言。

### 生成语言环境
我做了一个自动翻译成./locales/文件夹中已经准备好的所有语言的自动工具所以，你只需更新“locales/en.yml”并运行这个工具，它就会自动翻译成所有语言。

你可以运行：
 
```
yarn generate:locales

# or :

node ./tools/translator.js ./locales en.yml
```

### 图标
该项目使用 unplugin-icons 自动生成和导入图标作为组件。

您可以在以下网址查看收藏图标列表： [https://icones.js.org/](https://icones.js.org/)

可以使用 `<prefix-collection:icon />` or `<PrefixCollection:Icon />`.

在这个项目中，配置前缀为“图标”，您可以在 `nuxt.config.ts` :
```js
export default defineNuxtConfig({
    ...

    vite: {
        plugins: [
            UnpluginComponentsVite({
                dts: true,
                resolvers: [
                    IconsResolver({
                        prefix: 'Icon',
                    }),
                ],
            }),
        ],
    },

    ...
})
```

例子 ：
```vue
// use icon from collection "Simple Icons" and name icon is "nuxtdotjs"
<IconSimpleIcons:nuxtdotjs />

// use icon from collection "Unicons" and name icon is "sun"
<IconUil:sun />
```
### 预提交和后合并
该项目使用 husky 和 ​​commitlint 进行 precommit 和 postmerge。当你提交时，它会检查你的提交信息并运行“yarn lint-staged”来检查你的暂存文件。中的配置： `/path/to/.husky/pre-commit` 和 `/path/to/commitlint.config.js`

并且当 Postmerge 时，它​​会运行“yarn”来自动安装新的依赖项。配置在 `/path/to/.husky/post-merge`

## 许可证
由于项目来自于网络资源整合，而该项目在 MIT 许可下获得许可，版权所有 (c) 2022 Alfian Dwi Nugraha。有关详细信息，请参阅 [LICENSE](LICENSE.md) 文件.