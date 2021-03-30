# ElasticSearch

版本：ElasticSearch7.9.1

6.X、7.X的区别十分大，6.X的API（原生API、RestFul高级！）

```
讲解内容
```

SQL：like%狂神说%，如果是大数据，就很慢！

ElasticSearch: 搜索！（百度，github,google）同类有solr

## 1.Doug Cutting

Google搜索引擎，Lucene是Java编写的，目标是各种中小型应用软件加入全文检索功能，开源。

## 2.ElasticSearch概述

Elaticsearch，简称为es,es是一个开源的高扩展的分布式全文检索引擎，它可以近乎实时的存储、检素数据；本身扩展性很好可以扩展到上百台服务器，处理PB级别（大数据时代）的数据。es也使用Java开发并使用 Lusenet作为其核心来实现所有索引和搜索的功能，但是它的目的是通过简单的 RESTFUL API来隐藏 Lucene的复杂性，从而让全文搜索变得简单
 据国际权威的数据庳产品评测机构 DB Enginese的统计，在2016年1月， Elasticsearch已超过solr等，成为排名第一的搜素引擎类应

**谁在使用：**

维基百科、The Guardian、Stack Overflow、github、电商

### 2.1 ES和solr的差别

**ES简介**

Elasticsearch是一个实时分布式搜索和分析引擎。它让你以前所未有的速度处理大数据成为可能。
 它用于全文搜索、结构化搜索、分析以及将这三者混合使用：
 维基百科使用 Elasticsearch提供全文搜索并高亮关键字，以及输入实时搜索（ search- asyou-type）和搜索纠错（ did-you-mean）等搜索建议功能。
 英国卫报使用 Elasticsearch结合用户日志和社交网络数据提供给他们的编辑以实时的反馈，以便及时了解公众对新发表的文章的回应。
 Stackoverflow结合全文搜索与地理位置查询，以及 more-like-this功能来找到相关的问题和答案。
 Github使用 Elasticsearch检索1300亿行的代码。
 但是 Elasticsearch不仅用于大型企业，它还让像 Datadogl以及KIout这样的创业公司将最初的想法变成可扩展的解決方案。
 Elasticsearch可以在你的笔记本上运行，也可以在数以百计的服务器上处理PB级别的数据。
 Elasticsearch是一个基于 Apache Lucene(TM）的开源搜索引擎。无论在开源还是专有领域， Lucene可以被认为是迄今为止最先进
 性能最好的、功能最全的搜索引擎库。
 但是， Lucene只是一个库。想要使用它，你必须使用ava来作为开发语言并将其直接集成到你的应用中，更糟糕的是， Lucene非
 常复杂，你需要深入了解检索的相关知识来理解它是如何工作的
 Elasticsearch也使用ava开发并使用 Lucenet作为其核心来实现所有索引和搜索的功能，但是它的目的是通过简单的 RESTFUL API来隐藏 Lucene的复杂性，从而让全文搜索变得简单。

**Solr简介**

Solr是 Apache下的一个顶级开源项目，采用ava开发，它是基于 Lucene的全文搜索服务器。SoIr提供了比 Lucene更为丰富的查询语言，同时实现了可配置、可扩展，并对索引、搜索性能进行了优化
 Sor可以独立运行，运行在Jeety、 Tomcat等这些 Servlet容器中，Solr索引的实现方法很简单，用POST方法向Solr服务器发送一个描述Field及其内容的XML文档，Sor根据xm文档添加、删除、更新索引。Sor搜索只需要发送HTTP GET请求，然后对Solr返回Xml、json等格式的査询结果进行解析，组织页面布局。Solr不提供构建UI的功能，Solr提供了一个管理界面，通过管理界面可以查询Solr的配置和运行情况。
 solr是基于Lucene。开发企业级搜索服务器，实际上就是封装了 lucene.
 Solr是一个独立的企业级搜索应用服务器，它对外提供类似于Web- servicee的API接口。用户可以通过http请求，向搜索引擎服务器提交一定格式的文件，生成索引；也可以通过提出查找请求，并得到返回结果。

**Lucence简介**

Lucene是 apache软件基金会4 jakarta项目组的一个子项目，是一个开放源代码的全文检索引擎工具包，但它不是一个完整的全文检索引擎，而是一个全文检索引擎的架构，提供了完整的查询引擎和索引引擎，部分文本分析引擎（英文与德文两种西方语言）。
Lucene的目的是为软件开发人员提供一个简单易用的工具包，以方便的在目标系统中实现全文检索的功能，或者是以此为基础建立起完整的全文检索引擎。 Lucene是一套用于全文检索和搜寻的开源程式库，由 Apache：软件基金会支持和提供。 Lucene提供了简单却强大的应用程式接口，能够做全文索引和搜寻。在ava开发环境里 Lucene是一个成熟的免费开源工具。就其本身而言，
Lucene是当前以及最近几年最受欢迎的免费Java信息检素程序库。人们经常提到信息检索程序库，虽然与搜索引擎有关，但不应该
将信息检索程序库与搜索引擎相混淆。
Lucene是一个全文检索引擎的架构。那什么是全文搜索引擎？
全文搜索引擎是名副其实的搜索引擎，国外具代表性的有 Google、Fast/Alltheweb、 Altavista、 Inktomi、 Teoma、 Wisenute等，国内著名的有百度（ Baidu）。它们都是通过从互联网上提取的各个网站的信息（以网页文字为主）而建立的数据库中，检索与用
户查询条件匹配的相关记录，然后按一定的排列顺序将结果返回给用户，因此他们是真正的搜索引擎
从搜索结果来源的角度，全文搜索引擎又可细分为两种，一种是拥有自己的检索程序（ Indexer),俗称蜘蛛"( Spider）程序或机器人"( Robot）程序，并自建网页数据库，搜索结果直接从自身的数据库中调用，如上面提到的7家引擎；另一种则是租用其他引擎的数据库，并按自定的格式排列搜索结果，如 Lycos引擎

**Elasticsearch和Solr比较**



## 3.安装

**ElasticSearch安装**

声明：JDK 1.8及以上版本；ElasticSearch客户端，界面工具！

ES基于Java开发，ES的版本和我们之后对应的Java核心jar包！版本对应，保证JDK环境正常。

**下载**

官网下载即可！（web项目，需要Nodejs,python等依赖）

**安装**

解压到相应目录即安装成功

**熟悉目录**

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200919162016.png)

```
bin 启动文件
config 配置文件所在位置
		log4j2:日志配置文件；
		jvm.options:参数配置文件，电脑配置低的话可修改
		elasticsearch.yml: ES配置文件，集群配置，日志配置，网络配置，默		  认9200端口，有跨域问题，也可做配置。
logs 日志文件
lib 相关jar包
modules 功能模块
plugins 插件目录，比如ik分词器等
```

**启动**

```shell
./bin/elasticsearch
```

注意：ES为了保证安全，Linux下不允许使用root用户启动。

使用普通用户依然报如下错误，原因权限不够

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200919164817.png)

修改ES所有者

```
chown -R cxk:cxk elasticsearch-7.9.1
```

再次启动即可成功启动

**elasticsearch.yml详解**

```yaml
################################### 集群相关配置 ################################### 
# cluster.name可以确定你的集群名称,当你的elasticsearch集群在同一个网段中elasticsearch会自动的找到具有相同cluster.name的elasticsearch服务. 
# 所以当同一个网段具有多个elasticsearch集群时cluster.name就成为同一个集群的标识.，可以手动指定也可以自动生成
# cluster.name: elasticsearch 

#################################### 节点相关配置 ##################################### 
# 节点名称同理,可自动生成也可手动配置. 
# node.name: node-1

# 允许一个节点是否可以成为一个master节点,es是默认集群中的第一台机器为master,如果这台机器停止就会重新选举master. 
# node.master: true 

# 允许该节点存储数据(默认开启) 
# node.data: true 

# 默认情况下，多个节点可以在同一个安装路径启动，如果你想让你的es只启动一个节点，可以进行如下设置
# node.max_local_storage_nodes: 1 

#################################### 索引相关配置 #################################### 
# 设置索引的分片数,默认为5 
#index.number_of_shards: 5 

# 设置索引的副本数,默认为1: 
#index.number_of_replicas: 1 

# 配置文件中提到的最佳实践是,如果服务器够多,可以将分片提高,尽量将数据平均分布到大集群中去
# 同时,如果增加副本数量可以有效的提高搜索性能 
# 需要注意的是,"number_of_shards" 是索引创建后一次生成的,后续不可更改设置 
# "number_of_replicas" 是可以通过API去实时修改设置的 

#################################### 路径相关配置 #################################### 
# 配置文件存储位置 
# path.conf: /path/to/config 

# 数据存储位置(单个目录设置) 
# path.data: /path/to/data 
# 多个数据存储位置,有利于性能提升 
# path.data: /path/to/data1,/path/to/data2 

# 临时文件的路径 
# path.work: /path/to/work 

# 日志文件的路径 
# path.logs: /path/to/logs 

# 插件安装路径 
# path.plugins: /path/to/plugins 


################################### 内存相关配置 #################################### 
# 当JVM开始写入交换空间时（swapping）ElasticSearch性能会低下,你应该保证它不会写入交换空间 
# 设置这个属性为true来锁定内存,同时也要允许elasticsearch的进程可以锁住内存,linux下可以通过 `ulimit -l unlimited` 命令 
# bootstrap.mlockall: true 
# 确保 ES_MIN_MEM 和 ES_MAX_MEM 环境变量设置为相同的值,以及机器有足够的内存分配给Elasticsearch 
# 注意:内存也不是越大越好,一般64位机器,最大分配内存别才超过32G 

############################## 网络相关配置 ############################### 
# 设置绑定的ip地址,可以是ipv4或ipv6的，默认绑定本机ip
# network.bind_host: 192.168.0.1  

# 设置其它节点和该节点交互的ip地址,如果不设置它会自动设置,值必须是个真实的ip地址 
# network.publish_host: 192.168.0.1 

# 同时设置bind_host和publish_host上面两个参数 
# network.host: 192.168.0.1    #绑定监听IP

# 设置节点间交互的tcp端口,默认是9300 
# transport.tcp.port: 9300 

# 设置是否压缩tcp传输时的数据，默认为false,不压缩
# transport.tcp.compress: true 

# 设置对外服务的http端口,默认为9200 
# http.port: 9200 

# 设置请求内容的最大容量,默认100mb 
# http.max_content_length: 100mb 

# 使用http协议对外提供服务,默认为true,开启 
# http.enabled: false 
```

**取消主机限制：**

​	接下来我们具体来配置一下，让elasticsearch服务能够给外部IP访问：
​    首先我们通过刚刚的基础配置发现，网络相关配置中有3个配置项是跟IP有关的：network.bind_host、network.publish_host和network.host，他们的用法分别是：

**network.bind_host:**

在默认情况下elasticsearch服务只能本机访问，如果外部主机需要访问该elasticsearch服务，就需要把外部的这台主机的IP配置到该属性中。那如果希望elasticsearch服务不限制所有主机的访问，那么该属性可以设置为0.0.0.0。

**network.publish_host:**

在默认情况下elasticsearch的节点不能跨主机交互，如果需要，则在该属性配置elasticsearch节点服务所在的IP。那如果希望elasticsearch服务不限制所有主机的节点交互，那么该属性可以配置为0.0.0.0。

**network.host:**

同时设置bind_host和publish_host两个参数，那我们只需要把该属性设置为0.0.0.0，那么就不限制主机的访问和节点的交互。

**修改任意主机可以访问**

打开 `elasticsearch.yml` 找到network.host,打开注释，值设置为 `0.0.0.0`

```
network.host: 0.0.0.0
```

再次启动报以下错误：

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200919192915.png)

第[1]个错误由 `vm.max_map_count` 值太小导致

解决方法：

```
切换到root用户
su root
打开配置文件
vim /etc/sysctl.conf
添加以下配置
vm.max_map_count=655360
退出并保存，执行以下命令
sysctl -p
```

第[2]个问题解决方法

```
打开ES配置文件
vim ./config/elasticsearch.yml
在Discovery栏下添加以下语句
cluster.initial_master_nodes: ["node-1"]
```

再次重启发现启动成功。

通过浏览器访问： `IP/9200`

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/image-20200919194834376.png)

**安装可视化插件elasticsearch-head插件**

注意：需要前端基础环境 `Nodejs`

```
下载插件
git clone git://github.com/mobz/elasticsearch-head.git
下载后进入elasticsearch-head文件夹，安装依赖包
npm install  
进入elasticsearch-head文件夹，运行elasticsearch-head服务
npm run start
```

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200919212659.png)

可以看到访问端口是9100，而ES访问端口号是9200。因此依然无法访问到，需要解决跨域问题。

```
打开elasticsearch.yml配置文件
vim ./config/elasticsearch.yml
添加如下内容，解决与http相关的跨域问题
http.cors.enabled: true
http.cors.allow-origin=: "*"
```

配置ES的连接地址

```
vim /opt/module/elasticsearch-head/_site/app.js
```

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200919214219.png)

将上图中的IP地址改为虚拟机IP

**重启ES 和ES-head**

访问成功

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200919215745.png)

**安装kibana(版本需要与ES一致)**

官网下载即可

解压到安装目录

```
sudo tar -zxvf kibana-7.9.1-linux-x86_64.tar.gz -C ../module/
```

解压后的目录结构

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200919220724.png)

修改kibana的配置文件

```
vim kibana.yml
```

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200920094601.png)

启动Kibana

```
和ES一样kibana不允许root用户启动，需要更改kibana文件夹所有者
sudo chown -R cxk:cxk kibana-7.9.1-linux-x86_64/ 
直接启动，进入bin目录后
./kibana
后台启动，进入bin目录后
nohub ./kibana &
```

访问管理页面

`http://ip:5601`

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200920094901.png)

修改配置文件，使Kibana汉化

汉化文件所在目录： `/opt/module/kibana-7.9.1-linux-x86_64/x-pack/plugins/translations/translations$`

```shell
进入kibana的bin目录，打开配置文件
vim kibana.yml
```

在最后添加以下内容

```
i18n.locale: "zh-CN"
```

## 4.ES核心概念

**概述**

在前面的学习中，我们已经掌握了ES是什么，同时也把es的服务已经安装启动，那么es是如何去存储数据，数据结构是什么，又是如何实现搜索的呢？

**elasticsearch是面向文档 关系型数据库和elasticsearch客观对比**

一切都是JSON



| **RelationalDB**   | Elasticsearch       |
| ------------------ | ------------------- |
| 数据库（database） | 索引（indices）     |
| 表（tables）       | types(后面会被弃用) |
| 行（rows）         | documents           |
| 字段（columns）    | fields              |

elasticsearch（集群）中可以包含多个索引（数据库），每个索引中可以包含多个类型（表），每个类型下又包含多个文档（行），每个文档中又包含多个字段（列）

**物理设计**

elasticsearch在后台把**每个索引划分成多个分片**，每个分片可以在集群中的不同服务器间迁移，一个节点就是一个集群（通过es-head查看）

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200920152503.png)

**逻辑设计**

一个索引类型中，包含多个文档，比如说文档1,文档2.当我们索引ー篇文档时，可以通过这样的一个顺序找到它：索引->类型->文档ID，通过这个组合我们就能索引到某个具体的文档。注意：ID不必是整数，实际上它是个字符串.

`文档`

之前说elasticsearch是面向文档的，那么就意味着索引和搜索数据的最小单位是文档，elasticsearch中，文档有几个重要属性：

- 自我包含，一篇文档同时包含字段和对应的值，也就是同时包含key:value!
- 可以是层次型的，一个文档中包含自文档，负责的逻辑实体就是这么来的！
- 灵活的结构，文档不依赖预先定义的模式，我们知道关系型数据库中，要提前定义字段才能使用，在elasticsearch中，对于字段是非常灵活的，有时候，我们可以忽略该字段，或者动态添加一个新的字段。

尽管我们可以随意的新增或者忽略某个字段，但是，每个字段的类型非常重要，比如一个年龄字段类型，可以是字符串也可以是整形。因为 elasticsearch会保存字段和类型之间的映射及其他的设置。这种映射具体到每个映射的每种类型，这也是为什么在elasticsearch中，类型有时候也称为映射类型。

`类型`

类型是文档的逻辑容器，就像关系型数据库一样，表格是行的容器。类型中对于字段的定义称为映射，比如name映射为字符串类型。我们说文档是无模式的，它们不需要拥有映射中所定义的所有字段，比如新増一个字段，那么 elasticsearch是怎么做的呢？elasticsearch会自动的将新字段加入映射，但是这个字段的不确定它是什么类型， elasticsearch就开始猜，如果这个值是18,那么asticsearch会认为它是整形。但是 elasticsearch也可能猜不对，所以最安全的方式就是提前定义好所需要的映射，这点跟关系型数据库殊途同归了，先定义好字段，然后再使用，别整什么么蛾子。

`索引`

索引是映射类型的容器， elasticsearch中的索引是一个非常大的文档集合。索引存储了映射类型的字段和其他设置。然后它们被存储到了各个分片上了。我们来研究下分片是如何工作的

**物理设计：节点和分片 如何工作**

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200920154201.png)

一个集群至少有一个节点，而一个节点就是一个 elasricsearch进程，节点可以有多个索引默认的，如果你创建索引，那么索引将会有个5个分片（ primary shard，又称主分片）构成的，每一个主分片会有一个副本（ replica shard，又称复制分片）

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200920154302.png)

上图是一个有3个节点的集群，可以看到主分片和对应的复制分片都不会在同一个节点内，这样有利于某个节点挂掉了，数据也不至于丢失。实际上，一个分片是一个 Lucene索引，一个包含倒排索引的文件目录，倒排素引的结构使得 elasticsearch在不扫描全部文档的情況下，就能告诉你哪些文档包含特定的关键字。不过，等等，倒排索引是什么鬼？

`倒排索引`

elasticsearch使用的是一种称为倒排索引的结构，采用 Lucene倒排素作为底层。这种结构适用于快速的全文搜素，一个索引由文档中所有不重复的列表构成，对于每一个词，都有一个包含它的文档列表。例如，现在有两个文档，每个文档包含如下内容：

```yaml
Study every day, good good up to forever # 文档1包含的内容
To forever, study every day, good good up # 文档2包含的内容
```

为了创建倒排索引，我们首先要将毎个文档拆分成独立的词（或称为词条或者 tokens),然后创建一个包含所有不重复的词条的排序列表，然后列出每个词条出现在哪个文档:

| **term** | doc_1 | doc_2 |
| -------- | ----- | ----- |
| Study    | √     | ×     |
| To       | ×     | ×     |
| every    | √     | √     |
| forever  | √     | √     |
| day      | √     | √     |
| study    | ×     | √     |
| good     | √     | √     |
| every    | √     | √     |
| to       | √     | ×     |
| up       | √     | √     |

现在，我们试图搜索to forever,只需要查看包含每个词条的文档

| term    | doc_1 | doc_2 |
| ------- | ----- | ----- |
| to      | √     | ×     |
| forever | √     | √     |
| total   | 2     | 1     |

两个文档都匹配，但是第一个文档比第二个匹配程度更高。如果没有别的条件，现在，这两个包含关键字的文档都将返回。再来看一个示例，比如我们通过博客标签来搜索博客文章。那么倒排索引列表就是这样的一个结构：

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200920160725.png)

如果要搜索含有 python标签的文章，那相对于查找所有原始数据而言，查找倒排索引后的数据将会快的多。只需要查看标签这一栏，然后获取相关的文章ID即可。过滤掉无关的数据，提高效率。
elasticsearch的索引和 Lucene的索引对比
在elasticsearch中，索引这个词被频繁使用，这就是术语的使用。在 elasticsearch中，索引被分为多个分片，每份分片是一个Lucene的索引。所以一个 elasticsearch索引是由多个 Lucene索引组成的。别问为什么，谁让 elasticsearcht使用 Lucene作为底层呢！如无特指，说起索引都是指 elasticsearch的索引
接下来的一切操作都在 kibaha中 Dey Tools下的Console里完成。基础操作！

## 5.ik分词器

**什么是IK分词器**

分词：即把一段中文或者别的判分成一个个的关键字，我们在搜索时候会把自己的信息进行分词，会把数据库中或者索引库中的数据进行分词，然后进行一个匹配操作，默认的中文分词是将每个字看成一个词，比如“我爱狂神”会被分为”我","爱”，"狂","神”，这显
然是不符合要求的，所以我们需要安装中文分词器k来解决这个问题。

如果是中文，建议使用ik分词器

IK提供了两个分词算法： ik_smart和 ik_max_word，其中 ik smart为最少切分， ik max word为最细粒度划分！一会我们测试

**安装**

1.下载：`git clonehttps://github.com/medcl/elasticsearch-analysis-ik.git `

2.下载完毕之后，放入到elasticsearch的插件目录即可。

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200920164836.png)

3.重启观察ES，可以看到加载到了IK分词器。

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200920165933.png)

4.通过命令行也可以看到加载的插件

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200920170233.png)

5.使用kibana进行测试

查看不同的分词器

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200920173337.png)

有些词拆分后可能不是想要的，需要自己添加到分词器字典里面。

`ik分词器增加自己的配置`

配置文件所在位置

```
/opt/module/elasticsearch-7.9.1/plugins/ik/configIKAnalyzer.cfg.xml
```

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200920175009.png)

dic中存放的是分词字典。

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200920175340.png)

添加完字典后，重启ES，再次测试想要的词。

## 6.Rest风格说明

一种软件架构风格，而不是标准，只是提供了一组设计原则和约束条件，它主要用于客户端和服务器交互类的软件。基于这个风格设计的软件可以更简洁，更有层次，更易于实现缓存等机制。

| method | url地址                                         | 描述                   |
| ------ | ----------------------------------------------- | ---------------------- |
| PUT    | localhost:9200/索引名称/类型名称/文档id         | 创建文档（指定文档id） |
| POST   | localhost:9200/索引名称/类型名称                | 创建文档（随机文档id） |
| POST   | localhost:9200/索引名称/类型名称/文档id/_update | 修改文档               |
| DELETE | localhost:9200/索引名称/类型名称/文档id         | 删除文档               |
| GET    | localhost:9200/索引名称/类型名称/文档id         | 查询文档通过文档id     |
| POST   | localhost:9200/索引名称/类型名称/_search        | 查询所有数据           |

**基础测试**

1.创建一个索引，在kibana中执行以下命令！

```
put /索引名/~类型名~/文档id
{请求体}
```

注意：波浪线＋类型名意思是未来类型名会消失

```
PUT /test1/type1/1
{
	"name": "蔡向科",
	"age": 28
}
```

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200920181327.png)

从图中可以看到创建成功，可以通过es-head查看。

如果自己的文档字段没有指定，那么es就会给我们默认配置字段类型。

扩展：通过命令elasticsearch索引情况，通过 `_cat`命令获得很多es信息。

```
GET _cat/health  #查看健康状态
GET _cat/indices?v #查询有多少个库
```

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200920195400.png)

2.上述创建索引时并未指定数据类型，支持的类型有以下几种

- 字符串类型

  text、keyword

- 数值类型

  long、integer、short、byte、double、float、half float、scaled float

- 日期类型

  date

- 布尔值类型

  boolean

- 二进制类型

  binary

- 等等。。。

3.指定字段的类型

```
PUT /test2
{
  "mappings": {
    "properties": {
      "name":{
        "type": "text"
      },
      "age":{
        "type": "long"
      },
      "brithday":{
        "type":"date"
      }
    }
  }
}
```

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200920190128.png)

获得这个规则

```
GET test2
```

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200920193637.png)

4.修改，提交还是使用PUT即可，然后覆盖

曾经的办法（修改后版本号会增加）

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200920195804.png)

最新的方法

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200920200041.png)

5.删除索引

```
DELETE test1 # 删库
DELETE test1/type1/1 #精确删除文档
```

通过DELETE 命令实现删除，根据你的请求来判断是删除索引还是删除文档记录。

使用RestFul风格是我们ES推荐使用的！

## 7.关于文档的基本操作（重点）

### 7.1.基本命令

1.添加数据

```
PUT /yimisiyang/user/1
{
  "name": "一米思阳",
  "age": 28,
  "desc": "一顿操作猛如虎，一问工资2500",
  "tags": ["技术宅","旅游","科技"]
}
PUT /yimisiyang/user/2
{
  "name": "蔡向科",
  "age": 26,
  "desc": "一顿操作猛如虎，一问工资3200",
  "tags": ["技术宅","旅游","科技"]
}
```

2.获取数据

```
GET /yimisiyang/user/1
```

3.更新数据PUT(直接修改后再次执行)

该命令不传值则会置空。

```
PUT /yimisiyang/user/1
{
  "name": "李四",
  "age": 28,
  "desc": "一顿操作猛如虎，一问工资2500",
  "tags": ["技术宅","旅游","科技"]
}
```

POST更新数据（推荐使用）

```
POST /yimisiyang/user/1/_update
{
  "doc":{
    "desc":"我爱我家"
  }
}
```

**简单地搜索！**

```
GET /yimisiyang/user/1
```

**带条件的搜索**

```
GET /yimisiyang/user/_search?q=name:蔡向科
```

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200920205334.png)

**复杂操作搜索 select(排序、分页、高亮、模糊查询、精准查询)**

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200920205656.png)

查询语句格式

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200920205912.png)

查询结果安装匹配度排序

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200920210240.png)

查询结果过滤

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200920210559.png)

之后使用Java操作es,所有的方法和对象就是里面的key

排序查询

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200920210929.png)

分页查询

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200920211146.png)

数据下标还是从0开始的，和其它数据结构是一样的。

布尔值查询（实现多条件精确查询）

must (and),所有条件都要匹配

should (or)，任意条件匹配即可查询出来

must_not( not), 不必须的查询出来

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200920211537.png)

过滤查询

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200920212045.png)

- gt 大于
- gte 大于等于
- lt 小于
- lte 小于等于

匹配多个条件

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200921090006.png)

精确查询，term查询是直接通过倒排索引指定的词条进程精确查找的！

关于分词：

- term，直接查询精确的

- match，会使用分词器解析！（先分析文档，然后通过分析的文档进行查询！）

两个类型 text类型和keyword类型

text类型会被分词器解析，keyword类型不会被分词器解析。

创建索引，并插入多条数据

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200921090705.png)

查询测试

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200921091014.png)

多个值匹配精确查询

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200921170112.png)

高亮查询（每个字段都加了一个em标签）

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200921170346.png)

自定义高亮格式查询

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200922090614.png)



## 8.集成SpringBoot

学习步骤：找官方文档（与客户端相关的，这里学习推荐使用RESTful客户端）

1.找到原生的依赖

```html
<dependency>
    <groupId>org.elasticsearch.client</groupId>
    <artifactId>elasticsearch-rest-high-level-client</artifactId>
    <version>7.9.1</version>
</dependency>
```

2.找对象

```java
RestHighLevelClient client = new RestHighLevelClient(
        RestClient.builder(
                new HttpHost("localhost", 9200, "http"),
                new HttpHost("localhost", 9201, "http")));
```

使用完之后关闭

```java
clint.close()
```

3.分析这个类中的方法即可（配置项目）



4.所有的API讲解

`创建索引`

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200923093322.png)

`测试获取索引，只能判断是否存在`

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/image-20200923102716009.png)

`测试删除索引`

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/image-20200923103758638.png)

`测试添加文档`

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200923150002.png)

`测试获取文档`

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200923152703.png)

`更新文档记录`

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200923160214.png)

`删除文档`

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20200924100434.png)

`批量插入数据`

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/image-20200924165948318.png)

`搜索`

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/image-20200925091430116.png)

### 8.1.实战



### 8.2.前后端分离



### 8.3.搜索高亮

## 9.ElasticSearch导入json数据

### 1.获取json数据集

自己构建或者从网上下载

### 2.使用`_bulk`批量写入数据

`符合bulk API 的json文件数据格式`

```json
{"index":{"_id":"1"}}
{"title":"learn es","content":"work hard"}
{"index":{"_id":"2"}}
{"title":"learn hadoop","content":"work hard"}

```

`命令`

```shell
curl -XPOST '182.92.57.11:9200/test/book/_bulk?pretty' --data-binary @bookdata.json
```

`报错如下`

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20210220144732.png)

`报错原因`

自从ElasticSearch6版本之后，增加了安全机制，进行严格的内容类型检查，严格检查内容类型也可以作为防止跨站点请求伪造攻击的一层保护。

`解决方法`

增加请求头即可正常查询，修改后的命令如下。

```shell
curl -H "Content-Type:application/json" -XPOST '182.92.57.11:9200/test/book/_bulk?pretty' --data-binary @bookdata.json
```

`依然有报错，报错内容改为下图`

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20210220145315.png)

`报错原因`

json文件最后一行需要打回车进行换行，修改后可以导入数据。

### 3.使用GET查询数据

使用命令行查询ElasticSearch中有哪些索引

```shell
curl -XGET '182.92.57.11:9200/_cat/indices'
```

使用命令行查询ElasticSearch某个索引中的数据

```shell
curl -XGET '182.92.57.11:9200/test_book/_doc/666'
```

使用命令导入accounts.json数据

```shell
#导入数据
curl -H "Content-Type: application/json" -XPOST "182.92.57.11:9200/bank/_bulk?pretty&refresh" --data-binary "@accounts.json"
#查询是否导入成功
curl "182.92.57.11:9200/_cat/indices?v=true"
```

### 4.使用kibana进行数据查询

输入`IP:5601`进入kibana主页-左侧工具栏找到Dev Tools-输入查询命令

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20210222090136.png)

通过 `_search`请求查询数据

```
GET /test_bank/_search
{
  "query": { "match_all": {} },
  "sort": [
    { "account_number": "asc" }
  ]
}
```

**解释：** 查询 `test_bank` 索引中的所有数据，返回结果按照`account_number` 升序排序

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20210222093959.png)

查询结果中包含信息解释

- `took` – how long it took Elasticsearch to run the query, in milliseconds
- `timed_out` – whether or not the search request timed out
- `_shards` – how many shards were searched and a breakdown of how many shards succeeded, failed, or were skipped.
- `max_score` – the score of the most relevant document found
- `hits.total.value` - how many matching documents were found
- `hits.sort` - the document’s sort position (when not sorting by relevance score)
- `hits._score` - the document’s relevance score (not applicable when using `match_all`)

查询指定范围内的数据

内容从第10条开始显示，显示5条内容。

![](https://raw.githubusercontent.com/yimisiyang/cloudimage/master/Image/20210222095908.png)

使用 `match`构造查询

例如：查询地址中包含 `mill` 或 `lane` 的内容，查询结果不区分大小写。

```
GET /test_bank/_search
{
"query":{"match":{"address":"mill lane"}}
}
```

使用 `match_parase` 查询

例如：查询地址中包含 `mill lane`的内容，查询结果不区分大小写。

```
GET /test_bank/_search
{
"query":{"match_parase":{"address":"mill lane"}}
}
```

使用 `bool` 构造复杂查询

```
GET /test_bank/_search
{
	"query":{
		"bool":{
			"must":[
				{"match":{"age":"40"}}
			],
			"must_not":[
				{"match":{"state":"ID"}}
			]
		}
	}
}
```

### 5.使用汇总分析查询结果

按照倒叙排序返回账户最多的十个州，`size=0` 的目的是只返回聚合结果，而不反悔其它数据。

```
GET /test_bank/_search
{
  "size": 0,
	"aggs": {
	  "group_by_state": {
	    "terms": {
	      "field": "state.keyword"
	    }
	  }
	}
}
```

使用连续聚合构造复杂查询结果，查询账户数最多的十个州，并统计他们的评价存款，排序是按照账户数进行的逆序排序。

```
GET /test_bank/_search
{
  "size": 0,
	"aggs": {
	  "group_by_state": {
	    "terms": {
	      "field": "state.keyword"
	    },
	    "aggs": {
	      "average_balance": {
	        "avg": {
	          "field": "balance"
	        }
	      }
	    }
	  }
	}
}
```

使用连续聚合构造复杂查询结果，查询账户数最多的十个州，并统计他们的评价存款，排序是按照存款多少进行逆序排序。

```
GET /bank/_search
{
  "size": 0,
  "aggs": {
    "group_by_state": {
      "terms": {
        "field": "state.keyword",
        "order": {
          "average_balance": "desc"
        }
      },
      "aggs": {
        "average_balance": {
          "avg": {
            "field": "balance"
          }
        }
      }
    }
  }
}
```

## 10.设置ElasticSearch

**参考网址：**https://www.elastic.co/guide/en/elasticsearch/reference/current/install-elasticsearch.html

主要包含以下内容

- 各平台安装ElasticSearch
- 配置管理工具（通过配置管理工具完成批量集群部署）
  - puppet-elasticsearch
  - cookbook-elasticsearch
  - ansible-elasticsearch

## 11.索引模块

索引模块是为每个索引创建的模块并用于创建与索引相关方面的内容。每个索引可以设置成静态索引和动态索引。

在一个关闭的索引上更改静态或动态索引设置可能导致不正确，如果没有删除和重建这些索引就无法纠正这些错误。

- 静态索引设置

  - `index.number_of_shards` 索引具有的主要切片数，默认是1，只能在创建索引时设置，创建完成后无法更改。每个索引最大设置切片数为1024。可以在节点上指定以下系统设置来更改此值，`export ES_JAVA_OPTS="-Des.index.max_number_of_shards=128`
  - `index.number_of_routing_shards` 用于拆分索引的路由分片数，这个数的默认值取决于在索引中的主切片数，允许以2的因数进行差分，最大值为1024。
  - `index.shard.check_on_startup` 打开前是否检查切片是否损坏，若损坏，则禁止切片打开。

- 调整索引速度

  - 使用批量请求

    批量索引请求快于单个索引请求，为了知道批量请求的最佳大小，你应该在具有单个分片的单个节点上运行基准测试，测试单索引100文档、200文档、400文档等等。当索引速度趋于平稳时，你便知道了最佳大小。

  - 使用多工作/线程将数据发送到ES

    注意 `TOO_MANY_REQUESTS (429)` 响应代码，该代码告诉你无法保持当前的索引速率。

  - 取消设置或增加刷新时间

  - 禁用副本以初始化加载

  - 禁用交换

  - 将内存分配给文件系统进行缓存

  - 使用自动生成ID

  - 使用更快的硬件

  - 更改索引缓冲区大小

  - 使用跨集群复制来阻止搜索从索引中窃取资源。









## ElasticSearch使用建议

参考：https://www.elastic.co/guide/en/elasticsearch/reference/current/general-recommendations.html#maximum-document-size

- 不要返回大的结果集
  - ES擅长获取与搜索要求最匹配的文档。不擅长返回与查询结果相匹配的所有文档，这一点与数据库不一样，如果非要这么做，可以考虑 `Scroll API`。
- 避免过大的文档
  - 假设 `http.max_content_length` 设置为100MB，ES拒绝索引任何大于该值的文档，你可以更改该值大小，但是Lucene限制为2GB。