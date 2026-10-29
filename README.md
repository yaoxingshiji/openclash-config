# openclash-config

OpenClash 订阅转换配置与使用说明。INI 是转换模板，需配合你自己的节点订阅生成 YAML。

## 自定义模板 Raw 链接

[打开 Cash-All-Fixed.ini](https://raw.githubusercontent.com/yaoxingshiji/openclash-config/refs/heads/main/Cash-All-Fixed.ini)

```text
https://raw.githubusercontent.com/yaoxingshiji/openclash-config/refs/heads/main/Cash-All-Fixed.ini
```

## 使用方法

1. 在 OpenClash → 配置订阅中，填写你自己的节点订阅。
2. 开启在线订阅转换，模板选择“自定义模板”，填入上方 Raw 链接。
3. 使用可读取该 Raw 链接的转换后端，保存并更新订阅。
4. 启用生成的 YAML，选择“规则”模式。
5. 在“🚀 默认代理”中选择节点或地区；各业务默认跟随它。
6. 使用旧版且保存过 DIRECT 选择时，请重置组选择，或把业务组改选“🚀 默认代理”。

## 已修复

- Bybit 16 条规则内联转换，保留后缀与精确域名的区别，并放在 GitHub 前面。
- YouTube 的页面、视频和 API 规则优先于 Google 的广义规则。
- AI 不再抢整个 x.com、bing.com、googleapis.com、gstatic.com 或公共鉴权/支付/统计域名。
- 业务默认代理；国内与漏网流量分开，未匹配流量默认代理。
- 地区筛选忽略大小写；其他地区是六个地区名称匹配条件的补集。
- 空地区组保留 REJECT，避免被转换器自动替换为 DIRECT。

## 使用边界

- 地区根据节点名称匹配，不是实际出口地理位置检测；命名特殊时可使用“所有-手动”。
- 同时写有多个地区的节点名可能进入多个地区组，例如“香港中转 美国”；请按实际出口选择。
- 某地区没有节点时选择该组会拒绝连接，请切换到实际有节点的地区。
- 自动测速只证明探测地址可达，AI/流媒体解锁仍取决于你的节点；需要时手动选择支持该服务的地区。
- 公共鉴权/CDN 无法仅凭域名判断来自哪个网站。为减少出口差异，建议优先修改“🚀 默认代理”，让相关业务保持同一出口。
- AI、Bybit、检测规则已内联，未来服务新增域名时需维护；其他 27 个远程规则源在重新转换订阅时获取，生成后的客户端配置不会因此实时更新。
- 本文件不包含节点、账号或订阅密钥，也不设置客户端的 DNS、IPv6 和 TUN。
- 如公共转换站提示规则集数量超限，请使用允许至少 136 条 ruleset 的后端；本次验证使用标准 subconverter 的默认无限制设置。

## 验证记录（2026-10-30）

- 标准 subconverter v0.9.0：实际拉取 27 个远程规则源，转换成功，无下载失败或离线快照替代。
- 完整地区场景：9 个占位节点，生成 35 个策略组、42,411 条规则；Mihomo v1.19.33 配置检查通过。
- 仅香港场景：1 个占位节点，其他六个地区组均仅为 REJECT；Mihomo 配置检查通过。
- 565 项静态检查通过；实际生成 YAML 的 37 个域名分流样例和 Bybit 精确域名的子域反例通过。
- REJECT 哨兵另经本地 HTTP 204 运行对照验证：健康候选优先，空组拒绝；未使用真实订阅或真实节点验证服务解锁。
- INI SHA256：16e18cdb9aefae3bd98b6e8874a331c497d719df4bbf7ae39dab8ceb0657b61e
