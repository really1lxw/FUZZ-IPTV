## IPTV机顶盒FUZZ简述

机顶盒进行一次PPPOE拨号，连接到电信的专用网络，盒子内置直播APP访问专网的指定地址实现节目观看。现在的连接方式我们不好抓包，最好是让观看的线路经过我们的电脑，这样抓包更直接有效。我的方法是将IPTV口的网线连接到电脑的网口，由电脑PPPOE拨号连接到电信的专网，再用电脑的无线网卡进行WIFI共享，IPTV盒子通过WIFI连接到电脑进行漏洞挖掘，这时候在电脑上运行抓包软件，就能获取相关源的连接地址.

### FUZZ流程

Markdown is a lightweight and easy-to-use syntax for styling your writing. It includes conventions for

```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```

For more details see [GitHub Flavored Markdown](https://guides.github.com/features/mastering-markdown/).

### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/really1lxw/FUZZ-IPTV/settings). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://help.github.com/categories/github-pages-basics/) or [contact support](https://github.com/contact) and we’ll help you sort it out.
