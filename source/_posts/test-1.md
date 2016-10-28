---
title: hexo 使用说明
date: 2016-10-28 17:15:27
tags: hexo
categories: hexo
---

## 基本操作

### 安装

#### 安装前提
安装 Hexo 相当简单。然而在安装前，必须检查电脑中是否已安装下列应用程序：
- Node.js
- Git

如果电脑中已经安装上述必备程序，接下来只需要使用 npm 即可完成 Hexo 的安装。

    $ npm install -g hexo-cli

### 建站
安装 Hexo 完成后，请执行下列命令，Hexo 将会在指定文件夹中新建所需要的文件。

    $ hexo init <folder>
    $ cd <folder>
    $ npm install

新建完成后，指定文件夹的目录如下：

    .
    ├── _config.yml
    ├── package.json
    ├── scaffolds
    ├── source
    |   ├── _drafts
    |   └── _posts
    └── themes

#### _config.yml
网站的[配置](#configs)信息，您可以在此配置大部分的参数。
#### package.json
应用程序的信息。EJS, Stylus 和 Markdown renderer 已默认安装，您可以自由移除。

    package.json
    {
      "name": "hexo-site",
      "version": "0.0.0",
      "private": true,
      "hexo": {
        "version": ""
      },
      "dependencies": {
        "hexo": "^3.0.0",
        "hexo-generator-archive": "^0.1.0",
        "hexo-generator-category": "^0.1.0",
        "hexo-generator-index": "^0.1.0",
        "hexo-generator-tag": "^0.1.0",
        "hexo-renderer-ejs": "^0.1.0",
        "hexo-renderer-stylus": "^0.2.0",
        "hexo-renderer-marked": "^0.2.4",
        "hexo-server": "^0.1.2"
      }
    }

#### scaffolds
模版 文件夹。当您新建文章时，Hexo 会根据 scaffold 来建立文件。

#### source
资源文件夹是存放用户资源的地方。除 `_posts` 文件夹之外，开头命名为 `_`(下划线)的文件 / 文件夹和隐藏的文件将会被忽略。Markdown 和 HTML 文件会被解析并放到 'public' 文件夹，而其他文件会被拷贝过去。
#### themes
主题 文件夹。Hexo 会根据主题来生成静态页面。

<span id="configs"></span>
### 配置

在 Hexo 中有两份主要的配置文件，其名称都是 _config.yml。 其中，一份位于站点根目录下，主要包含 Hexo 本身的配置；另一份位于主题目录下，这份配置由主题作者提供，主要用于配置主题相关的选项。


```
# Hexo Configuration
## Docs: http://hexo.io/docs/configuration.html
## Source: https://github.com/hexojs/hexo/

# Site  这下面的几项配置都很简单，你看我的博客就知道分别是什么意思
title: Chillax blog #博客名
subtitle: Goals determine what you are going to be  #副标题
description: Goals determine what you are going to be #用于搜索，没有直观表现
author: huangjunhui #作者
language: zh-CN #语言
timezone:   #时区，此处不填写，hexo会以你目前电脑的时区为默认值

# URL   暂不配置，使用默认值
## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
url: http://opiece.me  #域名
root: /
permalink: :year/:month/:day/:title/
permalink_defaults:

# Directory     暂不配置，使用默认值
source_dir: source
public_dir: public
tag_dir: tags
archive_dir: archives
category_dir: categories
code_dir: downloads/code
i18n_dir: :lang
skip_render:

# Writing   文章布局等，使用默认值
new_post_name: :title.md # File name of new posts
default_layout: post
titlecase: false # Transform title into titlecase
external_link: true # Open external links in new tab
filename_case: 0
render_drafts: false
post_asset_folder: false
relative_link: false
future: true
highlight:
  enable: true
  line_number: true
  tab_replace:

# Category & Tag    暂不配置，使用默认值
default_category: uncategorized
category_map:
tag_map:

# Date / Time format    时间格式，使用默认值
## Hexo uses Moment.js to parse and display date
## You can customize the date format as defined in
## http://momentjs.com/docs/#/displaying/format/
date_format: YYYY-MM-DD
time_format: HH:mm:ss

# Pagination    
## Set per_page to 0 to disable pagination
per_page: 10    #每页显示的文章数，0表示不分页
pagination_dir: page

# Extensions    插件配置，暂时不配置
## Plugins: http://hexo.io/plugins/
## Themes: http://hexo.io/themes/
plugins:
- hexo-generator-feed
theme: light    #使用的主题，即：E:\myblog\themes文件夹下的主题文件夹名

feed:   #之后配置rss会用，使用如下配置即可
  type: atom
  path: atom.xml
  limit: 20  

# Deployment    用于部署到github，之前已经配置过
## Docs: http://hexo.io/docs/deployment.html

部署方式
deploy: 
  type: git  
  repository: http://github.com/angelwgh/angelwgh.github.io.git
  branch: master
```

### 指令

#### init
    $ hexo init [folder]
新建一个网站。如果没有设置 folder ，Hexo 默认在目前的文件夹建立网站。

#### new
    $ hexo new [layout] <title>
新建一篇文章。如果没有设置 `layout` 的话，默认使用 `_config.yml` 中的 `default_layout` 参数代替。如果标题包含空格的话，请使用引号括起来。

#### generate
    $ hexo generate
    $ hexo g

    -d, --deploy    文件生成后立即部署网站
    -w, --watch 监视文件变动
生成静态文件

#### publish
    $ hexo publish [layout] <filename>
发表草稿。

####
    $ hexo server
    $ hexo s
启动服务器。默认情况下，访问网址为：` http://localhost:4000/。`

    -p, --port  重设端口
    -s, --static    只使用静态文件
    -l, --log   启动日记记录，使用覆盖记录格式

#### deploy
    $ hexo deploy
部署网站

    -g, --generate  部署之前预先生成静态文件

#### render
    $ hexo render <file1> [file2] ...
渲染文件。

    -o, --output    设置输出路径

#### migrate
    $ hexo migrate <type>
从其他博客系统 迁移内容。

#### clean
    $ hexo clean
清除缓存文件 (`db.json`) 和已生成的静态文件 (`public`)。

#### list
    $ hexo list <type>
列出网站资料。

#### version
$ hexo version
显示 Hexo 版本。

### 选项

#### 安全模式
    $ hexo --safe
在安全模式下，不会载入插件和脚本。当您在安装新插件遭遇问题时，可以尝试以安全模式重新执行。

#### 调试模式
    $ hexo --debug
在终端中显示调试信息并记录到 debug.log。当您碰到问题时，可以尝试用调试模式重新执行一次，并 提交调试信息到 GitHub。

#### 简洁模式
    $ hexo --silent
隐藏终端信息。

#### 自定义配置文件的路径
    $ hexo --config custom.yml
自定义配置文件的路径，执行后将不再使用 _config.yml。

#### 显示草稿
    $ hexo --draft
显示 source/_drafts 文件夹中的草稿文章。

#### 自定义 CWD
    $ hexo --cwd /path/to/cwd
自定义当前工作目录（Current working directory）的路径。



### 写文章
#### 创建一篇新文章 
    $ hexo new "my new post"
然后在\source\ _posts中打开这个文件，配置开头
```
1. ---
2. title: my new post  \#文章标题，可以改为中文。
3. date: 2016-01-14 20:37:51  \#发表日期，自动生成，不改。
4. categories:  ***  \#文章分类
5. tags: 
6. - hexo   \#文章标签，多于一项是使用这种格式。
7. ---
8. #这里是正文，用markdown写，所有的书写切记需要在  " : "  后面留空格。
9.<!--more-->  \#在<!--more-->之前的内容会显示在首页，之后的内容会被隐藏，当游客点击Read more才能看到。
```