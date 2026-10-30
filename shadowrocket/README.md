# Shadowrocket 小火箭配置

**[📥 获取配置（Raw）](https://raw.githubusercontent.com/yaoxingshiji/openclash-config/main/shadowrocket/combined.conf)** · **[备用链接（CDN）](https://cdn.jsdelivr.net/gh/yaoxingshiji/openclash-config@main/shadowrocket/combined.conf)** · [返回下载首页](../README.md)

复制地址到小火箭「配置 → ＋」：

```text
https://raw.githubusercontent.com/yaoxingshiji/openclash-config/main/shadowrocket/combined.conf
```

## 导入与更新

1. 保留自己的节点订阅；本配置不包含节点。
2. 小火箭底部 **配置 → ＋ → 粘贴地址 → 下载**。
3. 点击下载的文件 → **使用配置**；首页全局路由选 **配置**。
4. 在代理分组中选择组合，例如 **ChatGPT → 台日新韩-自动**、**YouTube → 港台日新韩-自动**。
5. 已导入过原链接：点该文件的 **更新配置**，再使用配置并检查分组选择。

如果 Raw 无法访问，复制顶部 CDN 链接；CDN 可能延迟同步。仅重新编译配置主要更新远程规则，不等于重新下载 GitHub 主配置。

## 本次同步（2026-10-30）

- 39 个策略组：28 个业务组、11 个节点池。保留 Google、YouTube 和细分 AI。
- 所有业务组选项排列一致，DIRECT 最左；国内默认 DIRECT，其余默认所有-手动，已保存选择可能继续保留。
- 删除检测组，检测网站归国外；增加漏网之鱼，明确国内域名及中国 GeoIP 走国内，其余未匹配流量交给漏网之鱼。
- 10 个自动组统一 HTTPS 测速，间隔 180 秒、超时 5 秒、公差 100ms；所有节点池过滤流量、到期等通知名称。
- 同步 OpenClash 精简后的 ChatGPT、Copilot、Gemini、Claude、AI、Meta AI 规则，减少 Google 资源、普通 Bing 和共享服务误入 AI。
- 流媒体优先于品牌与公共服务规则；保留 Apple、Global 的小火箭域名补充表，以及 Bybit 精确域名边界。

## 节点与验证范围

| 节点池 | 范围 |
| --- | --- |
| 港台日新韩-自动 | 香港、台湾、日本、新加坡、韩国 |
| 台日新韩-自动 | 台湾、日本、新加坡、韩国 |
| 各单地区-自动 | 对应地区的节点 |
| 所有-手动 / 所有-自动 | 已有节点，排除识别到的通知名称 |
| 其他-自动 | 明确识别出的其他地区 |

自动组直接筛选节点，不嵌套自动组。没有匹配节点时请改选有节点的组；按名称识别地区不等于验证实际出口。自动测速不保证服务解锁，也不能证明间歇超时已修好。

已检查结构、分组引用、地区正则及关键域名的静态路由，并成功读取全部 37 个远程规则文件。尚未在用户 iPhone、真实节点或视频播放场景中验证。

两端共用本仓库 `rules/` 下的精简规则；其余公开规则随远程文件更新。节点凭据、路由器设置及手机当前选择不在此配置发布操作中修改。

[小火箭操作参考（社区维护）](https://github.com/LOWERTOP/Shadowrocket#配置文件) · [原始分类来源](https://github.com/liandu2024/clash/blob/main/Cash-All.ini)
