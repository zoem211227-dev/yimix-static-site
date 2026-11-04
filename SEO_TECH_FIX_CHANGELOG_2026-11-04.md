# YIMIX SEO 技术修复变更记录

日期：2026-11-04
分支：`phase6-small-buyer-inquiry`

## 已处理

1. 在 `vercel.json` 增加旧路径兼容跳转：
   - `/oem-odm.html` → `/blog/oem-odm.html`
   - `/blog/products.html` → `/products.html`
   - `/blog/massage-chair-buying-guide.html` → `/massage-chair-buying-guide.html`
   - `/blog/massage-chair-faq.html` → `/massage-chair-faq.html`
   - `/product.html` → `/products.html`
2. 修复 5 个博客页面中会被解析为 `/blog/` 下错误路径的裸相对链接，将产品目录、购买指南和 FAQ 链接统一为根路径。
3. 核验跳转目标文件存在：`products.html`、`massage-chair-buying-guide.html`、`massage-chair-faq.html`、`blog/oem-odm.html`。
4. 重新解析 4 个重点产品页 JSON-LD。当前真实实体为 `Organization`、`WebSite`、`WebPage`、`BreadcrumbList`、`Service`、`Brand`、`PropertyValue`；未发现应安全补写的 `Offer`、`Review` 或 `AggregateRating`。因此没有虚构商品价格、库存、评分或评论。

## 本地校验

- `vercel.json` 可被 JSON 解析。
- 4 个跳转目标均存在。
- 5 个博客页面不再包含会生成 `/blog/products.html`、`/blog/massage-chair-buying-guide.html` 或 `/blog/massage-chair-faq.html` 的裸链接。
- 4 个重点产品页 JSON-LD 均可解析。
- 变更范围仅包含 5 个博客页面、`vercel.json` 和本变更记录；没有改动视觉、图片、产品目录内容或 WhatsApp 逻辑。

## 发布后需验收

Production 发布后检查旧路径跳转、新路径状态、Canonical、sitemap.xml、robots.txt、关键内链和 JSON-LD。部署成功本身不代表已收录、排名、AI 推荐或产生新增询盘。
