# AID1905 第二次周测题

## 一、选择题

1. 下列哪项不是Linux操作系统的特征（C）

> A. Linux操作系统是开源的
>
> B. Linux操作系统有内核，文件系统，shell，应用构成
>
> C. Linux图形化界面和网络功能的支持较差
>
> D. Linux操作系统是一种常用的服务器系统

2. 关于绝对路径和相对路径的说法正确的是（A）

> A. 绝对路径是从根目录开始查找文件
>
> B. 相对路径是从当前位置查找文件
>
> C. 使用绝对路径比相对路径方便
>
> D. 使用相对路径比绝对路径方便

3. 关于二叉树的遍历，以下选项中描述错误的是（A）

> A. 前序遍历是先遍历左子树，然后访问根结点，最后遍历右子树
>
> B. 后序遍历二叉树的过程是一个递归的过程
>
> C.  二叉树的遍历是指不重复地访问二叉树中的所有结点
>
> D. 二叉树的遍历可以分为三种：前序遍历、中序遍历、后序遍历

4. 下面四个选项, 关于with语句描述正确的是( B)

> A. 任何对象都能用with语句进行管理
>
> B. open 函数返回的文件流对象可以用with语句中进行管理
>
> C. with 语句主要用于容易引发异常的异常处理中
>
> D. 在 with 语句内部创建的变量,在with语句之后无法再次访问

5. 下列说法不正确的是（A）

> A. 多进程并发，多线程并发，协程并发原理一样，都是每个客户端创建一个分支进行处
>
> B. select，poll，epoll都是IO多路复用的方法
>
> C. socketserver模块可以实现多进程和多线程的并发模型
>
> D. 协程拥有很好的处理IO并发请求的能力

## 二、简答题

1. 写出下列命令的作用

> ```
> mkdir：创建子目录
> touch：修改文件/目录的时间属性，包括存取时间和更改时间。若文件不存在，系统会建立一个新的文件。
> vi:编辑的方式查看文件，创建新文件，写文件的命令
> rm：删除一个文件或者目录。
> cp：用于容器与主机之间的数据拷贝。
> ```

2. 请阐述进程、线程、协程，以及他们的应用场景。

> ```
> 进程：程序在计算机中的一次运行。进程是一个动态的过程描述，占有计算机运行资源，有一定的生命周期。如果是相对独立的任务模块，可能使用多进程
> 线程：线程被称为轻量级的进程， 线程也可以使用计算机多核资源，是多任务编程方式， 线程是系统分配内核的最小单元，线程可以理解为进程的分支任务，如果是多个分支共同形成一个整体任务可能用多线程
> 协程：是允许在不同入口点不同位置暂停或开始的计算机程序，简单来说，协程就是可以暂停执行的函数。主要应用于处理多并发IO事件。
> ```

3. 请阐述七层模型、四层模型，说明其作用及并列举对应的协议。

> ```
> 七层模型：（应用程序http,ftp）
> 应用层 ： 提供用户服务，具体功能有应用程序实现
> 表示层 ： 数据的压缩优化加密
> 会话层 ： 建立用户级的连接，选择适当的传输服务
> 传输层 ： 提供传输服务
> 网络层 ： 路由选择，网络互联
> 链路层 ： 进行数据交换，控制具体数据的发送
> 物理层 ： 提供数据传输的硬件保证，网卡接口，传输介质
> 四层模型：
> 应用层（包含七层模型中的：应用层，表示层，会话层），传输层，网际层，网络接口（包含七层模型中的数据链路层，物理层）
> ```

4. 请使用正则匹配出邮箱及手机号

> ```
> pattern=r'\w+@\w+\.com|\w+@\w+\.cn'
> ```

## 三、编程题

1. 一只青蛙一次可以跳上1级台阶，也可以跳上2级……它也可以跳上n级。求该青蛙跳上一个n级的台阶总共有多少种跳法。

   ```python
   # -*- coding:utf-8 -*-
   class Solution:
       def jumpFloorII(self, number):
           # 写下你的代码（每个台阶都可以跳或者不跳，出去最后一级台阶必须跳）
           count=2^(n-1)
           return count
           
           
   ```

2. 请实现一个函数，将一个字符串中的每个空格替换成“%20”。例如，当字符串为We Are Happy.则经过替换之后的字符串为`We%20Are%20Happy`。

   ```python
   # -*- coding:utf-8 -*-
   class Solution:
       # s 源字符串
       def replaceSpace(self, s):
           # 写下你的代码
                  result=list(s)
           for i in range (len(result)):
               if result[i]==' ':
   
                   result[i]='%20'
           return ''.join(result)
   
   
   s01=Solution()
   s= "how are you?"
   s01.replaceSpace(s)
   print(s01.replaceSpace(s))
           
   ```
3.  请用代码实现`TCP`或`UDP`的`Socket`通信

   ```python
   import socket
   #TCP 服务端
sockfd = socket.socket(socket.AF_INET,socket.SOCK_STREAM)
   sockfd.bind(('0.0.0.0', 8800))
   sockfd.listen(5)
   connfd, addr = sockfd.accept()
   # 　收发消息
   data = connfd.recv(1024)
   print("收到:", data)
   n = connfd.send(b'Thanks') 
   connfd.close()
   sockfd.close()
   
   #TCP客户端：
   from socket import *
   sockfd = socket()  
   server_addr = ('127.0.0.1',8880)
   sockfd.connect(server_addr)
   while True:
       data = input("Msg>>")
       if not data:
           break
       sockfd.send(data.encode()) 
       data = sockfd.recv(1024)
       print("Server:",data.decode())
   
   sockfd.close()
   
   ```
   
   