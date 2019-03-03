---
layout: post
title: 'PHP发展史'
subtitle: 'PHP7内核'
date: 2018-08-23
categories: 技术
cover: ''
tags: php 内核
---

* content
{:toc}

![image](https://upload-images.jianshu.io/upload_images/13711841-1b01598bc8f065bc.jpg)

# PHP1
1994年，一位名叫Rasmus lerdorf的兄台为了在网上展示自己的履历和网页流量的统计，用Perl开发了一套脚本，后来因与日俱增的需求无法得到满足，lerdorf便使用c语言进行了重写，重写后的程序支持数据库的访问，以及web应用程序的简单开发，备受好评，随后便以Personal Home Page Tools为名发布了第一个版本。

![image](https://upload-images.jianshu.io/upload_images/13711841-7725f0796291fde2.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/219)

# PHP2
为了PHP的改进和快速发展，lerdorf在1995年6月8日将其开源，于是PHP2.0问世，并被命名为PHP/FI。随后，在经历了数次beta版本的发布，于1997年推出了官方正式版本。而此时，全世界已有50000个域名安装了PHP，占所有域名的1%。

# PHP3
其实在PHP/FI官方版本发布之前，两位来自以色列的工程师Zeev Suraski和Andi Gutmans就已经着手于PHP解析器的重写，为PHP3.0打下了基础，所以PHP/FI发布之后，便开放了PHP3.0的测试，并于1998年6月正式发布。而此时的PHP被正式更名为PHP:Hypertext Preprocessor。

PHP3.0有强大的扩展性，除了可以给用户提供数据库、协议和API的基础结构外，还吸引了大量的开发人员加入，并提交新的模块，这也是PHP3.0获得巨大成功的关键。

# PHP4
PHP3.0正式发布后，Zeev Suraski和Andi Gutmans开始改写PHP的内核，命名为Zend Engine（是Zeev和Andi的缩写），也就是我们熟知的Zend引擎。该引擎在1999年被引入PHP4.0，并在2000年正式发布。PHP4.0不仅拥有更好的性能，还支持了Session、输出缓冲等功能，吸引了大批开发者。此时安装PHP的网站已经达到了数百万，占据所有网站的20%。

![image](https://upload-images.jianshu.io/upload_images/13711841-1f5f05be2b0bbbf1.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/191)

# PHP5
2004年7月13日，基于Zend Engine 2.0的PHP5公开发布，全面引入了面向对象机制，并保留了向下兼容性。随后5.3到5.6版本的发布，相继增加了命名空间、闭包、Traits、短数组等特性，使PHP语法越来越灵活，直到目前，仍然有许多网站使用PHP5.6。

![image](https://upload-images.jianshu.io/upload_images/13711841-9a8b7a7ef619d470.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/547)


# PHP6
我们都知道，PHP并没有发布6.0，原因是曾有一群人创建了PHP6的项目，主要的目的是为PHP引擎增加Unicode支持，当时开发者们同时维护5和6的开发，慢慢的大家发现新功能都等着提交给6，而6因为开发速度慢导致很多新特性没法提交，状态很不理想，再后来6就没人开发了。最终经过PHP社群核心贡献者投票，超过7成的人同意最新的PHP版号将是PHP7而非PHP6，故PHP直接跳过了6.0版本。

# PHP7
2014年，PHP7正式发布，Zend引擎被再次重写，并以Zend Engine 3.0 的身份亮相，使得PHP语言的性能得到大幅度提升，大量测试显示PHP7比PHP5.6在各种开源项目中有60%到200%的性能提升。

在这里值得一提的是，PHP7的核心开发人员，PHP5.4、PHP5.5的主要开发人员“惠新宸”，是PHP开发组核心成员，也是中国最具影响力的PHP技术专家，人送外号“鸟哥”。


![PHP主要贡献者鸟哥](https://upload-images.jianshu.io/upload_images/13711841-7c30e6c778abd3da.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/500)












