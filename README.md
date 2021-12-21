
# 前言
docsify的官网地址：[https://docsify.js.org/#/zh-cn/](https://docsify.js.org/#/zh-cn/)

> 本站使用的版本是 4.4.3

# 第一步 安装docsify-cli

打开命令行，执行以下命令安装 docsify-cli，

推荐全局安装 docsify-cli 工具，可以方便地创建及在本地预览生成的文档。
```sh
npm i docsify-cli -g
```
# 第二步 初始化

创建一个文件夹,并在当前文件夹下执行以下命令创建文档目录并初始化。
```sh
docsify init ./docs
```
创建后之后会发现一个`docs`的目录,`docs`目录下有三个文件
   - index.html 入口文件
   - README.md 会做为主页内容渲染
   - .nojekyll 用于阻止 GitHub Pages 忽略掉下划线开头的文件

直接编辑 docs/README.md 就能更新文档内容，当然也可以添加更多页面。

# 本地预览

通过运行 `docsify serve` 启动一个本地服务器，可以方便地实时预览效果。

默认访问地址 http://localhost:3000 。

```sh
docsify serve docs
```


# 个性化操作
##  1.自定义导航栏
打开 index.html 文件，在 body 标签中添加 nav 标签，如下所示：

  <nav>
      <a href="https://www.baidu.com/">百度一下</a>
  </nav>

保存后，就可以在浏览器上查看到效果。

## 2.定制化配置项 

打开 index.html 文件，在 script 标签中对 window.$docsify 进行配置，如下所示：

window.$docsify = {
        name: '',
        repo: '',
}

1）name：文档标题，会显示在侧边栏顶部。

2）repo：GitHub 上的仓库地址，会在页面右上角渲染一个 GitHub 角标。


保存后，就可以在浏览器上查看到效果。
# 3.添加插件 

## 1）全文搜索

全文搜索插件会根据当前页面上的超链接获取文档内容，在 localStorage 内建立文档索引。默认过期时间为一天，也可以指定需要缓存的文件列表或者过期时间。

打开 index.html 文件，添加全文搜索配置项，并引入 search.min.js，如下所示：
```html
<body>
  <script>
    window.$docsify = {
      search: {
        paths: 'auto',
        placeholder: '搜索',
        noData: '找不到结果',
        depth: 3,
      },
    }
  </script>
  <!-- docsify的js依赖 -->
  <script src="//unpkg.com/docsify/lib/docsify.min.js"></script>
  <script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/search.min.js"></script>
</body>
```
## 2）图片缩放

在 index.html 文件中引入 zoom-image.min.js 即可，如下所示：
```html
<!-- 图片缩放插件,放大缩小支持 -->
<script src="//unpkg.com/docsify/lib/plugins/zoom-image.js"></script>
```


## 3）复制到剪贴板

在所有的代码块上添加一个简单的 Click to copy 按钮来允许用户从你的文档中轻易地复制代码。在 index.html 文件中引入 docsify-copy-code 即可，如下所示：
```html
<script src="//cdn.jsdelivr.net/npm/docsify-copy-code"></script>
```
保存后，就可以在浏览器上查看到效果。


## 4）字数统计

提供了统计中文汉字和英文单词的功能，并且排除了一些 markdown 语法的特殊字符例如 *、- 等。

打开 index.html 文件，添加 count 配置项，并引入 countable.js，如下所示：
```html
<body>
  <script>
    window.$docsify = {
      count:{
        countable:true,
        fontsize:'0.9em',
        color:'rgb(90,90,90)',
        language:'chinese'
      }
    }
  </script>
<!-- docsify的js依赖 -->
<script src="//unpkg.com/docsify/lib/docsify.min.js"></script>
<script src="//unpkg.com/docsify-count/dist/countable.js"></script>
</body>
```

保存后，就可以在浏览器上查看到效果。

## 05)代码高亮
docsify 内置的代码高亮工具是 Prism。Prism 默认支持的语言如下：

- Markup - markup, html, xml, svg, mathml, ssml, atom, rss
- CSS - css
- C-like - clike
- JavaScript - javascript, js
- Java 需要在 index.html 文件中添加额外的语法文件，如下所示：
```html
<!-- 代码高亮-->
<script src="https://cdn.jsdelivr.net/npm/prismjs@1.22.0/components/prism-java.min.js"></script>
<script src="//unpkg.com/prismjs/components/prism-python.js"></script>
<script src="//unpkg.com/prismjs/components/prism-bash.js"></script>
 ```

保存后，就可以在浏览器上查看到效果。

## 06)emoji表情支持
默认是提供 emoji 解析的，能将类似 :100: 解析成 100。

但是它不是精准的，因为没有处理非 emoji 的字符串。如果你需要正确解析 emoji 字符串，你可以引入这个插件。
```html
<!-- emoji表情支持 -->
<script src="//cdn.jsdelivr.net/npm/docsify/lib/plugins/emoji.min.js"></script>
```

## 07)分页导航插件 Pagination

docsify的分页导航插件，由@imyelo提供。

```html
  <!--分页导航插件  上一篇/下一篇 -->
  <script src="//unpkg.com/docsify-pagination/dist/docsify-pagination.min.js"></script>
```
## 08)返回顶部 
```html
  <!-- 返回顶部 -->
  <script src="//unpkg.com/docsify-scroll-to-top/dist/docsify-scroll-to-top.min.js"></script>
```  
## 09)侧边栏折叠 

```html
<script>
  window.$docsify = {
    loadSidebar: true,
    alias: {
      '/.*/_sidebar.md': '/_sidebar.md',
    },
    subMaxLevel: 3,
    ...
    sidebarDisplayLevel: 1, // set sidebar display level
  }
</script>
<script src="//cdn.jsdelivr.net/npm/docsify/lib/docsify.min.js"></script>

<!-- plugins -->
<!-- 侧边栏折叠 -->
<script src="//cdn.jsdelivr.net/npm/docsify-sidebar-collapse/dist/docsify-sidebar-collapse.min.js"></script>

```