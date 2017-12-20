#Ngrok服务器一键安装脚本【支持用户管理】（穿透DDNS）

##在此非常感谢[koolshare](http://koolshare.cn/forum-72-1.html)的[小宝](http://koolshare.cn/space-uid-2380.html)宝大对ngrok进行的二次开发，让我等可以用上非常好用的程序，同时感谢[woaihsw](http://koolshare.cn/space-uid-13735.html)在脚本制作中提供的帮助。

脚本是业余爱好，英文属于文盲，写的不好，不要笑话我，欢迎您批评指正。
安装平台：CentOS、Debian、Ubuntu。
Server
------
### Install
执行命令：
```Bash
wget --no-check-certificate https://github.com/clangcn/ngrok-one-key-install/raw/master/install_ngrok.sh -O ./install_ngrok.sh
chmod 500 ./install_ngrok.sh
./install_ngrok.sh install	
```
### 服务器管理

	Usage: /etc/init.d/ngrokd {start|stop|restart|status|config|adduser|deluser|userlist|info}
	Usage: /etc/init.d/ngrokd deluser {username}

### 补充说明

对于mac client端，需要执行 /etc/init.d/ngrokd config 设置password为空，否则好像无法通过认证

添加用户 /etc/init.d/ngrokd adduser返回结果

```
Server: ng.xxx.com
Server  4443
userId: xx
authId: mmmmmmmmm
Subdomain: "wx"
Your FQDN: "wx.ng.xxx.com"
```

对于 client conf文件
```
server_addr: ng.xxxcom:4443
trust_host_root_certs: false
inspect_addr: disabled
auth_token: xx
password: mmmmmmmmm

tunnels:
    httptun:
        remote_port: 80
        subdomain: "wx"
        proto:
            http: 192.168.1.150:80
```

客户端命令
```
./ngrok -config xx.cfg start httptun
```
