---
layout: post
title: "SEO 进阶实战 1/3：技术博客的 Technical SEO 实战指南（以 Jekyll 为例）"
date: 2025-02-17 10:00:00 +0800
categories: seo
tags: [SEO, Technical SEO, 技术SEO, Jekyll, 静态博客]
series: seo-intermediate
series_order: 1
excerpt: "SEO 进阶实战第一篇：面向技术博客的 Technical SEO 实战指南，聚焦站点结构、URL 设计、sitemap、robots 等技术层面的搜索引擎优化。"
---

> 关键词提示：Technical SEO、技术 SEO、Jekyll SEO、静态博客 SEO、sitemap、robots.txt。

在「SEO 入门必看」系列里，我们更多是从概念层面认识 SEO（搜索引擎优化）。从这一篇开始，我们进入 **SEO 进阶实战**，第一站就是很多技术人最熟悉、却又最容易忽略的部分：**Technical SEO（技术 SEO）**。

尤其是如果你像我一样，用 Jekyll + GitHub Pages 搭建了一个静态技术博客，那么下面这些技术向的 SEO 实战，会非常直接地提升你的网站「对爬虫友好」的程度。

## 一、为什么技术博客尤其需要 Technical SEO？

很多技术博客都有这些共同特点：

- URL 结构随缘，文章路径复杂或者不统一；
- 分类、标签、系列文章混在一起，没有清晰的信息架构；
- 缺少 `sitemap.xml` 和 `robots.txt`；
- 不太关注 404、重定向等细节，只要自己能打开就行。

对于搜索引擎爬虫来说，一个「技术上规整、结构清晰」的站点，会更容易：

- 被完整抓取（Crawling）；
- 被正确索引（Indexing）；
- 在合适的关键词上获得更稳定的排名（Ranking）。

Technical SEO 的核心目的很简单：

> 不让你的内容输在「机械层面」。你已经写了好文章，就让爬虫能轻松看懂它们的结构和关系。

## 二、用 Jekyll 打造清晰的 URL 与站点结构

对于静态博客，**URL 结构** 是 Technical SEO 的第一步。

### 1. 合理的 permalink 设计

在 Jekyll 中，你可以通过 `_config.yml` 配置全站 URL 模式。例如：

```yaml
permalink: /:categories/:year/:month/:day/:title/
```

对于技术博客，一个推荐思路是：

- 通过 `categories` 体现内容领域（如 `seo`、`python`、`go`）；
- 通过日期和标题构成唯一 URL；
- 避免无意义的 query 参数（比如 `?id=1234`）。

这样可以让搜索引擎更容易从路径中理解大致语义：

- `/seo/2025/02/17/seo-intermediate-technical-seo-for-blogs/`
- `/python/2025/02/20/python-logging-best-practices/`

### 2. 分类与标签（categories & tags）的使用策略

建议简单但清晰：

- `categories`：用来表示「大的主题领域」，例如 `seo`、`python`、`go`、`ai`；
- `tags`：用来标记更细粒度的特征，例如 `Technical SEO`、`静态博客`、`教程`。

示例（本篇的 front matter）：

```yaml
categories: seo
tags: [SEO, Technical SEO, 技术SEO, Jekyll, 静态博客]
```

好处是：

- `/seo/` 分类页可以聚合所有 SEO 相关文章；
- 标签可以帮助读者在站内筛选更细分的内容（未来如果你做标签页）。

## 三、sitemap.xml 与 robots.txt：给爬虫一张「地图」

### 1. 使用 jekyll-sitemap 自动生成 sitemap.xml

对于静态博客，不需要自己手写 sitemap，用官方插件即可：

1. 在 `_config.yml` 中添加插件：

   ```yaml
   plugins:
     - jekyll-sitemap
   ```

2. 构建后，站点根目录会自动生成 `/sitemap.xml`。

sitemap.xml 会列出你站点的所有重要页面 URL，帮助搜索引擎完整发现你的内容。这对 SEO 尤其是新站是非常有价值的基础设施。

### 2. 写一个简单、干净的 robots.txt

在站点根目录创建 `robots.txt`，例如：

```txt
User-agent: *
Allow: /

Sitemap: https://你的域名/sitemap.xml
```

如果你有一些不希望搜索引擎抓取的路径（例如测试页面、内部工具），可以适当使用 `Disallow`，但不要过度屏蔽，否则爬虫会丢失重要内容。

## 四、状态码、404 与重定向：不要让爬虫走进死胡同

### 1. 确保重要页面返回 200

- 正常存在的文章和页面，应该始终返回 HTTP 200；
- 删除文章时，要么：
  - 确认它确实可以返回 404；
  - 要么给出合理的 301 重定向到替代内容。

### 2. 合理处理 404 页面

- 提供一个自定义的 404 页面，告诉用户和爬虫「这里没有内容」；
- 但不要把所有 404 强行跳到首页或某个固定页面，这会让搜索引擎难以判断真实状态。

在 Jekyll 中，你可以创建一个 `404.html` 并用 `permalink: /404.html`，既方便人类用户，也对搜索引擎友好。

## 五、页面性能与移动端体验（简单版）

虽然性能优化可以写一本书，但对于个人技术博客，一些简单的 Technical SEO 实战就足够提升质量：

- 使用静态托管（GitHub Pages、Cloudflare Pages 等），本身就有不错的基础性能；
- 控制图片体积，避免在博客中直接使用超大原图；
- 确保主题是响应式的（Hacker 主题本身就是 Responsive 的）。

这些因素会影响搜索引擎的「页面体验」信号，并间接影响 SEO 排名。

## 六、针对 Jekyll 技术博客的 Technical SEO 行动清单

最后，我们把这篇 Technical SEO 实战总结成一个可以直接执行的清单：

1. 在 `_config.yml` 中设置清晰的 `permalink` 规则，让 URL 语义化；
2. 为文章合理设置 `categories` 和 `tags`，便于结构化归类；
3. 启用 `jekyll-sitemap`，让站点自动生成 `sitemap.xml`；
4. 添加 `robots.txt`，至少声明允许抓取并指向你的 sitemap；
5. 为站点配置自定义 `404.html` 页面；
6. 避免不必要的重复 URL 和不正确的重定向；
7. 控制资源大小，保持静态站点的轻量和响应速度。

在后续的 **SEO 进阶实战 2/3 和 3/3** 中，我们会进一步从「内容矩阵」和「数据驱动迭代」的角度，带你把技术博客的 SEO 做得更系统和可持续。
