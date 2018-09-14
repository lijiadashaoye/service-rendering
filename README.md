# service-rendering

把官网上的服务端渲染跑一遍

## 服务端渲染的好坏

好：<br>
1: 帮助网络爬虫（SEO）
2: 提升在手机和低功耗设备上的性能
3: 迅速显示出第一个页面
<br>
坏：由于服务端渲染页面的用户只能点击链接，所以你应该尽快让它切换到真正的客户端应用，以提供正常的交互体验。

<br>
那些标有 * 的文件都是新的，而不是来自原来的范例应用<br>
src/<br>
  index.html                 应用的宿主页<br>
  main.ts                    客户端应用的引导程序<br>
  main.server.ts             * 服务端应用的引导程序<br>
  tsconfig.app.json          TypeScript 的客户端配置<br>
  tsconfig.server.json       * TypeScript 的服务端配置<br>
  tsconfig.spec.json         TypeScript 的测试配置<br>
  style.css                  应用的样式表<br>
  app/ ...                   应用代码<br>
    app.server.module.ts     * 服务端的应用模块<br>
server.ts                    * Express 的服务程序<br>
tsconfig.json                TypeScript 的客户端配置<br>
package.json                 npm 配置<br>
webpack.server.config.js     * Webpack 的服务端配置<br>

