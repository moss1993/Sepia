# Sepia
Sepia(乌贼)是一款集PoC批量验证和攻击的内部安全团队工具，能满足内部团队在漏洞爆发时快速对资产状况进行查证的需求。目前工具的攻击功能还处于构思阶段，后期会增加上去（主要是由于攻击模块针对于不同漏洞的统一化问题较为复杂）。

![Sepia.gif](https://ooo.0o0.ooo/2017/08/24/599ed4b5a08fa.gif)

## 前言
Sepia是在POC-T的基础上修改的，因此首先要感谢@cdxy的POC-T项目：<https://github.com/Xyntax/POC-T>。

与POC-T相比，Sepia有以下一些变化：

##### 1. 数据搜集方式的变化

Sepia在POC-T的上去掉了Google dork、Shodan dork等功能，只保留了Zoomeye采集方式，同时添加了Baidu URL爬虫，这么做一是因为Zoomeye API可以免费使用，二是考虑到某些情况下Google API在国内使用效率比较低，对于批量URL采集个人感觉百度应该是足够的。

##### 2. 增加了URL正则定制功能 

由于每一个漏洞对应的URL可能千变万化，仅利用@cdxy批量规范URL的方法：<https://www.cdxy.me/?p=640>使得抓取效率会大大降低，进而导致在PoC验证过程中效率也降低，因此Sepia在POC-T的做法基础上增加了正则定制，通过修改toolkit文件中的urlfilter项能自定义要抓取的URL，通过配合百度URL爬虫，提升了抓取和验证的效率。

##### 3. 改变了一些输出显示

Sepia改变了一些使用过程中的显示，去掉了POC-T导出到文件的功能，引入prettytable直接将结果座位表格显示在命令行。

##### 4. 脚本编写要求的变化 

由于Sepia会增加攻击模块，但各种漏洞的攻击方式可能会有很大差异，因此考虑将攻击功能直接交给脚本，目前仍在构思这部分，这应该是和POC-T有比较大区别的地方。

**总之，POC-T专注的是并发批量处理任务，而Sepia只专注高效批量PoC验证并能实施攻击。**


