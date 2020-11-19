# Ubuntu mate配置
## 1、安装vncserver

  `sudo apt-get -y install vnc4server`
## 2、启动

  `vncserver`

## 3、设置密码

 `sudo vncpasswd`
## 4、编辑 /home/.vnc/xstartup 设置VNC要显示图形界面

  `sudo vim  /home/.vnc/xstartup`

  添加
  
  `mate-session & mate-panel &`
## 5、设置vncserver开机自启

这样不用每次都vncserver，编辑 /etc/rc.local 在　exit 0 前添加以下内容
   ```
   sudo nano  /etc/rc.local
   sudo vncserver
   ```
   
  ```
  在 /etc/init.d 目录下谢一个脚本vncserver，内容如下：
  #!/bin/bash
  vncserver :1
  sudo chmod 755 /etc/init.d/vncserver

  然后执行：
  update-rc.d vnc.sh defaults
  ```
  (以上对树莓派3B无效)
##   配置开机启动(定时任务法)

  `crontab -e`
  选择vim.basic即可
  新起一行加入
  
  `@reboot /usr/bin/vncserver :1`
  
  `sudo reboot`



## 6、改变分辨率
  查看目录
  
  `which vncserver`
  
  显示/usr/bin/vncserver
  
  `sudo vim /usr/bin/vnc4server`
  

# SSH连接
## 打开SSH服务，打开端口

`sudo raspi-config`

`sudo apt-get install openssh-server`
## 开防火墙打开端口
```
sudo apt-get install ufw
sudo ufw enable
sudo ufw allow 22         //vnc是5900、5901等
```
## 配置SSH文档

`sudo vim /etc/ssh/sshd_config`

`sudo service ssh restart`

  

