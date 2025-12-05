本项目采用scrapy框架，爬取知乎的回答，主要是为了学习scrapy框架，以及了解知乎的反爬机制。
## 1. 爬取知乎回答
### 1.1 爬取知乎回答的思路
知乎的回答是动态加载的，所以不能直接通过requests请求，需要通过selenium模拟浏览器请求，获取到动态加载的数据，然后再通过xpath解析数据，获取到需要的数据。
### 1.2 爬取知乎回答的过程
1. 通过selenium模拟浏览器请求，获取到动态加载的数据
2. 通过xpath解析数据，获取到需要的数据
3. 通过scrapy框架，将数据保存到mysql数据库中
### 1.3 爬取知乎回答的结果
爬取知乎回答的结果如下图所示：
![img_3.png](img_3.png)
![img_4.png](img_4.png)
## 2. 数据分析
### 2.1 数据分析的思路
1. 通过pandas将mysql数据库中的数据读取到dataframe中
2. 通过matplotlib将数据可视化
3. 通过wordcloud将数据生成词云
4. 通过jieba分词，获取到词频
5. 加载停用词，过滤掉停用词
6. 通过wordcloud将数据生成词云

### 2.2 数据分析的过程
1. 通过pandas将mysql数据库中的数据读取到dataframe中
2. 通过matplotlib将数据可视化
3. 通过wordcloud将数据生成词云
4. 通过jieba分词，获取到词频
5. 加载停用词，过滤掉停用词
6. 通过wordcloud将数据生成词云
![DataAnalysis/wordcloud_Content.png](DataAnalysis/wordcloud_Content.png)
![DataAnalysis/wordcloud_PersonalInfo.png](DataAnalysis/wordcloud_PersonalInfo.png)
![DataAnalysis/pie.png](DataAnalysis/pie.png)



### 项目结构

```text
├── DataAnalysis                  # 数据分析模块
│   ├── __init__.py               # 使 DataAnalysis 成为一个包
│   ├── baidu_stopwords.txt       # 停用词文件
│   ├── gen_wordcloud_content.py  # 生成内容词云 (修正了文件名)
│   ├── gen_wordcloud_personalinfo.py # 生成个人信息词云 (修正了文件名)
│   ├── plot.py                   # 绘图脚本
│   ├── pie.png                   # 饼图输出
│   ├── wordcloud_Content.png     # 内容词云图
│   └── wordcloud_PersonalInfo.png # 个人信息词云图
├── sql                           # SQL 脚本存放目录
│   └── MySQL.sql                 # 数据库建表语句
├── zhihu                         # Scrapy 项目主包 (核心)
│   ├── __init__.py               # 使 zhihu 成为一个包
│   ├── items.py                  # 定义数据项
│   ├── middlewares.py            # 中间件
│   ├── pipelines.py              # 数据管道
│   ├── pipelines2mysql.py        # 专门用于存入MySQL的管道
│   ├── settings.py               # Scrapy 设置
│   ├── user-agent.py             # User-Agent 工具
│   └── spiders                   # 爬虫文件夹
│       ├── __init__.py           # 使 spiders 成为一个包
│       └── zhihuspider.py        # 知乎爬虫 (修正了文件名)
├── chromedriver.exe              # ChromeDriver 可执行文件
├── main.py                       # 项目启动入口文件
├── requirements.txt              # 依赖包列表
├── readme.md                     # 项目说明文档
└── scrapy.cfg                    # Scrapy 配置文件 (必须在项目根目录)
```
