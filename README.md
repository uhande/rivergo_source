配置
切换主题
修改 Hexo 根目录下的 _config.yml 的 theme 的值：theme: hexo-theme-matery

_config.yml 文件的其它修改建议:
请修改 _config.yml 的 url 的值为你的网站主 URL（如：http://xxx.github.io）。
建议修改两个 per_page 的分页条数值为 6 的倍数，如：12、18 等，这样文章列表在各个屏幕下都能较好的显示。
如果你是中文用户，则建议修改 language 的值为 zh-CN。
新建分类 categories 页
categories 页是用来展示所有分类的页面，如果在你的博客 source 目录下还没有 categories/index.md 文件，那么你就需要新建一个，命令如下：

hexo new page "categories"
编辑你刚刚新建的页面文件 /source/categories/index.md，至少需要以下内容：

---
title: categories
date: 2018-09-30 17:25:30
type: "categories"
layout: "categories"
---
新建标签 tags 页
tags 页是用来展示所有标签的页面，如果在你的博客 source 目录下还没有 tags/index.md 文件，那么你就需要新建一个，命令如下：

hexo new page "tags"
编辑你刚刚新建的页面文件 /source/tags/index.md，至少需要以下内容：

---
title: tags
date: 2018-09-30 18:23:38
type: "tags"
layout: "tags"
---
新建关于我 about 页
about 页是用来展示关于我和我的博客信息的页面，如果在你的博客 source 目录下还没有 about/index.md 文件，那么你就需要新建一个，命令如下：

hexo new page "about"
编辑你刚刚新建的页面文件 /source/about/index.md，至少需要以下内容：

---
title: about
date: 2018-09-30 17:25:30
type: "about"
layout: "about"
---
新建友情连接 friends 页（可选的）
friends 页是用来展示友情连接信息的页面，如果在你的博客 source 目录下还没有 friends/index.md 文件，那么你就需要新建一个，命令如下：

hexo new page "friends"
编辑你刚刚新建的页面文件 /source/friends/index.md，至少需要以下内容：

---
title: friends
date: 2018-12-12 21:25:30
type: "friends"
layout: "friends"
---
同时，在你的博客 source 目录下新建 _data 目录，在 _data 目录中新建 friends.json 文件，文件内容如下所示：

[{
    "avatar": "http://image.luokangyuan.com/1_qq_27922023.jpg",
    "name": "码酱",
    "introduction": "我不是大佬，只是在追寻大佬的脚步",
    "url": "http://luokangyuan.com/",
    "title": "前去学习"
}, {
    "avatar": "http://image.luokangyuan.com/4027734.jpeg",
    "name": "闪烁之狐",
    "introduction": "编程界大佬，技术牛，人还特别好，不懂的都可以请教大佬",
    "url": "https://blinkfox.github.io/",
    "title": "前去学习"
}, {
    "avatar": "http://image.luokangyuan.com/avatar.jpg",
    "name": "ja_rome",
    "introduction": "平凡的脚步也可以走出伟大的行程",
    "url": "ttps://me.csdn.net/jlh912008548",
    "title": "前去学习"
}]
代码高亮
由于 Hexo 自带的代码高亮主题显示不好看，所以主题中使用到了 hexo-prism-plugin 的 Hexo 插件来做代码高亮，安装命令如下：

npm i -S hexo-prism-plugin
然后，修改 Hexo 根目录下 _config.yml 文件中 highlight.enable 的值为 false，并新增 prism 插件相关的配置，主要配置如下：

highlight:
  enable: false

prism_plugin:
  mode: 'preprocess'    # realtime/preprocess
  theme: 'tomorrow'
  line_number: false    # default false
  custom_css:
搜索
本主题中还使用到了 hexo-generator-search 的 Hexo 插件来做内容搜索，安装命令如下：

npm install hexo-generator-search --save
在 Hexo 根目录下的 _config.yml 文件中，新增以下的配置项：

search:
  path: search.xml
  field: post
中文链接转拼音（可选的）
如果你的文章名称是中文的，那么 Hexo 默认生成的永久链接也会有中文，这样不利于 SEO，且 gitment 评论对中文链接也不支持。我们可以用 hexo-permalink-pinyin Hexo 插件使在生成文章时生成中文拼音的永久链接。

安装命令如下：

npm i hexo-permalink-pinyin --save
在 Hexo 根目录下的 _config.yml 文件中，新增以下的配置项：

permalink_pinyin:
  enable: true
  separator: '-' # default: '-'
注：除了此插件外，hexo-abbrlink 插件也可以生成非中文的链接。

文章字数统计插件（可选的）
如果你想要在文章中显示文章字数、阅读时长信息，可以安装 hexo-wordcount插件。

安装命令如下：

npm i --save hexo-wordcount
然后只需在本主题下的 _config.yml 文件中，激活以下配置项即可：

wordCount:
  enable: false # 将这个值设置为 true 即可.
  postWordCount: true
  min2read: true
  totalCount: true
添加 RSS 订阅支持（可选的）
本主题中还使用到了 hexo-generator-feed 的 Hexo 插件来做 RSS，安装命令如下：

npm install hexo-generator-feed --save
在 Hexo 根目录下的 _config.yml 文件中，新增以下的配置项：

feed:
  type: atom
  path: atom.xml
  limit: 20
  hub:
  content:
  content_limit: 140
  content_limit_delim: ' '
  order_by: -date
执行 hexo clean && hexo g 重新生成博客文件，然后在 public 文件夹中即可看到 atom.xml 文件，说明你已经安装成功了。

修改页脚
页脚信息可能需要做定制化修改，而且它不便于做成配置信息，所以可能需要你自己去再修改和加工。修改的地方在主题文件的 /layout/_partial/footer.ejs 文件中，包括站点、使用的主题、访问量等。

修改社交链接
在主题的 _config.yml 文件中，默认支持 QQ、GitHub 和邮箱的配置，你可以在主题文件的 /layout/_partial/social-link.ejs 文件中，新增、修改你需要的社交链接地址，增加链接可参考如下代码：

<a href="https://github.com/blinkfox" class="tooltipped" target="_blank" data-tooltip="访问我的GitHub" data-position="top" data-delay="50">
    <i class="fa fa-github"></i>
</a>
其中，社交图标（如：fa-github）你可以在 Font Awesome 中搜索找到。以下是常用社交图标的标识，供你参考：

Facebook: fa-facebook
Twitter: fa-twitter
Google-plus: fa-google-plus
Linkedin: fa-linkedin
Tumblr: fa-tumblr
Medium: fa-medium
Slack: fa-slack
新浪微博: fa-weibo
微信: fa-wechat
QQ: fa-qq
注意: 本主题中使用的 Font Awesome 版本为 4.7.0。

修改打赏的二维码图片
在主题文件的 source/medias/reward 文件中，你可以替换成你的的微信和支付宝的打赏二维码图片。

配置音乐播放器（可选的）
要支持音乐播放，就必须开启音乐的播放配置和音乐数据的文件。

首先，在你的博客 source 目录下的 _data 目录（没有的话就新建一个）中新建 musics.json 文件，文件内容如下所示：

[{
	"name": "五月雨变奏电音",
	"artist": "AnimeVibe",
	"url": "http://xxx.com/music1.mp3",
	"cover": "http://xxx.com/music-cover1.png"
}, {
	"name": "Take me hand",
	"artist": "DAISHI DANCE,Cecile Corbel",
	"url": "/medias/music/music2.mp3",
	"cover": "/medias/music/cover2.png"
}, {
	"name": "Shape of You",
	"artist": "J.Fla",
	"url": "http://xxx.com/music3.mp3",
	"cover": "http://xxx.com/music-cover3.png"
}]
注：以上 JSON 中的属性：name、artist、url、cover 分别表示音乐的名称、作者、音乐文件地址、音乐封面。

然后，在主题的 _config.yml 配置文件中激活配置即可：

# 是否在首页显示音乐.
music:
  enable: true
  showTitle: false
  title: 听听音乐
  fixed: false # 是否开启吸底模式
  autoplay: false # 是否自动播放
  theme: '#42b983'
  loop: 'all' # 音频循环播放, 可选值: 'all', 'one', 'none'
  order: 'list' # 音频循环顺序, 可选值: 'list', 'random'
  preload: 'auto' # 预加载，可选值: 'none', 'metadata', 'auto'
  volume: 0.7 # 默认音量，请注意播放器会记忆用户设置，用户手动设置音量后默认音量即失效
  listFolded: false # 列表默认折叠
  listMaxHeight: # 列表最大高度
文章 Front-matter 介绍
Front-matter 选项详解
Front-matter 选项中的所有内容均为非必填的。但我仍然建议至少填写 title 和 date 的值。

配置选项	默认值	描述
title	Markdown 的文件标题	文章标题，强烈建议填写此选项
date	文件创建时的日期时间	发布时间，强烈建议填写此选项，且最好保证全局唯一
author	根 _config.yml 中的 author	文章作者
img	featureImages 中的某个值	文章特征图，推荐使用图床(腾讯云、七牛云、又拍云等)来做图片的路径.如: http://xxx.com/xxx.jpg
top	true	推荐文章（文章是否置顶），如果 top 值为 true，则会作为首页推荐文章
cover	false	v1.0.2版本新增，表示该文章是否需要加入到首页轮播封面中
coverImg	无	v1.0.2版本新增，表示该文章在首页轮播封面需要显示的图片路径，如果没有，则默认使用文章的特色图片
password	无	文章阅读密码，如果要对文章设置阅读验证密码的话，就可以设置 password 的值，该值必须是用 SHA256 加密后的密码，防止被他人识破。前提是在主题的 config.yml 中激活了 verifyPassword 选项
toc	true	是否开启 TOC，可以针对某篇文章单独关闭 TOC 的功能。前提是在主题的 config.yml 中激活了 toc 选项
mathjax	false	是否开启数学公式支持 ，本文章是否开启 mathjax，且需要在主题的 _config.yml 文件中也需要开启才行
summary	无	文章摘要，自定义的文章摘要内容，如果这个属性有值，文章卡片摘要就显示这段文字，否则程序会自动截取文章的部分内容作为摘要
categories	无	文章分类，本主题的分类表示宏观上大的分类，只建议一篇文章一个分类
tags	无	文章标签，一篇文章可以多个标签
reprintPolicy	cc_by	文章转载规则， 可以是 cc_by, cc_by_nd, cc_by_sa, cc_by_nc, cc_by_nc_nd, cc_by_nc_sa, cc0, noreprint 或 pay 中的一个
注意:

如果 img 属性不填写的话，文章特色图会根据文章标题的 hashcode 的值取余，然后选取主题中对应的特色图片，从而达到让所有文章都的特色图各有特色。
date 的值尽量保证每篇文章是唯一的，因为本主题中 Gitalk 和 Gitment 识别 id 是通过 date 的值来作为唯一标识的。
如果要对文章设置阅读验证密码的功能，不仅要在 Front-matter 中设置采用了 SHA256 加密的 password 的值，还需要在主题的 _config.yml 中激活了配置。有些在线的 SHA256 加密的地址，可供你使用：开源中国在线工具、chahuo、站长工具。
您可以在文章md文件的 front-matter 中指定 reprintPolicy 来给单个文章配置转载规则
以下为文章的 Front-matter 示例。

最简示例
---
title: typora-vue-theme主题介绍
date: 2018-09-07 09:25:00
---
最全示例
---
title: typora-vue-theme主题介绍
date: 2018-09-07 09:25:00
author: 赵奇
img: /source/images/xxx.jpg
top: true
cover: true
coverImg: /images/1.jpg
password: 8d969eef6ecad3c29a3a629280e686cf0c3f5d5a86aff3ca12020c923adc6c92
toc: false
mathjax: false
summary: 这是你自定义的文章摘要内容，如果这个属性有值，文章卡片摘要就显示这段文字，否则程序会自动截取文章的部分内容作为摘要
categories: Markdown
tags:
  - Typora
  - Markdown
---
