## TCP/IP

两台电脑之间通信时需要遵守一些规则，这些规则就是协议，例如我们在相互交流时用汉语来交流，汉语就是我们交流时的规则，但是别人用英语，如果你不会，那么这样不遵守协议则会导致双方不能明确对方的意图。

而协议之中 TCP/IP 协议族构成了网络协议的基础。而 HTTP 协议则是其中的子集。HTTP 协议是数据传输协议，用来沟通客户端和服务器。

TCP/IP 协议体现在传输层，而 HTTP 协议体现在应用层，后者拿到前者发送过来的数据，前者封装了计算机的差异性，隐藏的相关弱点，为 HTTP 协议提供的是相同接口。

为了方便设计和修改内容，TCP/IP 协议分为了四层结构，这样搞显然很方便修改和排错，就像函数一样，模块化，一旦出现问题逐层排错即可，修改的时候只需要保证接口一致接口，分层方便了管理和设计。

TCP/IP 协议族分了四层结构，分别是应用层，传输层，网路层和数据链路层。

1. 应用层提供通信，如果传输文件（FTP），解析域名（DNS）HTTP 协议就位于这一层。
2. 传输层为计算机提供数据传输，传输控制协议（TCP）用户数据报协议（UDP）位于这一层。
3. 网络层用于处理数据包的流动，数据包是信息传输的最小单位，就像一个句子中一个字一样的存在。如何选择一条合适的路线是网路层所决定的。
4. 链路层用来处理硬件部分，控制系统，适配器，驱动，网卡和电流等等。涉及到硬件均在链路层中。

当我们使用是在客户端是从顶至下的过程，每一层都包装一层的内容，传输到服务器则是从底之上的，逐层解析剥开外壳。

## IP
Internet Protocol 网络协议。

IP 指协议，不要和 IP 地址搞混，IP 协议的作用是将数据包准确的送达目的地，而这个过程需要 IP地址和 MAC 地址的的参与。

MAC （Media Access Control Address）地址即物理地址，不可变，IP 地址是指明了当前节点所在的地址，可以变换。

 
## ARP 

通信时计算机拿到的是对方的 IP 协议，但是如果想要找到对方还需要 MAC 协议，就像你去某地，只知道名字（IP）不行，还需要知道详细地址（MAC）。而 ARP 协议的存在就是解析地址的，根据 IP 地址可以拿到 MAC 地址。

## TCP

TCP 协议提供了可靠的字节流传输，将大的数据分割为小的数据包。为了提供可靠的传输，传输过程需要经过三次握手。

三次握手，第一次 发送端发送了一个含有 SYN 标志的数据包给对方，而自己怎么确保对方是否接受到了自己的消息呢?对方拿到后 SYN 后向里面添加了一段 ACK 标志，发送了回来，接收方收到后发现数据包添加了东西，那么就清楚自己发送的东西对方接受到了。而接收端也得明确发送端是否接受了 ACK，此时接收端将 ACK 发送回来，由此经过三次握手二者建立起了通信。

## DNS

IP 地址是一串数字显然不好记，我们经常看到的网址就是域名，我们要找到对方则需要的是对方的 IP 地址，通过域名解析到对方的 IP 地址，这一步是通过 DNS 实现的，也就是域名解析服务。

其实就是经过 DNS 这一层将域名对应到 IP 地址，然后拿到 IP 地址在进行后面的流程。

## URL/URI

URL 就是网址，也就是域名。例如 google.com 

一个完整的网址并不只是域名，例如 https://weijiew.com/ 里面加上了协议 HTTP。但是这个还不完整。 完整的称为 URI。

完整的 URI = 协议 + 登陆信息 + 域名 + 端口 + 文件 + 标识符。 而 url 只是域名部分，也可以称为 uri 的子集。


# HTTP 

首先明确两点，客户端，服务端。

客户端就是我们的电脑，而服务端则是储存信息的服务器，通过通过客户端发起放回，服务端响应回复，然后我们看到资源。

## 方法

HTTP 不存储状态，后续加入了 Cookie 实现了状态的保存。

URI 来实现定位资源。

GET 方法来告诉服务端自己想访问某个资源的想法。

POST 方法则是告诉服务器自己想方式东西给你的想法。

PUT 方法则是发送资源，但是不做限制存在安全问题。配合验证机制或 采用 REST标准可以避免这类问题。

HEAD 获取报文的首部，确认 URI 的有效性。

DELETE 用于删除文件，与 PUT 相反，删除指定的资源。同样不带验证机制存在安全问题。

OPTIONS 问一下服务器支持哪些方法。

TRACE 这个方法是用来记录自己的请求是否被篡改的。

CONNECT 和服务器建立了隧道，之中可以采用 SSL/TLS 加密。

## 持久连接

之前的通信传输的信息量小，所以用一次连一次，但是请求频繁的话显然比较耗费时间，夸张一点就是你点击每点击一次就得等上几秒钟，显然很烦。

为了保证持久连接，只要服务器和客户端之间任何一个没有说停，那么连接就不会断。

而持续连接则使得并发实现了，之前的连一次断一次使得只能一个方法一个方法的发送，服务器一个方法一个方法的响应，而持续连接可以一次性发送多个方法实现并行，也就是管线化。

## cookie
记录的状态，cookie 里面记录的用户的信息即状态，通过改变其中内容来实现对状态的记录。

# HTTP 报文

* 组成
* 压缩
* 分割
* 部分显示
* return

# HTTP 状态码

* 原因
* 2xx 成功正常处理
  * 200 OK 你的请求正常处理
  * 204 请求成功，但是没有服务端返回任何资源
  * 206 请求某部分资源
* 3xx 重定向


# 服务器

一个服务器可以为多个域名服务。

代理：介于服务器和客户端之间，提供转发。
网关：转发通信数据
隧道：提供远距离中转服务。

## 代理

缓存代理

透明代理

## 网关

## 隧道

## 缓存服务器 88

# HTTP 首部

组成 = 首部 + 空行 + 主体

HTTP 请求报文 = 方法 + URI + HTTP 版本 + HTTP 首部字段

HTTP 响应报文 = HTTP 版本 + 状态码 + HTTP 首部字段

## HTTP 首部字段

这个字段提供了浏览器和服务器报文主体大小使用语言认证信息等内容。

首部字段分四种类型:
* 通用首部字段
* 请求首部字段
* 响应首部字段
* 实体首部字段


# HttpS

HTTP 缺点
* HTTP 对内容不加密导致信息容易被窃听。
* 通信双方不需要验证身份导致容易遇到伪装。
* 无法保证报文的完整性，所以报文可能遭到篡改。

根据以上的三个缺点对应的解决方案如下：

## 加密
为了保证加密的实现出现了两种方式：
* 在通信上进行加密，HTTP + SSL/TLS 对内容加密，建立安全通信线路。
* 对内容加密，发送端接受端都有对应的加密解密机制，但是内容仍有可能被篡改。
 
## 身份验证

服务器端对所有的请求都来者不惧，全部接受，但是很多无意义访问占用了服务器，无法将服务提供给需要的人，为了解决这个问题需要引入身份验证，通过第三方审核自己的网站拿到一个证书，发送请求之前确认对方有这个证书，然后才进行下一步。

## 防止篡改

通常使用 MD5/SHA-1 散列值校验等方法。但是都需客户端本人检查文件，浏览器无法检查。无法百分之百确保正确。因为值如果被修改的话用户是意识不到的。而为了确保安全需要加上别的协议，也就是 HTTPS

## HTTPS 原理
HTTP + S (secure，安全) 
因为 HTTP 的三个缺点，HPPTS 则弥补上了这三个缺点。所以有了下面的这个关系：

HTTP + 加密 + 认证 + 完整性保护 = HTTPS

HTTPS 并非新的协议，只是在 HTTP 和 TCP 之间又加上了一层 SSL 。这样做将 HTTP 的缺点弥补了。

加密方式分为两种：
* 共享加密，信息加密后同时将密钥发送给对方，虽然快但是密钥在发送的过程中容易被窃取。
* 公开加密，密钥存在公开密钥和私有密钥两种类型，发送端根据公开密钥加密，接收端用私有密钥解密。公有密钥大家都清楚，但是根据公有密钥很难解密，所以比较安全，但是处理过程复杂比较费时间。但是公有密钥也存在被替换的可能，为了解决这个问题又引入了证书，数字证书已经被提前嵌入到了浏览器中。当公钥发送过来后都会去证书里面看看公钥的真实性。当然数字证书也存在伪造的可能，没有绝对的安全。

两种加密方式各有优缺点。所以 HTTPS 采用混合加密的方式，根据实际情况选择。


## SSL

因为加密解密等作用导致 HTTP 加上 SSL 后速度变慢，大概慢 2 到 100 倍，这个不可避免，当然还可以加速，利用 SSL 加速器专门的硬件来解决慢的问题提高计算速度，分担负载。

网站往往是 HTTP/HTTPS 混合的，一方面因为 SSL 速度慢，另一方面购买证书也需要开销。所以导致了并不全是 HTTPS 的网站。

# 身份认证

在网页中有些用户可以访问某些特定的页面，而其他用户不可以，例如网站的后台页面只能由管理员访问，其他人不能访问，这个就是身份认证，如何实现？

BASIC 认证
DIGEST 认证
SSL 客户端认证
Form Base 认证

# 追加功能

## AJAX 

# WEB 技术

# 安全