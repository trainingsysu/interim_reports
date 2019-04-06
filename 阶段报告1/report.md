### 一、 阶段任务
  hubot、slack、ansible、prometheus、grafana等基础环境的搭建。    
### 二、 完成情况  
   hubot + slack 智能机器人实现；ansible连接远程主机实现；prometheus 实现；prometheus + grafana未实现。    
### 三、 遇到的问题及解决方法  
（1）执行“npm install”时出现如下错误：    
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190406152808251.png)  
       想卸载npm重新安装，会出现错误：    
       ![在这里插入图片描述](https://img-blog.csdnimg.cn/20190406152830637.png)  
      解决办法：强制卸载 ，执行：`sudo apt-get purge nodejs-legacy nodejs`，然后再重新下载npm，nodejs等等。  
（2）安装部署ansible，执行`ssh-keygen -t rsa` ，在输入密码时填写了自己设置的密码，导致在远连接时需要远程主机用户的密码，而且在ssh远程主机时出现了要求输入本机密码的错误。
       解决办法：在执行`ssh-keygen -t rsa` 时，一直按回车，不输入密码生成公钥和密钥文件。  
 (3）ssh远程主机，出现“pression denied”。  
       解决办法：进入 `/etc/ssh/sshd_config`，修改为`PermitRootLogin yes`，然后重启ssh,即可。(注意：本机和远程主机要在同一网段！）  
       （4）在启动 grafana后，访问页面`http://loaclhost:3000`，登录执行设置数据源，配置  prometheus 时，出现错误：“HTTP ERROR:Bad Getway”。
       解决办法：还没找到。  
### 四、 后续工作  
 实现prometheus + grafana搭建监控系统，对数据进行采集，存储，并且能够对采集到的数据进行分析。  
