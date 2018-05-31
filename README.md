# vueexpress

vue+express 项目案例

## 环境搭建说明

# 全局安装 Vue-cli

npm install vue-cli -g

# 或使用淘宝镜像安装

npm config set registry https://registry.npm.taobao.org

cnpm install vue-cli -g

# 创建webpack模板项目文件

vue init webpack vueexpress

# 如上命令执行报错，请尝试使用如下命令安装,按照提示下一步操作，完成后按提示操作命令

vue-init webpack vueexpress

# 安装相关依赖包（如果上述命令已安装node_modules依赖包，此步骤可省略）

cd vueexpress

npm install 

npm run dev

# 修改文件结构

将 vueexpress文件目录下的src文件夹重新命名为client

将 build\webpack.base.conf.js 内的所有 src 地址修改为 client

# 创建服务器端

mkdir server

cd server

npm init

#安装express

npm install express --save

npm install body-parser --save

# 在server文件夹目录下新建index.js文件，编写启动代码

const express = require('express');
const fs = require('fs');
const path = require('path');
const bodyParser = require('body-parser');
const app = express();
app.use(bodyParser.json());
app.use(bodyParser.urlencoded({ extended: false }));

app.use(express.static(path.resolve(__dirname, '../dist')));

app.get('*', function (req, res) {
    const html = fs.readFileSync(path.resolve(__dirname, '../dist/index.html'), 'utf-8');
    res.send(html);
});

app.listen(8081, function () {
    console.log('success listen...8081');
});


# 打包并部署

npm run build

node server/index.js

# 启动程序
在浏览器输入 http://127.0.0.1:8081/ 

# build for production and view the bundle analyzer report
npm run build --report

# run unit tests
npm run unit

# run e2e tests
npm run e2e

# run all tests
npm test

