> ## 服务器测速
       [http://speedtest-tor1.digitalocean.com/](url)


<br><br><br>


> ## PUTTY
       [https://github.com/larryli/putty](url)


<br><br><br>



> ## 源代码
<br>
①    yum install epel-release

        yum update

        yum install python-setuptools m2crypto supervisor

        easy_install pip

        pip install shadowsocks
<br><br>
②    vi /etc/shadowsocks.json
      
         {

            "server":"0.0.0.0",

            "server_port":5848（default）,

            "local_port":1080,

            "password":"yourpassword"（替换为真实密码）,

            "timeout":600,

            "method":"aes-256-cfb"

        }
<br><br>
③    vi /etc/supervisord.conf(文章**尾部**空行)

        [program:shadowsocks]
        command=ssserver -c /etc/shadowsocks.json
        autostart=true
        autorestart=true
        user=root
        log_stderr=true
        logfile=/var/log/shadowsocks.log
<br><br>
④    vi /etc/rc.local(文件**中部**空行处)
<br>
        service supervisord start
<br><br>

⑤    reboot
<br><br><br>
> ## Download Link
电脑端:
   https://sourceforge.net/projects/shadowsocksgui/files/dist/
   <br>
安卓端:
  https://play.google.com/store/apps/details?id=com.github.shadowsocks
   <br>
iOS端:
  https://itunes.apple.com/cn/app/shadowrocket-for-shadowsocks/id932747118
   <br>
