# 关于

## mkdocs

MkDocs是一种简单易用的静态网站生成工具，允许开发者使用Markdown文档编写网站，并支持自定义主题和插件。基于Python语言开发，MkDocs可以帮助用户快速创建美观、易读的文档网站。

### 安装

安装MkDocs最简单的方法是通过Python包管理器pip进行安装：

```bash
pip install mkdocs
```

### 使用

使用MkDocs创建一个新项目很容易。执行以下命令将在当前目录下创建一个名为“myproject”的新项目：

```bash
mkdocs new myproject
```

这将生成如下文件结构：

```text
myproject/
    ├── docs/
    │   └── index.md
    ├── mkdocs.yml
    └── README.md
```

其中，“docs”文件夹存放所有的Markdown文档，“mkdocs.yml”是配置文件，“README.md”是项目的说明文件。

编辑“docs/index.md”文件，添加一些内容：

```md
# 欢迎使用MkDocs

MkDocs是一个简单易用的静态网站生成工具，通过Markdown文档编写网站。
```

保存文件后，在命令行中进入项目根目录并执行以下命令：

```bash
mkdocs serve
```

然后在浏览器中打开“<http://localhost:8000>”就可以看到刚才编辑的页面了。

### 自定义主题和插件

MkDocs支持自定义主题和插件。用户可以通过安装第三方主题和插件来增强MkDocs的功能。

例如，要安装“mkdocs-material”主题，执行以下命令：

```powershell
pip install mkdocs-material
```

然后在“mkdocs.yml”文件中将主题设置为“material”:

```yml
theme:
    name: material
```

这样就可以使用代码高亮和其他扩展功能了。

### 部署

要将MkDocs网站部署到远程服务器上，最简单的方法是使用GitHub Pages或GitLab Pages。只需要将生成的HTML文件上传到GitHub或GitLab上的相应仓库中即可。

另外，也可以使用Python Web框架（如Flask、Django等）将MkDocs生成的HTML文件作为静态文件部署到Web服务器上。

以上就是Python MkDocs的简介，更多详细信息请参考MkDocs官方文档：<https://www.mkdocs.org/>
