# 各种技巧tips

#### 
iphone连接苹果电脑连不上，一直反复跳闪是否信任
解决办法（关闭usbd）：
打开终端输入：
sudo killall -STOP -c usbd

回车后输入密码，密码输入不可见
(期间输入的密码为开机设置密码)
要重开启（按流程输入回车）：
udo killall -CONT usb
