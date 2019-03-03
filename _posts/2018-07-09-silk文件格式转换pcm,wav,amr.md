---
layout: post
title: silk文件格式转换pcm、amr、wav方法
date: 2018-07-09
categories: 工具技巧
tags: [小程序, pcm, 阿里云, amr, wav, ubuntu]
---

* content
{:toc}

> 这两天参加明源云的黑客马拉松，需要开发一款语音搜索房源的小程序。小程序上传的为silk文件，而语音转文字需要pcm、wav或amr格式文件，下面我来教你linux(ubuntu)环境下如何转换silk文件格式。

### 安装ffmpeg

- 添加源
```
sudo add-apt-repository ppa:djcj/hybrid
```

- 更新源
```
sudo apt update
```

- 安装ffmpeg
```
sudo apt install ffmpeg
```

### 安装silk-v3-decoder

- 下载
```
wget https://codeload.github.com/kn007/silk-v3-decoder/zip/master
unzip master
```

- 编译
```
cd silk-v3-decoder-master
cd silk
make
```

- 编译完成后，退回上一级目录，赋予convert.sh执行权限
```
cd ..
sudo chmod +x converter.sh
```

### 转换测试

- 找到需要转换的silk文件，通过convert.sh转换
```
convert.sh test.silk wav
```

### 注意

转换完成的文件默认放在被转换文件的同级目录中，名称保持不变，只是后缀名将silk改为了要转换的文件格式。