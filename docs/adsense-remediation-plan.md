# Square Face Generator AdSense 整改文档

## 1. 目标

本文档用于指导 `squarefacegenerator.run` 从“单页工具站”升级为“工具 + 内容 + 信任页 + 示例库”的完整产品站，以提升：

- AdSense 审核通过率
- 站点整体信任度
- 搜索引擎可索引页面数量
- 用户停留时长与二次浏览深度
- 后续 SEO / AEO / 内容增长空间

本次整改的核心不是继续堆首页字数，而是系统性解决以下问题：

1. 首页内容重复、关键词堆叠明显
2. 站点结构过薄，容易被判定为 low-value tool page
3. 法务与隐私内容与真实行为不一致
4. 缺少 About / Contact / License / FAQ 等信任页
5. 缺少 Examples / Guides 等可独立索引内容页
6. 缺少站点级内链、sitemap、robots、结构化数据等基础设施
7. 模板痕迹较强，缺少真实经营感

---

## 2. 当前问题总结

### 2.1 首页问题

当前首页虽然字很多，但大量内容属于重复性表述：

- 反复出现 `square face generator`
- 反复出现 `square face icon generator`
- 反复出现 `picrew alternative`
- 多段文案实际表达的是同一层意思，只是换句式重写

这类写法的风险：

- 用户感知为“营销页 / SEO 页”，而不是产品页
- 审核视角会认为页面信息密度低、可替代性高
- 搜索引擎可能将其识别为低原创度或低帮助性内容

### 2.2 站点结构问题

当前站点公开层面主要是：

- 首页生成器
- Privacy Policy
- Terms of Service

这类结构太薄，容易被识别为：

- 单工具页
- 模板法务页
- 缺乏真实运营内容

### 2.3 信任问题

当前存在以下典型问题：

- 隐私页声称不使用 analytics/tracking，但代码中实际启用了 Vercel Analytics
- 品牌、域名、邮箱信息不完全统一
- 页面中仍有明显模板/生成工具痕迹
- 缺少 About / Contact / License 等说明页面

### 2.4 内容层问题

网站缺少可以独立索引和独立阅读的页面，例如：

- 风格示例页
- 教程页
- 使用指南页
- 平台场景页
- 头像风格灵感页

这导致站点看起来更像一个“可玩但很薄的工具”，而不是一个“持续更新的创作产品网站”。

---

## 3. 整改总体策略

整改方向分为四层：

### 第一层：站点基础与信任层

目标：让网站看起来像一个真实产品，而非模板页。

包括：

- 重写首页
- 增加 About / Contact / FAQ / License
- 重写 Privacy / Terms
- 统一品牌与联系方式
- 删除明显模板痕迹

### 第二层：内容层

目标：把一页内容拆成多页高价值页面。

包括：

- Examples hub
- Guides hub
- 6 个 example 子页
- 6 个 guide 子页

### 第三层：索引与结构层

目标：增强搜索引擎和审核系统对站点完整性的理解。

包括：

- sitemap
- robots
- canonical
- page-level metadata
- structured data
- 更强的内链网络

### 第四层：产品沉淀层（可选但强烈建议）

目标：让工具产出可沉淀、可分享、可索引。

包括：

- avatar state URL 化
- share link
- `/avatar/[slug]` 页面
- remix 功能

---

## 4. 文件级整改任务

---

### 4.1 `app/layout.tsx`

#### 目标

去除模板站感，补全全局 metadata。

#### 必改项

- 添加 `metadataBase: new URL("https://squarefacegenerator.run")`
- 使用 title template
- 添加 canonical 支持
- 添加 Open Graph metadata
- 添加 Twitter metadata
- 删除 `generator: "v0.app"` 等明显模板痕迹
- 保留 favicon / apple icon

#### 验收标准

- 页面 source 中有 canonical
- 社交分享有 OG 信息
- 全站 metadata 风格统一
- 不再暴露低信任模板信息

---

### 4.2 `app/page.tsx`

#### 目标

把首页从“SEO 长文页”改成“产品首页”。

#### 新首页结构

1. Hero
2. Generator block
3. How it works
4. Use cases
5. Example styles preview
6. Short FAQ preview
7. Internal links section
8. Footer

#### 首页文案原则

- 不堆关键词
- 不长篇反复解释同一件事
- 以用户可读性优先
- 每个 section 只负责一类信息
- 多用“用途 / 场景 / 选择建议”，少用空泛夸赞

#### 建议移除内容

- 重复描述功能的超长 About 文案
- 重复描述“免费 / 无限 / Picrew alternative”的段落
- 空泛的 competitors comparison 段落
- 一切对用户帮助不大的关键词复读文案

#### 验收标准

- 首页明显更短
- 但内容更清晰
- 对 Examples / Guides / FAQ / About / Contact 有明确入口
- 更像产品首页，而不是 SEO landing page

---

### 4.3 `components/footer.tsx`

#### 目标

增强站点结构完整性。

#### 需新增链接

- About
- Contact
- FAQ
- License
- Examples
- Guides
- Privacy Policy
- Terms of Service

#### 验收标准

- 用户能在任意页面底部快速找到信任页与内容页
- footer 不再显得过薄

---

### 4.4 `app/about/page.tsx`

#### 页面目标

解释这个工具是什么、给谁用、为什么做。

#### 内容必须包含

- What this tool is
- Who it is for
- What problems it helps solve
- Why it exists
- Link to contact

#### 文案风格

- 像真实产品站
- 不要公司空话
- 不要模板式愿景口号

---

### 4.5 `app/contact/page.tsx`

#### 页面目标

提供真实联系方式与反馈入口。

#### 内容必须包含

- General feedback
- Business & licensing inquiries
- Copyright / takedown concerns
- Contact email
- Simple response expectation

#### 验收标准

- 页面有明确邮箱
- 品牌和域名统一
- 用户看得出有人在维护这个站

---

### 4.6 `app/faq/page.tsx`

#### 页面目标

把常见问题集中回答，避免首页承担全部解释职责。

#### 建议问题

- What is Square Face Generator?
- Is it free?
- Do I need an account?
- Does it work on mobile?
- Can I use avatars for social media?
- Are avatars stored?
- Can I use them commercially?
- How can I contact you?

#### 验收标准

- FAQ 回答问题，而不是重复首页营销文案
- 每条回答简洁、明确、可执行

---

### 4.7 `app/license/page.tsx`

#### 页面目标

说明头像使用范围，提升信任度，减少版权模糊地带。

#### 内容建议

- Personal use allowed
- Social profile use allowed
- Non-commercial creative use allowed
- Commercial use may require permission
- Prohibited uses
- Contact for unclear cases

#### 验收标准

- 语言简洁
- 不要写成复杂法律协议
- 但边界清晰

---

### 4.8 `app/privacy-policy/page.tsx`

#### 页面目标

让隐私政策与真实技术行为一致。

#### 重点整改

如果继续使用 Vercel Analytics：

- 明确说明使用匿名 / 聚合统计
- 说明用途是性能监测、使用趋势分析、产品优化
- 不写“完全不使用 analytics”这种与事实冲突的表述

#### 必须统一

- 品牌名称
- 主域名
- 联系邮箱

#### 验收标准

- 隐私声明与代码行为一致
- 无明显模板遗留
- 审核员看到不会一眼觉得自相矛盾

---

### 4.9 `app/terms-of-service/page.tsx`

#### 页面目标

用产品相关语言取代通用模板条款。

#### 建议内容

- Acceptance of terms
- Description of service
- Permitted use
- Prohibited use
- Intellectual property scope
- Commercial use note
- Disclaimer
- Contact information

#### 验收标准

- 与产品能力匹配
- 不要保留明显套版内容
- 品牌和联系方式统一

---

### 4.10 `next.config.mjs`

#### 目标

提高工程质量和上线可控性。

#### 建议

- 长期移除 `typescript.ignoreBuildErrors: true`
- 保留确有必要的 `images.unoptimized`

#### 验收标准

- 构建错误不再被长期忽略
- 项目发布前更容易暴露问题

---

## 5. 内容层建设

---

### 5.1 `app/examples/page.tsx`

#### 目标

构建风格灵感入口页。

#### 页面结构

- H1: Avatar Examples
- Intro
- 6 个 style card
- How to use these examples
- CTA back to generator

#### 作用

- 增加可索引页面
- 给用户第二步浏览路径
- 提升内链深度

---

### 5.2 `app/guides/page.tsx`

#### 目标

构建教程入口页。

#### 页面结构

- H1: Avatar Guides
- Intro
- 6 个 guide card
- How to use these guides
- CTA back to generator

#### 作用

- 将原首页的说明性内容拆分出去
- 形成工具 + 教程的站点形态

---

### 5.3 Example 子页

建议新增以下 6 个页面：

- `app/examples/cute-square-avatar/page.tsx`
- `app/examples/gaming-square-avatar/page.tsx`
- `app/examples/pastel-square-avatar/page.tsx`
- `app/examples/pixel-square-avatar/page.tsx`
- `app/examples/anime-square-avatar/page.tsx`
- `app/examples/discord-square-avatar/page.tsx`

#### 每个 page 模板

1. H1
2. Intro
3. What makes this style work?
4. Best for
5. How to recreate the look
6. Style tips
7. Related links
8. CTA

#### 原则

- 每页聚焦一个风格
- 不要只是换标题
- 内容要能真正帮助用户做选择

---

### 5.4 Guide 子页

建议新增以下 6 个页面：

- `app/guides/how-to-make-a-discord-avatar/page.tsx`
- `app/guides/best-profile-picture-size-for-x/page.tsx`
- `app/guides/how-to-create-a-cute-avatar/page.tsx`
- `app/guides/avatar-color-combination-guide/page.tsx`
- `app/guides/how-to-make-a-pixel-avatar/page.tsx`
- `app/guides/picrew-alternative-guide/page.tsx`

#### 每个 page 模板

1. H1
2. Intro
3. Why this matters
4. Practical advice
5. Common mistakes / style tips
6. Related links
7. CTA

#### 原则

- 解决一个清晰问题
- 少废话，多建议
- 不要写成首页的复制版本

---

## 6. 建议的英文文案方向

本次整改建议采用以下文案原则：

### 应该写什么

- 使用场景
- 设计建议
- 风格差异
- 选择方法
- 常见错误
- 简单明了的价值表达

### 不该写什么

- 大量重复核心关键词
- “best / ultimate / perfect / amazing” 这类空泛自夸
- 一段话里连续重复 3 次产品名
- 明显像为 SEO 机器写的句子

---

## 7. 技术基础设施整改

---

### 7.1 `app/sitemap.ts`

#### 目标

明确告诉搜索引擎有哪些公开页面。

#### 至少包含

- `/`
- `/about`
- `/contact`
- `/faq`
- `/license`
- `/privacy-policy`
- `/terms-of-service`
- `/examples`
- `/guides`
- 所有 example 页面
- 所有 guide 页面

---

### 7.2 `app/robots.ts`

#### 目标

提供基本爬取指引。

#### 要求

- Allow public pages
- Reference sitemap URL
- 不要误屏蔽 example / guide 页面

---

### 7.3 Structured Data

建议新增：

- `components/structured-data.tsx`

#### 使用场景

- 首页：WebApplication schema
- FAQ 页面：FAQPage schema
- Example / Guide 页面：BreadcrumbList schema

#### 目标

- 提升页面语义清晰度
- 增强搜索引擎对站点结构的理解

---

### 7.4 Page-level metadata

#### 每个新增页面都应具备

- 唯一 title
- 唯一 description
- canonical
- 合理的 OG / Twitter metadata

---

## 8. 产品沉淀能力（可选但强烈建议）

当前生成器能生成和下载头像，但没有沉淀路径。建议后续升级：

### 8.1 URL state sharing

新增：

- `lib/avatar-url.ts`

功能：

- 将 `AvatarState` 编码到 URL
- 支持恢复当前头像状态
- 允许复制链接 / 分享当前头像

### 8.2 Share link 按钮

修改：

- `components/square-face-generator.tsx`

建议新增：

- Copy Link
- Share current avatar

### 8.3 Avatar permalink 页面（第二阶段）

新增：

- `app/avatar/[slug]/page.tsx`

目标：

- 恢复一个 avatar state
- 显示预览
- 提供 `Remix this avatar`
- 提供 `Open in generator`

#### 价值

- 让工具产出可索引
- 提升站点页面规模
- 增加作品沉淀能力

---

## 9. 建议的目录结构

```txt
app/
  about/page.tsx
  contact/page.tsx
  faq/page.tsx
  license/page.tsx
  examples/page.tsx
  guides/page.tsx
  examples/
    cute-square-avatar/page.tsx
    gaming-square-avatar/page.tsx
    pastel-square-avatar/page.tsx
    pixel-square-avatar/page.tsx
    anime-square-avatar/page.tsx
    discord-square-avatar/page.tsx
  guides/
    how-to-make-a-discord-avatar/page.tsx
    best-profile-picture-size-for-x/page.tsx
    how-to-create-a-cute-avatar/page.tsx
    avatar-color-combination-guide/page.tsx
    how-to-make-a-pixel-avatar/page.tsx
    picrew-alternative-guide/page.tsx
  sitemap.ts
  robots.ts
components/
  structured-data.tsx
lib/
  avatar-presets.ts
  avatar-url.ts
public/
  examples/
    cute-square-avatar.png
    gaming-square-avatar.png
    pastel-square-avatar.png
    pixel-square-avatar.png
    anime-square-avatar.png
    discord-square-avatar.png
  og-default.png
docs/
  adsense-remediation-plan.md
```

---

## 10. 页面素材建议

建议新增 `public/examples/` 素材目录，至少准备 6~12 张静态示例图：

- cute
- gaming
- pastel
- pixel
- anime-inspired
- discord
- minimal
- colorful
- retro
- soft
- professional
- playful

#### 作用

- 让 example 页更像真实内容页
- 增强视觉说服力
- 降低“纯文字占位页”的感觉

---

## 11. 推荐开发顺序

### Phase 1：站点骨架与信任层

1. 更新 `app/layout.tsx`
2. 重构 `app/page.tsx`
3. 更新 `components/footer.tsx`
4. 新增 `about/contact/faq/license`
5. 重写 `privacy-policy/terms-of-service`
6. 统一品牌、联系邮箱、域名信息

### Phase 2：内容层

7. 新增 `examples` hub
8. 新增 `guides` hub
9. 新增 6 个 example 页面
10. 新增 6 个 guide 页面
11. 增加 example 静态图
12. 强化内链

### Phase 3：索引与技术基础设施

13. 新增 `sitemap.ts`
14. 新增 `robots.ts`
15. 添加 structured data
16. 补齐 page-level metadata

### Phase 4：产品沉淀能力

17. URL state share
18. Copy Link / Share 按钮
19. `/avatar/[slug]` 页面
20. Remix 流程

---

## 12. AdSense 重新申请前检查表

只有满足以下条件后，才建议重新申请：

### 基础结构

- [ ] 首页不再是关键词堆叠长页
- [ ] About 页面上线
- [ ] Contact 页面上线
- [ ] FAQ 页面上线
- [ ] License 页面上线
- [ ] Privacy Policy 与真实行为一致
- [ ] Terms 内容已重写

### 内容层

- [ ] Examples hub 上线
- [ ] Guides hub 上线
- [ ] 至少 6 个 example 页面上线
- [ ] 至少 6 个 guide 页面上线
- [ ] example 页配图存在

### 技术层

- [ ] sitemap 可访问
- [ ] robots 可访问
- [ ] canonical 生效
- [ ] OG / Twitter metadata 生效
- [ ] structured data 已添加

### 品牌与信任层

- [ ] 品牌名称统一
- [ ] 主域名统一
- [ ] 联系邮箱统一
- [ ] 无明显模板残留

### 收录层

- [ ] 至少一部分 example / guide 页面已被索引
- [ ] 站内链接可从首页和 footer 到达主要内容页

---

## 13. 最终判断

`squarefacegenerator.run` 当前不是“功能不行”，而是“站点层太薄”。

如果继续维持现状：

- 一个生成器
- 一页超长首页
- 两个模板法务页
- 没有内容层
- 没有真实信任页

则极有可能持续被判定为 low value。

但只要按本文档执行整改，网站会从：

**单页工具站**

升级为：

**工具 + 示例库 + 指南页 + 信任页 + 可持续扩展的产品站**

这是通过 AdSense 审核、提高后续 SEO/AEO 价值、以及提升整体用户体验的正确方向。

---

## 14. 建议给 Coding Agent 的执行原则

在实际开发时，需遵守以下原则：

1. 不破坏现有 generator 功能
2. 不做不必要的复杂架构
3. 优先静态实现
4. 不引入数据库
5. 不加入无必要依赖
6. 文案优先用户可读性，而非关键词重复
7. 页面应可独立存在，而不是首页内容复制
8. 保持当前视觉风格一致
9. 实现后应可直接部署
10. 所有链接和页面必须可用，不留死链

---

## 15. 推荐文档用途

本文件可用于：

- 与 Coding Agent 对接整改工作
- 作为 GitHub Repo 内部产品整改说明
- 作为未来 PR/Issue 的总纲
- 作为重新申请 AdSense 前的检查依据
