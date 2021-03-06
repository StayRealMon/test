## 装新ubuntu ##
1. DHCP-->Manual
2. sudo apt-get install openssh-server
3. sudo ufw disabled/enabled
	1. sudo ufw status 
4. sudo apt-get install vim/git
5. sh Anaconda-xxxx.sh
6. source ~/.bashrc
7. conda list
	1. pip install --upgrade pip
8. pip install xgboost
9. sudo apt-get install cmake/gcc/g++  (--version)
10. sudo git clone https://github.com/aksnzhy/xlearn.git
11. head/tail -n 10 /etc/profile
12. wc -l train.txt
13. sudo apt-get install mysql-server
 apt-get isntall mysql-client
 sudo apt-get install libmysqlclient-dev
mysql -u root -p (root)
14. 复制：1,2 co 3(1&2行复制到2之后)
(n)yy -> p
15. scp xxx-xxx.xml ts@192.168.0.1:/home/ts
16. hosts文件生效
    1. sudo /etc/init.d/networking restart
    2. sudo /etc/init.d/dns-clean start
17. wc -lwc user_data
18. cat ad_operation.dat |head -n 30 | tail -n -20 前20行的后10行，即10-30
19. cat ad_operation.dat |tail -n +10 | head -n 20 10行开始显示20行，即10-30
20. sed -n '10,30p' user_data 直接查看10-30行
21. 新建文件用`touch`;覆盖文字到文件`echo 'comments' > file1.txt`;追加内容到文件`echo 'second line' >> file1.txt`


## 文件权限 ##

```bash
‐rwxrw‐r‐‐233 root staff 1412 9 30 11:17 directory
```

1. 修改权限 `chmod u=rwx,g=rx,o=x directory/`
2. `r=4,w=2,x=1`，以上命令可以改写成`chmod 731 directory/`
3. 再改回原权限可以使用`chmod g-x,g+w directory/`
4. `root`代表当前用户，`staff`代表当前用户所在组；可以用`whoami`查看当前用户；`groups`查看组的信息；`groups $USER_NAME`查看当前用户所在组信息；`id -a $USER_NAME`查看更加详细的组信息
5. `233`代表文件数目；`1412`表示文件大小(字节)；`9 30 11:17`代表最后修改时间

按1/3/3/3分，即-/rwx/r--/r--，分别为 **文件类型**、**文件属主**、**文件属组**和 **其他用户**的对应权限。
 第一段为文件类型：-为常规文件，d为目录，l为符号链接等。 其中rwx分别为read可读、write可写和可执行executable


## ubuntu Server ##
1. VM虚拟机网络桥接模式设定
2. 更新apt-get sudo apt-get update/install vim
3. 查看ip和网关 ifconfig/netstat -rn/route -n
4. 配置静态ip vim /etc/networks/interfaces
①dhcp-static②address 192.168.31.131③netmask 255.255.255.0④gateway 192.168.31.2⑤dns-nameservers 192.168.213.2
5. 重启生效 sudo /etc/init.d/networking restart
6. 测试外网 ping www.baidu.com
7. 用户权限和密码设置sudo passwd -u root查看用户root是否设置密码；sudo passwd root给root设置密码
8. 安装postgresql sudo agt-get install postgresql  (自带了一个用户postgres，在这个用户下创建用户createuser --interavtive，创建数据库createdb -e hello，进入psql命令模式查看用户和库和表\du \l \d)
9. 查看网关nm-tool
10. apt-get install rpm 利用rpm查看java版本


## 压缩包 ##
```bash
		tar -cf all.tar *.gif		//c产生新的包；f指定文件名
		tar -rf all.tar *.jpg		//r增加文件到all.tar
		tar -tf all.tar			//t列出tar包下所有文件
		tar -xf all.tar			//x解压tar包

		tar -zxf all.tar.gz		//z调用gzip解压.gz压缩包
		tar -jxf all.tar.bz2		//j调用bzip2解压.bz2压缩包
		tar -Zxf all.tar.Z		//Z调用compress解压.Z压缩包

		zip all.zip *.jpg/unzip all.zip
		gzip -d all.gz/gunzip all.gz
		bzip -d all.bz2/bunzip all.bz2
		uncompress all.Z
```
## iTerm + zsh ##

1. 查看所有shell `cat /etc/shell`
2. 查看当前使用的shell `echo $SHELL`，查看zsh版本`zsh --version`
3. 下载`iTerm2`/`oh my zsh`/包管理`homebrew`
4. omz下载安装`curl -L https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh | sh` 或者 `sh -c "$(curl -fsSL https://github.com/robbyrussell/oh-my-zsh/raw/master/tools/install.sh)"`
5. bash与zsh互相切换`chsh -s /bin/zsh(bash)`
6. 变更iTerm2的主题，`ZSH_THEME="agnoster"`
7. 乱码情况需要下载`powerline`字体包，`git clone https://github.com/powerline/fonts.git --depth=1`
8. 主题和插件的修改在路径`~/.oh-my-zsh/custom/`下

