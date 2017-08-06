# curl

### 1. curl 是什么

> cURL 是一个利用 URL 语法在命令行下工作的文件传输工具，它支持文件的上传和下载。
> cURL 支持多种传输协议，例如：
> FTP、FTPS、HTTP、HTTPS、TFTP、SFTP、Gopher、SCP、Telnet、DICT、FILE、LDAP、LDAPS、IMAP、POP3、SMTP、RTSP等

### 2. cURL 的用法

1. 下载单个文件，默认输出到标准输出(STDOUT)中
```
    $ curl www.sina.com
```

```
<html>
<head><title>301 Moved Permanently</title></head>
<body bgcolor="white">
<center><h1>301 Moved Permanently</h1></center>
<hr><center>nginx</center>
</body>
</html>
```

2. 保存 cURL 的结果到指定的文件

如果想把执行结果保存起来，则需要 `-o` 参数

```
    $ curl -o [file_name] www.sina.com
```
使用小写字母 `o` 必须指定下载之后文件的名称，使用大写字母 `O` 则直接使用要下载的文件的名称命名，如下：

```
$ curl -O https://www.kernel.org/pub/software/scm/git/git-0.01.tar.gz
```
最后下载下来的文件为 `git-0.01.tar.gz` 。

3. 同时获取多个文件

```
    $ curl -O URL1 -O URL2
```
如果是从同一个服务器下载文件的话，`curl` 会尝试重用链接。

4. 使用 `-L` 重定向新的地址

```
    $ curl www.sina.com
```
执行如上命令，结果就会自动跳转到 `www.sina.com.cn`

5. 显示头信息

`-i` 参数可以显示 http response 的头信息，连同网页代码一起显示

```
    $ curl -i www.sina.com
```
使用 `-I` 则只显示 http response 的头信息，不显示网页代码内容。

6. 显示通信过程
`-v` 参数可以显示一次 `http` 通信的整个过程，包括端口和 `http request` 头信息

```
    $ curl -v www.sina.com
```
可以使用如下命令查看更详细的通信过程  
```
    $ curl --trace out.txt www.sina.com
    或者
    $ curl --trace-ascii out.txt www.sina.com
```

6. 断点续传
使用 `-C` 可以实现断点续传，尤其是针对一些大文件的下载

```
    $ curl -O https://www.kernel.org/pub/software/scm/git/git-2.14.0.tar.gz
```
在下载此文件时，执行 `CTRL-C` 将该命令结束，使用如下命令，可实现断点续传。
```
    $ curl -C - -O https://www.kernel.org/pub/software/scm/git/git-2.14.0.tar.gz
```
`-C -` 将使文件继续从中断的地方开始下载，`-C <offset>` 这表示跳过 `offset` 字节开始下载文件，常用的还是 `-C -` 。

7. 针对网络传输做最大限制
 使用 `--limit-rate` 可以限制网络传输的最大速率。例如：
 ```
    $ curl --limit-rate 1000B -O https://www.kernel.org/pub/software/scm/git/git-2.14.0.tar.gz
 ```
 以上命令是限制下载的最大速率是 1000Bytes/second，一开始传输速率可能会大于 1000Byte/second ，但是过一会，平均速率就会平稳在 1000Bytes/second 。

 8. 发送表单信息
发送表单信息分 `GET` 和 `POST` 两种方法，`GET` 方法相对简单，只需要将数据附在网址后面就行。
```
    $ curl example.com/form.action?data=xxx
```
`POST` 方法必须把数据和网址分开，此时需要使用 `--data` 参数
```
    $ curl -X POST --data "data=xxx" example.com/form.action
```
如果你的数据没有经过表单编码，还可以让 `curl` 为你编码，参数是 `--data-urlencode`
```
    $ curl -X POST --data-url-encode "data=xxx" example.com/form.action
```

---

参考资料：  

http://www.thegeekstuff.com/2012/04/curl-examples/   
http://www.ruanyifeng.com/blog/2011/09/curl.html  
































