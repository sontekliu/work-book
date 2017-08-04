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
使用 `-I` 则只显示 http response 的头信息，不现实网页代码内容。

















