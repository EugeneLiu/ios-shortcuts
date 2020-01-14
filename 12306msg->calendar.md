##我做了什么？

12306 短信👉📅 的快捷指令，链接地址https://www.icloud.com/shortcuts/2f9d9d6f0071429396728208cf7aa361

![shortcut](https://raw.githubusercontent.com/EugeneLiu/ios-shortcuts/master/images/shortcut.jpeg)

只需要两步就能将 12306 短信变成日历的日程

1. 复制 12306 短信
2. 点击 12306 短信👉📅快捷指令

##我为什么要做？

每次在12306（APP 或者 网站）购买火车票之后，手机上都会收到 12306 发来的短信。短信内容包含订单号，乘车日期，车次，车厢号，座位号，车站，开车时间，检票口。

![12306msg](https://raw.githubusercontent.com/EugeneLiu/ios-shortcuts/master/images/12306msg.jpeg)

而我不喜欢很早就去车站等车，由于没有预留足够多的时间，到车站的时候会有些手忙脚乱。这个时候想查询乘车信息，无论是通过 12306 手机 app 查询，还是翻看之前的短信或事先的截图都是不是很方便。因为网络信号的问题 12306 手机 app 可能加载缓慢，短信和图片也可能早就被其他信息淹没了。所以将乘车信息作为日程在日历应用中维护起来就能很方便的查看了。

如果是在 iMessage 中直接创建日程比较麻烦，所以我想通过快捷指令自动将 12306 的短信内容添加到日历的日程当中。

##我是怎么做的？

整体流程

1. 读取粘贴板中的文本，判断是否是 12306 短信
2. 从短信内容中提出乘车时间，车次、车厢和座位号，车站这三部分主要信息，并保存在变量当中
3. 创建日程设置好提醒时间

具体操作

在指令中心中找到“整理剪贴板”模版，创建快捷指令，然后使用了快捷指令提供的脚本，APP，文稿三部分的功能来编写指令逻辑。

![shortcut-apps](https://raw.githubusercontent.com/EugeneLiu/ios-shortcuts/master/images/shortcut-apps.jpeg)

脚本提供了变量和控制流，用来保存提取出来的文本参数和检查是不是 12306 短信。

文稿提供了匹配文本和替换文本，这两个操作都支持正则表达式。不过我没有找到将两个变量的文本合并到一个变量当中的方法，所以我使用了匹配文本来提取主要信息，通过替换文本的方式将需要的信息合并在一起，比如日期和时间。

替换文本的正则表达式可以通过 () 来对匹配到的文本进行分组，使用$1来提取第一组的文本。

![text](https://raw.githubusercontent.com/EugeneLiu/ios-shortcuts/master/images/text.jpeg)

日历应用中提供了添加新日程的模板，我们把对应的变量放到指定的地方就完成了整个功能。

![calendar](https://raw.githubusercontent.com/EugeneLiu/ios-shortcuts/master/images/calendar.jpeg)

##总结

这个功能很简单，但是由于可使用的工具并不多而且手机上的操作也不方便，导致在手机上编写这些指令很麻烦。如果大家有类似的想法建议先把变量设计好，避免在中途频繁添加变量，减少切换功能的次数。：）