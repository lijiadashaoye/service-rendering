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

<br>

## 方法

1：npm install --save @angular/platform-server @nguniversal/module-map-ngfactory-loader ts-loader @nguniversal/express-engine<br>
2:修改 app.module.ts 文件中 imports 为<br>
imports: [BrowserModule.withServerTransition({ appId: "tour-of-heroes" })]<br>
appId 值它可以是任何字符串<br>
3:在软件的所有 http 服务中注入 APP_BASE_HREF 令牌来提供服务器的源地址（origin），把它注入到服务中，并把这个源地址添加到所请求的 URL 之前（看 src\app\app.server.module.ts）
<br>
4：在 src/app/ 目录下创建 app.server.module.ts 文件
<br>
5：在 src/ 目录下创建一个 main.server.ts 文件（src\main.server.ts），并导出 AppServerModule
<br>
6：在根目录下创建 server.ts 文件（与 angular.json 同级）
<br>
7：在项目的根目录下创建一个 tsconfig.server.json 文件（src\tsconfig.server.json）来配置 TypeScript 和这个 Universal 应用的 AOT 编译选项。
<br>
8：在项目的根目录下创建一个 webpack.server.config.js 文件（与 angular.json 同级）
<br>
9：在 angular.json 的 architect 下添加服务配置：architect -> server{}
<br>
10：在 package.json 中添加打包、启动命令：scripts -> build:ssr 等
<br>
11：打包：npm run build:ssr
<br>
12:用 vscode 打开打包后的文件夹 dist，然后终端输入：npm run serve:ssr
<br>
13：浏览器打开：http://localhost:4000 即可
