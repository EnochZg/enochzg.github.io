---
layout: post
title: 跟厂长学PHP7内核（三）：目录解析
date: 2018-08-08
categories: PHP内核
tags: [php, internal, 目录解析, PHP源码]
---

* content
{:toc}

### 核心目录
浏览过源码的同学应该知道有很多个目录，实际上实现整个PHP的核心目录只有以下几个：
- sapi
- main
- Zend
- ext
- TSRM

### sapi
sapi是对输入输出层的抽象，是PHP对外提供服务的规范。

我们知道，PHP可以在多个场景下使用，比如命令行、CGI、FPM、mod_php，甚至可以在Embed模式下供C或C++程序调用。

那么sapi是如何实现多场景下的调用呢？这个要归功于通用模板sapi_module_struct结构体，该结构体定义了模式启动、关闭、激活、失效等多个钩子函数指针，每个模式将这些函数指针指向自己的函数，就可以轻松扩展PHP对外服务的方式。常见的sapi有：
- apache2handler
- cgi
- fpm
- cli
- embed

### Zend
Zend就是大家所熟知的Zend引擎，是PHP最核心的部分，主要负责PHP的语法实现、内存管理及脚本的编译运行环境等。

它主要包含两大部分：编译器、执行器。它的主要执行流程为：

1. 词法分析
2. 语法分析
3. 生成AST(abstract syntax tree)
4. 编译为opcode
5. 执行

### main
main目录是sapi与zend的连接器。

我们刚才已经了解到，sapi负责输入与输出的抽象，它解析出要执行的脚本和参数后，交由main进行环境、配置等初始化，然后再将脚本交给Zend引擎解析执行。

### ext
顾名思义，ext是extension的缩写，也就是扩展目录，它分为PHP扩展与zend扩展，都支持用户自定义开发，但是php扩展比较常用，而zend扩展主要应用于zend vm。

常用的PHP扩展为`array、str、pdo`，常用的Zend扩展为`opcache`。

### TSRM
TSRM全称叫做Thread Safe Resource Manager，也就是线程安全资源管理器。

我们知道，全局变量就是定义在函数外的变量，它属于公共资源，在多线程的环境下，访问公共资源就可能会引起冲突，TSRM就是为解决该问题而诞生的。它为每个线程分配一个独立的自增ID，该ID作为当前线程的全局变量内存区的索引，从而实现线程的完全独立。

其实PHP大部分SAPI都是单线程的，所以并不需要过多关注线程安全，但是在Apache或者用户自己实现的PHP环境下，就需要考虑线程安全问题了。
