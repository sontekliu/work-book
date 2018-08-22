# Github Pages 对自定义域名支持 HTTPS

大约忘记了年月，某天访问自己的个人网站时，突然跳转到了一个黄色网站，让我大吃一惊，这怎么能行，广大网友访问我的网站时，要是突然跳转到黄色网站，这不成了给别人做嫁衣了，那还了得。这个问题必须解决！

但是这是什么原因导致的？我还一头雾水，但是根据猜测应该是域名解析或者网站没有启用 HTTPS 的原因吧。既然知道了原因那就说干就干。

因为之前了解过网站启用 HTTPS 需要购买证书，需要花钱，当然也有免费的，但是肯定稍微麻烦点，考虑到钱的问题，我还是先尝试一下第一种解决方案吧。

### 1. 修改 DNS域名解析

登录到购买主机的网站——戈戈主机，将域名的解析迁移到 [DNSPOD](https://www.dnspod.cn/Login?default=email) ，具体迁移此处不做详解。迁移完成之后，效果好像并不理想，偶尔还是会跳转到不健康网站。这可怎么办呢，由于当时有其他事情要处理，此问题就一直搁置了。

就在 2018.08.21 我在公司打开我的个人网站时，突然跳转到了不健康网站，当时就吓了我一身冷汗，赶紧把浏览器关闭了，要是让同事或者领导看见那得多尴尬。之前修改 DNS 的方案没能解决，那就尝试一下，改成支持 HTTPS 的吧。毕竟早在很多年前就提倡网站要使用 HTTPS 协议。

### 2. 个人网站由 HTTP 升级到 HTTPS

网上查了很多资料，很多资料都是购买证书升级 HTTPS，也有使用免费的证书升级 HTTPS，就在查找资料的过程中，突然发现了一个链接 [Custom domains on GitHub Pages gain support for HTTPS](https://blog.github.com/2018-05-01-github-pages-custom-domains-https/) ，Github Pages 对自定义域名支持 HTTPS，这不正符合我的情况吗，本网站就是基于 Github Pages + Hexo 搭建的一个静态博客网站。根据此教程，我将我的网站升级到 HTTPS 了。下面我就大体说一下步骤。

首先，说一下个人网站有 HTTP 到 HTTPS 的好处：简单来说，HTTPS 支持数据传输加密，防劫持等特性，Github   官方基于 HTTPS 配合 CDN 使得网站的加载速度更快，还能提供额外的防御 DDoS 攻击的保护。

关于 Github Pages 搭建静态博客以及配置自定义域名不再赘述，网上有很多教程，此次仅对开启域名支持 HTTPS 这一特性进行说明。

首先，在 Github 上找到博客对应该的仓库，例如，我的博客仓库地址是：https://github.com/sontekliu/sontekliu.github.io，然后点击 `Settings` 标签。在 Github Pages 选项卡找到如下内容：

```gfm
Your site is published at http://javaliu.com/
Custom domain
Custom domains allow you to serve your site from a domain other than sontekliu.github.io. 
```

正常情况下是这样，如果勾选了 `Enforce HTTPS` 开启强制跳转到 HTTPS 即可，相应的 Github Pages 的内容将会变成如下内容：

```gfm
 Your site is published at https://javaliu.com/
```

如果 `Enforce HTTPS` 无法勾选怎么办？

按如下步骤操作：

1. 把 Custom domain 中的值清空，并点击 `Save` 进行保存；
2. 在 Custom domain 中的填入之前清空的值，我这里是 `javaliu.com` ，填入后点击保存；
3. 刷新项目设置页，如果 `Enforce HTTPS` 可勾选，勾选即可；
4. 如果 `Enforce HTTPS` 不可勾选，并且提示 `Not yet available for your site because the certificate has not finished being issued”`，说明证书尚未申请完成，等待一天即可。

如果一切正常的话，那么你的网站已经使用的 HTTPS 协议了，地址栏左侧显示小绿锁并伴有安全二字。



###### 参考资料：

【Github Pages】  [Custom domains on GitHub Pages gain support for HTTPS](https://blog.github.com/2018-05-01-github-pages-custom-domains-https/)



































