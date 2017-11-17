# MaxPress：MarkDown+Python实现微信公众号一键排版

## 环境

使用Python 3.5.2开发，CSS样式表使用LESS编译。

依赖的包：[mistune](https://github.com/lepture/mistune)，
[premailer](https://github.com/peterbe/premailer)，
[lesscpy](https://github.com/lesscpy/lesscpy)

## 用法

### 基础使用

1. 使用Markdown创作你的内容，保存为`.md`文件，放入`workspace/md`目录中。（可以添加多个`.md`文件，支持批量转换）
2. 运行`maxpress.py`，`workspace／html`目录下将生成同名`.html`文件；同时原始`.md`的文件将被移动到`workspace／archive`目录中存档。
3. 用浏览器打开生成的`.html`文件，全选复制，粘贴到微信编辑器中。
4. 检查，预览，调整。

**【注意】推送前请务必发送到手机预览仔细检查，作者不为最终样式的绝对正确担保。**

### 格式调整

在转换之前，修改`config.json`文件，可自定义常用格式变量。

包括：

| 变量名 | 默认值 | 说明 |
| :----- | :----- | :---- |
|main_size     |16px   |正文主字号|
|accent_color  |#2298a5|强调色，用于标题、强调元素等文字颜色|
|text_color    |#555   |正文文字颜色|
|quote_color   |#999   |引用框和代码框内文字颜色|
|line_height   |2em    |正文行高|
|para_spacing  |1.5em  |正文段间距|
|title_align   |left   |标题水平方式，建议`left`或`center`（仅支持h3-h6，h1、h2固定使用左对齐）|
|main_margin   |3%     |内容两侧留白比例|
|poster_url    |""     |底部二维码／海报图片的地址|

### 更多自定义

1. 如果你希望覆盖默认样式中的个别样式，可以自主编写`custom.css`，它将在`default.css`之后被引入。
2. 如果你希望整体弃用默认样式并启用自定义CSS样式表，也可以直接调用脚本中的`convert_all`函数，通过`styles`参数传入自定义CSS文件路径（支持用列表传入多个），这时`custom.css`将在你的全部自定义样式表之后引入。

### 注意事项

1. **列表格式丢失问题：**带样式的列表粘贴到微信编辑器时，可能出现意外格式丢失的情况（貌似是微信的bug？），目前通过在每个`li`元素内额外添加一个`span`元素包装样式，暂时可以解决。但要注意，如果自定义样式的话，为`li span`所设置的字号、颜色等不能与上级元素完全一致，否则在粘贴到微信编辑器时会被自动去掉。

## 示例

[`example.md`](https://github.com/insula1701/maxpress/blob/master/workspace/md/example.md) -> 
[`example.html`](https://github.com/insula1701/maxpress/blob/master/workspace/md/example.html)

## 后续开发计划

- [ ] 自动在文首添加引导关注Banner
- [ ] 代码的精简&重构（不影响功能）
- [ ] 支持更多样的文中小标题设置模式

## Reference

默认样式部分参考了李笑来[`markdownhere.css`](https://gist.github.com/xiaolai/aa190255b7dde302d10208ae247fc9f2)

## License

MIT