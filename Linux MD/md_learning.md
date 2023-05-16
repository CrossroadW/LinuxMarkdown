# Markdown 表格
[markdown基本语法](https://markdown.com.cn/basic-syntax/horizontal-rules.html)
[markdown扩展语法](https://markdown.com.cn/extended-syntax/)
| *Syntax*  | Description |
| --------- | ----------- |
| Header    | Title       |
| Paragraph | Text        |

单元格宽度可以变化，呈现的输出将看起来相同。

| Syntax    | Description |
| --------- | ----------- |
| Header    | Title       |
| Paragraph | Text        |


1. 对齐
    您可以通过在标题行中的连字符的左侧，右侧或两侧添加冒号（:），将列中的文本对齐到左侧，右侧或中心。

| Syntax                |       Description        |                       key |
| :------------s-------- | :----------------------: | ------------------------: |
| Header                | Tiiiiiiiiiiiiiiiiiiiitle |                      jojo |
| Paragraphhhhhhhhhhhhh |           &#124;           | \ jokerssssssssssssssssssss |


1. 在表中转义管道字符
    您可以使用表格的HTML字符代码（&#124;）在表中显示竖线（|）字符。

### 代码块

```javascript
{
    sssssss,
    
    ssssssss
}
```
---
# link
<https://markdown.com.cn>
<fake@example.com>
# image_link
[这是一张图片](https://ts1.cn.mm.bing.net/th/id/R-C.987f582c510be58755c4933cda68d525?rik=C0D21hJDYvXosw&riu=http%3a%2f%2fimg.pconline.com.cn%2fimages%2fupload%2fupc%2ftx%2fwallpaper%2f1305%2f16%2fc4%2f20990657_1368686545122.jpg&ehk=netN2qzcCVS4ALUQfDOwxAwFcy41oxC%2b0xTFvOYy5ds%3d&risl=&pid=ImgRaw&r=0)

![alt](https://ts1.cn.mm.bing.net/th/id/R-C.987f582c510be58755c4933cda68d525?rik=C0D21hJDYvXosw&riu=http%3a%2f%2fimg.pconline.com.cn%2fimages%2fupload%2fupc%2ftx%2fwallpaper%2f1305%2f16%2fc4%2f20990657_1368686545122.jpg&ehk=netN2qzcCVS4ALUQfDOwxAwFcy41oxC%2b0xTFvOYy5ds%3d&risl=&pid=ImgRaw&r=0)


\***正文第二段。正文第二段。***


This is a regular paragraph.

<table>
    <tr>
        <td>Foo</td>
        <td>aaa</td>
    </tr>
    <tr>
        <td>p21</td>
        <td>p22</td>
    </tr>
</table>
# 列表语法
This is another regular paragraph.
: sssssssssssssssssssssssssssssssssss
: hhhhhhhhhhhhhhhhhhhhhhhhhhhhh

: ~~我是删除线~~

# 任务列表
- [ ] 任务1
- [x] 任务2

# emoji 
 
hhhhhhhhhh :joy:

ssssssssssssssssssss :grinning face:
ssssssssssss :smile:
[表情符号中文网](https://www.webfx.com/tools/emoji-cheat-sheet/)
# 在 markdown 中使用表情符号
语法：&#xcode; (注意最后的分号 ; 不可少)
其中 code 可以从表情符号 [Unicode](https://apps.timwhitlock.info/emoji/tables/unicode#) 列表中查到
例子：
    表情对应的 Unicode 编码为 U+1F600，(舍弃前面的 U+)。我们只需在 Markdown 文档中输入 &#x1F600; 即可显示为 😀。

- &#x1F600;
- &#x1F601;
- &#x1F602;
- &#x1F603;
- &#x1F604;
- &#x1F605;
- &#x1F601;

```python 
#这是Python代码块 
a = 10 b = 20 print(a + b)

```