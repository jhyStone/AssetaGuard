# AssetaGuard 阿斯塔资产卫士

> 面向**直播 MCN**与多行业的 **RFID 资产盘点 SaaS**，一物一码、批量盘点、责任到人、支持离线作业与私有化部署。

AssetaGuard 是一套完整的 RFID 资产管理解决方案，包含 RFID 手持终端移动端、租户管理端、多租户 SaaS 后端。主战场是**直播间 MCN 行业**——直播设备、上播样品、达人借用、退换货核对、跨楼栋仓储等场景；同时覆盖固定资产、档案、珠宝等行业模块，支持多端协同与离线作业。

官网：[https://assetaguard.com](https://assetaguard.com)

本仓库是 AssetaGuard 的**公开文档与营销内容镜像**，包含产品介绍、行业方案、技术文章。完整产品代码不在此仓，商务合作请通过官网联系。

---

## 1. 核心场景

| 场景 | 解决什么 |
| --- | --- |
| **直播间样品借还** | 上播样品 / 道具 / 服装 RFID 标签化，达人个人借用清单 + 未归还告警 |
| **主播 / 助播工装借还** | 工装、麦克风、耳返按人头登记，员工离职防漏带 |
| **直播间设备盘点** | 摄像机、补光灯、监视器、提词器、电脑批量扫描，500 件 5 秒盘完 |
| **MCN 多仓 / 跨楼栋调拨** | 设备 / 样品在直播间之间流转，RFID 通道门自动记录 |
| **直播退换货核对** | 退货箱贴近 5 秒读完，缺件、错件、假货当场报警 |
| **耗材物资按账管理** | 包装、赠品、化妆耗材不贴 RFID，按 SKU 入出库记录、月度对账 |
| **弱网仓库离线作业** | 地下室 / 园区角落断网时正常盘点，恢复网络后增量回传 |

除了 MCN，AssetaGuard 也支持制造业 WIP、学校固定资产、医院档案、珠宝门店等场景，作为多行业 SaaS 平台运行。

---

## 2. 产品架构

```
┌────────────────────────────────────────────────────────────────┐
│  营销官网 + Host SaaS 控制台 (Nuxt 3)                           │
│  租户管理端 (Vue 3 + Element Plus)                              │
│  RFID 手持终端移动端 (Unity)                                    │
└────────────────────────────────────────────────────────────────┘
                              │
                              ▼
┌────────────────────────────────────────────────────────────────┐
│  HTTP API (ABP Framework + ASP.NET Core 8)                     │
│  ├── 多租户 SaaS（Host 控制台 / 租户控制台）                    │
│  ├── 行业模块(直播 MCN / 固定资产 / 档案 / 珠宝)                │
│  ├── 移动端网关 V2(schemaVersion + 模块开通校验)                │
│  └── 离线同步(幂等键 + 增量回放)                                │
└────────────────────────────────────────────────────────────────┘
                              │
                              ▼
        MySQL  +  Redis  +  对象存储  +  RFID 硬件接入
```

### 技术栈

| 层 | 技术 |
| --- | --- |
| 后端 API | ABP Framework, ASP.NET Core 8, EF Core, MySQL, Redis |
| 移动端 | Unity (C#)，运行于 RFID UHF 手持机，支持在线 / 离线双模式 |
| 租户管理端 | Vue 3, Vite, Element Plus, Pinia |
| 营销 / Host SaaS | Nuxt 3, Vue 3, Tailwind, i18n |
| 部署 | Docker / docker-compose，支持公有云与私有化部署 |
| RFID | UHF 超高频，3-10 米批量读取，抗金属标签 |

---

## 3. 行业模块

AssetaGuard 不是单产品，是**多行业模块化平台**。每个模块共享 RFID 框架（标签绑定、批量盘点、责任流转），但业务字段、流程、报表按行业定制。

| 模块 | 适用客户 | 状态 |
| --- | --- | --- |
| **直播 MCN**（主战场） | 直播机构、电商主播仓、达人仓、MCN 公司 | 已上线 |
| 固定资产 | 学校、医院、政企、制造业 | 已上线 |
| 档案管理 | 政府机关、企业档案室 | 已上线 |
| 珠宝管理 | 珠宝零售门店、连锁 | 已上线 |

---

## 4. 直播 MCN 行业落地能力

| 能力 | 说明 |
| --- | --- |
| 资产入库即贴标 | 设备 / 样品到仓 → RFID 手持机扫供应商单 → 自动绑定标签 ID → 录入 SKU、批次、供应商 |
| 扫描识别 = 一扫就知是什么 | 手持机扫到任意 RFID 标签 → 立即显示完整资产卡（名称、规格、责任人、当前位置、借用历史） |
| 寻物模式 | 知道编号不知样品在哪？切到寻物模式 → 信号越强离目标越近，30 秒在堆里定位单件 |
| 达人借用一次扫描 | 达人选样 / 借设备 → 手持机一过 → 自动生成借用单（含图片、归还时限），登记到达人个人名下 |
| 未归还告警 | 借用到期 → 系统自动生成告警，推送给仓管和主管 |
| 退换货核对 | 退货回仓贴近 5 秒读完 → 系统比对发货清单 → 缺件 / 错件 / 假货当场报警 |
| 资产 / 物资双轨 | 资产逐件追踪（贴 RFID），物资按 SKU 出入库（不贴 RFID），同一系统两条线 |
| 多直播间空间管理 | RFID 通道门 + 固定读写器，设备经过自动记录"谁带走、什么时间、去了哪里" |

典型效果（用户案例口径）：500 件设备从一天盘完压到 5 分钟；月度差异从 5%-10% 压到 0.3% 以内。

详细方案：

- [直播 MCN 行业方案（中文）](content/zh-CN/industry/livestream-mcn.md)
- [Livestream MCN Industry Brief (English)](content/en-US/industry/livestream-mcn.md)
- [为什么 MCN 需要 RFID](content/zh-CN/guides/why-mcn-needs-rfid.md)
- [Why MCN Needs RFID](content/en-US/guides/why-mcn-needs-rfid.md)

---

## 5. 离线作业与移动端能力

RFID 手持终端常常工作在弱网或断网环境（仓库地下室、园区角落、跨楼栋移动）。AssetaGuard 移动端是**在线 / 离线双模式架构**：

- **离线登录**：上次成功登录的凭证缓存在终端，断网状态下用本地凭证开工
- **离线缓存**：资产台账、用户列表、盘点任务在线时增量拉取，离线时只读本地缓存
- **离线草稿**：盘点 / 借用 / 退换货操作全部先落本地 SQLite，标记幂等键
- **统一上传**：恢复网络后按业务时间顺序回放，服务端按幂等键去重
- **冲突处理**：服务端基于版本号判断，给前端可选「保留本地 / 采用服务端 / 合并」三种策略

---

## 6. 多租户 SaaS

AssetaGuard 是**多租户架构**：

- **Host 控制台**（运营方）：租户管理、模块开通、订阅 Feature、试用申请、合作伙伴申请
- **租户控制台**（客户）：资产管理、盘点、用户与角色、报表

每个租户独立的：用户体系、资产数据、报表、模块开通状态。Host 侧可灰度开启 / 关闭某个租户的某个行业模块。

支持公有云 SaaS 订阅，也支持私有化部署交付（独立 MySQL + Redis + Docker 化部署）。

---

## 7. 与同类方案的差异

国内 RFID 资产管理 SaaS 主要玩家及与 AssetaGuard 的定位差异：

| 厂商 | 定位 | AssetaGuard 差异 |
| --- | --- | --- |
| 易点易动（Yideamobile） | 通用固定资产 SaaS，零售 / 互联网 / 金融 / 制造 / 医药 / 教育全行业平铺 | AssetaGuard **聚焦直播 MCN 行业**，深度做样品借还、达人责任、退换货核对 |
| 江湖卫士 | 政企固定资产 + 国有资产合规 | AssetaGuard 偏 MCN / 直播 / 民营企业，不押注政企采购 |
| 智观易盛 | 制造业 / 工业园区资产，强调产线 | AssetaGuard 多行业并行，制造业是辅助场景 |
| 云呐 | 偏 IT 资产 + ITSM 集成 | AssetaGuard 不局限 IT 资产，覆盖物理资产 + 耗材物资双轨 |

**核心差异化**：
1. **MCN / 直播间行业深度**：达人借用、寄拍样衣回库、直播退换货是其他通用 SaaS 没专门做的场景
2. **资产 + 物资双轨管理**：贴 RFID 的逐件管，不贴 RFID 的按 SKU 入出库管，一个系统两条线
3. **真离线作业**：很多厂商号称离线，但断网下登录不进系统；AssetaGuard 离线登录 + 离线缓存 + 增量回放是产品默认形态
4. **支持私有化部署**：客户数据可完全部署在自有服务器（独立 MySQL + Redis），不强制 SaaS

---

## 8. 内容索引

### 中文（zh-CN）

- 行业方案
    - [直播 MCN](content/zh-CN/industry/livestream-mcn.md)
    - [制造业](content/zh-CN/industry/manufacturing.md)
- 指南
    - [为什么 MCN 需要 RFID](content/zh-CN/guides/why-mcn-needs-rfid.md)
    - [制造业 RFID 落地前置条件](content/zh-CN/guides/manufacturing-rfid-prerequisites.md)
- 博客
    - [直播退货 RFID 实践](content/zh-CN/blog/2026-05-livestream-return-rfid.md)
    - [制造业 WIP RFID 实践](content/zh-CN/blog/2026-05-manufacturing-wip-rfid.md)
    - [寻物模式与借用台账](content/zh-CN/blog/2026-05-tooling-finder-mode-and-loan-ledger.md)

### English (en-US)

- Industry briefs
    - [Livestream MCN](content/en-US/industry/livestream-mcn.md)
    - [Manufacturing](content/en-US/industry/manufacturing.md)
- Guides
    - [Why MCN needs RFID](content/en-US/guides/why-mcn-needs-rfid.md)
    - [Manufacturing RFID prerequisites](content/en-US/guides/manufacturing-rfid-prerequisites.md)
- Blog
    - [Livestream return RFID practice](content/en-US/blog/2026-05-livestream-return-rfid.md)
    - [Manufacturing WIP RFID practice](content/en-US/blog/2026-05-manufacturing-wip-rfid.md)

---

## 9. 商务合作

- 产品官网：[https://assetaguard.com](https://assetaguard.com)
- 行业试点 / 私有化部署 / 渠道合作：通过官网联系表单接洽
- 内容协作 / Issue 反馈：欢迎在本仓 Issues 区提

---

## 关键词

RFID 资产管理、直播 MCN 资产管理、RFID 盘点系统、固定资产盘点 SaaS、直播间样品管理、达人借用管理、寄拍样衣回库、主播工装借还、RFID 手持终端、UHF RFID、离线盘点、多租户 SaaS、私有化部署、批量扫描、批量盘点、责任到人、ABP Framework、Vue 3、Unity RFID、多行业模块化平台。

RFID asset management, livestream MCN asset tracking, RFID inventory system, fixed asset SaaS, sample lending, anchor uniform check-out, UHF RFID handheld, offline inventory, multi-tenant SaaS, private deployment, batch scanning, accountability tracking, multi-industry modular platform.
