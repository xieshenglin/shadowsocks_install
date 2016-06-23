# shadowsocks_install
关于本脚本：

一键安装 ShadowsocksR 服务端脚本。

注：本脚本来源于teddysun的一键脚本：https://shadowsocks.be/9.html

并参考了https://www.91yun.org/archives/2079的脚本。

本脚本适用环境：
系统支持：CentOS6,7，Debian，Ubuntu
内存要求：≥128M
日期：2016 年 05 月 12 日

脚本默认配置：
服务器端口：自己设定（如不设定，默认为 8989）
客户端端口：1080
密码：自己设定（如不设定，默认为m）

我主要修改了：
默认协议为：auth_sha1_v2_compatible
默认混淆为：tls1.2_ticket_auth_compatible
使用git的方式安装，以方便以后使用git来升级
增加了修改时区的操作。把时区设置成了北京-上海时间。
修改的内容主要是我自己的一些默认设置，所以大家对这些没需求的话可以继续使用teddysun的原版脚本。

一键脚本的安装：
root用户登录，运行以下命令：
wget -N --no-check-certificate https://raw.githubusercontent.com/xieshenglin/shadowsocks_install/master/shadowsocksR.sh && bash shadowsocksR.sh
本脚本安装完成后，已将 ShadowsocksR 自动加入开机自启动。

卸载方法：
使用 root 用户登录，运行以下命令：
./shadowsocksR.sh uninstall

升级方法：
cd /usr/local/shadowsocks/shadowsocks
git pull

使用命令：
启动：/etc/init.d/shadowsocks start
停止：/etc/init.d/shadowsocks stop
重启：/etc/init.d/shadowsocks restart
状态：/etc/init.d/shadowsocks status

配置文件路径：/etc/shadowsocks.json
日志文件路径：/var/log/shadowsocks.log
安装路径：/usr/local/shadowsocks/shadowsoks

多用户配置
如果要多个用户一起使用的话，请写入以下配置（vi /etc/shadowsocks.json）：

多用户的核心是这个配置，把这个配置替代掉/etc/shadowsocks.json的相关密码的配置就行了：

“port_password”:{

“80”:”password1″,

“443”:”password2″

},

完整的多用户配置：
{
    "server":"0.0.0.0",
    "server_ipv6": "[::]",
    "local_address":"127.0.0.1",
    "local_port":1080,
    "port_password":{
        "80":"password1",
        "443":"password2"
    },
    "timeout":300,
    "method":"aes-256-cfb",
    "protocol": "auth_sha1_compatible",
    "protocol_param": "",
    "obfs": "http_simple_compatible",
    "obfs_param": "",
    "redirect": "",
    "dns_ipv6": false,
    "fast_open": false,
    "workers": 1
}
如果你想修改配置文件，请参考：
https://github.com/breakwa11/shadowsocks-rss/wiki/Server-Setup

参考连接：参考链接：
https://github.com/breakwa11/shadowsocks-rss
https://shadowsocks.be/9.html
https://www.91yun.org/archives/2079
