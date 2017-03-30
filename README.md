dcmd
项目中老是要把一群进程变成后台独立运行的状态，所以写了这个，没有依赖，只要是Linux环境, python2.6或者python2.7都能用

python script , can let any program run as daemon, and can stop it 
for python2.6 and 2.7 in linux


进程运行后台化工具
用于python2.6 及 2.7 linux环境




Usage: dcmd [options]


Options:
  -h, --help            show this help message and exit
  --pidfile=FILE, --pidfile=FILE
                        pid file path
  --outpid, --outpid    is wait cmd create pid file
  --lockfile=FILE, --lockfile=FILE
                        lock file path
  --homedir=FILE, --homedir=FILE
                        start cmd path
  --stdout=FILE, --stdout=FILE
                        start cmd path
  --stderr=FILE, --stderr=FILE
                        start cmd path
  --cmd=cmdline, --cmd=cmdline
                        start cmdline
  --action=start|stop|restart|status|debug, --action=start|stop|restart|status|debug
                        do what




说明
--pidfile=FILE：（必须）pid文件所在位置，如/var/run/showpwd.pid
--outpid：设置后被执行进程自身生成此pid文件，缺省为dcmd自动生成pid文件
--lockfile：（必须）用于确认程序运行cmd内容的cmdline，dcmd在执行stop和restart时需要这个文件，如/var/run/showpwd.lock
--homedir：调用目标进程的初始环境路径，缺省为/
--stdout=FILE：指定标准输出到哪个文件，缺省为/dev/null
--stderr=FILE：指定标准错误到哪个文件，缺省为/dev/null
--cmd=cmdline：（必须）要执行的命令
--action=start|stop|restart|status|debug：（必须）执行的动作，是start启动，还是stop停止

安利一波，使用示例
ssserver的/etc/init.d/运行控制脚本
#!/bin/bash
runcmd='ssserver -p 11111 -k 000000 -m aes-256-cfb --user nobody -d start'
Python /usr/bin/dcmd --action=$1 --pid='/var/run/shadowsocks.pid' --outpid --lock='/var/run/my_shadowsocks.lock' --cmd="${runcmd}"

是不是炒鸡简单！！！！！！！
