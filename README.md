# Academic Literature Route / 学术论文搜索

一个用于学术论文检索的 Codex Skill。它把“找论文”拆成一条可追溯的路线：拆题、扩展检索式、多源发现、稳定来源核验、A/B/C/D 分级、引文链扩展和人工复核清单。

它特别适合这些场景：

- 围绕一个论文题目、综述题目或课题申报题名搜集海内外研究。
- 需要同时覆盖中文数据库、海外索引、开放元数据、出版社页面和实时网页线索。
- 想区分“线索”和“可引用文献”，避免把 LLM 或网页搜索结果直接当成参考文献。
- 需要保留检索式、命中数、筛选理由和人工复核步骤，便于复查或写方法说明。

## What Makes It Different

多数搜索助手只给一串文献标题。这个 Skill 的重点不是堆积结果，而是建立可审计的检索过程：

1. **检索式先行**：先把选题拆成研究对象、领域、问题框架、方法词，再生成中文、英文和站点定向检索式。
2. **线索分层**：OpenAlex、Crossref、Semantic Scholar、Kimi、TinyFish、AnySearch、Grok/X、Google Scholar、CNKI 等来源各有不同身份。
3. **核验后再引用**：LLM、网页和社交媒体结果只能作为 lead，必须经过 DOI、出版社页面、开放元数据、数据库记录或仓储页面核验，才可进入直接引用列表。
4. **A/B/C/D 分级**：把文献分为可直接引用、值得细读、背景材料、排除项。
5. **引文链扩展**：从强种子文献出发做 backward chaining、forward chaining 和 similar-paper expansion。
6. **PRISMA-S 式审计**：记录搜索源、检索式、日期、过滤条件、命中数、保留数和排除理由。

## Install

Clone this repository into your Codex skills directory:

```bash
mkdir -p ~/.codex/skills
git clone https://github.com/anon-research-tools/academic-literature-route.git ~/.codex/skills/academic-literature-route
```

Restart Codex or reload skills if your runtime requires it.

## How To Use

In Codex, ask for the skill by name:

```text
用“学术论文搜索”这个 Skill，围绕“中古佛教写经制度与知识生产”搜索并筛选海内外学术论文。
```

Or:

```text
Use the Academic Literature Route skill to build a traceable literature-search route for:
"Buddhist manuscript culture and institutional knowledge production in medieval China".
```

For a substantial task, the expected output includes:

- Search terms: Chinese, English, and site-directed.
- Source coverage: machine sources, Chinese manual sources, overseas manual sources.
- Candidate literature table: title, authors, year, venue, URL/DOI, source, hit query, grade, note.
- Direct-citation candidates.
- Next close-reading queue.
- Manual follow-up checklist.
- Citation-chaining expansion from seed papers.
- Search audit log with exact database queries and hit counts.
- Excluded-result rules and examples.
- Optional AnySearch, Kimi, TinyFish, Grok/X, or social-lead verification tables.

## Method

The Skill works as a methodological wrapper around whatever search tools your agent environment can actually access.

### 1. Topic Parsing

The topic is decomposed into four term groups:

- Research object: texts, people, institutions, corpus, period, region.
- Field: religious studies, linguistics, digital humanities, library science, history, philology, etc.
- Problem frame: transmission, reception, institutional change, knowledge production, comparison, etc.
- Method terms: bibliography, corpus, database, text mining, knowledge graph, citation analysis.

### 2. Query Expansion

The agent generates layered search strings:

- Exact title plus `论文`.
- Object + problem frame.
- Object + field.
- Object + method.
- Synonyms and historical terms.
- English equivalents.
- `site:` queries for specific databases, journals, publishers, or repositories.

### 3. Source Layering

The Skill distinguishes source types:

- `academic_metadata`: OpenAlex, Crossref, Semantic Scholar, PubMed, etc.
- `database_record`: CNKI, Wanfang, CQVIP, JSTOR, Web of Science, Scopus, etc.
- `publisher_page`: journal or publisher pages.
- `repository`: arXiv, Zenodo, OSF, institutional repositories, GitHub release pages.
- `anysearch_lead`: AnySearch leads before scholarly verification.
- `llm_web_lead`: Kimi/TinyFish/general LLM-web leads before scholarly verification.
- `x_social_lead`: Grok/X/Twitter leads before scholarly verification.

### 4. Verification

The Skill does not treat LLM output, web snippets, or social posts as bibliographic truth. A record becomes a direct citation candidate only after stable fields are confirmed:

- Title
- Author names
- Year
- Venue
- DOI, URL, repository link, or database record
- Full-text availability when relevant

### 5. Grading

Each result receives a grade:

- **A**: verified, directly useful, cite candidate.
- **B**: plausible and worth close reading.
- **C**: background or peripheral literature.
- **D**: duplicate, book/news/wiki/column/search page, or off-topic.

X/Twitter-only or LLM-only hits cannot be Grade A until independently verified.

## Optional Integrations

This Skill can use these tools when your Codex environment has them:

- OpenAlex
- Crossref
- Semantic Scholar
- Kimi / Moonshot
- TinyFish
- AnySearch
- Grok/X through OpenRouter
- Browser-assisted CNKI or Google Scholar workflows
- Zotero, BibTeX, RIS, or GB/T 7714 export workflows

No integration is mandatory. If a tool is unavailable, the Skill should still produce a clear manual search route and audit checklist.

## Credentials

Use environment variables or a private credential store. Never paste raw keys into prompts, reports, scripts, public Markdown, or command history.

Common environment variable names:

- `KIMI_API_KEY`
- `MOONSHOT_API_KEY`
- `TINYFISH_API_KEY`
- `ANYSEARCH_API_KEY`
- `OPENROUTER_API_KEY`

## Safety And Ethics

- Do not use unauthorized full-text routes.
- Prefer DOI, publisher pages, institutional access, library links, open-access PDFs, and legal repository copies.
- CAPTCHA or login walls should be handled manually by the user.
- Treat social-media posts as discovery evidence, not academic literature, unless the research object is social-media discourse itself.
- Keep private drafts, API keys, passwords, and personally sensitive text out of third-party search APIs unless the user explicitly approves the risk.

## Example Output Skeleton

See [examples/output-skeleton.md](examples/output-skeleton.md).

## License

MIT License. See [LICENSE](LICENSE).
