
<p align="center">
<h1 align="center">vite-plugin-enhance-log</h1>
</p>

<div align="center">
  一个用来为console.log添加代码所在文件名，log参数名以及添加分隔符的 vite 插件

[![NPM version][npm-image]][npm-url] ![NPM downloads][download-image]

![Test][test-badge] 

<!-- ![codecov][codecov-badge] -->


[npm-image]: https://img.shields.io/npm/v/vite-plugin-enhance-log.svg?style=flat-square
[npm-url]: http://npmjs.org/package/vite-plugin-enhance-log


[download-image]: https://img.shields.io/npm/dm/vite-plugin-enhance-log.svg?style=flat-square



[test-badge]: https://github.com/baozouai/vite-plugin-enhance-log/actions/workflows/ci.yml/badge.svg

[codecov-badge]: https://codecov.io/github/baozouai/plugin-vite-plugin-enhance-log/branch/master/graph/badge.svg


</div>

中文 | [English](./README.md)

## 📦  安装

```sh
pnpm add vite-plugin-enhance-log -D
# or
yarn add vite-plugin-enhance-log -D
# or
npm i vite-plugin-enhance-log -D
```
## ⚙️ 参数

```ts
interface Options {
  /**
   * 打印文件名
   * 如果你文件名太长，希望不显示文件path的目录，比如src/pages/xxx/yyy/a.tsx, 那么可以配置enableDir为false，则只打印a.tsx
   * 
   * @default true
   */
  enableFileName?: boolean | {
    enableDir?: boolean
  }
  /**
   * 打印的前缀提示，这样方便快速找到log 🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀
   * @example
   * console.log(' 🚀🚀🚀🚀🚀🚀🚀🚀🚀🚀', ...)
   */
  preTip?: string
  /** 每个参数分隔符，默认空字符串，你也可以使用换行符\n，分号；逗号，甚至猪猪🐖都行~ */
  splitBy?: boolean
}
```

 ## 🔨 使用

```ts
import { defineConfig } from 'vite'
import EnhanceLog from 'vite-plugin-enhance-log'

const config = defineConfig({
  plugins: [
    // 如果用vue, 请确保 vuePlugin 在 log plugin 之前
    EnhanceLog({
      splitBy: '\n',
      preTip: '🐖🐖🐖🐖🐖🐖🐖🐖🐖🐖',
      enableFileName: true, // or enableFileName: { enableDir: false}
    }),
  ],
})

export default config

```

## 👇 例子

拉项目后通过运行启动playgrounds：
```shell
pnpm play # 对应vue
# 或者
pnpm play:react # 对应react
```

来启动项目

具体配置可以看 [vue/vite.config.ts](./playgrounds/vue/vite.config.ts) 或者 [react/vite.config.ts](./playgrounds/react/vite.config.ts)

比如说，你不喜欢小 🚀，你喜欢猪猪 🐖，那可以配置 preTip 为 🐖🐖🐖🐖🐖🐖🐖🐖🐖🐖：

![img](./assets/pig_pretip.png)

比如说，在参数较多的情况下，你希望 log 每个参数都换行，那可以配置 splitBy 为 `\n`：

![img](./assets/linefeed.png)

或者分隔符是`;`:

![img](./assets/semicolon_delimiter.png)

当然，你也可以随意指定，比如用个狗头🐶来分隔：

![img](./assets/dog_delimiter.png)

比如说，你希望知道log所在的文件名，那么可以配置enableFileName为true（当然默认就是true）：

![img](./assets/filename.png)

如果文件路径太长:
![img](./assets/deep_file.png)


你只希望打印文件名，不需要目录前缀，那么可以配置 `enableFileName: { enableDir: false }`:
![img](./assets/only_file_name.png)

<!-- 又比如说，有个 log 跨了多行，你希望 log 开始和结束的行数，中间是 log 实体，那可以将 endLine 设置为 true：

![img](./assets/log_multi_line.png)

![img](./assets/log_multi_line_res.png)

> 我们可以看到开始的行数是13，结束的行数是44，跟源码一致  -->

## 📄 协议

vite-plugin-enhance-log 遵循 [MIT 协议](./LICENSE).