  ```
   docker run -d -p 5000:5000  --restart=always   -v /opt/registry:/tmp/registry  --name registry registry
 
  docker tag cisco/jenkins 192.168.143.191:5000/jenkins 
  
  
  vim  /etc/sysconfig/docker  
    ------------  
    other_args="--graph=/docker --exec-driver=lxc --selinux-enabled"  
    # 删除--exec-driver=lxc即可，改为  
    other_args="--graph=/docker --selinux-enabled"  
    
    visudo /etc/sudoers

  
  vim /usr/lib/systemd/system/docker.service 
  
  vim /etc/sysconfig/docker
  
  OPTIONS='--selinux-enabled --insecure-registry 192.168.0.109:5000'
  
  curl -L https://github.com/docker/compose/releases/download/1.1.0/docker-compose-`uname -s`-`uname -m` > /usr/local/bin/docker-compose  
  chmod +x /usr/local/bin/docker-compose 
  
  docker-compose up  -d
  docker-compose ps 
  
  /maven-tar/
  cp apache-maven-3.3.3-bin.tar.gz /maven-tar/
  
  docker run -d -p 8080:8080 --name jenkins -v /usr/bin/docker:/usr/bin/docker -v /var/run/docker.sock:/var/run/docker.sock -v /maven-tar:/root -v  cisco/jenkins
  
  安装Git插件

在可选插件里面搜索git

勾选

git Client Plug-In

Git Parameter Plug-In


clone git https://git.oschina.net/jack1225/build-nginx

shell:
docker build -t cisco/php:5.1 $WORKSPACE(jenkins clone代码回来的路径) / php-fpm

copy maven 打好的包

docker cp maven 

代码

https://git.oschina.net/jack1225/build-nginx/

```
