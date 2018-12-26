---
title: Linux常用命令学习总结
date: 2018-12-26 06:58:43
tags: [Linux]
categories: [Linux]
---

![analysis-json](analysis-json/blog-pic.jpg) 

### 一、Windows连接Linux服务器常用工具使用
#### 1.winscp
&emsp;&emsp;Winscp是Windows环境下的图形化SFTP客户端，同时支持SCP协议。主要功能是实现在本地与远程计算机之间安全的复制文件。winscp可连接Linux系统。
#### 2.SecureCRT
&emsp;&emsp;Windows下登录UNIX或Linux服务器主机的软件。
### 二、Linux常用命令
#### 新建文件
```
touch filename
```
例：新建一个名为zrxJuly的txt文件。
```
touch zrxJuly.txt
```
#### 新建目录
```
mkdir directory
```
例：新建一个名为zrxJuly的目录(文件夹)
```
mkdir zrxJuly
```
#### 查看文本内容
| 命令 | 描述 | 实例 |
| ------ | ------ | ------ |
| cat filename | 从第一行开始显示所有的文本内容 | cat zrxJuly.txt |
| tac filename | 从最后一行开始显示所有文本内容,与cat相反 | tac zrxJuly.txt |
| nl filename | 显示文本，输出行号 | nl zrxJuly.txt |
| more filename | 按页显示文本内容 | more zrxJuly.txt |
| tail -f | 实时查看日志文件 | tail -f web.log |
#### 压缩文件(zip)
```
zip 参数 打包后的文件名 打包的目录路径
```
例：
```
zip zrxJuly.zip zrxJuly
```
#### 解压文件(zip)
| 命令 | 描述 | 实例 |
| ------ | ------ | ------ |
| unzip zipName | 解压文件到当前目录 | unzip zrxJuly.zip |
| unzip -o zipName | 解压时不询问直接覆盖 | tac zrxJuly.txt |
| unzip zipName -d  directory | 将文件解压到指定文件夹 | unzip zrxJuly.zip -d  /data/bak |
| unzip -v zipName | 查看压缩包内容但不解压 | unzip -v zrxJuly.zip |
| zcat gzName | 查看压缩后的文件内容 | zcat zrxJuly.gz |
#### 复制文件及文件夹到指定目录
将aa复制到/aa/bb目录下
```
cp -rf aa /aa/bb
```
aa: 要复制的文件或文件夹
/aa/bb:将文件或文件夹复制到的指定目录
#### 移动文件到指定目录
移动file到tofile目录中：
```
mv file tofile
```
#### 删除文件
```
rm -rf filename
```
#### vim
1. 查看或编辑文件
```
vi filename
```
2. vim编辑模式下快捷键
命令ctrlb或键盘ctrl+B：向上翻页；
命令ctrlf或键盘ctrl+F：向下翻页；
关键词搜索：vim下，按ESC，若查询关键词“hello”，则输入  /hello  进行查找；
跳至文件首行：gg
清空整个文件：dG
保存并退出：:wq
退出编辑： :q


