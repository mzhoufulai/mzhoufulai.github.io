# Hugo+Github搭建个人博客


**Hugo + Github 搭建个人博客**

## 1 准备工作
以苹果电脑为例：
1. Hugo的安装
2. Github的账号的注册
3. Git的安装
## 2 搭建流程
### 软件安装
1. Hugo 安装
2. Github 账号注册
3. Git的安装
### 搭建流程

**初始化**
初始化我们的 Hugo 我们首先需要选择一个路径来存放我们的博客，在你选好的路径下执行   
hugo new site Blog   
这条命令会创建一个名为 Blog (你也可以使用你喜欢的任意名字) 的文件夹来存放你的博客。执行 cd Blog 进入文件夹。

`git clone https://github.com/dillonzq/LoveIt.git themes/LoveIt`

创建新页面   
`hugo new about.md`


此时你就可以在 http://localhost:1313 访问到你的博客了  
`hugo server --buildDrafts -w`


`hugo`   
此时你的博客目录下会多出一个 public 文件夹来。这便是 Hugo 生成的网站

第一次发布
```
git init
git remote add origin https://github.com/[Github 用户名]/[Github 用户名].github.io.git
git add -A
git commit -m "[介绍，随便写点什么，比如日期]"
git push -u origin master # 如果该命令失败，尝试 git push -f origin master

```
以后发布
```
git add -A
git commit -m "[介绍，随便写点什么，比如日期]"
git push -u origin master
```
## 参考文章
1. [使用 Hugo + GitHub Pages 搭建个人博客](https://mogeko.me/2018/018/)
2. [使用Hugo搭建静态站点](https://tonybai.com/2015/09/23/intro-of-gohugo/)
3. [Hugo中文文档](https://hugo.aiaide.com)



