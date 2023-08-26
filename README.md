## 输出jsonl文件格式

1. 每个jsonl文件，其大小略大于500MB。每行是一个以一个主题，论坛针对该主题进行回复的对话。
2. 对于每一个论坛主题对话，其最高层次结构如下。

```json
{
    "ID": 10000,
    "主题": "主题",
    "来源": "清华树洞",
    "回复": [],
    "元数据": {
        "发帖时间": "20200628 06:38:34",
        "回复数": 37,
        "扩展字段": ""
    }
}
```

3. 其中回复是关于该语料的回复的相关评论的字典的列表，其结构如下所示。

```json
{
    "楼ID": "abcdef",
    "回复": "",
    "扩展字段": "",
}
```

6. 主题是楼主的话，由于楼主如果只发了链接由于会被过滤掉，所以主题有可能是空字符串。
7. 扩展字段会以字符串的格式给出，格式不完全固定，原始数据里面有什么就当前的内部格式如下所示，可以通过json.loads来解析。

最高层次结构的扩展字段：

```json
{
    "标签": "label", 
    "点赞数": 0, 
    "原文": "",
}
```

回复里面的扩展字段：

```json
{
    "回复人": "等站", 
    "回复时间": "", 
    "回复ID": "abcde",
    "点赞数": 1,
    "点踩数": 1,
}
```

3. label代表这个帖代表什么类型的讨论。
4. 原文是该语料的完整来源，如果我们代码解析出错可以在原文中自行提取。

## 结果示例

```json
{
    "id": 10000,
    "主题": "我爱jc！",
    "来源": "清华树洞",
    "回复": [
        "[Alice] 恭喜恭喜",
        "[Bob] 警察？",
        "[Carol] 恭喜",
        "[Dave] 啊这",
        "[Eve] 啊这",
        "[Francis] 恭喜",
        "[Grace] 怎么这么激烈",
        "[Hans] jc是谁",
        "[Isabella] 韭菜",
        "[Jason] 恭喜恭喜！",
        "[Kate] jc是什么啊",
        "[Eve] jicha？",
        "[Eve] jingcha？",
        "[Eve] jiancha？",
        "[Louis] 警察",
        "[Carol] 新世界的卡密",
        "[Margaret] 恭喜小破洞进入五位数时代！",
        "[Nathan] 蒋丞？",
        "[洞主] jc是我的一位无9好友，让万洞来纪念我们的友情（狗头）",
        "[Olivia] 第一反应是团团转hhhh",
        "[Carol] Re 洞主: 变紫了吗",
        "[洞主] Re Olivia: 哈哈哈",
        "[洞主] Re Carol: 啊，什么会变紫",
        "[Paul] jk jc js?",
        "[Queen] 啊这",
        "[Richard] 要不要举报呢（哈哈",
        "[Susan] jiaochuan？",
        "[Thomas] Re 洞主: 团团转(",
        "[Uma] 啊这",
        "[Vivian] 百洞！",
        "[Winnie] 百方洞！！ ",
        "[Xander] 电子系九字班的jcxgg啊，大家都不认识吗，不会吧不会吧",
        "[Yasmine] 团团转",
        "[Zach] 团团转",
        "[Angry Alice] 团团转",
        "[Angry Bob] 考古",
        "[Angry Carol] 考古"
    ],
    "元数据": {
        "发帖时间": "20200628 06:38:34",
        "回复数": 37,
        "扩展字段": "{\"原文\": \"<h1>10000 [★万洞认证★ ]</h1>2020/06/28, 06:38:34<br>我爱jc！<ul><li>[Alice] 恭喜恭喜</li><li>[Bob] 警察？</li><li>[Carol] 恭喜</li><li>[Dave] 啊这</li><li>[Eve] 啊这</li><li>[Francis] 恭喜</li><li>[Grace] 怎么这么激烈</li><li>[Hans] jc是谁</li><li>[Isabella] 韭菜</li><li>[Jason] 恭喜恭喜！</li><li>[Kate] jc是什么啊</li><li>[Eve] jicha？</li><li>[Eve] jingcha？</li><li>[Eve] jiancha？</li><li>[Louis] 警察</li><li>[Carol] 新世界的卡密</li><li>[Margaret] 恭喜小破洞进入五位数时代！</li><li>[Nathan] 蒋丞？</li><li>[洞主] jc是我的一位无9好友，让万洞来纪念我们的友情（狗头）</li><li>[Olivia] 第一反应是团团转hhhh</li><li>[Carol] Re 洞主: 变紫了吗</li><li>[洞主] Re Olivia: 哈哈哈</li><li>[洞主] Re Carol: 啊，什么会变紫</li><li>[Paul] jk jc js?</li><li>[Queen] 啊这</li><li>[Richard] 要不要举报呢（哈哈</li><li>[Susan] jiaochuan？</li><li>[Thomas] Re 洞主: 团团转(</li><li>[Uma] 啊这</li><li>[Vivian] 百洞！</li><li>[Winnie] 百方洞！！<br></li><li>[Xander] 电子系九字班的jcxgg啊，大家都不认识吗，不会吧不会吧</li><li>[Yasmine] 团团转</li><li>[Zach] 团团转</li><li>[Angry Alice] 团团转</li><li>[Angry Bob] 考古</li><li>[Angry Carol] 考古</li></ul>\", \"标签\": \"★万洞认证★ \"}"
    }
}
```
