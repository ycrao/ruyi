tunnel
------

一些场景下（如本地网站给外部客户演示、微信开发调试等）可能需要内穿服务，可以借助于一些免费服务，来实现临时访问。


### Cloudflare

从 [cloudflared](https://github.com/cloudflare/cloudflared/releases) 下载最新的对应操作系统的二进制文件，然后执行下面类似命令：

```bash
# 更多帮助可以使用 --help 参数
./cloudflared --help
# --url 后面追加的参数是本地需要映射的网站（`9999`为端口，请根据实际修改）
./cloudflared tunnel --url http://localhost:9999
```

### localhost.run 服务

```bash
# `9999` 为本地网站对应端口
ssh -R 80:localhost:9999 nokey@localhost.run
```

### tunnelmole 服务

>   比较新的服务，可以尝试一下。官网：https://tunnelmole.com/ 。

安装好之后，只需要使用下列命令：

```bash
# 80 换成需要内穿的本地服务端口
tmole 80
```

### 其它稳定可行方案

- 购买专业的通道服务，为了广告避嫌，请自行搜索，建议先试用再购买包月包年套餐，以免上当受骗。
- 自组，购买云商服务器，安装 [frp](https://github.com/fatedier/frp) 等之类软件，更加安全可控。
