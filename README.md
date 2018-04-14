本文参考https://www.findhao.net/res/956#4_BBR
https://blog.csdn.net/QingHeShiJiYuan/article/details/53330581
# vps

 TCP-BBR加速方案
```
wget --no-check-certificate https://github.com/iyuco/scripts/raw/master/bbr.sh
chmod +x bbr.sh
./bbr.sh
```

一键安装ssr
```
wget --no-check-certificate https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocksR.sh
chmod +x shadowsocksR.sh
./shadowsocksR.sh 
```
更改配置文件

```
/etc/shadowsocks.json
```
下面是多用户设置

```
{
"server":"0.0.0.0",
"server_ipv6": "[::]",
"local_address":"127.0.0.1",
"local_port":1080,
"port_password":{
    "8989":"password1",
    "8990":"password2",
    "8991":"password3"
},
"timeout":300,
"method":"aes-256-cfb",
"protocol": "origin",
"protocol_param": "",
"obfs": "plain",
"obfs_param": "",
"redirect": "",
"dns_ipv6": false,
"fast_open": false,
"workers": 1
}
```
安装完成后即已后台启动 ShadowsocksR ，运行：```/etc/init.d/shadowsocks status```
可以查看 ShadowsocksR 进程是否已经启动。
本脚本安装完成后，已将 ShadowsocksR 自动加入开机自启动。

使用命令：

启动：```/etc/init.d/shadowsocks start```
停止：```/etc/init.d/shadowsocks stop```
重启：```/etc/init.d/shadowsocks restart```
状态：```/etc/init.d/shadowsocks status```

配置文件路径：```/etc/shadowsocks.json```
日志文件路径：```/var/log/shadowsocks.log```
代码安装目录：```/usr/local/shadowsocks```

如果你想修改配置文件，请参考：
https://github.com/iMeiji/shadowsocks_install/blob/master/shadowsocksR-wiki/config.json.md

注意事项：
本脚本没有对防火墙（IPv4 是 iptables，IPv6 是 ip6tables）进行任何设置。
因此，在安装完毕，如果你发现连接不上，可以尝试更改防火墙设置或关闭防火墙。

参考链接：
https://github.com/breakwa11/shadowsocks-rss
https://shadowsocks.be/9.html

# vps ip被谷歌学术禁掉
有些vps运营商的ip会被谷歌学术禁掉。

简单的解决方案是，购买支持ipv6的机器，修改机器的/etc/hosts指向谷歌学术的ipv6地址。

使用github上的ipv6的hosts：

https://github.com/lennylxx/ipv6-hosts
copy里面谷歌学术部分（在文件里搜索“学术搜索”）添加到hosts里即可。注意，里面谷歌学术的部分，谷歌的后缀比较少，可以手动添加你所在的地区域名。

比如新加坡访问谷歌学术的地址是scholar.google.com.sg。

修改完成后记得重启vps。
