# pydcmd
python script run on python2.6 and 2.7 in linux, can let any program run as daemon, and can stop it 

后台化运行辅助工具pydcmd 用于python2.6 及 2.7 linux环境

Usage
标准模式
usage: [pid_path] [lock_path] [cmdline many part] [start|stop|restart|status]
或者指定运行路径的模式
usage:  -r [pid_path] [lock_path] [run_dir] [stdout] [stderr] [cmdline many part] [start|stop|restart|status]

示例
标准模式
dcmd /var/run/showpwd.pid /var/run/showpwd.lock /root/xlab/showpwd.sh start
或者指定运行路径的模式，注意那个 -r
dcmd -r /var/run/showpwd.pid /var/run/showpwd.lock " " " " " " /root/xlab/showpwd.sh start

关闭之前被后台化的进程
dcmd -r /var/run/showpwd.pid /var/run/showpwd.lock " " " " " " /root/xlab/showpwd.sh stop


说明
pid_path：pid文件所在位置，如showpwd.pid
lock_path : 用于确认程序运行cmd内容的文件，如showpwd.lock
run_dir : 指定后台运行环境的当前路径，不想写可以用 “ ” 或者 “” 或者 null 替代，自动换成默认的 /
stdout : 指定标准输出到哪个文件，不想写可以用 “ ” 或者 “” 或者 null 替代，自动换成默认的 /dev/null
stdout : 指定标准错误到哪个文件，不想写可以用 “ ” 或者 “” 或者 null 替代，自动换成默认的 /dev/null
