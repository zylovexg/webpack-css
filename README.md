## npm install
## npm run dev 或者 npm run build

### 步骤
#### npm i -d style-loader css-loader
#### webpack 配置
```javascript
  module.exports = {
    module: {
      rules: [
        {
          test: /\.css$/,   // 要处理什么类型的文件，用正则去匹配。这里是 css 文件
          use: ['style-loader', 'css-loader']   // 顺序从右往左的执行，如果loader需要参数，就得写成对象的形式
        }
      ]
    }
  }
```
### 单独提取CSS
#### webpack版本4.3以上，低版本请使用 extract-text-webpack-plugin
#### npm i -d mini-css-extract-plugin
#### webpack 配置
```javascript
  const MiniCssExtractPlugin = require('mini-css-extract-plugin');
  module.exports = {
    plugins: [
      new MiniCssExtractPlugin({
        filename: 'css/index.css'   // 文件目录会放入 output.path 里
      })
    ],
    module: {
      rules: [
        {
          test: /\.css$/,
          use: [MiniCssExtractPlugin.loader, 'css-loader']   // 代替 style-loader
        }
      ]
    }
  }
```
