## 博客

参考：[https://mostearly.com](https://mostearly.com)

一个使用TypeScript搭建的Gatsby项目

命令行工具：[bmt](https://github.com/mostearly/bmt)

### 功能

- 评论(基于Firebase)
- 分页
- 生成RSS
- 生成SiteMap

其他功能将逐步添加

### 结构

```
|Root
|-config 存放配置文件
|-src 源代码
|---component React组件
|---pages 将直接生成的页面
|---templates 将在gatsby-node.js创建的页面
|---assets 资源文件
```


### 运行

1. 修改配置

   编辑`config/index.js`文件中的`path`字段，项目使用了`gatsby-transformer-remark`解析Markdown文档，这个字段存放的为你的文章存放文件夹
   
   例如：`C://Users/user/Documents/posts`

2. 安装项目依赖

   ```powershell
   yarn install
   ```

3. 运行

   每篇Markdown的YAML应该具有`title`，`date`，`status`字段

   - title：文件名，没有将自动使用文件名作为title

   - date: 创建时间，没有将自动使用文件的`atime`作为date

   - status: 如果值不为`publish`这篇文章将被忽略掉

   除了上面的字段还可以拥有以下字段

   - modified: 文章更新使用，没有将使用文件的`mtime`作为值
   
   - thumbnail: 作为特色图片将展示在文章列表出

   - tags: 文章标签，应该是一个数组的格式

   - category: 文章分类，没有将自动分类到`默认`下面
   
   - path: 这篇文章的路径，设置后将覆盖默认的路径，如果发生错误将抛出`The post path is repeated, title: ***`
   
   - type: 文章的类型，用于使用对应模板，默认为`post`，可能的值为: `about`, `links`
   
   - comment: 是否启用评论，默认启用, 评论使用Firebase, 需要修改src/components/comment/firebase文件的firebase配置

   运行开发模式：

   ```powershell
   yarn run develop
   ```

   运行构建模式：

   ```powershell
   yarn run build
   ```
   
### 其他配置

- 修改通用颜色

  gatsby-config.js、src/assets/styles/variable.styl文件

- 修改首页标题字体

  src/assets/styles/global.styl文件

  阿里在线字体

  修改后需重新运行命令

