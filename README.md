# OpenClash 配置模板

原有两个INI已同步替换为多地区组合与AI细分版，继续使用原地址即可。

## 模板链接

[Cash-All-OpenClash.ini](https://raw.githubusercontent.com/yaoxingshiji/openclash-config/main/Cash-All-OpenClash.ini)

旧地址 [Cash-All-Fixed.ini](https://raw.githubusercontent.com/yaoxingshiji/openclash-config/main/Cash-All-Fixed.ini) 保持相同内容。

## OpenClash 设置

1. 配置订阅 → 编辑原来的节点订阅，保留自己的订阅地址。
2. 开启在线订阅转换，模板选“自定义模板”，填入上面的INI链接。
3. 保留原来可用的转换服务，保存并更新订阅。
4. 启用生成的YAML，使用“规则”模式。
5. 给ChatGPT、Google、YouTube等业务独立选择组合。DIRECT统一排最左；无历史选择时首项DIRECT生效，需要代理的业务请重新选节点组。
6. 如果转换服务仍返回旧分组，使用[本次刷新链接](https://raw.githubusercontent.com/yaoxingshiji/openclash-config/refs/heads/main/Cash-All-OpenClash.ini?v=2cbbdc0b0598)后再更新订阅。

这是订阅转换模板，应填在“自定义模板URL”栏；节点订阅栏继续使用自己的订阅地址。

## 分组与修复

- 港台日新韩-自动：香港、台湾、日本、新加坡、韩国。
- 台日新韩-自动：台湾、日本、新加坡、韩国。
- 保留单地区、所有手动和所有自动节点池；自动测试周期180秒，延迟公差100毫秒。
- ChatGPT、Copilot、Gemini、Claude单独分组，保留总AI、Meta AI、Perplexity及其他业务。
- 已删除“默认代理”和“检测”组，专用检测网站归入国外；保留Google组，Gemini及YouTube各自分流。
- 28个业务组使用相同选项和顺序，DIRECT第一；无历史选择时为直连，国外、漏网之鱼及需要代理的业务必须选好节点。空地区组保留REJECT。
- 保留YouTube先于Google、Bybit先于GitHub及精确域名边界；Copilot不使用整家云商ASN匹配。
- 模板39条ruleset、39个策略组，兼容本次验证的64条规则集上限。
- 四份新增AI列表位于rules/openclash-combined/；原有rules下的AI、MetaAI、Crypto、Check列表继续保留使用。

## 验证（2026-10-30）

- 本地subconverter v0.9.0：完整19个占位节点、仅香港、仅美国三种场景均正确生成39个组和42,456条规则，Mihomo v1.19.33配置检查通过，每场景33个分流与精确匹配用例通过。
- GitHub原INI及别名同步更新；通过GitHub连接器回读Raw内容与本地逐字一致。
- 公开转换遇到缓存，换用等价Raw路径和刷新参数后已验证最新内容：api.asailor.org使用8个占位节点生成39组、42,462条规则，四份细分AI表的45个条目全部存在，Mihomo检查通过。具体缓存层未确定。
- 所有测试只使用127.0.0.1:1占位节点，没有读取真实订阅或验证路由器、节点解锁能力。

## ChatGPT转圈排查

已根据[OpenAI网络说明](https://help.openai.com/en/articles/9247338-network-recommendations-for-chatgpt-errors-on-web-and-apps)补上精确资源域名cdn.openaimerge.com。这是覆盖缺口，不代表已定位真实超时原因。

台日新韩自动组只测试gstatic网络连通性，不能保证ChatGPT可用。先将ChatGPT、国外、漏网之鱼都选“所有-手动”，在“所有-手动”固定同一个具体节点，再完全关闭并重开ChatGPT；仍超时则检查连接面板中chatgpt.com、auth.openai.com的实际节点和错误。

## 使用边界

- 地区按转换后的名称识别，未知名称可用所有-手动。Other采用明确地区白名单，不接管所有未知命名。
- 模板请求保留原名；后端若强行传旧式emoji参数会去掉旗帜，纯旗帜节点可能丢失地区信息，应保留地区文字或调整后端参数。
- LiveKit host/turn属于共享域名，不能按App完全区分；测速可用也不保证服务解锁。
- 规则在更新订阅时由后端读取，实际路由器还需能访问相应资源。
- 小火箭配置仍在[shadowrocket目录](./shadowrocket/README.md)，使用对应客户端的配置格式。

原始分类来源：[liandu2024/Cash-All.ini](https://github.com/liandu2024/clash/blob/main/Cash-All.ini)。各规则来源保留在INI与自有列表中。
