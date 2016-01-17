## npm是什么

> npm makes it easy for JavaScript developers to share and reuse code, and it makes it easy to update the code that you're sharing.

## 前置任务

1. 安装node.js
2. 升级npm `sudo npm install npm -g`
3. 遇到权限问题怎么解决.[https://docs.npmjs.com/getting-started/fixing-npm-permissions](https://docs.npmjs.com/getting-started/fixing-npm-permissions)

## npm常用命令

1. `npm init` 命令式创建package.json

2. `npm install`/`npm install xxx --save `/`npm install xxx --save -dev` 安装packge

3. `npm update/ npm outdated` 更新本地包

4. `npm uninstall xxx` 删除本地包(仅node_modules)

5. `npm uninstall --save xxx` 同时删除package.json中声明的依赖

6. `npm prune` 删除node_modules目录中多余的依赖(即package.json中不存在但node_modules中存在)

7. `npm uninstall -g xxx` 删除全局的node依赖

7. `npm ls` 当前package.json中声明的所有依赖树

8. `npm ls --depth=0` 只打印根依赖

## 关于版本

如果你当前的版本是1.0.4,那么有以下几种选择(package.json中)

1. Patch releases: 1.0 or 1.0.x or ~1.0.4

2. Minor releases: 1 or 1.x or ^1.0.4

3. Major releases: * or x




## 参考资料

1. [官方文档,!!强烈推荐!!](https://docs.npmjs.com/getting-started/)
