# Crack_BT_Panel
<p>宝塔面板5.9.X Pro破解版一键脚本已完成，欢迎使用。</p>
<p>网上主流的破解方法是导入其他已授权用户的配置信息，部分下载源并非来自宝塔官方渠道，安全性无法保障，本方法全部基于修改本地配置文件实现，安全绿色无后门。</p>
<p>本破解方法的原理是通过劫持宝塔面板的 common.py 里，第 164 行记录 release 的信息，将其延期到 2999 年，实现了永久破解的目的。</p>

## 使用须知
<p>本脚本必须在完全干净的 CentOS/Debian/Ubuntu 系统上安装</p>
<p>如已安装更高版本的宝塔面板，请先卸载高版本再安装</p>
<p>如已安装其他种类的面板，或 LNMP 之类的运行环境、一键包，建议备份好数据，重装干净系统再安装</p>

## 使用方法
<code>wget -O crack_bt_panel_pro.sh https://git.io/fprzD && bash crack_bt_panel_pro.sh</code>

运营还是支持正版，这个可以自己玩一下，还是挺简单的

首先安装面板免费版

yum install -y wget && wget -O install.sh http://download.bt.cn/install/install.sh && sh install.sh

然后升级专业版

wget -O update.sh http://download.bt.cn/install/update_pro.sh && bash update.sh pro

找到路径/www/server/panel/class 找到文件名或者直接搜索：common.py

搜索代码164行

data = panelAuth().get_order_status(None);

替换成

data = {'statu' : True,'msg':{'endtime' : 32503651199 }};

完成后，进入 /www/server/panel/data 新建一个文件 文件名为：userInfo.json 内容空的，如果存在这个文件的删掉重新新建文件。

最后输入命令 /etc/init.d/bt restart 重启宝塔 完美嗨皮！！

注意：安装前请关闭宝塔网页  防止错误

如果使用失败，请恢复成免费版 代码为

wget -O update.sh http://download.bt.cn/install/update.sh && bash update.sh free

以下为实际操作代码:


1.切换用户

sudo su root

2.升级到宝塔专业版

wget -O update.sh http://download.bt.cn/install/update_pro.sh && bash update.sh pro

3.运行

touch /www/server/panel/data/userInfo.json

echo > /www/server/panel/data/userInfo.json

4.重启面板

/etc/init.d/bt restart

