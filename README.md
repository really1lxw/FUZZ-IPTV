## IPTV机顶盒FUZZ简述

   机顶盒在现在是挺常见的，但是在网上关于机顶盒测试漏洞的文章是少之又少，正好最近对机顶盒进行学习，现在总结了几个对机顶盒进行fuzz的方法！
  


### FUZZ流程

```
1.配置机顶盒连接到电视机显示器
2.电脑（攻击机器）需开启wifi共享
3.通过机顶盒的系统设置连接到电脑开启的wifi（机顶盒设置弱口令123456）
4.在电脑上面开启Wireshark或BURP等抓包软件
```

## FUZZ过程
1.在wireshark或burp抓包工具上面开启抓包后，使用遥控器控制连接机顶盒的电视机不断进行电视节目更换或相关操作

* 这个过程和使用burp对放开Intercept收集web的页面等非常相似


2.在wireshark抓包工具上面对操作过程的流量进行获取分析

<img src="http://upload.ouliu.net/i/20171115171008lwigc.png"  />

* PS：各地IPTV的实现型式都不一样，因些抓包分析也不一样。像江苏，四川，上海等地用的是组播 所以有的大佬抓出来的包没有rtsp协议，取而代之的都是rtp的协议

<img src="http://upload.ouliu.net/i/20171115194947bwj6m.jpeg"  />



3.重点分析协议（IGMP、RTSP、HTTP）等
* 这些流量要认真查看




4.对流量内的请求地址进行分析比对后进行保存（留着最后FUZZ）


5.IGMP和RTSP协议存在但不限于泄露源播放地址、远程服务器等敏感信息泄露漏洞

<img src="http://upload.ouliu.net/i/2017111517085897w2o.jpeg"  />


6.HTTP协议存在但不限于WEB TOP10漏洞，深入即可对远程服务器进行攻击

<img src="http://upload.ouliu.net/i/20171115170656ryiki.png"  />

* 这个我相信各位大佬不用小弟说都知道的



7.对机顶盒IP进行端口扫描

```
1.常见开放端口23（Telnet）
2.大部分的23端口是会存在默认口令，或者是未授权的
3.通过telnet进入后肯定就是翻目录找远程服务器的IP(在这里推荐一个好用的软件'TV盒子助手'直接备份系统文件、源码等)
```
<img src="http://upload.ouliu.net/i/20171115200822ueawm.png"  />
