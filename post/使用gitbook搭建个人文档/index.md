# 使用Gitbook搭建个人文档


{{<admonition>}}
	Gitbook
	Github
{{</admonition>}}
以Mac为例

### 1 安装node.js (Homebrew安装)

查找node.js

`brew search node.js`   

安装node.js   

`brew install node.js`   

查看node.js版本   

`node -v`

更新node.js

`brew upgrade node`

### 2 安装gitbook

安装gitbook

`npm install gitbook-cli -g`

查看gitbook版本

`gitbook -V`

### 3 创建Book目录
```markdown
cd Book
gitbook init # Book目录下多了README.md和SUMMARY.md文件
```
{{<admonition note "注意:">}}
    在运行gitbook init后，Book目录下只产生了README.md，SUMMARY.md文件产生失败，同时还报错。后面在创建book.js后安装插件报错失败。所以后面改用docsify进行个人文档的搭建。
{{</admonition>}}

### 4 生成网页并启动gitbook
```markdown
gitbook serve # 通过http://localhost:4000即可访问
```
### 5 生成网页不启动gitbook
```markdown
# 默认将静态页面生成在 _book目录下,
gitbook build

# 如果想指定目录,比如托管在github上,则需要生成在docs目录,可以使用以下命令
gitbook build ./ ./docs
```
### 6 目录结构生成
再次执行gitbook init，即可看到目录下初始化了在SUMMARY.md里配置的目录结构
```markdown
gitbook init
```
我们只需要在相应目录下添加内容即可

### 7 插件使用
```
Gitbook默认自带有5个插件：
如果不用可以前面加-去掉
highlight： 代码高亮
search： 导航栏查询功能（不支持中文）
sharing：右上角分享功能
fontsettings：字体设置（最上方的"A"符号）
livereload：为GitBook实时重新加载
```
如果想使用插件等,可以在目录下创建book.json配置文件,附上配置文件
```json
{
    "title": "古道长亭",  //标题
    "author": "古道长亭", //作者
    "description": "welcome to my docs", //书描述
    "language": "zh-hans", //语言 en, zh-hans, zh-tw
    "gitbook": "3.2.3",  //指定gitbook版本
    "styles": {       //样式文件
        "website": "./style/website.css"
    },
    "structure": {   //指定 Readme、Summary、Glossary 和 Languages 对应的文件名
        "readme": "README.md"
    },
    "links": {      //左侧导航栏链接信息
        "sidebar": {
            "回到博客": "https://blog.zhaojq.top"
        }
    },
    "plugins": [    //插件列表
        "anchors",
        "anchor-navigation-ex",  //给页面H1-H6标题增加锚点效果,浮动导航模式,页面内顶部导航模式等
        "auto-scroll-table", //表格滚动条
        "advanced-emoji",   //支持emoji表情    
        "code", //代码添加行号&复制按钮
        "chapter-fold", //导航目录折叠
        "donate", //打赏插件
        "expandable-chapters-small",//可扩展导航章节,比toggle-chapters好用
        "favicon", //标题栏图标配置
        "fontsettings",   //字体设置（最上方的"A"符号）                     
        "github",  //在右上角添加github图标
        "github-buttons",//github按钮显示,包括可配置stars数量等
        "klipse",  //嵌入类似IDE的功能
        "-livereload", //为GitBook实时重新加载
        "-lunr", //自带搜索
        "pageview-count", //阅读量计数
        "page-toc-button", //page-toc-button
        "popup", //弹出大图
        "sharing-plus", //分享插件
        "-sharing", //自带分享
        "splitter", //侧边栏宽度可调节
        "-search",  //自带搜索,前面加-去掉
        "search-pro", //高级搜索插件 需要将默认的search和lunr 插件去掉
        "toggle-chapters", //扩展导航章节,由expandable-chapters-small代替
        "tbfed-pagefooter", //页面添加页脚（简单的）
        "todo", //待做项
        "hide-element" //隐藏元素,比如导航栏中Published by GitBook,"elements": [".gitbook-link"]
    ],
    "pluginsConfig": {   //配置插件的属性
        "github": {
            "url": "https://github.com/zhao-xiaoer"
        },
        "hide-element": {
            "elements": [".gitbook-link"]
        },
        "theme-default": {
            "showLevel": true
        },
        "code": {
            "copyButtons": true
        },
        "tbfed-pagefooter": {
            "copyright": "Copyright © zhaojq 2019",
            "modify_label": "本书发布时间：",
            "modify_format": "YYYY-MM-DD HH:mm:ss"
        },
        "donate": {
            "wechat": "/gitbook/source/images/wechat.jpeg",
            "alipay": "/gitbook/source/images/alipay.jpeg",
            "title": "感谢支持",
            "button": "\uD83D\uDE00",
            "alipayText": "支付宝打赏",
            "wechatText": "微信打赏"
        },
        "github-buttons": {
            "buttons": [{
                "user": "zhao-xiaoer",
                "repo": "gitbook",
                "type": "star",
                "size": "small",
                "count": true
                }
            ]
        },
        "page-toc-button": {
            "maxTocDepth": 2,
            "minTocSize": 2
        },
        "sharing": {
            "douban": false,
            "facebook": false,
            "google": false,
            "hatenaBookmark": false,
            "instapaper": false,
            "line": false,
            "linkedin": false,
            "messenger": false,
            "pocket": false,
            "qq": true,
            "qzone": true,
            "stumbleupon": false,
            "twitter": false,
            "viber": false,
            "vk": false,
            "weibo": true,
            "whatsapp": false,
            "all": [
                "weibo","qq", "qzone", "douban", "facebook","google",
                              "linkedin","twitter","whatsapp"
            ]
        },
        "anchor-navigation-ex": {
            "showLevel": true
        },
        "favicon":{
            "shortcut": "",
            "bookmark": ""
        }
    }
}
```
使用以下命令安装插件
```
gitbook install
```

### 8 发布到Github

首先build到docs目录

在github新建一个工程,例如:gitbook

将gitbook整个目录push到github/gitbook

配置个人域名的方法和hugo的配置一样,github会自动从docs目录加载静态页面.

接下来你可以通过个人域名访问gitbook


### 参考资料
1. [如何使用Gitbook搭建个人文档](https://www.jianshu.com/p/e2f2f11d1369)

