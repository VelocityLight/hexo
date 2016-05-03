---
title: 站点建设及参考
date: 2016-04-24 19:02:08
comments: false
---
 > **优秀参考站点：**
 > - [MoFive](http://moxfive.xyz/)
 > - [VoidKing](http://www.voidking.com/2015/05/31/deve-hexo-theme-optimize/)
 > - [页面借鉴](http://huzerui.com/)
 > - [NexT主题](http://zhiho.github.io/2015/09/29/hexo-next/)
 
 <br>
 > 2016.4.24 -- 添加标签云  
 > - 参考:[建设球形状标签云](http://magicwangs.github.io/post/Hexo-Yilia-%E4%B8%BB%E9%A2%98%E4%BC%98%E5%8C%96%E6%80%BB%E7%BB%93/)
 
<br>
> 修改favicon. 参考:[icon制作网址](http://www.easyicon.net/language.en/iconsearch/github/&min=10&max=48)

 <br>
 > 添加source/about, source/tags方法
 ```
 hexo new page about/tags
 ```
 > 删除该页面评论方法
 ``` 
 comments: false
 ```

<br>
> 修改头像后背景图片
> - themes/yilia/source/css/_partial/main.styl:
```
       .overlay{
            width: 100%;
            height: 180px;
            /* background-color: black; */
            background-image:url("../img/bg.jpg");
            background-size:cover;
            position: absolute;
            opacity: 0.7;
        }               
 ```

<br>

> 书写文章Markdown语法
> 参考:[Github+Markdown](https://guides.github.com/features/mastering-markdown/#syntax)
> [Github&Markdown](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)

<br>

> Markdown Latex语法:数学公式
> 参考:[Markdown Latex](https://github.com/cben/mathdown/wiki/math-in-markdown)

<br>