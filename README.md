# digitalocean-vps-ss搭建指南
displayed in centOS 6.8 x64

## 服务器测速
   Click it to test:[digitalocean-speed-test](http://speedtest-tor1.digitalocean.com/)





## PUTTY
   Download:[you need it to log in your vps](https://github.com/larryli/putty)





## 源代码

### 1.Get ready to install shadowsocks: 

        yum install epel-release

        yum update

        yum install python-setuptools m2crypto supervisor

        easy_install pip

        pip install shadowsocks


### 2.Modifyjson file
       vi /etc/shadowsocks.json
      
         {

            "server":"0.0.0.0",

            "server_port":5848（default）,

            "local_port":1080,

            "password":"yourpassword"（替换为真实密码）,

            "timeout":600,

            "method":"aes-256-cfb"

        }

### 3.Add follow codes to the end of the relative file
        vi /etc/supervisord.conf(文章**尾部**空行)
        
        ----------以下内容为复制内容----------
        [program:shadowsocks]
        command=ssserver -c /etc/shadowsocks.json
        autostart=true
        autorestart=true
        user=root
        log_stderr=true
        logfile=/var/log/shadowsocks.log
        ----------以下内容为复制内容----------


       vi /etc/rc.local(文件**中部**空行处)
       
       ----------以下内容为复制内容----------       
       service supervisord start
       ----------以下内容为复制内容----------        


### 4.reboot your vps
         reboot



## Download Link
   下载:[电脑端](https://sourceforge.net/projects/shadowsocksgui/files/dist/)


   下载:[安卓端](https://play.google.com/store/apps/details?id=com.github.shadowsocks)


   下载: [iOS端](https://itunes.apple.com/cn/app/shadowrocket-for-shadowsocks/id932747118)

## Reference article
   [How to build a ss](http://shadowsocks.blogspot.jp/2015/01/shadowsocks.html)
