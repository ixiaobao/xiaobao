![xiaobao](https://socialify.git.ci/haoruilee/xiaobao/image?font=Rokkitt&logo=https%3A%2F%2Fs3.ax1x.com%2F2020%2F12%2F03%2FD72Nid.jpg&pattern=Circuit%20Board&theme=Light)

# 东南大学i小宝使用说明

- 我是谁
- 使用说明
  - 写在前面
  - 常用口令
  - 常用指令
  - 与上一版本口令的区别
  - 关键词响应机制
  - 判断对话对象
  - 口令模板匹配菜单

如果阅读本页有困难，请访问[镜像地址](https://gitee.com/Li_Haor/xiaobao)

## 我是谁

i小宝是东南大学至善小宝社团用课余时间免费为学生群体开发的QQ回复机器人，希望可以让大家在东大的生活更简单！本页为机器人的使用说明，初步撰写可能有所疏漏，欢迎在[调查问卷](https://www.wjx.cn/jq/98433077.aspx)中提供反馈或在本项目中提出issue 🤗

[点击这里加我好友](https://res.abeim.cn/api/qq/?qq=2142364173)

阅读本文可能需要一定的模板匹配基础。

## 使用说明

### 写在前面

- 请勿拉小宝进奇奇怪怪的群。小宝的流量负担、硬盘负担很重，作为免费机器人请大家对我好一点。
- 如果你喜欢小宝，请[为我们点个star吧](https://github.com/ixiaobao/xiaobao)⭐，这会让我们的开发更有动力的，谢谢你！

### 常用口令

这些口令是提供用户使用的。部分口令以`/`开头。

- **绑定相关**

  - 绑定

    ```
    绑定 <一卡通号> <学号>
    例: 绑定 213191234 01019123
    ```

  - 解绑

    `即将支持`

- **教学相关**

  - 教学（全局关键字）【更新：教学可回答文字+图片】

    ```
    教学<A>回答<B>
    例: 教学逸逸回答逸逸是小宝最萌的姐姐
    ```

  - 群设置（群内关键字）

    ```
    群设置<A>回答<B>
    例:`群设置逸逸回答逸逸是小宝最萌的姐姐
    ```

- **随机数生成器**

  `即将支持`

- **内嵌关键词**

  `见后文`

### 常用指令

这些指令是提供群管理员与群主使用的，便于对小宝进行管理的指令。以`//`统一开头。

- **教学相关**

  - 封禁关键词

    ```
    //ban <教学关键词>
    ```

  - 解封关键词

    ```
    //unban <教学关键词>
    ```

  - 解封全部关键词

    ```
    //unbanall
    ```

- **签到相关**

  - 签到启停

    ```
    //signin <true / false>
    ```

- **内嵌关键词相关**

  `即将支持`

### 与上一版本口令的区别

由于众所周知的原因，小宝从2020年9月起阵亡了三个月，原代码基本完全被推翻重写，因此部分口令暂未实现。

未实现的口令有：

```
查询
查权限
校园活动
```

**好消息是小程序的功能不断丰富，如果有小宝无法满足的需求，欢迎使用东大小宝微信小程序或QQ小程序，向小宝发送“小宝小程序”即可获取链接**

### 关键词响应机制

小宝采用对每一句收到的消息进行 模板匹配+判断对话对象 的策略来判断是否需要回复


### 判断对话对象

编写一个既不打扰大家，又可以及时响应的机器人非常困难，本团队采取：**在响应函数前判断“是否是对小宝说的话”**来决定部分口令的响应。在**私聊、艾特、句子以“小宝”或“i小宝”开头时，则认为该句话是对小宝说的**，需要作出响应。简单来说，如果在群聊中小宝不理你，可以在一句话前加上“小宝”或艾特他，或者私聊。

例：

群聊中发送下文不会被回复，私聊中发送则会被回复

```
小程序
```

群聊中发送下文会被回复

```
小宝小程序
```

```
i小宝小程序
```

```
小程序@i小宝
```

### 口令的模板匹配菜单

本节的阅读难度略高，阅读[正则匹配教程](https://www.runoob.com/regexp/regexp-syntax.html)会对理解下文有帮助。

【时间充足的情况下会重写此节】

如果没有时间阅读正则匹配教程，简单来说：

1、开头结尾匹配：

- 如果下文的口令以```^```开头，则意味着您发送的口令必须与口令模板的开头相同。
- 如果下文的口令以```$```结尾，则意味着您发送的口令必须与口令模板的结尾相同。


例子：

- ```"^东大办公室$"```口令，则必须严格向小宝发送“东大办公室”，才可以得到相应。
- ```"^中午好|^午安"```口令，则只要口令是以“午安”或者“中午好”开头，则会被相应，如“午安ABCD”。
- ```|```代表或关系，“中午好EFGH”会得到和上文同样的响应

2、变长度匹配记录：

- ```(.+)```与```(.*)```代表着您在这个位置填写的变长度语句将被小宝记录.
  例子：
- "^教学(.+)回答(.*)"可以匹配到“教学ABCD回答EFG”，小宝会记录到ABCD和EFG


准备好了吗？下面是口令菜单：


SEU相关口令菜单：

```
"^东大办公室$"
"^查srtp$"
"^校历$"
"^接驳车地点$"
"^无线谷班车$"
"^班车$|^接驳车$"
"开水房|开水间"
"^校医院$|^就医指南$|^九龙湖医院$|^医保$|^医保报销$"
"^查课表$"
"^空教室$"
"^竞赛网站$|^竞赛管理平台$|^竞赛报名$"
"^小程序$|^QQ小程序$|^东大小宝小程序$"
"^选课$|^换课$|^退改补$"
"^上课时间$|^下课时间$"
```

小宝功能相关菜单：

```
"绑定"
"^教学(.+)回答(.*)"
"^教学(.+)$"
"^群设置(.+)回答(.*)"
```

早午晚安类菜单：

```
"^早安$|^早上好$"
"^中午好|^午安"
"^晚安$|^睡觉咯$|^睡睡了$|^睡睡$|^晚安小宝$|^晚上好$"
```

日常功能类菜单：

```
"查天气"
"点歌|来一首|我想听"
"夸夸|彩虹屁|来点彩虹屁|夸我"
"网抑云"
"不要理i小宝了"
"唱首歌吧"
"你是机器人吗"
"我好累"
"摸[头摸]"
"喜欢|爱你|爱|贴贴|想你啦|我爱你|想你了"
"^出现$|^快出现$|^小宝$"
"^领萌$"
"^揉揉$"
"^揉揉[图片]"
"^许愿$"
```

