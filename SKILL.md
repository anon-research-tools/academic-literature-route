---
name: 学术论文搜索
description: 用于围绕一个选题、申报题名、综述或论文草稿收集、路线规划、筛选和整理海内外学术论文。覆盖检索式扩展、OpenAlex/Crossref/Semantic Scholar/Kimi/TinyFish/AnySearch/Grok/X 式机器检索、中文数据库补查、海外索引补查、重点期刊复核和 A/B/C/D 文献分级。
---

# 学术论文搜索

使用这个 Skill，把一个选题、草拟题名、课题申报题名或文献综述问题，转化成一条可追踪的文献检索路线和筛选后的候选文献表。目标不是简单列出论文，而是说明中文和海外文献是怎么找到的，哪些地方还需要人工补查，哪些条目可以支持正式写作。

## 工作流程

1. 将选题拆成四组关键词：
   - 研究对象：文本、人物、机构、语料、时代、地域。
   - 学科领域：宗教学、语言学、数字人文、图书情报、历史学、文献学等。
   - 问题框架：本土化、传播、制度变化、知识生产、接受史、比较研究等。
   - 方法词：目录学、语料库、数据库、文本挖掘、知识图谱、引文分析等。

2. 分层生成检索式：
   - 题名精确检索，加上 `论文` 等限定词。
   - 研究对象 + 问题框架。
   - 研究对象 + 学科领域。
   - 研究对象 + 方法词。
   - 同义词、历史术语、异名。
   - 英文对应词。
   - 面向重点数据库、期刊平台、出版社或机构仓储的 `site:` 检索式。

3. 在条件允许时，使用机器检索和线索扩展：
   - OpenAlex：开放学术元数据。
   - Crossref：DOI 和出版社元数据。
   - Semantic Scholar：摘要、引文关系、相关论文和 PDF 线索。
   - Kimi：中文学术网页、机构页面、期刊页面和中文数据库线索。
   - TinyFish：结构化网页搜索和站点定向中文数据库线索。
   - AnySearch：实时网页搜索、学术垂直搜索、批量检索式扩展、DOI 或主题探查、网页提取。
   - Grok/X：X/Twitter 上的新论文、预印本、作者发布、会议讨论、数据集、工具发布和同行评论线索。
   - 注意：LLM、网页和社交媒体结果都只是线索，不是文献事实。只有在题名、作者、年份、刊物、DOI/URL、全文可得性等字段通过稳定学术来源核验后，才能进入可引用候选列表。

4. 设置人工补查路线：
   - 中文：CNKI、万方、维普、国家哲学社会科学文献中心、CSSCI 目录、北大核心目录、台湾学术平台等。
   - 海外索引：Web of Science Core Collection、A&HCI、SSCI、Scopus、MLA International Bibliography、LLBA、DOAJ、JSTOR、Project MUSE。
   - 出版社平台：Springer Nature、Taylor & Francis、SAGE、Wiley、Oxford Academic、Cambridge Core、Brill、De Gruyter、ACL Anthology。
   - 浏览器辅助流程：CNKI 检索、详情页、期刊信息和引文导出；Google Scholar 发现、被引追踪和 BibTeX / Zotero 导出。

5. 做重点期刊复核：
   - 佛教与宗教学：世界宗教研究、宗教学研究、Journal of the International Association of Buddhist Studies、Buddhist Studies Review、Journal of Chinese Religions、History of Religions、Numen、Religions。
   - 语言学：中国语文、当代语言学、语言科学、Language、Linguistic Inquiry、Journal of Linguistics、Lingua、Diachronica、Journal of Chinese Linguistics。
   - 数字人文与图书情报：数字人文、情报学报、图书情报工作、Digital Scholarship in the Humanities、Digital Humanities Quarterly、Journal of Cultural Analytics、JASIST、Journal of Documentation。

6. 给每条结果分级：
   - A：已经核验，和选题直接相关，可以作为引用候选。
   - B：看起来相关，值得进一步精读。
   - C：背景性或外围性文献。
   - D：重复、图书、新闻、百科、栏目文章、搜索页面、跑题或无法核验。
   - 只有 X/Twitter 或 LLM 线索的条目不能评为 A。它们必须先通过稳定学术来源核验。

7. 找到强种子论文后，加入引文链扩展：
   - 向前查：检查种子论文引用了哪些早期研究。
   - 向后查：检查后来的论文谁引用了种子论文。
   - 相似论文扩展：使用 Semantic Scholar、ResearchRabbit、Connected Papers、Litmaps 等相关论文推荐工具。
   - Google Scholar 的 `data-cid` 聚合编号可以用来追踪被引页面和交叉核对结果。
   - 当新发现的论文主要是重复项、低相关项或明显偏离领域时停止扩展。

8. 对严肃综述任务保留类似 PRISMA-S 的审计轨迹：
   - 数据库或来源名称。
   - 实际运行的完整检索式。
   - 检索日期。
   - 年份、语言、文献类型、字段等过滤条件。
   - 命中记录数。
   - 去重和筛选后保留的记录数。
   - 重要但被排除记录的排除理由。
   - 对 Grok/X 线索，记录查询词、日期范围、账号或帖子 URL，以及后续用于核验的稳定学术来源。

9. 在认为检索完成前，复核检索策略：
   - 每个关键概念是否都有同义词和中英文变体？
   - 布尔运算、短语引号、截词、字段限定是否适合当前数据库？
   - 年份、语言、文献类型等限制是否有合理理由？
   - 已知的重要种子论文能否被当前检索式找回？如果不能，需要修正检索式。
   - 不同数据库的检索语法是否正确转换，而不是机械复制？

10. 保守使用浏览器辅助数据库流程：
   - CNKI 浏览器检索可以补充结构化搜索结果、文章详情、摘要、关键词、基金信息、期刊层级和 GB/T 7714 引文导出。
   - Google Scholar 浏览器检索可以补充广泛发现、引用次数、向后被引、全文链接和 BibTeX 导出。
   - 遇到验证码或登录墙，应停下来请用户手动处理，不要自动反复尝试。
   - 不使用未经授权的全文获取方式。优先使用 DOI、出版社页面、机构权限、图书馆链接、开放获取 PDF 和合法仓储副本。

11. 把 Grok/X 搜索作为“社交信号层”：
   - 适合快速变化、预印本密集、工具或数据集导向、作者和实验室会先在社交平台讨论的主题。
   - 查询词可以把主题和 `paper`、`preprint`、`arXiv`、`DOI`、`dataset`、`benchmark`、作者名、项目名、会议简称组合起来。
   - API 凭证只从环境变量或私密凭证存储读取。
   - 除非研究对象本身就是社交媒体话语，否则不要把推文当作学术文献引用。普通文献综述中，推文只作为发现证据，应指向论文、数据集、项目页、仓库或作者主页。
   - 输出时把社交信号和同行评议文献、数据库索引文献分开，并标记核验状态。

## 不同检索来源的角色

- Kimi：用于中文学术网页发现、文章题名扩展、机构和期刊页面、中文报告、CNKI / 万方 / 维普线索发现。最终记录仍需在学术数据库或出版社、期刊页面中核验。
- AnySearch：用于实时网页发现、学术垂直搜索、DOI 或主题探查、批量扩展检索式。AnySearch 命中先标为 `anysearch_lead`，只有通过 OpenAlex、Crossref、Semantic Scholar、PubMed、DOI、出版社页面、仓储、CNKI、万方、维普或 Google Scholar 核验后，才能升级为可引用候选。
- Grok/X：用于发现 X/Twitter 上的新论文、预印本、数据集、工具、基准测试、作者发布和会议讨论。最终记录需通过 DOI、arXiv、Zenodo、OSF、GitHub release、出版社页面、OpenAlex、Crossref、Semantic Scholar 或 Google Scholar 核验。
- TinyFish / 普通网页搜索：用于结构化网页覆盖和站点定向查询。结果只作为发现线索，直到书目信息稳定。
- 不要把这些来源混成同一种可信度。输出中应记录 `source_type`，例如 `academic_metadata`、`database_record`、`publisher_page`、`repository`、`anysearch_lead`、`llm_web_lead`、`x_social_lead`。

## 核验规则

对每条 LLM 或 X/Twitter 线索：

1. 提取其声称的论文或项目题名、作者、刊物、年份、DOI、arXiv、仓储链接和发布者。
2. 到稳定学术来源中搜索同一条目。
3. 以稳定来源的信息为准，规范化书目记录，不以 LLM 或推文文字为准。
4. 核验完成后再分级。未核验的社交线索保持 B 或 C，不进入直接引用列表。
5. 社交帖子或 LLM 结果可以作为溯源记录保存在审计日志中，但不能作为引文来源。

对每条 AnySearch 线索：

1. 记录准确的 AnySearch 命令或查询对象，包括 `domain`、`sub_domain`、`content_types`、`freshness`、`max_results` 等参数。
2. 如果使用垂直领域，先调用领域列表并遵守返回的查询约束，不凭空编造参数。
3. 通过稳定学术来源确认书目信息后，才可评为 A。
4. 只有在摘要不足以筛选或溯源时，才对非敏感 URL 使用网页提取。
5. 不要把私人草稿、API key、密码或个人敏感信息发送给 AnySearch。

## 凭证使用

优先使用环境变量，其次使用私密凭证存储，例如 macOS Keychain、1Password 或当前 agent 运行环境支持的密钥管理方式：

- Kimi / Moonshot：`KIMI_API_KEY` 或 `MOONSHOT_API_KEY`。
- TinyFish：`TINYFISH_API_KEY`。
- AnySearch：`ANYSEARCH_API_KEY`；部分场景可以匿名低频使用。
- Grok / OpenRouter：`OPENROUTER_API_KEY`。

不要把真实 key 写进提示词、报告、脚本、示例、命令历史或项目文档。如果用户把 key 粘贴到对话里，只能用于存入私密凭证位置，并建议轮换。

向用户报告结果时，要说明使用的是哪一层来源，例如 `Kimi 线索`、`TinyFish 线索`、`AnySearch 线索`、`Grok/X 线索`、`OpenAlex 已核验`、`Crossref 已核验`。这样可以把发现信号和可引用书目分开。

## 输出结构

对较完整的任务，输出这些部分：

1. 检索词：中文、英文和站点定向检索式。
2. 来源覆盖：机器来源、中文人工来源、海外人工来源。
3. 候选文献表：题名、作者、年份、刊物、URL/DOI、来源、命中检索式、等级、备注。
4. 可直接引用文献。
5. 下一步精读队列。
6. 人工补查清单。
7. 从种子论文出发的引文链扩展。
8. 检索审计日志，包括准确数据库查询和命中数。
9. 排除规则和排除示例。
10. 使用 Grok/X 时，输出社交线索表：帖子或账号、日期、声称的论文或项目、核验来源、状态。
11. LLM / 社交线索核验表：声称条目、已检查的稳定来源、确认的书目信息、剩余不确定性。
12. AnySearch 审计行：查询、domain/sub_domain、过滤条件、结果数、保留记录、核验来源。
13. 可选导出：RIS、BibTeX、Zotero、GB/T 7714。

## 关键安全规则

绝不要把真实 API key 写入公开 Markdown、前端代码、命令历史或可分享报告。只写环境变量名，例如 `KIMI_API_KEY`、`MOONSHOT_API_KEY`、`TINYFISH_API_KEY`、`ANYSEARCH_API_KEY`、`OPENROUTER_API_KEY`；真实 key 只应保存在本地私密环境文件、系统钥匙串或服务器环境变量中。
