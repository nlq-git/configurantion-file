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
- 6、配置x11跟随系统自启新建一个文件/etc/init/x11vnc.conf

  `sudo touch /etc/init/x11vnc.conf`
- 加入内容
  ```
  start on login-session-start 
  script 
  x11vnc -display :0 -auth /var/run/lightdm/root/:0 -forever -bg -o /var/log/x11vnc.log -rfbauth /etc/x11vnc.pass -rfbport 5900 
  end script 
  ```
# SSH连接
##打开SSH服务，打开端口
`sudo raspi-config`

`sudo apt-get install openssh-server`
##开防火墙打开端口
```
sudo apt-get install ufw
sudo ufw enable
sudo ufw allow 22         //vnc是5900、5901等
```
##配置SSH文档
`sudo vim /etc/ssh/sshd_config`

`sudo service ssh restart`

  

