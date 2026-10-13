# 竞品 fuint H5 UI 拆解规格（会员端 / 商户端）

> 目的：为 bahar 四行业矩阵 H5（会员端 `baharUniapp/pages/`、商户端 `baharUniapp/merchantPages/`）改版提供**可照做**的设计依据。
> 产出人：许清楚（产品经理） ｜ 日期：2026-10-08
> **合规声明**：fuint 官网明示「开源版本仅供学习和交流，商用必须购买授权」。本文档只吸收**布局顺序、视觉数值、交互范式**，**不复制任何源码文件**；文中所有 CSS 均为「按数值重写的自研参考写法」，不得整段粘贴竞品源码进我们仓库。

---

## 0. 信息源与可信度

| 级别 | 来源 | 内容 |
|---|---|---|
| **A（线上实测）** | `https://www.fuint.cn/h5/`（v4.2.0 运行时构建） | HTML 壳 + `static/index.*.css` + `static/js/index.*.js` |
| **A（线上实测）** | 页面级 chunk：`pages-index-index.be673e24.js`、`pages-user-index.e09196b0.js`、`merchantPages-index.38f9e011.js`、`merchantPages-data-index.5dd999e3.js`、**共享 chunk `pages-custom-index~pages-index-index.72177346.js`** | 逐页真实 CSS（含 rpx 数值）、渲染函数、类名、文案 |
| **A** | 线上 DOM 文本抽取 | 首页真实模块顺序与文案 |
| **B（源码仓库）** | GitHub `zzy-awesome/fuintUniapp`（2024-09，Apache-2.0），官方仓库 `gitee.com/fuint/fuint-uniapp` | vue 源文件（模板 + scss），用于交叉验证 2024→2025 差异 |
| **C** | 用户三张截图（经团队转述） | 视觉层级与模块存在性确认 |

**重要发现**：我们的工程与 fuint **同源同构**（`pages/` + `merchantPages/` + `uview-ui` + `uni.scss` + 同一套 `components/page/*` 装修组件）。因此这不是"从零抄"，而是**把我们已有的 fuint 底座对齐到 fuint v4.2.0 的最新实践**——改造成本很低。

---

## 1. 竞品技术栈与主题机制

| 项 | 值 |
|---|---|
| 框架 | uni-app（Vue 2）+ uView 1.x + mescroll-uni（上拉/下拉） |
| 首页形态 | **后台 DIY 装修页**：`banner / blank / navBar / image / video / notice / richText / article / goods / coupon` 模块按序渲染，样式由 `itemStyle` 下发 |
| 主题 | **运行时 CSS 变量**，`utils/theme.js` 注入 `document.documentElement.style`：<br>`--theme-primary` `--theme-secondary` `--theme-text` `--theme-bg` `--theme-price` `--fuint-theme`<br>兜底值：`primary:#ffffff`、`secondary:#e0f4f4`、`text:#333333`、`bg:#f5f5f5`、`price:#fa5151`；实际由后台 `/theme` 接口按商户下发（演示商户为青绿） |
| 编译期变量 | `uni.scss` → `$fuint-theme: #00acac` |
| 图表 | **无第三方图表库**（未发现 echarts / uCharts / qiun-data-charts / F2 依赖），柱状图与折线图为 **纯 view + CSS 手写** |

---

## 2. 取色规格（Design Token）

### 2.1 主色与语义色（实测）

| Token | 色值 | 用途 | 来源 |
|---|---|---|---|
| 品牌主色 | **`#00acac`**（青绿） | 门店条/搜索区底、按钮、强调边框 | `uni.scss $fuint-theme`（实测）+ 线上 `--fuint-theme` 下发值 |
| 主色浅版 | `#e0f4f4` | 主色 6% 辅助底/描边 | `--theme-secondary` 兜底 |
| 价格红 | **`#fa5151`**（`--theme-price`）/ 旧版硬编码 `#f03c3c` | 商品价格、统计数值、资产数值 | 实测 |
| 促销橙 | `#e49a3d` | 商品卖点文案 | 实测 |
| 服务图标橙 | `#ff3800` | 「我的服务 / 我的管理」宫格图标 | 实测 |
| 角标红 | `#fa5151`（会员端）/ `#fa2209`（商户端订单角标） | 数字徽标 | 实测 |
| 定位图标红 | `#f03c3c` | 门店条地址前的定位钉 | 实测（**我们当前误改为 #ffffff**） |
| 会员等级标签 | 底 `#3c3c3c` / 字 `#eee0c3` | 「普通会员」标签 | 实测 |
| 金色（会员等级卡） | 价格 `#E3BE83`、选中底 `#FBF1E5`、选中边 `#EDD2A9` | 会员升级价格卡 | 实测 |

### 2.2 文字色阶

| 层级 | 色值 | 场景 |
|---|---|---|
| 主标题 | `#333333` | 资产数值、卡片主数值 |
| 正文/商品名 | `#484848` | 商品名称（30rpx/700） |
| 常规标签 | `#545454` | 宫格文字、订单入口文字 |
| 次要标签 | `#666666` | 资产三宫格标签 |
| 辅助/占位 | `#999999` | 划线价、销量、副说明 |
| 弱辅助 | `#A5A3A2` | 会员卡权益说明 |
| 反色 | `#ffffff` | 头部卡片内文字 |

### 2.3 背景与描边

| 用途 | 色值 |
|---|---|
| 页面底 | `#fafafa`（`app.scss page`）/ 商品区底 `#F6F6F6`、线上 `.goods-item` 底 `#f5f5f5` |
| 卡片底 | `#ffffff`（资产卡特殊：`linear-gradient(180deg,#fff,#fafbfc)`） |
| 描边 | `#f5f5f5`（列表卡）、`#e6e6e6`（装修模块外框）、`#e5e5e5`（宫格内卡）、`#f0f0f0`（分隔线）、`#eeeeee` |
| 商品搜索框底 | `#f5f5f5`（胶囊内填充）、外描边 `#ffffff` |

---

## 3. 尺寸栅格与字号层级

### 3.1 间距栅格（rpx）

- 页面左右安全边距：**20rpx**（列表/商户端）/ **25rpx**（会员中心卡片）/ **24rpx**（我们的 `bahar-card` 工具类）
- 卡片外间距：**10rpx**（会员中心纵向）/ **20rpx**（商户端）/ **25rpx**（首页装修模块）
- 卡片内间距：16rpx / 20rpx / 24rpx / 30rpx（会员卡）/ 36rpx（资产卡纵向）
- 元素级间距：4rpx / 6rpx / 8rpx / 10rpx / 12rpx / 15rpx / 16rpx / 20rpx / 30rpx

### 3.2 圆角与阴影

| 对象 | 圆角 | 阴影 |
|---|---|---|
| 装修模块外框（四宫格/券区） | **20rpx** | 无（用 1rpx 边框） |
| 资产卡（会员端） | **16rpx** | `0 2rpx 12rpx rgba(0,0,0,.04), 0 0 0 1rpx rgba(0,172,172,.06)` |
| 宫格内卡 | **12rpx** | 无（渐变 `#fff→#f5f5f5` + `1rpx solid #e5e5e5`） |
| 通用列表卡（订单/服务/统计） | **10rpx** | `0 1rpx 5rpx 0 rgba(0,0,0,.05)` |
| 商品图（单列） | **10rpx**；双列图 **40rpx**、卡 **16rpx** | — |
| 搜索框 | **100rpx**（全胶囊） | — |
| 按钮/券按钮 | 5rpx（去购买）/ 26rpx（领券）/ 999rpx（胶囊） | — |

### 3.3 字号层级（rpx）

| 级别 | 字号 | 示例 |
|---|---|---|
| 特大数值 | **58rpx** | 商户端「今日交易金额」 |
| 一级数值 | **48rpx** | 会员余额、会员升级价格 |
| 二级数值 | **42rpx** | 资产卡数值（优惠券/储值卡/计次卡） |
| 三级数值 | **40rpx**（券面额）/ **36rpx**（商户统计）/ **34rpx**（双列商品价格）/ **33rpx**（单列价格） | |
| 区块标题 | **30rpx**（数据概况/运营走势）/ **28rpx**（我的服务、我的管理、会员升级） | |
| 一级文字 | **32rpx**（店名、会员昵称） | |
| 正文 | **26rpx**（商品名双列）/ **30rpx**（商品名单列，700） | |
| 辅助 | **24rpx**（标签、卖点、销量）/ **22rpx**（副说明、券范围）/ **20rpx**（最小标签、tabbar） | |

---

## 4. 逐页组件规格（★ = 我们 P0 必须改）

### 4.1 ★ 会员端首页（线上真实模块顺序）

```
[.index-sticky-header]            ← 整块 sticky 吸顶（★P0 新增）
   ├─ Location  门店条：店名 [切换店铺] / 📍地址
   └─ Search    搜索胶囊：请输入搜索关键字...
Banner        通栏焦点图（圆角 10rpx，左右 20rpx，指示点）
NavBar        四宫格（rowsNum=4）买单支付/领券中心/积分兑换/邀请有礼
Coupon        优惠券区（¥100 无门槛 指定商品可用 [立即领取]）
Goods         「热门商品」区块标题 + 商品列表（单列左图右文 + 去购买）
Tabbar        首页 / 微店 / 订单 / 我的
```

#### ★4.1.1 吸顶容器（本次最关键的修复，竞品 v4.2.0 已解决）

竞品线上注释原文（已转述，不引用源码）：
> 「默认布局：门店信息 + 搜索框作为一个整体吸顶固定」
> 「搜索组件内部默认是 fixed 定位，默认布局中由上面 sticky 容器负责吸顶，这里改回文档流，**否则其不占位会遮挡下方的焦点图**」

**目标规格（自研重写）**：
```css
.index-sticky-header { position: -webkit-sticky; position: sticky; top: 0; z-index: 100; }
.index-sticky-header .search-wrapper { position: static; }   /* 取消子组件自身的 fixed */
```
同时：**删除** `.diy-banner { margin-top: 100rpx; /*H5*/ margin-top: 120rpx; }` 这层旧补偿（sticky 后元素已占位，再留 margin 会空出一大块）。

> 我们当前的 bug 机理已定位：`pages/index/index.vue` 在 `Location` **之前**插入了 `.bahar-gradient-header`（「商城首页」装饰头，padding `36rpx 30rpx 64rpx`），而 `Location`/`Search` 仍是 `position:fixed` 且**未设 `top`**——fixed 未设 top 时按"静态位置"定位，被装饰头整体下移；Banner 的 120rpx 补偿是按"无装饰头"算的，于是顶部两条与内容错位、随滚动"跑"。

#### ★4.1.2 门店条 `.main-loc`（实测）

| 项 | 竞品 v4.2.0 | 我们现状 |
|---|---|---|
| 定位 | 随 sticky 容器（**不再 fixed**） | `position:fixed; z-index:99999`（★待改） |
| 底色 | `linear-gradient(180deg, var(--fuint-theme,#fff), var(--fuint-theme,#fff))` | 同（`$bahar-theme`） |
| padding | `3rpx 20rpx 16rpx 20rpx` | `3rpx 10rpx 10rpx`（H5 padding-top 15rpx） |
| 店名 | 32rpx / 700 / `#fff` | 同 |
| [切换店铺] | 22rpx / `#fff` / margin-left 15rpx | 同 |
| 地址 | 23rpx / `#fff` / `display:block` / margin-top 2rpx | 同 |
| 定位图标 | **24rpx / `#f03c3c` / 700** | **`#ffffff`**（★待改回红色） |

交互：整条点击 → `pages/location/index` 切换店铺。

#### ★4.1.3 搜索框（实测）

```
.search-wrapper : padding 0 10rpx 10rpx; background:#fff   （不再 fixed、不再加卡片样式）
.index-search   : height 82rpx; line-height 82rpx; background:#f5f5f5;
                  border-radius:100rpx; border:2rpx solid #fff; font-size:28rpx; color:#6d6d6d; margin-top:10rpx
搜索图标        : 30rpx / 700 / float left
占位文案        : "请输入搜索关键字..."（28rpx，居中，padding-left 30rpx）
```
交互：**点击跳转** `pages/search/index`（首页不做输入）。

> 我们现状：`.search-wrapper` 被加了 `bahar-card`（`margin:24rpx` + `padding:24rpx` + `radius:16rpx` + 阴影），而自身 `width:100%` → **100% 宽 + 左右 24rpx margin 超出视口 = 左右不对称**，且与门店条留白体系不一致。★ 去掉 `bahar-card`。

#### 4.1.4 四宫格 `.diy-navBar`（v4.2.0 已重写，★ 我们落后一代）

| 项 | 竞品 v4.2.0 | 我们现状（fuint 2024 版） |
|---|---|---|
| 布局 | `display:flex; flex-wrap:wrap`，**不再依赖 `avg-sm-N`** | `float:left` + `avg-sm-N`（★待改） |
| 容器 | `margin:24rpx; padding:6rpx; background:#fff; border:1rpx solid #e6e6e6; border-radius:20rpx` | 无外框 |
| 容器 margin 落地值 | **24rpx**（≠ 竞品的 20rpx，见下方说明） | — |
| 格子 | `.item-nav{padding:10rpx}`，宽度 = `100/rowsNum %` | `margin:10rpx 0 4rpx` |
| 内卡（layout-card） | `flex-direction:row; padding:20rpx; min-height:120rpx; border-radius:12rpx;`<br>`background:linear-gradient(180deg,#fff,#f5f5f5); border:1rpx solid #e5e5e5` | `height:150rpx; radius:20rpx; border:1rpx solid #ccc; padding:38rpx 10rpx 10rpx` |
| 内卡（icon-top） | `flex-direction:column; min-height:140rpx; padding:16rpx 8rpx; radius:12rpx` | — |
| 图标 | card `72rpx`（margin-right 16rpx）/ top `80rpx`（margin-bottom 10rpx） | 88rpx 容器 / 80rpx 图 |
| 主标题 `.text` | **24rpx**，单行省略 | 32rpx |
| 副标题 `.tip` | **20rpx**，`opacity:.8`，margin-top 4rpx | 22rpx `#999` |
| rowsNum 默认 | **4**（后台下发） | 2（首页 options.navStyle） |

线上四宫格文案（可直接作为我们的默认数据）：
`买单支付/支付攒积分`、`领券中心/领券更优惠`、`积分兑换/纯积分换好礼`、`邀请有礼/好礼相送`。
交互：整格点击 → 各自 url。

> **落地修正（2026-10-09）：容器 margin 取 24rpx，不取竞品的 20rpx。**
> 依据：我们首页同屏的优惠券卡 / 商品卡走全局 `.bahar-card{margin:24rpx}`，
> 四宫格若跟 20rpx 会比它们各外扩 2px，左边缘错开 —— 而"左右不对齐"正是用户报的原始缺陷之一。
> QA 复测（375 / 414 / 320 三视口）：24rpx 下搜索框 wrapper、四宫格、优惠券卡、商品卡四类区块
> 边缘逐像素重合（375 `12~363`、414 `13~401`、320 `10~310`）；回 20rpx 则四宫格退化为
> `10~365`(375) / `11~403`(414)，判定为回归。故**以我们自己的规矩为准，此处更正规格**。
>
> **状态：已采纳并锁定（2026-10-09 用户拍板），不要再回滚到 20rpx。**
> 四套会员端（零售 / 汽车 / 餐饮 / 康养）的装修模块外框统一 24rpx：
> 零售、康养走 `components/page/navBar`；汽车、餐饮首页用的是各自的 `HomeNav`，
> 原内层 `margin:0 10rpx 25rpx`（比 `.bahar-card` 窄 14rpx）已一并去掉，改由外层卡片统一给边距。

#### 4.1.5 优惠券区 `.diy-coupon`（我们有组件但未在首页用，P1）

```
.diy-coupon   : margin 0 20rpx 20rpx; padding 20rpx 16rpx; border 1rpx solid #e6e6e6; radius 20rpx
.coupon-card  : width calc(50% - 12rpx); margin 6rpx; padding 20rpx; min-height 160rpx;
                flex 左右分布（左：面额/门槛/范围，右：按钮）；左右各一个 24rpx 圆形缺口（coupon-notch）
面额 40rpx/700 ｜ 门槛 24rpx ｜ 范围 20rpx(opacity .75)
按钮          : height 48rpx; line-height 48rpx; padding 0 22rpx; radius 26rpx; font 22rpx
```

#### ★4.1.6 商品列表（形态差异最大）

竞品线上按 `showType==="1"` → **column=1（单列左图右文）**；我们是 `column=2`（两列网格）。

```
【单列 column__1】
.goods-item      : width 100%; height 250rpx; margin-bottom 10rpx; padding 20rpx; background #fff
左图 ._left      : width 40%; image 220rpx × 200rpx; radius 10rpx
右文 ._right     : width 60%
  名称           : 30rpx / 700 / #484848 / max-height 69rpx / 2 行截断
  卖点           : 24rpx / #e49a3d
  销量           : 24rpx / #999（"已售 N 件"）
  价格 .price_x  : 33rpx / 700 / var(--theme-price,#fa5151)；划线价 line-through
  「去购买」      : float right; margin-right 20rpx; padding 8rpx 20rpx; radius 5rpx;
                   background var(--theme-primary); color #fff
【区块标题】.goods-container .recommend .txt : border-left: solid var(--fuint-theme) 10rpx; padding-left: 10rpx
                   （即"热门商品"前面那个主色竖条）

【双列 column__2】（我们当前形态，保留给分类页）
item 50%；图 1:1；.detail height 180rpx / radius 16rpx；名称 26rpx；价格 34rpx
```

> 好消息：`components/page/goods/index.vue` **已内置** `column__1` 布局与 `.buy-now`（去购买）按钮。首页只需把 `options.goodsStyle.column` 由 `2` 改为 `1`，并补「热门商品」标题条。

#### 4.1.7 Tabbar（H5 自绘）
`.h5-tabbar__item` flex:1；图标 40rpx；文字 20rpx；选中换 `selectedIcon` + 主色。我们保持现状即可。

---

### 4.2 会员中心（pages/user/index.vue，v4.2.0 实测）

```
main-header   会员卡（主色底，height 280rpx，radius 10rpx，margin 20rpx 25rpx）
              ├ 头像 100rpx（圆形 999rpx）
              ├ 昵称 32rpx/700/#fff ｜ 「普通会员」标签（#3c3c3c 底 + #eee0c3 字，height 40rpx，radius 10rpx）
              ├ 右上 二维码 icon 40rpx（absolute top/right 20rpx）
              └ 底部 absolute（left/right/bottom 20rpx）：会员号 + 「储值有礼」
asset-card    资产卡（优惠券 / 储值卡 / 计次卡）★ 渐变白卡 + 分隔线
member-update 会员升级：三张并排价格卡（银牌/金牌/钻牌）
order-navbar  订单入口三宫格（全部订单 / 待支付 / 已支付）
my-service    「我的服务」宫格（25% 宽 = 4 列；线上支持 33.33%/20% 变体）
```

关键数值：
- **会员卡**：`background: var(--theme-primary); height:280rpx; padding:30rpx 20rpx 20rpx; margin:20rpx 25rpx; border-radius:10rpx; display:flex; flex-direction:column; justify-content:center`
- **资产卡**（v4.2.0 新增，我们可升级）：`margin:10rpx 25rpx; background:linear-gradient(180deg,#fff,#fafbfc); border-radius:16rpx; border:1rpx solid rgba(0,0,0,.04); box-shadow:0 2rpx 12rpx rgba(0,0,0,.04), 0 0 0 1rpx rgba(0,172,172,.06); padding:36rpx 0`；每项 flex:1，图标 64rpx（iconfont 50rpx），数值 **42rpx/700/#333**，标签 **22rpx/#999**，中间分隔线 `2rpx × 60rpx #f0f0f0`
- **会员升级价格卡**：`width:29.33%; height:270rpx; padding:40rpx 0; margin-left:15rpx; border:1rpx solid #CBCCCE; border-radius:12rpx`；选中态 `border:2rpx solid #EDD2A9; background:#FBF1E5`；名称 26rpx `#1C1C1C`；价格 **48rpx `#E3BE83`**；权益说明 22rpx `#A5A3A2`；左上角有效期角标 170rpx×36rpx（20rpx 白字）
- **订单入口**：`margin:10rpx 25rpx; padding:20rpx 0; radius:10rpx; background:#fff; border:2rpx solid #f5f5f5`；item 33%；图标 48rpx `#545454`；文字 24rpx `#545454`；角标 `#fa5151` 20rpx
- **我的服务**：`margin:10rpx 25rpx; radius:10rpx; background:#fff`；标题 28rpx（padding-left 20rpx）；item 25%（`service-col-3`→33.33%、`service-col-5`→20%）；图标 40rpx `#ff3800`；文字 24rpx `#545454`

---

### 4.3 商户端首页（merchantPages/index.vue，v4.2.0 实测）

```
main-header  主色卡（商家名 + 姓名 / 今日交易金额（元）864.90）
             └ quick-actions：核销卡券（扫码卡券二维码核销）/ 扫码收款（扫会员二维码收款）
my-asset     三宫格统计：总会员 14086 / 今日活跃 5 / 今日订单 3（数值红 36rpx）
order-navbar 三宫格快捷：核销订单 / 售后审核 / 预约管理（带数字角标）
my-service   「我的管理」宫格：会员登记、会员查找、卡券管理、商品管理、商品分类、
             订单管理、报表数据、售后订单、商家设置、员工管理（+积分设置/充值设置/库存盘点）
tabbar
```

关键数值：
- **主色卡**：`background: var(--fuint-theme,#fff); padding:10rpx 10rpx 30rpx 10rpx; margin:20rpx; border-radius:12rpx`
- **交易金额**：tip 28rpx；数值 **58rpx / 700**
- **快捷按钮**：`.quick-actions{display:flex; margin-top:30rpx; padding-bottom:10rpx}`，item flex:1；圆底 **96rpx**（`background: var(--theme-primary)`）；图标 52rpx，用 `filter: brightness(0) invert(1)` **把任意图标转纯白**；标题 **28rpx/600/#fff**；副说明 **22rpx / `rgba(255,255,255,.65)`**（"扫码卡券二维码核销"/"扫会员二维码收款"）——**副说明是我们可补的差异化细节**
- **统计三宫格**：`padding:40rpx 0; radius:10rpx; margin:25rpx 20rpx 5rpx 20rpx; background:#fff`；item `width:33.33%; padding:4px 72rpx`；数值 **36rpx / `#f03c3c` / 700**；标签 24rpx `#666`
- **快捷三宫格**：`width:94%; margin:20rpx auto; padding:20rpx 0; radius:10rpx; background:#fff`；item 33.33%；图标 40rpx；角标 `#fa2209` 22rpx
- **我的管理**：`width:94%; margin:10rpx auto; padding:20rpx 0; radius:10rpx; background:#fff`；标题 28rpx；item **25%（4 列 × N 行）**；图标 40rpx `#ff3800`；文字 24rpx `#545454`

> 结论：**我们的商户端首页已与竞品基本一致**（`quick-actions`/`q-title`/`q-desc`/三宫格统计/我的管理齐全），只需补齐快捷按钮的**副说明文案**与对齐数值。

---

### 4.4 数据统计页（merchantPages/data/index.vue）

```
time-filter   店铺 picker「全部店铺 ▾」+ 时间 tab（今天/昨天/近3天/近7天/近15天/近30天，选中态主色）
数据概况      2 列 × 4 行 = 8 个指标格
              订单数 / 交易金额 / 新增会员数 / 活跃会员数 / 总会员数 / 总支付金额 / 总订单数 / 总支付人数
              每格 = 左侧彩色圆角方图标 + 数值（红）+ 灰色标签
运营走势      近七日订单数量（柱状图，红色柱 + 数值标签）
              近七日会员活跃数（柱状/折线）
数据排行      商品销售排行 / 用户消费排行（表头 + 行）
```

**图表实现判定（重要）**：竞品**没有使用任何图表库**。线上 chunk 中 `echarts/uCharts/qiun/canvas` 命中数为 **0**，全部为手写 DOM：
`chart-container / chart-box / chart-title / chart-y-axis / y-label / chart-content / grid-lines / bars-wrapper / bar-wrapper / bar-column / bar-value / bar-label / x-labels / x-label / line-chart / line-wrapper / dot-point / dot-value / chart-legend / legend-text`。
→ 我们的实现路线（纯 CSS 柱状/折线）**与竞品一致，无需引入 uCharts**，可省一个依赖、避免跨端兼容问题。

---

## 5. 差距清单（现状 → 目标）

### P0（必须改，影响可用性与"像不像"）

| # | 现状 | 目标 | 落点 |
|---|---|---|---|
| **P0-1** | 首页在 `Location` 前插入 `.bahar-gradient-header`「商城首页」装饰头；`Location`/`Search` 仍 `position:fixed` 且无 `top`，被装饰头下移；`Banner` 仍留 `margin-top:120rpx` 旧补偿 → **顶部条跑位、遮挡焦点图** | ①删首页装饰头（或移入导航区）；②新增 `.index-sticky-header` 包裹 Location+Search，`position:sticky;top:0;z-index:100`；③`.index-sticky-header .search-wrapper{position:static}`；④删除 Banner `margin-top:100/120rpx` | `pages/index/index.vue`、`components/page/banner/index.vue`、`App.vue` |
| **P0-2** | `.search-wrapper` 被加 `bahar-card`（margin 24rpx + padding 24rpx + 阴影），自身 `width:100%` → **左右溢出、左右不对称** | 去掉 `bahar-card`；改 `padding:0 10rpx 10rpx; background:#fff`；`.index-search{height:82rpx; line-height:82rpx; background:#f5f5f5; border-radius:100rpx}` | `components/search/index.vue` |
| **P0-3** | 首页 `goodsStyle.column = 2`（两列网格），无区块标题 | `column: 1`（单列左图右文：图 220×200 / 名称 30rpx / 卖点橙 24rpx / 销量灰 / 价格红 33rpx / 主色「去购买」），并补「热门商品」主色竖条标题 | `pages/index/index.vue` options + `components/page/goods/index.vue` |
| **P0-4** | 门店条定位图标 `#ffffff`，与白字混在一起，指向性弱 | 改回 `#f03c3c`（24rpx/700） | `components/page/location/index.vue` |

### P1（应该改，明显提升质感与一致性）

| # | 现状 → 目标 | 落点 |
|---|---|---|
| P1-1 | 四宫格仍用 `avg-sm-N` + float，内卡 150rpx/`#ccc` 边/图标 88rpx/主标题 32rpx → 改 flex-wrap + `layout-card`：容器 `radius:20rpx + 1rpx #e6e6e6`、内卡 `min-height:120rpx; radius:12rpx; 渐变 #fff→#f5f5f5; 1rpx #e5e5e5`、图标 72rpx、主标题 24rpx、副标题 20rpx(opacity .8)、`rowsNum` 默认 4 | `components/page/navBar/index.vue`、`pages/index/index.vue` |
| P1-2 | 首页缺优惠券领取区 → 接入已有的 `components/page/coupon/index.vue`，两列券卡 + 24rpx 半圆缺口 + 「立即领取」胶囊按钮（48rpx 高 / radius 26rpx） | `pages/index/index.vue` |
| P1-3 | 门店条 padding `3rpx 10rpx 10rpx` → `3rpx 20rpx 16rpx 20rpx`，与搜索框 10rpx 外距形成统一左右留白 | `components/page/location/index.vue` |
| P1-4 | 主色硬编码 `$bahar-theme:#00acac` → 引入 `--bahar-theme / --bahar-theme-secondary(#e0f4f4) / --bahar-text(#333) / --bahar-bg(#f5f5f5) / --bahar-price(#fa5151)` CSS 变量，为四行业换肤预留（零售青绿/汽车蓝/餐饮橙/康养绿） | `uni.scss` + `App.vue` + 主题注入 util |
| P1-5 | 会员端资产三宫格（`.my-asset`，红字 + 灰边）→ 升级为 `asset-card`：渐变白卡、`radius:16rpx`、主色 6% 描边阴影、图标 64rpx、数值 42rpx `#333`、标签 22rpx `#999`、2rpx 分隔线 | `pages/user/index.vue` |
| P1-6 | 商户端快捷按钮缺副说明 → 补 22rpx `rgba(255,255,255,.65)` 文案（"扫码卡券二维码核销"/"扫会员二维码收款"） | `merchantPages/index.vue` |

### P2（锦上添花）

| # | 内容 |
|---|---|
| P2-1 | 会员升级卡对齐金色体系（价格 48rpx `#E3BE83`、选中 `#FBF1E5` + `#EDD2A9`、角标 170×36rpx） |
| P2-2 | 「我的服务 / 我的管理」宫格支持列数变体（25% / 33.33% / 20%），按服务项数量自适应 |
| P2-3 | 数据统计页卡片圆角/阴影统一为 `radius:10rpx + 0 1rpx 5rpx rgba(0,0,0,.05)`，数值色统一到 `--bahar-price` |
| P2-4 | 首页 DIY 化：模块顺序与 `itemStyle` 由后台下发（banner/blank/navBar/coupon/goods 可编排），对齐竞品 v4.2.0 架构 |
| P2-5 | 商户端「我的管理」补齐积分设置 / 充值设置 / 库存盘点 / 分类页模板等入口 |

---

## 6. 交互清单（对齐竞品）

| 元素 | 交互 |
|---|---|
| 门店条 | 点击 → `pages/location/index` 切换店铺 |
| 搜索框 | **只读跳转型**，点击 → `pages/search/index` |
| Banner | 点击 → 活动/商品链接；自动轮播（interval 2.5s，指示点圆角） |
| 四宫格 | 整格 → 各自 url（买单支付 / 领券中心 / 积分兑换 / 邀请有礼） |
| 优惠券 | 「立即领取」→ 领取；已领取态按钮置灰 `rgba(0,0,0,.1)` |
| 商品卡 | 整卡 → `pages/goods/detail`；「去购买」同跳转 |
| 商品列表 | mescroll 上拉分页（pageSize 10），下拉刷新 |
| 会员升级卡 | 点击 → 等级弹窗（权益说明 + 支付） |
| 订单入口 | 带待处理数量角标 |
| 商户快捷 | `uni.scanCode` → 核销卡券 / 扫码收款 |
| 时间筛选 | picker（店铺）+ tab（今天/昨天/近3/7/15/30 天），选中主色 |

---

## 7. 给架构/工程的落地建议

1. **本次改造集中在 3 个文件**：`pages/index/index.vue`（去装饰头 + 加 sticky 容器 + `column:1` + 接优惠券）、`components/search/index.vue`（去 `bahar-card`）、`components/page/navBar/index.vue`（换 flex 布局）。风险可控。
2. **四行业换肤**：借 P1-4 的 CSS 变量改造一次到位——零售 `#00acac`（青绿，与竞品一致）/ 汽车（深蓝）/ 餐饮（暖橙）/ 康养（柔和绿），只改变量不动组件。
3. **不要引入图表库**：竞品与我们都用纯 CSS 图表，保持零依赖。
4. **同步范围**：`baharUniapp` 改完后，需同步到 `baharCatering` 等同源工程（按既有同步流程）。
5. **验收口径**：① 首页滚动时门店条+搜索框整体吸顶不跑位；② 搜索框左右各 10rpx、与门店条同宽对齐；③ 商品区为单列左图右文 + 「去购买」；④ 四宫格四格等宽、主副标题层级清晰。

---

## 8. 版权合规

- fuint 会员端 uniapp 仓库（`zzy-awesome/fuintUniapp`）License：**Apache-2.0**；后端主仓库 `KC20191026/fuint` 同源。
- 但 fuint 官网明示：**「开源版本仅供学习和交流，商用必须购买授权，违者必究」**（v4.2.0）。
- **执行口径**：只采用布局顺序、数值、交互范式，以自研代码重写；**禁止**复制页面级源码文件、禁止搬运 `static/nav/*.png` 等素材图标。图标请使用我们自有图标库或通用 iconfont（竞品用的是 iconfont：`icon-sousuo / icon-dingwei / icon-qpdingdan / icon-daifukuan / icon-daishouhuo` 等，同类图标自行替换即可）。
