# spacecloudnet.cn — 跳转站

生产地址：**https://spacecloudnet.cn/** → 立即跳转到 **https://spacecloudnet.com/**

## 为什么单独建一个仓库

GitHub Pages 的每个站点只能绑定一个自定义域名，`.com` 与 `.cn` 无法共用同一个 Pages 站点。因此本仓库只做一件事：占住 `spacecloudnet.cn` 这个域名并做跳转。

跳转采用三重保底，任意一层生效即可：

1. `<meta http-equiv="refresh" content="0; url=...">`
2. `<script>location.replace(...)</script>`
3. 页面上的可见链接（禁用 JS 且不认 meta refresh 时兜底）

## 文件

| 文件 | 作用 |
|---|---|
| `index.html` | 跳转页 |
| `404.html` | 任意未知路径同样跳回主站 |
| `CNAME` | 声明自定义域名 `spacecloudnet.cn`（**不要删除**） |
| `favicon.svg` | 与主站一致的图标 |
| `robots.txt` | `Disallow: /` —— 本域仅作跳转，不参与收录 |
| `.nojekyll` | 跳过 Jekyll 处理 |

页面通过 `<link rel="canonical">` 与 `noindex, follow` 明确告知搜索引擎：内容归属 `spacecloudnet.com`。

## DNS 记录（阿里云云解析 · 权威 NS `dns15/dns16.hichina.com`）

| 类型 | 主机记录 | 记录值 | TTL |
|---|---|---|---|
| A | `@` | `185.199.108.153` | 600 |
| A | `@` | `185.199.109.153` | 600 |
| A | `@` | `185.199.110.153` | 600 |
| A | `@` | `185.199.111.153` | 600 |
| AAAA | `@` | `2606:50c0:8000::153` ~ `8003::153` | 600 |
| CNAME | `www` | `moozaa75.github.io` | 600 |

## 如果以后想让 .cn 独立成站

把本仓库内容替换成真正的站点，并把 `index.html` 里的 `canonical` 与 `robots.txt` 改成本域即可，DNS 与 Pages 配置都不用动。
