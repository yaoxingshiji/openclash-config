# Shadowrocket 多地区组合配置

[下载 combined.conf](https://raw.githubusercontent.com/yaoxingshiji/openclash-config/main/shadowrocket/combined.conf)

## 小火箭导入

1. 底部“配置” → 右上角“＋”。
2. 粘贴上面的 Raw HTTPS 链接，点击下载。
3. 点击下载的配置 → 使用配置。
4. 首页全局路由选择“配置”。
5. 在代理分组中，例如 ChatGPT → 台日新韩-自动，或 YouTube → 港台日新韩-自动。

## 节点组合

- 港台日新韩-自动：香港、台湾、日本、新加坡、韩国。
- 台日新韩-自动：台湾、日本、新加坡、韩国。
- 使用小火箭已有节点，按名称筛选，自动测速选择；默认测试周期180秒、超时5秒。
- 保留28个业务分类、11个节点组，以及已审查修复的ChatGPT/Claude依赖和Copilot ASN等规则。

## 更新与范围

GitHub主配置改变后，在小火箭中点击该文件的“更新配置”。此操作会重新下载并覆盖配置；更新后检查各业务所选策略。仅“使用配置/编译配置”主要刷新规则集等外部资源，不等于重新下载GitHub主配置。

Copilot过滤后的49条与Bybit16条为2026-10-30快照，需维护主配置才能更新；其余36个公开规则文件保持远程引用。自动测速不保证服务解锁；尚未在用户iPhone或真实节点上实测。

[小火箭操作参考](https://github.com/LOWERTOP/Shadowrocket#配置文件)

原始模板来自[liandu2024/Cash-All.ini](https://github.com/liandu2024/clash/blob/main/Cash-All.ini)，各规则来源保留在配置注释和远程URL中。
