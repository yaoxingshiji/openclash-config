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
5. 在“🚀 默认代理”中选择组合，相关业务默认跟随；也能给ChatGPT、YouTube等业务单独选组合。

这是订阅转换模板，应填在“自定义模板URL”栏；节点订阅栏继续使用自己的订阅地址。

## 分组与修复

- 港台日新韩-自动：香港、台湾、日本、新加坡、韩国。
- 台日新韩-自动：台湾、日本、新加坡、韩国。
- 保留单地区、所有手动和所有自动节点池；自动测试周期180秒，延迟公差100毫秒。
- ChatGPT、Copilot、Gemini、Claude单独分组，保留总AI、Meta AI、Perplexity及其他业务。
- 国内直连、漏网流量默认代理；空地区组保留REJECT。
- 保留YouTube先于Google、Bybit先于GitHub及精确域名边界；Copilot不使用整家云商ASN匹配。
- 模板39条ruleset、41个策略组，兼容本次验证的64条规则集上限。
- 四份新增AI列表位于rules/openclash-combined/；原有rules下的AI、MetaAI、Crypto、Check列表继续保留使用。

## 验证（2026-10-30）

- 本地subconverter v0.9.0：完整19个占位节点、仅香港、仅美国三种场景均正确生成41个组和42,455条规则，Mihomo v1.19.33配置检查通过，每场景31个分流与精确匹配用例通过。
- 两个原INI和四份新增列表匿名Raw下载均HTTP 200，并与本地验证内容逐字节一致。
- 公开转换服务api.asailor.org实际读取已替换的Cash-All-OpenClash.ini：8个占位节点，41组、42,461条规则；四份新列表的44个条目均出现在结果中，两个组合正确，Mihomo检查通过。
- 所有测试只使用127.0.0.1:1占位节点，没有读取真实订阅或验证路由器、节点解锁能力。

## 使用边界

- 地区按转换后的名称识别，未知名称可用所有-手动。Other采用明确地区白名单，不接管所有未知命名。
- 模板请求保留原名；后端若强行传旧式emoji参数会去掉旗帜，纯旗帜节点可能丢失地区信息，应保留地区文字或调整后端参数。
- LiveKit host/turn属于共享域名，不能按App完全区分；测速可用也不保证服务解锁。
- 规则在更新订阅时由后端读取，实际路由器还需能访问相应资源。
- 小火箭配置仍在[shadowrocket目录](./shadowrocket/README.md)，使用对应客户端的配置格式。

原始分类来源：[liandu2024/Cash-All.ini](https://github.com/liandu2024/clash/blob/main/Cash-All.ini)。各规则来源保留在INI与自有列表中。
