# Ubuntu mate配置
- 1、安装x11vnc
  `sudo apt-get install x11vnc  `
- 2、手动连接
  `sudo /usr/bin/x11vnc -display :0 -auth /var/run/lightdm/root/:0 -forever -bg -o /var/log/x11vnc.log -rfbauth /etc/x11vnc.pass -rfbport 5900 `
- 3、开机自启
 `sudo x11vnc -storepasswd `
- 4、密码保存位置
 `sudo x11vnc -storepasswd in /etc/x11vnc.pass`
- 5、将用户目录下的password文件内容拷贝至/etc/x11vnc.pass下
  `sudo cp /home/"user"/.vnc/passwd /etc/x11vnc.pass `
- 6、配置x11跟随系统自启

  

