---
title: hexo
date: 2018-08-16 22:03:01
tags: server
---

1、安装node.js
```bash
https://nodejs.org/zh-cn/
安装：https://blog.csdn.net/qq_40712862/article/details/120231621

node -v判断是否安装成功
```
下载慢解决方法:
```bash
更换淘宝镜像下载源：npm config set registry https://registry.npm.taobao.org
或国内的npm镜像命令：npm install -g cnpm --registry=https://registry.npm.taobao.org
```
安装指定版本
```bash
安装：https://blog.csdn.net/weixin_44198965/article/details/124140283
版本：https://nodejs.org/download/release/v15.7.0/
```
2、注册github
https://github.com/

3、安装hexo
新建文件夹，打开cmd，输入命令npm install hexo-cli -g
hexo -v出现版本号即安装成功
如果卸载hexo

安装成功后可在C:\Users\Administrator\AppData\Roaming文件夹下看到npm文件夹
卸载命令：卸载成功后npm文件夹会消失npm uninstall hexo-cli -g
安装指定版本
```bash
查看版本hexo --version
安装 Hexo 指定版本npm i hexo@4.2.1 --save
```
4、生成本地静态网页
```bash
hexo init 博客名称初始化
cd 博客名称进入文件夹，npm install安装依赖
hexo g生成静态网页
hexo s打开本地预览
hexo clean，清除缓存文件 db.json 和已生成的静态文件在 ./public/文件夹下
```
5、上传github
创建仓库create repository
填写仓库名称需要和gihub账号一致，勾选Add a README file，点击创建
进入仓库点击settings->Pages，找到Github Page
Branch分支改成main或master
6、安装git
```bash
https://git-scm.com/
```
配置ssh密钥

鼠标右键打开Git Bash Here窗口，执行ssh-keygen
然后打开此电脑–>C盘–>用户–>Administrator–>.ssh(文件夹)–>用记事本打开 id_rsa.pub 文件，全选复制
或者：打开Git Bash Here窗口输入cat ~/.ssh/id_rsa.pub输出SSH Key，然后复制
打开注册的github，进入设置–>SSH公钥–>在公钥区粘贴刚才复制的公钥，点击确定输入github登陆密码进行验证即可
克隆github项目到本地
```bash
git init初始化本地仓库，后会在本地文件夹下生成一个 .git 文件夹
开始克隆：git clone 仓库地址
git的推送操作

git status 查看当前状态。
git add 文件名表示将某个文件添加至暂存区。
git add .表示将所有(进行修改的)文件添加至暂存区。
git commit -m “xxx” xxx表示自己对本次提交所进行的备注或者标注。
git remote add origin SSH链接 表示建立本地库与想要操作的远程仓库的联系。
git push -u origin master 表示实现由本地库向远程仓库的推送。

git的拉取操作

git pull origin master 表示将远程仓库的内容文件同步更新拉取到本地库。
```
问题
如果执行git push origin master报错:The project you were looking for could not be found，则通过(管理员运行)git config --system --unset credential.helper清除账户信息并且在windows凭证里添加账户信息

7、连接github，git config配置用户账户:
```bash
git config --global user.name "username"
git config --global user.email "email"
```
将username和email换成github的用户名和邮箱
–global 表示全局的，即当前用户都有效，该配置会出现在 ~/.gitconfig 文件中，~表示当前用户的目录，比如：C:\Users\username.gitconfig
```bash
ssh-keygen -t rsa -C "你GitHub账号的邮箱"来生成SSH Key，中途按3次回车
```
8、hexo 关联github
打开hexo文件夹里面的_config.yml文件，这是hexo的配置文件修改：
```bash
deploy:
      type: git
      repo: ssh://git@github.com/github账号名称/github账号名称.github.io.git
      branch: master
```
然后在cmd上输入npm install hexo-deployer-git --save安装GitHub推送插件
安装好了以后再输入hexo g生成静态网页，再输入hexo d上传到GitHub就可以了
9、hexo 主题
```bash
https://hexo.io/themes/
```
比如安装主题next：npm install hexo-theme-next

10、hexo 配置
```bash
    # Hexo Configuration Hexo配置文件
    ## Docs: https://hexo.io/docs/configuration.html
    ## Source: https://github.com/hexojs/hexo/
    
    
    # 网站信息
    #标题
    title: 学志の博客
    #副标题
    subtitle: 记录学习的技能和遇到的问题
    #网站描述
    description: 做自己爱做的事，爱自己在做的事！
    #作者昵称
    author: 张学志
    #网站语言，默认英语，设置简体汉语
    language: zh-Hans
    
    #时区，默认电脑时区
    #timezone: 
    timezone: Asia/Shanghai
    
    
    # 网址设置
    #如果网站是放在子目录中，将url设置成'http://yoursite.com/child'，将root设置成'/child/'
    ## If your site is put in a subdirectory, set url as 'http://yoursite.com/child' and root as '/child/'
    #网址
    url: http://zhangxuezhi.com
    #网站根目录。如果网站是放在子目录中，将root设置成'子目录名'
    root: /
    #文章链接地址格式 。即文章存放的目录。
    permalink: :year/:month/:day/:title/
    permalink_defaults:
    
    
    # 目录设置
    #资源文件夹，放在里面的文件会上传到github中
    source_dir: source
    #公共文件夹，存放生成的静态文件
    public_dir: public
    #标签文件夹，默认是tags。实际存放在source/tags中。
    tag_dir: tags
    rss_dir: rss
    #档案文件夹，默认是archives。
    archive_dir: archives
    #分类文件夹，默认是categories。实际存放在source/categories中。
    category_dir: categories
    #代码文件夹，默认是downloads/code
    code_dir: downloads/code
    #国际化文件夹，默认跟language相同
    i18n_dir: :lang
    #不需要渲染的文件夹或文件夹,放在[]中
    # 这两个文件是百度和google的站长验证文件，不能渲染，否则会改变内容，不能验证过
    skip_render: [baidu_verify_R9MZjdMkXT.html, google0f8fac7da2b48ef8.html, README.md, 模板.md]
    
    
    # 写作选项
    # 新建博文（帖子）的默认名称
    # File name of new posts
    new_post_name: :title.md 
    #默认布局模板是post，而不是draft和page
    default_layout: post
    #是否将标题转换成标题形式（首字母大写）
    titlecase: false # Transform title into titlecase
    #在新标签页面中打开网页
    external_link: true # Open external links in new tab
    filename_case: 0
    #是否渲染草稿
    render_drafts: false
    #启动 Asset 文件夹
    post_asset_folder: false
    #把链接改为与根目录的相对位址
    relative_link: false
    #显示未来的文章
    future: true
    #代码块的设置
    highlight:
      enable: true          #  使用代码高亮
      line_number: true # 显示行号
      auto_detect: true  # 自动检测语言
      tab_replace:
    
      
    # 分类和标签
    # 默认分类
    default_category: uncategorized
    #分类别名
    category_map:
    #标签别名
    tag_map:
    
    
    # 日期和时间格式
    #Hexo 使用 Moment.js 来解析和显示时间。
    ## You can customize the date format as defined in
    ## http://momentjs.com/docs/#/displaying/format/
    date_format: YYYY-MM-DD
    time_format: HH:mm:ss
    
    
    # 分页配置
    # ---------------下面选项需要对应插件的支持---------------
    # npm install hexo-generator-index --save
    # npm install hexo-generator-archive --save
    # npm install hexo-generator-category --save
    # npm install hexo-generator-tag --save
    ## Set per_page to 0 to disable pagination
    #每页显示的文章量 
    #per_page: 20
    #首页的分页设置
    index_generator:
      per_page: 5
    #归档页的分页设置
    archive_generator:
      per_page: 30
      yearly: true
      monthly: true
    #标签页的分页设置
    tag_generator:
      per_page: 20
    
    #分页路径，在public中可以看到
    #pagination_dir: page
    
    
    # Extensions 拓展插件配置
    ## Plugins: https://hexo.io/plugins/
    plugins: 
    baidusitemap: 
      path: baidusitemap.xml
    
    
    # 配置RSS
    feed: 
      #feed 类型 (atom/rss2)
      type: atom   
      #rss 路径
      path: atom.xml  
      #在 rss 中最多生成的文章数(0显示所有)
      limit: 0
      
      
      
    # 自定义站点内容搜索
    # 需要先安装插件：
    # npm install hexo-generator-search --save
    search:
      path: search.xml
      # 如只想索引文章，可设置为post
      field: all 
      
    # 主题配置
    ## Themes: https://hexo.io/themes/
    #theme: false #禁用主题
    #theme: landscape
    theme: next
    
    
    # 部署配置
    ## Docs: https://hexo.io/docs/deployment.html
    deploy:
      type: git
      #repo: https://github.com/xuezhisd/xuezhisd.github.io.git
      repo: 
        # 部署到github
        github: git@github.com:xuezhisd/xuezhisd.github.io.git,master
        # 部署到coding.net。取消注释，可同时部署
        #coding: git@git.coding.net:xuezhisd/blog.git,coding-pages
      #type: baidu_url_submitter
```

11、 新增菜单栏选项
添加新页面：hexo new page "xx"
在主题配置文件的menu中加上该页面
在zh-CN.yml文件中加上中文意思
12、图片处理
配置文件中的post_asset_folder改成true
安装依赖npm install hexo-asset-image --save
放到该文件夹下，按照md格式输入(文件名称/图片名.jpg)
13、搜索
```bash
-安装依赖 npm install hexo-generator-searchdb --save
```
站点配置文件的扩展下添加
```bash
 search:
      path: search.xml
      field: post
      format: html
      limit: 10000

主题配置文件下，local_search改成true即可
local_search:
      enable: true
```
14、新建文章
hexo new 文章名称
存储在/source/_posts下
hexo 插件
插件汇总：https://blog.csdn.net/qq_43701912/article/details/107310923
