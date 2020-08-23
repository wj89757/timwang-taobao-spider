# 淘宝店铺爬虫
#### 一、介绍

代码用python实现，主要用于爬取淘宝店铺搜索列表页结果数据，链接如下：https://shopsearch.taobao.com/search?q=<搜索关键词>，主要爬取的信息有（店铺名称/店铺图片/卖家名称/销量/宝贝数量/好评率/主营/店铺链接等信息），用于辅助分析一些竞品数据信息和产品信息。通过该信息可以更好的掌握行业情况

#### 二、软件架构

该软件python实现改爬虫，mongodb进行持久化操作，selenium进行模拟浏览器的操作。代码逻辑还是整体比较简单

> Selenium`是开源的自动化测试工具，它主要是用于Web 应用程序的自动化测试，不只局限于此，同时支持所有基于web 的管理任务自动化。Selenium 是用于测试 Web 应用程序用户界面 (UI) 的常用框架。它是一款用于运行端到端功能测试的超强工具。您可以使用多个编程语言编写测试，并且 Selenium 能够在一个或多个浏览器中执行这些测试。
>
> Selenium 官网：[seleniumhq.org/](https://link.jianshu.com/?t=http%3A%2F%2Fseleniumhq.org%2F)
>
> Selenium Github 主页：[github.com/SeleniumHQ/…](https://link.jianshu.com/?t=https%3A%2F%2Fgithub.com%2FSeleniumHQ%2Fselenium)

#### 三、安装教程

##### 1. Python 依赖安装

本实例采用python3

```shell
vi ~/.bashrc

export PYTHONPATH=$PYTHONPATH:/usr/local/lib/python3.7/site-packages
export PATH=/usr/local/mongoDB/bin:$PATH

source ~/.bashrc
```

1. 安装selenium

   ```
   pip install -U selenium // 安装
   pip show selenium  //是否安装成功
   ```

2. 安装pymongo

   ```linux
   pip install PyMongo
   ```

##### 2. 安装Mongodb

此外你还可以使用 OSX 的 brew 来安装 mongodb：

```shell
brew tap mongodb/brew
brew install mongodb-community@4.4
```

安装信息：

- 配置文件：**/usr/local/etc/mongod.conf**
- 日志文件路径：**/usr/local/var/log/mongodb**
- 数据存放路径：**/usr/local/var/mongodb**

我们可以使用 brew 命令或 mongod 命令来启动服务。

brew 启动：

```
brew services start mongodb-community@4.4
```

brew 停止：

```
brew services stop mongodb-community@4.4
```

mongod 命令后台进程方式：

```
mongod --config /usr/local/etc/mongod.conf --fork
mongod --config /usr/local/etc/mongod.conf
```

##### 3. 配置Chrome的Default数据

具体可以查看：[chrome://version/](chrome://version/)，有一个**个人资料路径**，拷贝Default目录，到python执行文件的统计目录下

![](https://tva1.sinaimg.cn/large/007S8ZIlgy1gi0pzgs1d3j30iu01imx8.jpg)

#### 四、使用说明

1. 启动python

   ```python
   python3 shop_spider.py
   ```

2. 导出csv数据，进行分析

```
sudo mongoexport -d shops -c akf -o <download-file-path> --type csv -f  "_id,shoptitle,shopimg,seller,sales,products,goodcomt,main,link"
```

#### 五、参与贡献

1. 克隆 本仓库 git clone https://github.com/wj89757/timwang-taobao-spider.git
2. 新建 dev-xxx 分支 git checkout -b dev-xxx
3. 提交代码
4. 新建 Pull Request