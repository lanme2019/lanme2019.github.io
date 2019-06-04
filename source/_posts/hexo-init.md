# 环境准备
- [Node.js](<https://nodejs.org/zh-cn/>)  (6.9版本及以上)
- [git](<https://git-scm.com/>)

{% note info %}
 Hexo 依赖于 Node.js 和 git，所以在安装 Hexo 之前先确保已安装了这两项应用。
{% endnote %}

具体安装方法自行google啦~

# 开始使用

##  安装 yarn

在 `cmd` 下输入

```bash
$ npm install -g  yarn
```
{% note info %}

`-g`  表示全局安装    将插件加入系统环境变量中   使 `cmd`  可以在任意目录下使用 `yarn` 指令

{% endnote %}

##  安装 Hexo

```bash
$ yarn add  hexo 
```
## 项目初始化
安装 Hexo 完成后，执行下列命令，Hexo 将会在指定文件夹中新建所需要的文件。
```bash
$ hexo init <folder>
$ cd <folder>
$ yarn
```
执行完毕后，你的项目会生成以下目录结构
```plain
.
├── node_modules       //依赖安装目录
├── scaffolds          //模板文件夹，新建的文章将会从此目录下的文件中继承格式
|   ├── draft.md         //草稿模板
|   ├── page.md          //页面模板
|   └── post.md          //文章模板
├── source             //资源文件夹，用于放置图片、数据、文章等资源
|   └── _posts           //文章目录
├── themes             //主题文件夹
|   └── landscape        //默认主题
├── .gitignore         //指定不纳入git版本控制的文件
├── _config.yml        //站点配置文件
├── db.json            
├── package.json
└── yarn-lock.json
```



