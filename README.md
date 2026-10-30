# 小火箭 / OpenClash 配置

按你使用的客户端选一行，直接获取配置链接。配置不包含节点，需要保留自己的节点订阅。

## 📥 获取链接

| 使用设备 | 下载内容 | 主链接 | 备用链接 |
| --- | --- | --- | --- |
| **iPhone / iPad · Shadowrocket 小火箭** | 可直接导入的 `.conf` 配置 | **[获取小火箭配置](https://raw.githubusercontent.com/yaoxingshiji/openclash-config/main/shadowrocket/combined.conf)** | [CDN 备用](https://cdn.jsdelivr.net/gh/yaoxingshiji/openclash-config@main/shadowrocket/combined.conf) |
| **路由器 · OpenClash** | 订阅转换用的 `.ini` 模板 | **[获取 OpenClash 模板](https://raw.githubusercontent.com/yaoxingshiji/openclash-config/main/Cash-All-OpenClash.ini)** | [CDN 备用](https://cdn.jsdelivr.net/gh/yaoxingshiji/openclash-config@main/Cash-All-OpenClash.ini) |

链接打不开时使用同一行的 CDN 备用。也可以复制下面代码框里的完整地址。

### 小火箭：复制到「配置 → ＋」

```text
https://raw.githubusercontent.com/yaoxingshiji/openclash-config/main/shadowrocket/combined.conf
```

下载后选择 **使用配置**，首页的 **全局路由** 选择 **配置**。已有此配置时，点它的 **更新配置**，再使用配置。

在代理分组中选择节点组合，例如「ChatGPT → 台日新韩-自动」「YouTube → 港台日新韩-自动」。

**[查看小火箭完整说明 →](./shadowrocket/README.md)**

### OpenClash：复制到「自定义模板 URL」

```text
https://raw.githubusercontent.com/yaoxingshiji/openclash-config/main/Cash-All-OpenClash.ini
```

进入 **配置订阅 → 编辑订阅 → 在线订阅转换 → 自定义模板**，填入上面地址，然后更新订阅并使用生成的 YAML。

**节点订阅地址栏继续填写自己的订阅。** 这个 INI 是转换模板，不能作为 YAML 直接启用。原来的 [Cash-All-Fixed.ini](https://raw.githubusercontent.com/yaoxingshiji/openclash-config/main/Cash-All-Fixed.ini) 地址也继续可用，内容相同。

## 🧭 分组怎么选

| 分组 | 节点范围 |
| --- | --- |
| 港台日新韩-自动 | 香港、台湾、日本、新加坡、韩国 |
| 台日新韩-自动 | 台湾、日本、新加坡、韩国 |
| 香港 / 台湾 / 日本 / 新加坡 / 韩国 / 美国-自动 | 对应单个地区 |
| 所有-手动 | 自己固定一条节点 |
| 所有-自动 | 自动测速选择节点 |
| 其他-自动 | 明确识别出的其他地区；未知名称请用所有-手动 |

- 39 个策略组：28 个业务组、11 个节点池。保留 Google、YouTube 及 ChatGPT / Copilot / Gemini / Claude 独立分组。
- DIRECT 统一在最左侧，业务组选项顺序一致；已去掉默认代理和检测组，检测网站归入国外。
- YouTube 等流媒体先匹配，AI 使用精简名单，减少 Google 资源和公共网站被误分。
- 自动测速使用 HTTPS，间隔 180 秒、公差 100ms。它检查连通性，不能保证所有网站或流媒体都可用。

**更新后检查选择：** 小火箭的国内组初始选 DIRECT，其余初始选所有-手动；已保存的选择可能被保留。OpenClash 没有历史选择时首项 DIRECT 生效，需为 Google、YouTube、ChatGPT、国外、漏网之鱼等选好代理。

## ❓ 常见问题

<details>
<summary><strong>Raw 打不开，或更新后还是旧内容</strong></summary>

使用顶部表格同一行的 CDN 备用链接。CDN 可能有缓存，刚发布后更新可能延迟。

小火箭需要点 **更新配置** 重新下载主文件，仅重新编译主要刷新远程规则。OpenClash 需要更新订阅，才能重新转换模板；转换服务也可能缓存旧内容。

更新后，小火箭应有「漏网之鱼」分组，且不再有「检测」分组；自动组的测速地址应为 `https://www.gstatic.com/generate_204`。

</details>

<details>
<summary><strong>Google / YouTube / ChatGPT 转圈或超时</strong></summary>

先查看该业务组实际选中的节点。两个业务组如果都选同一个自动组，会共享该自动组当前选中的节点。

可临时固定一条具体节点进行对比；测速有延迟数字不代表实际网站持续可用。OpenClash 的「覆写设置」能覆盖模板里的测速地址、间隔等参数，也需核对实际值。

不要仅凭转圈就判断分流规则、DNS 或 IPv6 一定有问题；超时发生时的实际节点和连接日志才是定位依据。

</details>

<details>
<summary><strong>验证范围、来源与使用边界</strong></summary>

- 小火箭同步版：已核对分组引用、规则顺序、地区筛选及关键域名的静态分流；37 个远程规则文件已读取验证。没有进行用户 iPhone 实机导入、真实节点或视频播放测试。
- OpenClash：此前使用 subconverter v0.9.0 与 Mihomo v1.19.33，通过本地及公开转换服务验证占位节点配置；这不代表真实节点可用或服务解锁。
- 地区依节点名称识别，混合中转名称可能有歧义。小火箭空地区组需自行改选有节点的组；OpenClash 模板为空组保留 REJECT。
- 两端共享本仓库精简 AI 规则；Apple / Global 保留小火箭格式所需的域名补充表。远程规则可能随上游更新。
- LiveKit 的部分 host / turn 域名属于共享服务，不能仅凭域名完全区分应用。

原始分类：[liandu2024/Cash-All.ini](https://github.com/liandu2024/clash/blob/main/Cash-All.ini)。规则来源：[blackmatrix7/ios_rule_script](https://github.com/blackmatrix7/ios_rule_script)、[ACL4SSR](https://github.com/ACL4SSR/ACL4SSR)、[v2fly/domain-list-community](https://github.com/v2fly/domain-list-community)。具体引用保留在配置内。

</details>
