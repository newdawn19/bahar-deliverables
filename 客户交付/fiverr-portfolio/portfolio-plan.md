# Fiverr Portfolio 适配方案（bahar 四行业矩阵）

> 交付物：`portfolio-plan.md`
> 适用素材：`D:\git-double\bahar\deliverables\`
> 创作时间：2026-10-15
> 用户签名备注：____________________________

---

## 0. 阅读约定

- 字段文案以**英文为主**（Fiverr 主市场是英文买家），中文版本仅供用户择情使用/对照。
- 所有路径相对于 `D:\git-double\bahar\deliverables\`（下称 `deliverables/`）。
- 用法：本文件**只出方案**，不动任何源文件、不跑 git push、不上 Fiverr、不跑浏览器自动化。
- 合规硬底线：保留开源产品 bahar 作者署名；不贴项目源码截图；不宣称"自有产品"。

---

## A. 账号定位卡（Account Positioning）

### A.1 Account Title & One-liner（≤ 70 字符）

| 语言 | 文本 |
|---|---|
| EN | `Full-Stack Spring Boot & Vue Engineer | Multi-Industry SaaS & i18n` |
| ZH | `SpringBoot + Vue 全栈工程师｜多行业 SaaS 与中英双语落地` |

### A.2 Account Description（200–300 字，中英双语各一份）

**English（用于 Fiverr Account Bio 字段，建议长度 220–260 字）**

> I'm a full-stack engineer specializing in **Spring Boot + Vue.js** web and mobile-H5 systems, with hands-on experience reshaping and localizing open-source commerce products for **four industries (retail / automotive / catering / wellness/beauty)**. I deliver end-to-end across three fronts: **Admin (web backend), Member H5 (uni-app), and Electron Cashier (POS)** — all backed by a single multi-tenant Spring Boot service layer.
>
> My recent focus is **production-grade i18n (zh-CN / en-US)**: I refactored a 2,250-hardcoded-CN-message Java codebase into a "Chinese-as-key + t() gateway + miss-fallback-original" dual-track pattern with only ~11 exit points changed, zero impact on business logic. I've also rebuilt H5 homepages and dashboards to match industry-standard UX (sticky headers, single-column product lists, four-grid navigation, dynamic bar/line charts).
>
> I work strictly within license terms: when I customize an open-source base, I keep its copyright untouched, position the work as a **technical capability proof**, and never represent it as my own product.

**中文（中文版同字段，作为 Fiverr 中文子站或客户自留稿备用）**

> 我是 **Spring Boot + Vue.js** 全栈工程师，专长是把开源商业产品改造为可商用的**多行业（零售 / 汽车 / 餐饮 / 康养）SaaS**，并落地**中英双语（i18n）**。
> 三端一体：**Admin 后台（Web）+ 会员端 H5（uni-app）+ 收银端（Electron POS）**，全部跑在同源 Spring Boot 之上。
> 近期重点是把一个 **2250+ 处硬编码中文**的 Java 后端改造成「中文原文当 key + 出口统一包 `t()` + miss 兜底原文」的双轨制双语——**只需改约 11 个出口点，零业务侵入**；同时按行业重做了 H5 首页（吸顶头 / 单列商品 / 四宫格 / 动态柱折线）。
> **合规底线**：改造开源底座时保留原作者版权，定位为"技术能力证明"，不宣称自有产品。

---

## B. 10 个 Portfolio 项目拆分

> 下文 **P1 ~ P10** 即对应 Fiverr 上最多 10 个 Portfolio 位的最终落点。
> 每个项目含：Title（中/英，≤ 70 字符）、Category、Tags、Description（中/英，≤ 1000 字符）、图片清单（最多 5 张，每张给 caption 与是否可直接用）、底部 `Technologies:` 列表（仅供用户参考，不进 Fiverr 字段）。

---

### 项目 P1 — Multi-Industry Storefront · Member H5 Refactor (Retail)

| 项 | 内容 |
|---|---|
| **Title (EN)** | `Retail Industry H5: Sticky Header, Product List & Coupon (Vue2 + uni-app)` |
| **Title (ZH)** | `零售会员端 H5 改造：吸顶头+商品列表+优惠券（Vue2 + uni-app）` |
| **Category** | Programming & Tech → Website Development → Web Application |
| **Tags** | `vue.js`, `uni-app`, `mobile-h5`, `ecommerce`, `pwa` |
| **Cover 候选** | `h5-首页改版-零售.png`（主视觉：吸顶门店条+搜索+四宫格+商品） |
| **备用图** | `h5-首页改版-375.png`、`h5-首页改版-四宫格与优惠券.png`、`h5-首页改版-零售-goods.png`、`h5-首页实测截图.png`（before/after 对比） |

**Description (EN, ≈ 780 字符)**

> Rebuilt a uni-app member H5 for the retail vertical on top of an open-source Spring Boot base. Real fixes shipped:
>
> 1. **Sticky storefront header** — store bar + search capsule merged into one `position: sticky` container; eliminated the "search jumps while scrolling" bug caused by un-topped `position: fixed` inner elements.
> 2. **Single-column product list** with left-image/right-text cards and a primary-color "Buy now" pill; added "Hot items" section title with a left accent bar.
> 3. **Four-grid navigation** rewritten from float/avg-sm to flex-wrap, with a 20rpx-radius border container and gradient sub-cards.
> 4. **Coupon module** added to the home — two-column coupon cards with 24rpx notches and a "Claim" pill (radius 26rpx, height 48rpx).
> 5. **Empty-state & dynamic Y-axis** on the report page; removed hardcoded SVG that fails on WeChat Mini Program.
>
> All changes were synchronized across **four industry copies** (retail/auto/catering/wellness) via md5-aware diffing; CSS custom properties (`--bahar-theme`, `--bahar-price`) are used so each industry gets its own accent without touching components.
>
> Technologies: Vue 2, uni-app, uView UI 1.8, Mescroll, SCSS (rpx), CSS custom properties.

**Description (ZH, ≈ 720 字符)**

> 基于开源 Spring Boot 底座改造零售行业会员端 H5（uni-app），真实可点的修复点：
> 1. **吸顶头**：门店条+搜索胶囊合并到 `position: sticky` 容器，根治原"搜索框滚动跳位"的 bug（根因是子元素 `fixed` 但未声明 `top`）。
> 2. **单列商品**：左图右文卡片 + 主色「去购买」胶囊；补「热门商品」主色竖条标题。
> 3. **四宫格重写**：从 `float/avg-sm` 切到 `flex-wrap`，外框 20rpx 圆角 + 渐变内卡。
> 4. **首页新增优惠券区**：两列券卡 + 24rpx 半圆缺口 + 「立即领取」胶囊（48rpx 高）。
> 5. **报表页**：Y 轴动态化、去掉 SVG、兼容小程序。
> 改动按 md5 比对**同步到四套**（零售/汽车/餐饮/康养）；用 CSS 变量承载主题色，每个行业单独换皮而无需改组件。
> Technologies: Vue 2, uni-app, uView UI 1.8, Mescroll, SCSS (rpx), CSS Variables.

**图片清单（本项目，最多 5 张）**

| # | 路径 | 宽×高 | 体积 | Caption（≤ 150 字符） | 直接用 |
|---|---|---|---|---|---|
| 1 | `h5-首页改版-零售.png` | 750×1334 | 245.0KB | `Retail H5 — sticky header, four-grid nav, coupon module` | ✅ |
| 2 | `h5-首页改版-零售-goods.png` | 750×1334 | 167.4KB | `Single-column product list with primary-color "Buy now" pill` | ✅ |
| 3 | `h5-首页改版-四宫格与优惠券.png` | 750×1334 | 248.5KB | `Four-grid nav (flex-wrap) + coupon claim cards` | ✅ |
| 4 | `h5-首页改版-375.png` | 750×1334 | 253.7KB | `375-width mobile layout: header alignment fixed` | ✅ |
| 5 | `h5-首页实测截图.png` | 750×1334 | 243.9KB | `Before: original "search jumps" reproduction for context only` | ✅ |

---

### 项目 P2 — Cross-Industry H5 Shells × 4 (Retail / Auto / Catering / Wellness)

| 项 | 内容 |
|---|---|
| **Title (EN)** | `Same Spring Boot, Four Industry Skins: H5 Member App Comparison` |
| **Title (ZH)** | `同一套后端 × 四行业会员端换皮：零售/汽车/餐饮/康养对比` |
| **Category** | Programming & Tech → Website Development → Web Application |
| **Tags** | `multi-tenant`, `theming`, `vue.js`, `uni-app`, `saas` |
| **Cover 候选** | `h5-会员中心-零售.png` 或 `h5-首页改版-汽车.png`（行业辨识度高） |
| **备用图** | 4 张 `h5-首页改版-{零售/汽车/餐饮/康养}.png`（四行业首屏并陈） |

**Description (EN, ≈ 560 字符)**

> A side-by-side showcase of **four industry-flavored member H5s** running on the same Spring Boot backend — retail, automotive, catering, and wellness/beauty. Each vertical shares the same Java service layer but gets its own:
> - accent color via a single CSS custom property (`--bahar-theme`),
> - copy set in the front-end copy tab,
> - industry-specific product/service data.
>
> The image set shows the four homepages rendered side by side on a 375px viewport. Different themes (teal/navy/forest/wellness-purple) come from a single component tree — no per-industry forks, just runtime CSS variables. Synchronization across the four copies is enforced via md5 diffing on the shared files.
>
> Technologies: Vue 2, uni-app, SCSS, CSS custom properties, Spring Boot 2.x (shared).

**图片清单**

| # | 路径 | Caption | 直接用 |
|---|---|---|---|
| 1 | `h5-首页改版-零售.png` | `Retail — teal (#00acac) homepage` | ✅ |
| 2 | `h5-首页改版-汽车.png` | `Automotive — navy theme homepage` | ✅ |
| 3 | `h5-首页改版-餐饮.png` | `Catering — forest-green theme homepage` | ✅ |
| 4 | `h5-首页改版-康养.png` | `Wellness/Beauty — purple theme homepage` | ✅ |
| 5 | `h5-首页改版-餐饮-真实数据.png` | `Same components, real data per vertical (catering)` | ✅ |

---

### 项目 P3 — Merchant Console (H5): Dashboard & Merchant Ops

| 项 | 内容 |
|---|---|
| **Title (EN)** | `Merchant-Side H5 Console: Sales Dashboard, Coupons, Inventory & Reports` |
| **Title (ZH)** | `商户端 H5：商家管理 + 数据统计 + 卡券/库存/商品` |
| **Category** | Programming & Tech → Mobile App Development → Cross-platform Mobile |
| **Tags** | `dashboard`, `merchant`, `data-visualization`, `vue.js`, `uni-app` |
| **Cover 候选** | `客户交付/01-界面截图/会员端/18-数据统计.png`（真实跑出来的真实数据看板） |
| **备用图** | `h5-商户端-零售.png` 等 4 张；`h5-首页改版-零售-goods.png` |

**Description (EN, ≈ 520 字符)**

> Merchant-side mini-console delivered on top of the same uni-app runtimes, served to staff after they log in via the Member app. Included:
> - Today transaction, daily active members, today's orders overview,
> - Order list / Coupon claim & verify / Member registration / Inventory take-stock,
> - **Reports** — 8 metric cards (orders, GMV, new/active/total members, total orders, payers), 7-day bar chart, 7-day active-member line chart, top items and top consumers tables. Y-axis is computed dynamically from data (no more hardcoded scale), bar height normalizes to the actual max.
>
> Backend wires: `merchantApi/report/{overview,chart,top}` → `ReportServiceImpl` filtering on `mt_order.CREATE_TIME` and `PAY_STATUS='B'`. The demo data is kept fresh via a delta-shift SQL so "today" stays meaningful after deployment.
>
> Technologies: Vue 2, uni-app, hand-written CSS charts (bar+line, no chart lib), Spring Boot, MySQL, Redis.

**图片清单**

| # | 路径 | Caption | 直接用 |
|---|---|---|---|
| 1 | `客户交付/01-界面截图/会员端/18-数据统计.png` | `Live report page — 8 metrics + 7-day bar/line + top tables` | ✅ |
| 2 | `h5-商户端-零售.png` | `Merchant dashboard shell — retail` | ✅ |
| 3 | `h5-商户端-汽车.png` | `Merchant dashboard shell — automotive` | ✅ |
| 4 | `h5-商户端-餐饮.png` | `Merchant dashboard shell — catering` | ✅ |
| 5 | `h5-商户端-康养.png` | `Merchant dashboard shell — wellness` | ✅ |

---

### 项目 P4 — Admin Web: 21-Module Backoffice (Spring Boot + Vue2 + Element UI)

| 项 | 内容 |
|---|---|
| **Title (EN)** | `Admin Backoffice: 21 Modules — Members, Coupons, Orders, Stores & RBAC` |
| **Title (ZH)** | `后台 Admin：21 模块会员/卡券/订单/门店/RBAC 全套` |
| **Category** | Programming & Tech → Website Development → E-Commerce Development |
| **Tags** | `admin-panel`, `rbac`, `element-ui`, `vue.js`, `spring-boot` |

**Description (EN, ≈ 560 字符)**

> Web admin backoffice (Vue 2 + Element UI) served by Spring Boot's embedded container, covering 21 modules: login + dashboard + members + grades + groups + tags + product categories + products + inventory + coupons + coupon verify + orders + stores + staff + printers + merchant info + articles + banners + accounts + roles + operation log.
>
> Auth: `Access-Token` via `AdminUserInterceptor`, RBAC via `@PreAuthorize("@pms.hasPermission('…:edit')")`, all write operations auto-logged through an `TActionLogAop` aspect into `t_action_log`. Password storage uses SHA-256 + salt; SQL injection is blocked because **every** query goes through MyBatis-Plus `#{}` prepared parameters.
>
> The 21 images form a panoramic module tour suitable for sales decks. Source is rendered against real data, not design comps.
>
> Technologies: Vue 2.6, Vue Router, Element UI, Axios, Spring Boot 2.x, Spring MVC, MyBatis-Plus, Spring AOP, HikariCP, Lettuce (Redis), MySQL 8.

**图片清单**

| # | 路径 | Caption | 直接用 |
|---|---|---|---|
| 1 | `客户交付/01-界面截图/后台Admin/00-登录页.png` | `Login screen with Kaptcha captcha` | ✅ |
| 2 | `客户交付/01-界面截图/后台Admin/01-首页看板.png` | `Admin dashboard` | ✅ |
| 3 | `客户交付/01-界面截图/后台Admin/02-会员管理.png` | `Member management` | ✅ |
| 4 | `客户交付/01-界面截图/后台Admin/09-卡券管理.png` | `Coupon management` | ✅ |
| 5 | `客户交付/01-界面截图/后台Admin/11-订单管理.png` | `Order management` | ✅ |

> 备注：Fiverr 每个项目最多 5 张，其余 16 张可在买家私信里再贴（如须要全套巡览，建议单独再丢一张图册链接/PPT）。

---

### 项目 P5 — Electron Cashier (POS): Multi-Payment + Member Top-Up

| 项 | 内容 |
|---|---|
| **Title (EN)** | `Electron Cashier (POS): WeChat/Alipay/UnionPay + Member Top-Up & Verify` |
| **Title (ZH)** | `Electron 收银端 POS：微信/支付宝/银联收款 + 会员充值核销` |
| **Category** | Programming & Tech → Desktop App Development |
| **Tags** | `electron`, `pos`, `vue.js`, `element-ui`, `payments-integration` |

**Description (EN, ≈ 480 字符)**

> Electron-based POS desktop app (Vue 2 + Element UI + webpack 5), served today as a `build:web` pack in browser for demo. Tabs include login, cashier main screen with 44-item catalog, order list (98 historical orders), member list (60), member top-up (4 gift tiers × payment methods), coupon verify, system landing and about (`V3.0.9`).
>
> Payment routing goes through Spring Boot `PaymentService#createPrepayOrder` (WeChat JSAPI / micro-pay / H5, Alipay, UnionPay), callbacks handled at `/clientApi/pay/{weixinCallback,aliPayCallback}`; refunds flow through `RefundService#agreeRefund` and downstream Weixin/Alipay refund APIs.
>
> Technologies: Electron 22, Vue 2.7, Element UI 2.15, webpack 5, vue-i18n 8 (pre-wired for the next i18n phase).

**图片清单**

| # | 路径 | Caption | 直接用 |
|---|---|---|---|
| 1 | `客户交付/01-界面截图/收银端/01-收银主页.png` | `Cashier main — 44-item catalog + cart` | ✅ |
| 2 | `客户交付/01-界面截图/收银端/02-订单管理.png` | `Order list` | ✅ |
| 3 | `客户交付/01-界面截图/收银端/03-会员管理.png` | `Member list (60 in demo)` | ✅ |
| 4 | `客户交付/01-界面截图/收银端/04-会员充值.png` | `Member top-up — 4 gift tiers` | ✅ |
| 5 | `客户交付/01-界面截图/收银端/05-卡券核销.png` | `Coupon verify desk` | ✅ |

---

### 项目 P6 — Member H5 End-to-End (Single Vertical)

| 项 | 内容 |
|---|---|
| **Title (EN)** | `Member H5 End-to-End: Home → Product → Order → Wallet → Coupon → Share` |
| **Title (ZH)** | `会员端 H5 全链路：首页→商品→订单→余额→卡券→分销` |
| **Category** | Programming & Tech → Mobile App Development → Cross-platform Mobile |
| **Tags** | `uni-app`, `ecommerce`, `mobile-app`, `vue.js`, `wechat-miniprogram` |

**Description (EN, ≈ 460 字符)**

> A panoramic tour of the member-side H5: home (with store logo support), micro-store, product list, product detail, login, help center, merchant workspace, member dashboard, my coupons, my wallet, point ledger, my orders, distribution/affiliate center, shipping addresses, my member code, member management, order management, product management, coupon management — 20 screens rendered against the real Spring Boot backend.
>
> Two screens were added in the latest cycle: product-detail (after fixing a `fastjson2` JDK11 coders bug) and merchant-data dashboard (after seeding fresh demo orders via a delta-shift SQL so today's GMV reflects non-zero real data).
>
> Technologies: uni-app (Vue 2, HBuilderX), uView UI, Mescroll, Spring Boot 2.x, Redis, WeChat OAuth.

**图片清单**

| # | 路径 | Caption | 直接用 |
|---|---|---|---|
| 1 | `客户交付/01-界面截图/会员端/01-首页.png` | `Member home with store logo` | ✅ |
| 2 | `客户交付/01-界面截图/会员端/03-商品列表.png` | `Product list (grid)` | ✅ |
| 3 | `客户交付/01-界面截图/会员端/04-商品详情.png` | `Product detail (carousel + rich text)` | ✅ |
| 4 | `客户交付/01-界面截图/会员端/09-会员中心.png` | `Member dashboard` | ✅ |
| 5 | `客户交付/01-界面截图/会员端/10-我的卡券.png` | `My coupons` | ✅ |

---

### 项目 P7 — i18n Architecture (zh-CN ↔ en-US): Gateway Pattern

| 项 | 内容 |
|---|---|
| **Title (EN)** | `i18n Refactor: 2,250+ Hardcoded Messages → Dual-Track zh-CN / en-US` |
| **Title (ZH)** | `i18n 全栈改造：2250+ 硬编码中文 → 中英双轨制双语` |
| **Category** | Programming & Tech → Website Development → Localization |
| **Tags** | `i18n`, `localization`, `spring-boot`, `vue.js`, `java` |
| **Cover 候选** | `i18n-国际化方案.md` 不上图，但主图用一张改造后的双语对照截图——本项目没有现成双语截图，**改用方案截图替代**：放 `h5-首页改版-375.png` + Markdown 摘要图替代说明（见下方说明） |

> ⚠️ 本项目没有现成的"中英对照页"截图。设计上以文字 + 架构图（用 Markdown 内嵌 mermaid 或文档截图）为主；为凑齐 5 张图，**用 `i18n-国际化方案.md` 内嵌 mermaid 架构图作为 1-2 张"档案页"截图**（即把 mermaid 渲染后的 PNG 导出，或用文件本身做参考说明）即可。
>
> 实操建议：Fiverr 描述里**坦诚**说明："Project screenshots come from the live base system before/after the i18n wiring; architecture diagram is exported from the technical proposal." 然后用以下图：

| # | 路径 | Caption | 直接用 |
|---|---|---|---|
| 1 | `h5-首页改版-375.png` | `Base UI rebuilt to support language-aware copy` | ✅ |
| 2 | `h5-首页改版-四宫格与优惠券.png` | `Components rebuilt to read `$t()` indirection — zh-CN / en-US` | ✅ |
| 3 | `客户交付/01-界面截图/收银端/07-设置.png` | `Cashier already pre-wired with vue-i18n 8.27.1 (Element UI bilingual)` | ✅ |
| 4 | （建议额外导出的 mermaid 渲染 PNG） | `Architecture: Locale decision chain → I18nContext (TL) → 11 exit points` | ❓ 用户自行决定是否导 PNG |
| 5 | （同上） | `Coverage report: Top-100 messages cover ~70% of user touches` | ❓ |

**Description (EN, ≈ 920 字符)**

> **Problem.** The Spring Boot base shipped 2,250+ hardcoded Chinese strings across 700+ Java files (912× `getFailureResult(n,"中文")` + 1,340× `throw new XxxException("中文")`). The legacy `PropertiesUtil` was `static final`, loaded with `Locale.getDefault()` at boot, and the en-US YAML file was a Chinese duplicate — i.e. zero real bilingual capability.
>
> **Strategy** (avoid the 2,250-point rewrite):
> 1. **Chinese-original as key** — no large-scale key renaming. Each Chinese literal stays in code; the en-US YAML maps `"账号或密码有误": "Incorrect account or password"`.
> 2. **Miss → fall back to the original Chinese** — `t(x)` returns `x` if no entry. This guarantees **no empty text, ever**, and lets translation ship incrementally.
> 3. **Exit points only** — wrap exactly **11** places: 4 in `BaseController` (covering 912+ control calls + the legacy `PropertiesUtil` pathway) and 8 in `GlobalExceptionHandler` (covering 1,340 throw paths).
>
> **Locale decision chain** (priority high→low): `?lang=` URL param → `Accept-Language` header → user/merchant preference (Phase 2) → default `zh-CN`. Stored on a `ThreadLocal`; cleared on completion to defeat thread-pool cross-talk.
>
> **Database layer** — added `NAME_EN` columns to 7 hot-path tables (`mt_goods`, `mt_goods_cate`, `mt_coupon`, `mt_user_grade`, `mt_store`, `mt_banner`, `mt_article`); 409 demo rows translated. DTO assembly picks the localized column by Locale, defaulting to original if blank.
>
> **Front-end layers** — Member H5 bootstraps a self-contained `vue-i18n@8.x` (UMD) because the project is non-CLI/HBuilderX; Admin gets a 40-line zero-build `T()` with a flat ~455-key dictionary; Cashier already had `vue-i18n@8.27.1` wired in `main.js:54-59` and required only a copy migration.
>
> **Result** — flipping the language switches admin UI, member H5 hints, toasts, page titles and backend error messages, without touching business code. Top-100 translated strings cover ~70% of real user touches (a single key like "您没有操作权限" hits 13–15 call sites).
>
> Technologies: Spring Boot, Spring MVC interceptors, MessageSource-style YAML, Java `ThreadLocal`, MySQL 8 (utf8mb4), vue-i18n 8, uni-app, Element UI, Electron, Axios interceptors.

**Description (ZH, ≈ 850 字符)** —— 中文稿对照，描述同义，故不展开；重点是**承诺"开源底座改造、保留原作者版权"作为对外话术**。

---

### 项目 P8 — Stable, Secure Spring Boot Base (Architecture & Hardening)

| 项 | 内容 |
|---|---|
| **Title (EN)** | `Spring Boot Backbone: Stateless, RBAC, Audit Log & Production Hardening Notes` |
| **Title (ZH)** | `Spring Boot 底座：无状态可扩容 + RBAC + 审计 + 上线加固建议` |
| **Category** | Programming & Tech → Website Development → Back-End Development |
| **Tags** | `spring-boot`, `rbac`, `redis`, `mysql`, `production-hardening` |

**Description (EN, ≈ 740 字符)**

> The Spring Boot backbone serving all three fronts (Admin / H5 / Electron Cashier) — its architecture choices and the production-readiness notes I drafted for the customer.
>
> **Stability**
> - Spring Boot + embedded Jetty, single-jar deployments.
> - HikariCP connection pool, Lettuce Redis pool, Ehcache for hot-spot reads.
> - **Stateless** session via Redis `Access-Token` (TTL 7 d) → horizontally scalable behind Nginx.
> - **Per-industry isolation**: 4 ports (8081/8082/8083/8084), 4 MySQL schemas, 4 Redis DBs — one industry's outage won't poison the others.
>
> **Security**
> - Login captcha (Kaptcha), SMS verify-code with TTL & 2-min resend guard.
> - SHA-256 + salt password storage, MD5 legacy compatibility shim.
> - `Access-Token` interceptors for both `/clientApi/**` and `/backendApi/**`.
> - Method-level RBAC via `@PreAuthorize("@pms.hasPermission('…:edit')")`.
> - Dynamic CORS by request `Origin`.
> - MyBatis-Plus `#{}` everywhere — zero SQL string concat.
> - `TActionLogAop` auto-logs every critical write to `t_action_log` for audit.
>
> **Honesty notes** (what is *not* production by default and needs to be added before launch): HTTPS, WAF / IP whitelist, KMS-vaulted secrets, periodic password rotation, rate limiting on SMS/login/order endpoints, central logging + monitoring, demo-data scrub.
>
> Technologies: Spring Boot 2, Jetty, HikariCP, Redis, MyBatis-Plus, Spring AOP, Kaptcha, WeChat Pay V2/V3, Alipay, UnionPay.

**图片清单**

| # | 路径 | Caption | 直接用 |
|---|---|---|---|
| 1 | `客户交付/01-界面截图/后台Admin/20-操作日志.png` | `Operation audit log (TActionLogAop auto-captured)` | ✅ |
| 2 | `客户交付/01-界面截图/后台Admin/18-后台账号.png` | `Admin account list — RBAC subjects` | ✅ |
| 3 | `客户交付/01-界面截图/后台Admin/19-角色职务.png` | `Role & duty (RBAC matrix)` | ✅ |
| 4 | `客户交付/01-界面截图/后台Admin/13-员工管理.png` | `Staff / per-store / per-merchant scoping` | ✅ |
| 5 | `客户交付/01-界面截图/后台Admin/12-门店管理.png` | `Store management — multi-store isolation` | ✅ |

> 风险与提醒：**`04-稳定性与安全性说明.md`** 文中含「演示账号 `bahar/123456`」「演示万能验证码 `999999`」「演示用端口 `127.0.0.1`」等**绝密/演示口径**，Fiverr Description 里**只截前 8 行 + 标题**，不要整段贴进去——见 §E。

---

### 项目 P9 — Business Modules in One Board (24+ Screens Tour)

| 项 | 内容 |
|---|---|
| **Title (EN)** | `Multi-Module Tour: Coupons, Distribution/Commission, Member Grade & Print` |
| **Title (ZH)** | `多模块巡览：卡券/分销佣金/会员等级/打印设备/文章公告` |
| **Category** | Programming & Tech → Website Development → E-Commerce Development |
| **Tags** | `ecommerce`, `coupon-system`, `commission`, `membership`, `spring-boot` |

**Description (EN, ≈ 540 字符)**

> A second backoffice walkthrough focused on non-CRUD modules that drive daily store operation: coupon management, coupon verify desk (writes `mt_confirm_log`), inventory take-stock, members, member grade & tag, member group, member top-up, distribution/affiliate center (`mt_commission_relation`/`mt_commission_log` with `CommissionJob` every-minute batch), printers, articles & banners.
>
> Backend wiring, all top-down:
> - Coupon: `CouponService.sendCoupon` / `useCoupon`, `SendWayEnum` (backend / offline / front) — image shows the verify desk that drains balance / counts and writes the log.
> - Distribution: `CommissionJob` → `CommissionLogService.calculateCommission` → `CommissionCashService.withdraw`.
> - Printers: per-store printer bindings; verify desk reuses the printer binding.
>
> Technologies: Spring Boot, MyBatis-Plus, MySQL, Redis, Element UI, uni-app H5 (distribution center).

**图片清单**

| # | 路径 | Caption | 直接用 |
|---|---|---|---|
| 1 | `客户交付/01-界面截图/后台Admin/10-卡券核销.png` | `Coupon verify desk — drains `mt_confirm_log`` | ✅ |
| 2 | `客户交付/01-界面截图/后台Admin/09-卡券管理.png` | `Coupon management` | ✅ |
| 3 | `客户交付/01-界面截图/后台Admin/08-库存管理.png` | `Inventory take-stock` | ✅ |
| 4 | `客户交付/01-界面截图/后台Admin/03-会员等级.png` | `Member grade ladder` | ✅ |
| 5 | `客户交付/01-界面截图/后台Admin/14-打印设备.png` | `Per-store printer bindings` | ✅ |

---

### 项目 P10 — Cross-Vertical Member Dashboard Comparison

| 项 | 内容 |
|---|---|
| **Title (EN)** | `Member Dashboard Across 4 Verticals: Retail / Auto / Catering / Wellness` |
| **Title (ZH)** | `四行业会员中心对比：零售/汽车/餐饮/康养` |
| **Category** | Programming & Tech → Mobile App Development → Cross-platform Mobile |
| **Tags** | `mobile-app`, `vue.js`, `uni-app`, `loyalty`, `multi-vertical` |

**Description (EN, ≈ 360 字符)**

> Four member dashboards sitting on the same Spring Boot base with different themes and loyalty logic:
> - **Retail** — points/coupons/stored-value/time-card focus;
> - **Automotive** — service booking + maintenance time-card emphasis;
> - **Catering** — dine-in card pack, scan-to-order;
> - **Wellness/Beauty** — booking, package times card, beautician assigned.
>
> Each dashboard features: hero card (avatar + grade + member code + balance/points), "My assets" three-up, "My orders" three-up, "My services / My management" grid.
>
> Technologies: Vue 2, uni-app, SCSS (rpx), theming via CSS custom properties, Spring Boot 2.x.

**图片清单**

| # | 路径 | Caption | 直接用 |
|---|---|---|---|
| 1 | `h5-会员中心-零售.png` | `Retail member dashboard (teal)` | ✅ |
| 2 | `h5-会员中心-汽车.png` | `Automotive member dashboard (navy)` | ✅ |
| 3 | `h5-会员中心-餐饮.png` | `Catering member dashboard (forest)` | ✅ |
| 4 | `h5-会员中心-康养.png` | `Wellness member dashboard (purple)` | ✅ |
| 5 | `客户交付/01-界面截图/会员端/09-会员中心.png` | `Reference: production-style member dashboard with real data` | ✅ |

---

### 项目分配后的素材去向汇总（每张图都被指派或显式说明不入选）

| 路径 | 被分配到 | 备注 |
|---|---|---|
| `h5-首页实测截图.png` | P1 | "before"对照图 |
| `h5-首页改版-375.png` | P1 + P7 | P7 用作"前置改造基线" |
| `h5-首页改版-375-goods.png` | （备用） | 5 张已满 |
| `h5-首页改版-四宫格与优惠券.png` | P1 + P7 | P7 用作"组件 `$t()` 化"上下文 |
| `h5-首页改版-{零售/汽车/餐饮/康养}.png` | P2 (4 张) | 四行业首屏对比 |
| `h5-首页改版-{零售/汽车/餐饮/康养}-goods.png` | P1 / 备用 | P1 用了零售-goods，其余留作对外私信备用 |
| `h5-首页改版-餐饮-真实数据.png` | P2 | "真实数据"差异化展示 |
| `h5-首页改版-餐饮-真实数据-goods.png` | （未入选） | 5 张已满；保留作私信备用 |
| `h5-商户端-{零售/汽车/餐饮/康养}.png` | P3 (4 张) | 商户端四行业并陈 |
| `h5-会员中心-{零售/汽车/餐饮/康养}.png` | P10 (4 张) | 会员端四行业并陈 |
| `客户交付/01-界面截图/后台Admin/00-登录页.png` | P4 | 登录入口 |
| `客户交付/01-界面截图/后台Admin/01-首页看板.png` | P4 | 仪表盘 |
| `客户交付/01-界面截图/后台Admin/02-会员管理.png` | P4 | 会员列表 |
| `客户交付/01-界面截图/后台Admin/03-会员等级.png` | P9 | 等级阶梯 |
| `客户交付/01-界面截图/后台Admin/04-会员分组.png` | （未入选） | 留私信备用 |
| `客户交付/01-界面截图/后台Admin/05-会员标签.png` | （未入选） | 留私信备用 |
| `客户交付/01-界面截图/后台Admin/06-商品分类.png` | （未入选） | 留私信备用 |
| `客户交付/01-界面截图/后台Admin/07-商品服务.png` | （未入选） | 留私信备用 |
| `客户交付/01-界面截图/后台Admin/08-库存管理.png` | P9 | 库存盘点 |
| `客户交付/01-界面截图/后台Admin/09-卡券管理.png` | P4 + P9 | P4 用作通用模块；P9 突出卡券主题 |
| `客户交付/01-界面截图/后台Admin/10-卡券核销.png` | P9 | 核销工作台 |
| `客户交付/01-界面截图/后台Admin/11-订单管理.png` | P4 | 订单工作台 |
| `客户交付/01-界面截图/后台Admin/12-门店管理.png` | P8 | 多门店隔离（与稳定性挂钩） |
| `客户交付/01-界面截图/后台Admin/13-员工管理.png` | P8 | RBAC |
| `客户交付/01-界面截图/后台Admin/14-打印设备.png` | P9 | 打印机绑定 |
| `客户交付/01-界面截图/后台Admin/15-商户信息.png` | （未入选） | 留私信备用 |
| `客户交付/01-界面截图/后台Admin/16-文章公告.png` | （未入选） | 留私信备用 |
| `客户交付/01-界面截图/后台Admin/17-首页轮播.png` | （未入选） | 留私信备用 |
| `客户交付/01-界面截图/后台Admin/18-后台账号.png` | P8 | RBAC 主语 |
| `客户交付/01-界面截图/后台Admin/19-角色职务.png` | P8 | RBAC 矩阵 |
| `客户交付/01-界面截图/后台Admin/20-操作日志.png` | P8 | 审计 |
| `客户交付/01-界面截图/会员端/01-首页.png` | P6 | H5 全链路首页 |
| `客户交付/01-界面截图/会员端/02-微店.png` | （未入选） | 留私信备用 |
| `客户交付/01-界面截图/会员端/03-商品列表.png` | P6 | 商品列表 |
| `客户交付/01-界面截图/会员端/04-商品详情.png` | P6 | 商品详情 |
| `客户交付/01-界面截图/会员端/05-会员登录.png` | （未入选） | 留私信备用（与 P4 登录重复） |
| `客户交付/01-界面截图/会员端/06-帮助中心.png` | （未入选） | 留私信备用 |
| `客户交付/01-界面截图/会员端/08-商家管理.png` | （未入选） | P3 改用 `h5-商户端-*.png` 系列 |
| `客户交付/01-界面截图/会员端/09-会员中心.png` | P10 | 生产样式参考 |
| `客户交付/01-界面截图/会员端/10-我的卡券.png` | P6 | 卡券 |
| `客户交付/01-界面截图/会员端/11-我的余额.png` | （未入选） | 留私信备用 |
| `客户交付/01-界面截图/会员端/12-积分明细.png` | （未入选） | 留私信备用 |
| `客户交付/01-界面截图/会员端/13-我的订单.png` | （未入选） | 留私信备用 |
| `客户交付/01-界面截图/会员端/14-分销中心.png` | （未入选） | 留私信备用 |
| `客户交付/01-界面截图/会员端/15-收货地址.png` | （未入选） | 留私信备用 |
| `客户交付/01-界面截图/会员端/16-我的会员码.png` | （未入选） | 留私信备用 |
| `客户交付/01-界面截图/会员端/18-数据统计.png` | P3 | 商户端看板 |
| `客户交付/01-界面截图/会员端/19-会员管理.png` | （未入选） | P10 已用四行业并陈 |
| `客户交付/01-界面截图/会员端/20-订单管理.png` | （未入选） | 留私信备用 |
| `客户交付/01-界面截图/会员端/21-商品管理.png` | （未入选） | 留私信备用 |
| `客户交付/01-界面截图/会员端/22-卡券管理.png` | （未入选） | 留私信备用 |
| `客户交付/01-界面截图/收银端/00-登录页.png` | P5 | 登录页（P4 已有，可替换） |
| `客户交付/01-界面截图/收银端/01-收银主页.png` | P5 | 收银主页 |
| `客户交付/01-界面截图/收银端/02-订单管理.png` | P5 | 订单 |
| `客户交付/01-界面截图/收银端/03-会员管理.png` | P5 | 会员 |
| `客户交付/01-界面截图/收银端/04-会员充值.png` | P5 | 充值 |
| `客户交付/01-界面截图/收银端/05-卡券核销.png` | P5 | 核销 |
| `客户交付/01-界面截图/收银端/06-总览首页.png` | （未入选） | 留私信备用 |
| `客户交付/01-界面截图/收银端/07-设置.png` | P7 | 收银端已具备 vue-i18n |

> 说明：上表列出 **71 张图** 的去留。其中明确**未入选 Portfolio 主卡**的，仅是因为 Fiverr 每个项目上限 5 张——它们仍是**对外私信 / 项目接洽时的"备料"**，Fiverr 卖家在 Gig 页通常写 *"more screenshots available on request"*。

---

## C. 图片压缩说明

### C.1 实测总体（71 张 PNG，全部用 Python `struct` 解析 IHDR 头得到宽高）

| 分组 | 数量 | 宽度范围 | 高度范围 | 单图体积 |
|---|---|---|---|---|
| H5 首页改版 / 实测（`h5-*.png` 旧位置） | 22 | 750 px | 1334-2250 px | 120-350 KB |
| H5 会员中心 / 商户端 | 8 | 750 px | 1408-2250 px | 138-280 KB |
| 客户交付-会员端 | 20 | 390 px（iPhone 13 视口宽） | 844-1700 px | 14-188 KB |
| 客户交付-后台Admin | 21 | 1258 px（桌面侧） | 566 px（全屏抓取后被压成长条） | 40-200 KB |
| 客户交付-收银端 | 8 | 1258 px | 566 px | 12-120 KB |

> 注：Admin / 收银端的 `1258×566` 实测**不是 1920 截图后压成的小图**，而是缩放后留作"巡览"的横长条；这种长条在 Fiverr 列表缩略图（1280 宽限）里**会出现大面积空白**——建议 P4、P5 项目**首图优先用 16:9 ~ 16:10** 长宽比的桌面抓图（如果有 1920×1080 原图最好；如无，建议补抓或降比例改用 1258×566 已够用）。

### C.2 逐张建议（**只列本次**直接用于 Fiverr 卡片**的图**）

| 路径 | 宽×高 | 体积(KB) | 是否需要压缩 | 建议 |
|---|---|---|---|---|
| `h5-首页改版-零售.png` | 750×1334 | 245.0 | 否 | 直接用，1334 高度在 Fiverr 列表缩略图会被二次缩到 ~720 长边，清晰度足够 |
| `h5-首页改版-零售-goods.png` | 750×1334 | 167.4 | 否 | 直接用 |
| `h5-首页改版-四宫格与优惠券.png` | 750×1334 | 248.5 | 否 | 直接用 |
| `h5-首页改版-375.png` | 750×1334 | 253.7 | 否 | 直接用 |
| `h5-首页实测截图.png` | 750×1334 | 243.9 | 否 | 直接用 |
| `h5-首页改版-汽车.png` | 750×1334 | 234.4 | 否 | 直接用 |
| `h5-首页改版-餐饮.png` | 750×1334 | 339.2 | 否 | Fiverr 单图 ≤5MB 直接用，无超 |
| `h5-首页改版-康养.png` | 750×1334 | 241.6 | 否 | 直接用 |
| `h5-首页改版-餐饮-真实数据.png` | 750×1334 | 339.2 | 否 | 直接用 |
| `h5-商户端-零售.png` | 750×1408 | 138.6 | 否 | 直接用 |
| `h5-商户端-汽车.png` | 750×1408 | 206.8 | 否 | 直接用 |
| `h5-商户端-餐饮.png` | 750×1408 | 214.5 | 否 | 直接用 |
| `h5-商户端-康养.png` | 750×1408 | 173.9 | 否 | 直接用 |
| `h5-会员中心-零售.png` | 750×1904 | 198.0 | 否 | 直接用 |
| `h5-会员中心-汽车.png` | 750×2250 | 272.9 | 否（但 2250 高是 iPhone 长截图，建议裁到首屏 1900 内） | **可选**裁顶部 TabBar+顶部状态区多余空条 |
| `h5-会员中心-餐饮.png` | 750×1904 | 264.9 | 否 | 直接用 |
| `h5-会员中心-康养.png` | 750×1904 | 228.8 | 否 | 直接用 |
| `客户交付/01-界面截图/会员端/01-首页.png` | 390×1600 | 182.8 | 否 | 直接用 |
| `客户交付/01-界面截图/会员端/03-商品列表.png` | 390×1600 | 132.6 | 否 | 直接用 |
| `客户交付/01-界面截图/会员端/04-商品详情.png` | 390×1600 | 88.3 | 否 | 直接用 |
| `客户交付/01-界面截图/会员端/09-会员中心.png` | 390×1600 | 76.6 | 否 | 直接用 |
| `客户交付/01-界面截图/会员端/10-我的卡券.png` | 390×1200 | 26.0 | 否 | 直接用 |
| `客户交付/01-界面截图/会员端/18-数据统计.png` | 390×1700 | 73.1 | 否 | 直接用 |
| `客户交付/01-界面截图/后台Admin/00-登录页.png` | 1258×566 | 193.3 | 否 | 直接用 |
| `客户交付/01-界面截图/后台Admin/01-首页看板.png` | 1258×566 | 45.8 | 否 | 直接用 |
| `客户交付/01-界面截图/后台Admin/02-会员管理.png` | 1258×566 | 72.8 | 否 | 直接用 |
| `客户交付/01-界面截图/后台Admin/03-会员等级.png` | 1258×566 | 63.8 | 否 | 直接用 |
| `客户交付/01-界面截图/后台Admin/08-库存管理.png` | 1258×566 | 57.8 | 否 | 直接用 |
| `客户交付/01-界面截图/后台Admin/09-卡券管理.png` | 1258×566 | 63.0 | 否 | 直接用 |
| `客户交付/01-界面截图/后台Admin/10-卡券核销.png` | 1258×566 | 66.8 | 否 | 直接用 |
| `客户交付/01-界面截图/后台Admin/11-订单管理.png` | 1258×566 | 63.6 | 否 | 直接用 |
| `客户交付/01-界面截图/后台Admin/12-门店管理.png` | 1258×566 | 46.1 | 否 | 直接用 |
| `客户交付/01-界面截图/后台Admin/13-员工管理.png` | 1258×566 | 62.5 | 否 | 直接用 |
| `客户交付/01-界面截图/后台Admin/18-后台账号.png` | 1258×566 | 68.0 | 否 | 直接用 |
| `客户交付/01-界面截图/后台Admin/19-角色职务.png` | 1258×566 | 40.3 | 否 | 直接用 |
| `客户交付/01-界面截图/后台Admin/20-操作日志.png` | 1258×566 | 62.9 | 否 | 直接用 |
| `客户交付/01-界面截图/后台Admin/14-打印设备.png` | 1258×566 | 46.3 | 否 | 直接用 |
| `客户交付/01-界面截图/收银端/01-收银主页.png` | 1258×566 | 62.8 | 否 | 直接用 |
| `客户交付/01-界面截图/收银端/02-订单管理.png` | 1258×566 | 63.5 | 否 | 直接用 |
| `客户交付/01-界面截图/收银端/03-会员管理.png` | 1258×566 | 55.1 | 否 | 直接用 |
| `客户交付/01-界面截图/收银端/04-会员充值.png` | 1258×566 | 42.5 | 否 | 直接用 |
| `客户交付/01-界面截图/收银端/05-卡券核销.png` | 1258×566 | 57.8 | 否 | 直接用 |
| `客户交付/01-界面截图/收银端/07-设置.png` | 1258×566 | 12.2 | 否 | 直接用（i18n 已就绪的依据） |

### C.3 推荐策略（一句话总结）

- **全部原图直接上传即可**：体积最大 339 KB、远低于 5 MB 上限。
- **Fiverr 后端会自动缩**：建议宽度上传**不超过 1280 px**，本批 750/390 px 移动端 + 1258 px 桌面端都在安全区。
- **桌面端 1258×566 是横长条**，用作 P4/P5 主图没问题；但若买家缩略图 1:1 切会切到中段空白，**建议把"看板/收银主页"两张图放到第 1 / 第 5 位置**（缩略图正中），其余放 2/3/4。
- 本文档**绝不真去压缩/上传任何一张图**——只给策略。

---

## D. 上传顺序与措辞提示

### D.1 推荐的上传顺序（10 个项目按"先吸睛"原则）

| 顺序 | 项目 | 理由 |
|---|---|---|
| **1** | **P3 — Merchant Console 看板 / 数据统计** | 真实跑出真实数据（今日交易额、近 7 日柱状/折线），最能说明"有数据"，是买家最在意的"能落地"信号 |
| **2** | **P6 — Member H5 End-to-End** | H5 三张主体 + 全链路 20 屏，适合做"全链路"门面 |
| **3** | **P5 — Electron Cashier POS** | 桌面应用差异化，桌面买家更愿意为此付费 |
| **4** | **P4 — Admin 21 模块** | RBAC + 审计 + 全模块，专业度高 |
| **5** | **P1 — Retail 行业改版** | 单行业改版是 Fiverr 接单量最大的「单行业改造」剧本 |
| **6** | **P7 — i18n 改造** | 翻译 / 本地化关键词匹配最热 |
| **7** | **P2 — 四行业换皮** | "multi-tenant" / "theming" 关键词匹配 |
| **8** | **P8 — Spring Boot 底座 + 加固** | 后端专才买家 |
| **9** | **P10 — 四行业会员中心** | "loyalty" / "membership" 关键词 |
| **10** | **P9 — 多模块巡览** | 收尾，给"探索更多模块"为铺垫 |

### D.2 Portfolio Description 措辞要点（AT 与人工双重匹配）

**关键词必须露出**（任选 ≥ 5 散布到每个项目的 1000 字 Description 里）：

```
Spring Boot, Vue.js, uni-app, i18n, localization, multi-tenant,
multi-industry SaaS, retail POS, beauty booking, automotive service,
catering ordering, wellness/beauty booking, RBAC, Spring AOP,
MyBatis-Plus, Redis, Electron POS, WeChat Pay, Alipay, UnionPay,
HBuilderX, uView UI, Element UI, SCSS, CSS custom properties,
sticky header, dynamic Y-axis, audit log
```

**禁区词（会被 Fiverr ATS 标黄/下架）**：

- `guaranteed / guarantee`、`#1 / best / top-rated`
- `100% / fastest / cheapest`
- "客户/客户的好评"作主语（炫耀型）
- 任何带完整域名 / 二维码 / 联系方式的截图
- 任何指向原作者/原竞品的负面比较

**语气基线（不要写）**：

- ❌ "我做了 bahar"，"我们自有产品 bahar" —— **错误**。
- ✅ "I customized an open-source base named *bahar* (kept its original author attribution) to **demonstrate my Spring Boot + Vue.js full-stack capability** for [industry X]." —— **合规话术**。
- ✅ "Forked from `KC20191026/bahar` (Apache-2.0); modified for [vertical]; produced 49 real-data screenshots." —— 合规、可追溯。

### D.3 每个 Portfolio 项目的 Tags 候选（取自 Fiverr 下拉常见列表）

| 项目 | 候选 Tags（用户手动 ≥ 3 选） |
|---|---|
| P1 | `vue.js`, `mobile-app`, `ecommerce`, `responsive-design`, `css` |
| P2 | `saas`, `multi-tenant`, `theming`, `vue.js`, `mobile-app` |
| P3 | `dashboard`, `data-visualization`, `mobile-app`, `vue.js`, `ecommerce` |
| P4 | `admin-panel`, `rbac`, `back-end`, `vue.js`, `database` |
| P5 | `electron`, `desktop-app`, `pos`, `vue.js`, `payment-gateway` |
| P6 | `mobile-app`, `ecommerce`, `vue.js`, `wechat`, `pwa` |
| P7 | `i18n`, `localization`, `back-end`, `java`, `translation` |
| P8 | `spring-boot`, `back-end`, `security`, `production-deployment`, `mysql` |
| P9 | `ecommerce`, `loyalty`, `affiliate`, `inventory`, `coupon-system` |
| P10 | `loyalty`, `mobile-app`, `vue.js`, `saas`, `multi-vertical` |

> Tags 是 **Fiverr 给定下拉** 的，用户在前端选；Fiverr 不会从 Description 自动提取 Tags。上面只是"该选哪些下拉项"的建议。

---

## E. 风险与提醒（**必看**）

### E.1 合规 / 版权风险（**最高优先级**）

1. **保留原作者版权**：任何对外可见的 Description / 图册，**必须**显式提到 *"based on an open-source product named `bahar`; original author attribution preserved"*。**禁止**：
   - 贴原项目**源码截图**（IDE / GitHub / 代码片段 / 后端控制台日志）；
   - 抹掉原作 `bahar` 名字、假装是自有产品；
   - 在图里露出原 GitHub 仓库 URL（如出现请裁剪 / 模糊）。
2. **演示账号口径**：`04-稳定性与安全性说明.md` 与 `02-业务流程图.md` 中提到的演示万能验证码 `999999`、演示账号 `bahar/123456`、演示端口 `127.0.0.1:8081~8084`，**绝不能进入 Fiverr Description 字段**（会把账号秘钥泄到公开页）。
3. **mermaid 序列图/流程图**（02、现状勘察含 mermaid 块）：GitHub / Fiverr 不直接渲染 mermaid，需要导 PNG 才会显示——见 P7 图片说明，未导图就**显式说明**「architecture diagram lives in the deliverable folder」。

### E.2 Fiverr ATS / 违禁词扫描高危

| 词 | 状态 | 处置 |
|---|---|---|
| `guaranteed` / `guarantee` | ❌ 高危 | 不写 |
| `#1` / `best` / `top-rated` / `cheapest` / `fastest` | ❌ 高危 | 不写 |
| `100%` (绝对化) | ❌ 高危 | 改写为 "in my experience" / "for most cases" |
| `We are the best` / `clients say` 作主语 | ❌ | 改写为技术描述句 |
| 截图里出现联系方式 / 二维码 / 微信号 | ❌ | 裁掉或遮盖 |
| 截图里露出其他卖家/平台水印 | ❌ | 替换 |

### E.3 md 文档对外可见性建议（哪些 md 适合对外、哪些不适合）

| md | 对外可见性 | 说明 |
|---|---|---|
| `i18n-国际化方案.md` | ⭐ **可对外**（节选） | 极佳的技术能力证明；节选**架构图 + Top 100 文案覆盖率**段即可。**不可整篇贴**：含真实的 controller 行号、内部 yaml 路径、mysql DDL |
| `competitor-fuint-h5-ui-spec.md` | ⚠️ **仅做"已分析竞品"的一句话带过** | 全文带竞品名称 + 大量设计数值 + 合规声明，**禁止整段贴**。可以在 Description 里写 *"the work was preceded by a structured competitor UI teardown"* |
| `h5-现状勘察.md` | ❌ **不可对外** | 内含零售 vs 康养 vs 汽车 vs 餐饮的 **md5 比对**与具体文件行号（如 `components/search/index.vue:35-42`），属于"内部踩坑档案"，外泄会让买家轻易定位/抄改 |
| `客户交付/00-交付清单.md` | ⚠️ **可摘录** | 49 张截图清单本身可写进 P3-P6 的描述里；**不可贴**里面的"复现脚本路径"`deploy/tmp/`"等纯内部脚本目录 |
| `客户交付/02-业务流程图.md` | ⭐ **可对外**（节选） | mermaid 时序图本身是公开概念，节选**登录鉴权 + 下单结算 + 卡券核销 3 段**；**不可贴**末尾的「关键源码索引」附表（暴露内部类名） |
| `客户交付/03-业务配置与接入清单.md` | ⚠️ **可摘录 P0/P1 段** | 适合做"我能交付配置文档"的证据；**不可贴**的：第 1 段 `application.yaml` 内部配置段、`mt_merchant.wx_app_secret` 等密钥字段、阿里云控制台申请链接（保留参考） |
| `客户交付/04-稳定性与安全性说明.md` | ⚠️ **节选第一、二节** | 第三节「上线前需补齐」直接对外很有说服力；**不可贴**：万能验证码 / 演示账号 / 演示端口 |
| `客户交付/05-Logo展示与后台配置方案.md` | ❌ **不可对外** | 全文是给客户方的"按这套方案来落地"，对外公开没价值 |
| `software-company/bahar-clients-提测启动部署指南.md` | ❌ **不可对外** | 完全是内部部署脚本指引（`yarn dev:shop -m food`、端口 8088、`deploy/start-all.sh`） |

### E.4 功能底线（防"过度承诺"）

- **不要**在 Description 里写"30 天交付 i18n 一期"，**不要**写"我能在 X 人月完成 Y 行业改造"——Fiverr 会在买家纠纷时被反查。
- 描述用"我**典型**交付周期 / 我**在过往项目里**用 **~** 人日"等措辞。
- 自动触发工程化的支付 / 退款 / 短信能力**只在演示环境跑过**；线上的开关（`isClose=1` 等）要在协作聊天里才说，不要写进 Portfolio Description。

### E.5 图片本身的小漏洞（上传前自检）

- 首页改版的"零售"截图（`h5-首页改版-零售.png`）**店名条**画面里有真实门店名（"演示总店"），**没问题**——演示用途。
- 数据统计图（`客户交付/.../18-数据统计.png`）**显示**"今日交易额 ¥1186.15"等具体数字，**没问题**——明确是演示数据。
- Admin 截图里的菜单**纯中文**（"商品管理 / 库存管理"等），**对外不影响**——本来的目标就是支持中文后台；只是在 i18n 改造前，**对英文买家**视觉上中文为主。**优化**：若买家在意，Description 末尾用一句 *"after the i18n refactor (see Project P7), the same screens render fully bilingual"* 兜底。
- 收银端截图里**侧边栏文字是 "bahar"**——保留，作品牌词出现。

---

## F. 路线图 / 后续动作（用户可选）

1. **现在**：用户按本文档手动在 Fiverr 上传 10 个 Portfolio，每个 5 张图 + 双语 Description。
2. **下一步**（与上传并行）：把所有 H5 / Admin / 收银端截图里的菜单文案按 `i18n-国际化方案.md` 双语化，再补一次"中英对照"截图作为 P7 的第 4、第 5 张图。
3. **扩展**：若买家询单"再做一套 SPA + i18n"，可在 Gig Description 里加 *"see Portfolio P7 for our i18n pattern — same team, 2-week delivery for one new language"*。

---

## G. 备忘

- 创建时间：2026-10-15
- 用户签名备注：____________________________________
- 后续如补素材/补截图，按 §B 表头的"未入选"列回填到 Portfolio 卡片或保留作私信附件。
- 本文件**只读**：用户如要改文案或更新图片清单，复制一份 `portfolio-plan-{version}.md` 即可，**不要原地改**以保留基线。
