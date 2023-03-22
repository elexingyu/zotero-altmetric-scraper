# zotero-altmetric-scraper

这个 JavaScript 脚本用于批量获取 Zotero 条目的 Altmetric 分数，并将分数的整数值返回在 Zotero 的 “extra” 字段中。

Altmetric 是一个全球性的指标数据库和测量服务，用于衡量学术论文和其他研究成果在社交媒体和传统新闻媒体上的影响力和关注度。

该脚本使用论文的 DOI ，通过Altmetric的 API 接口获取 altmetric 分数。如果接口没有分数，则返回 “no altmetric”；如果条目没有 DOI，则返回 “missing doi”。脚本会在每次查询之间插入一个随机时间间隔，以避免频繁调用 API 被封禁 IP。

# 使用方法

![](https://picsaving-1258754708.cos.ap-guangzhou.myqcloud.com/img/WX20230322-214705@2x.png)

1. 打开 Zotero 桌面应用程序，并进入您要更新 Altmetric 分数的 Zotero 库。

2. 选择要更新的条目，然后点击菜单中的 “工具” -> “开发者” -> “运行 JavaScript”（快捷键：Ctrl + Shift + E）。

3. 在弹出的对话框中，把[代码](https://github.com/elexingyu/zotero-altmetric-scraper/blob/main/zotero-altmetric-scraper)复制进左边的空白栏，然后点击左上角的“run”。

4. 脚本将开始运行，目前脚本运行时会随机停顿0.5s~2s。

5. 更新后的 Altmetric 分数将以整数形式显示在 Zotero 条目的 “extra” 字段中。如果 Altmetric 的 API 接口无法返回分数，则该字段将显示 “no altmetric”；如果条目没有 DOI，则该字段将显示 “missing doi”。

# 可配置项

脚本中有一些可配置项，您可以根据需要进行修改。这些可配置项包括：

altmetricUrl：Altmetric API 的 URL。默认为 'https://api.altmetric.com/v1/doi/' ，这是免费的，不建议大家用力过猛导致封禁。如果你有单独申请API，可以替换。

wait：每次查询之间的等待时间（以毫秒为单位）。默认为一个返回 1 到 5 秒之间随机整数值的函数。

您可以修改这些可配置项，以适应您自己的需求。
