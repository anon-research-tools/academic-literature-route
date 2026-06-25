---
name: 学术论文搜索
description: 用于围绕一个选题、申报题名、综述或论文草稿收集、路线规划、筛选和整理海内外学术论文。覆盖检索式扩展、OpenAlex/Crossref/Semantic Scholar/Kimi/TinyFish/AnySearch/Grok/X 式机器检索、中文数据库补查、海外索引补查、重点期刊复核和 A/B/C/D 文献分级。
---

# Academic Literature Route

Use this skill to turn a topic, draft title, grant proposal, or literature-review question into a traceable literature-search route and screened bibliography. The goal is not just to list papers, but to show how Chinese and overseas literature was found, where it still needs manual checking, and which items can support writing.

## Workflow

1. Parse the topic into four term groups:
   - Research object: texts, people, institutions, corpus, period, region.
   - Field: religious studies, linguistics, digital humanities, library and information science, history, philology, etc.
   - Problem frame: sinicization, transmission, institutional change, knowledge production, reception, comparison.
   - Method terms: bibliography, corpus, database, text mining, knowledge graph, citation analysis.

2. Generate search strings in layers:
   - Exact title plus `论文`.
   - Object + problem frame.
   - Object + field.
   - Object + method.
   - Synonyms and historical terms.
   - English equivalents.
   - `site:` queries for high-value databases and journal platforms.

3. Machine retrieval and lead expansion, when available:
   - OpenAlex for open academic metadata.
   - Crossref for DOI and publisher metadata.
   - Semantic Scholar, when available, for abstracts, summaries, citation graph, related papers, and PDF links.
   - Kimi Web Search for Chinese scholarly web leads.
   - TinyFish Search API for structured web search and site-directed Chinese database pages.
   - AnySearch, when installed, for real-time general web search, academic vertical search, batch query expansion, DOI/topic lookup, and page extraction.
   - Grok/X search, usually through OpenRouter or a local X/Twitter-capable workflow, for X/Twitter-native leads such as new preprints, author announcements, conference discussions, dataset/tool releases, and recent peer commentary.
   - Treat LLM, web, and social results as leads, not bibliographic truth. Promote them to cite candidates only after verifying title, author, year, venue, DOI/URL, and full-text availability through academic metadata, publisher pages, repositories, or database records.

4. Manual follow-up route:
   - Chinese: CNKI, Wanfang, CQVIP, NCPSSD, CSSCI lists, Peking University Core lists, Jikan, Airiti.
   - Overseas indexes: Web of Science Core Collection, A&HCI, SSCI, Scopus, MLA International Bibliography, LLBA, DOAJ, JSTOR, Project MUSE.
   - Publisher platforms: Springer Nature, Taylor & Francis, SAGE, Wiley, Oxford Academic, Cambridge Core, Brill, De Gruyter, ACL Anthology.
   - Browser-assisted modules, when available: CNKI search/detail/journal indexing/export; Google Scholar discovery, citation tracking, and BibTeX/Zotero export.

5. Journal-directed checks:
   - Buddhist/religious studies: World Religion Studies, Studies in World Religions, Journal of the International Association of Buddhist Studies, Buddhist Studies Review, Journal of Chinese Religions, History of Religions, Numen, Religions.
   - Linguistics: 中国语文, 当代语言学, 语言科学, Language, Linguistic Inquiry, Journal of Linguistics, Lingua, Diachronica, Journal of Chinese Linguistics.
   - Digital humanities and LIS: 数字人文, 情报学报, 图书情报工作, Digital Scholarship in the Humanities, Digital Humanities Quarterly, Journal of Cultural Analytics, JASIST, Journal of Documentation.

6. Grade every result:
   - A: verified, directly useful, cite candidate.
   - B: plausible and worth close reading.
   - C: background or peripheral literature.
   - D: duplicate, book/news/wiki/column/search page, or off-topic.
   - X/Twitter-only or LLM-only hits cannot be A. Keep them as B or C until verified through a stable scholarly source.

7. Add citation-chaining when at least one strong seed paper is found:
   - Backward chaining: inspect the references cited by the seed paper.
   - Forward chaining: inspect later papers that cite the seed paper.
   - Similar-paper expansion: use related-work/recommendation tools such as Semantic Scholar, ResearchRabbit, Connected Papers, or Litmaps when available.
   - Google Scholar `data-cid` style cluster IDs are useful for tracking cited-by pages and cross-referencing results.
   - Stop when newly found papers are mostly duplicates, low relevance, or outside the target field.

8. Keep a PRISMA-S-style audit trail for serious review tasks:
   - Database or source name.
   - Exact search string as run.
   - Date searched.
   - Filters or limits used, such as year, language, document type, or field.
   - Number of records found.
   - Number retained after deduplication and screening.
   - Reason for excluding important-looking records.
   - For Grok/X leads, record the query, date range if used, handle or post URL when available, and the later scholarly source used for verification.

9. Peer-check the search strategy before treating it as complete:
   - Does each key concept have synonyms and Chinese/English variants?
   - Are Boolean operators, phrase quotes, truncation, and field limits appropriate for the database?
   - Are any limits justified rather than arbitrary?
   - Are known seed papers recoverable by the search? If not, revise the query.
   - Are database-specific syntaxes translated correctly instead of pasted blindly?

10. Use browser-assisted database workflows conservatively:
   - CNKI browser search can supplement API/web results with structured search results, article details, abstracts, keywords, fund info, journal levels, and GB/T 7714-style citation export.
   - Google Scholar browser search can supplement broad discovery, citation counts, forward-citation tracking, full-text links, and BibTeX export.
   - CAPTCHA or login walls must be handled manually by the user; stop and ask the user to complete verification instead of retrying automatically.
   - Do not use unauthorized full-text routes. Prefer DOI, publisher pages, institutional access, library links, open-access PDFs, and legal repository copies.

11. Use Grok/X search as a social-signal layer:
   - Use it when the topic is fast-moving, preprint-heavy, tool/dataset-centered, or likely to be discussed by authors and labs before formal indexing.
   - Prefer queries that combine the topic with `paper`, `preprint`, `arXiv`, `DOI`, `dataset`, `benchmark`, author names, project names, or venue acronyms.
   - Read API credentials only from environment variables or private credential stores.
   - Do not cite tweets as academic literature unless the user is explicitly studying social-media discourse. For ordinary literature reviews, tweets are discovery evidence and should point to a paper, dataset, project page, repository, or author profile.
   - Keep social signals separate from peer-reviewed or database-indexed results in the output table, and mark their verification status.

## LLM Search Roles

- Kimi: use for Chinese-language scholarly web discovery, article-title expansion, institution/journal pages, Chinese reports, and CNKI/Wanfang/CQVIP lead finding. Verify final records in academic databases or publisher/journal pages.
- AnySearch: use for fast real-time web discovery, broad academic vertical search, DOI/topic probing, and batch expansion across several independent search strings. Treat AnySearch hits as `anysearch_lead` until confirmed through OpenAlex, Crossref, Semantic Scholar, PubMed, DOI/publisher pages, repositories, CNKI/Wanfang/CQVIP, or Google Scholar.
- Grok/X: use for X/Twitter-native discovery of recent papers, preprints, datasets, tools, benchmark releases, author self-announcements, lab threads, and conference chatter. Verify final records through DOI, arXiv, Zenodo, OSF, GitHub release pages, publisher pages, OpenAlex, Crossref, Semantic Scholar, or Google Scholar.
- TinyFish/general web search: use for structured web coverage and site-directed queries. Treat results as discovery leads until the bibliographic record is stable.
- Do not merge these sources into one confidence level. Record `source_type` as `academic_metadata`, `database_record`, `publisher_page`, `repository`, `anysearch_lead`, `llm_web_lead`, or `x_social_lead`.

## Verification Loop

For every LLM or X/Twitter lead:

1. Extract the claimed paper/project title, author names, venue, year, DOI/arXiv/repository link, and who posted it.
2. Search stable scholarly sources for the same item.
3. Normalize the bibliographic record from the stable source, not from the LLM/tweet text.
4. Grade the item only after verification. Unverified social leads stay B/C and should not enter the direct-citation list.
5. Keep the social post or LLM result as provenance in the audit log, not as the citation source.

For every AnySearch lead:

1. Record the exact AnySearch command or query object, including `domain`, `sub_domain`, `content_types`, `freshness`, and `max_results` when used.
2. If using a vertical domain, call `list_domains` first and follow the returned query constraints rather than inventing natural-language parameters.
3. Confirm the bibliographic record through a stable scholarly source before assigning grade A.
4. Use AnySearch `extract` only for non-sensitive URLs and only when snippets are insufficient for screening or provenance.
5. Do not send private drafts, API keys, passwords, or personally sensitive text to AnySearch.

## Credential Lookup

Prefer environment variables first, then a private credential store such as macOS Keychain, 1Password, or the secret manager used by your agent runtime:

- Kimi / Moonshot: `KIMI_API_KEY` or `MOONSHOT_API_KEY`.
- TinyFish: `TINYFISH_API_KEY`.
- AnySearch: `ANYSEARCH_API_KEY`; anonymous access may be available with lower rate limits.
- Grok / OpenRouter: `OPENROUTER_API_KEY`.

Do not copy keys into prompts, reports, scripts, examples, command history, or project docs. If a key was pasted into chat, use it only to store/update the private credential location and recommend rotation.

When reporting results to the user, say which source layer was used, such as `Kimi lead`, `TinyFish lead`, `AnySearch lead`, `Grok/X lead`, `OpenAlex verified`, or `Crossref verified`. This keeps discovery signals separate from citeable bibliography.

## Output Shape

For substantial tasks, create or return these sections:

1. Search terms: Chinese, English, and site-directed.
2. Source coverage: machine sources, Chinese manual sources, overseas manual sources.
3. Candidate literature table: title, authors, year, venue, URL/DOI, source, hit query, grade, note.
4. Direct-citation candidates.
5. Next close-reading queue.
6. Manual follow-up checklist.
7. Citation-chaining expansion from seed papers.
8. Search audit log with exact database queries and hit counts.
9. Excluded-result rules and examples.
10. Social/X lead table when Grok/X search was used: post or handle, date, claimed paper/project, verification source, status.
11. Verification table for LLM/social leads: claimed item, stable source checked, bibliographic fields confirmed, remaining uncertainty.
12. AnySearch audit rows when used: query, domain/sub_domain, filters, result count, retained records, verification source.
13. Optional export path: RIS/BibTeX/Zotero/GB/T 7714 when browser-assisted tools are available.

## Key Safety Rule

Never put raw API keys in public Markdown, frontend code, command history, or shareable reports. Refer to environment variable names such as `KIMI_API_KEY`, `MOONSHOT_API_KEY`, `TINYFISH_API_KEY`, `ANYSEARCH_API_KEY`, and `OPENROUTER_API_KEY`; only store real keys in private local environment files, system keychains, or server environment variables.
