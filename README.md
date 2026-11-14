# Wiktor Wojtarowicz

I build LLM systems and the parts around them that decide whether they hold up in production:
what an agent may do, what it may read, what it leaves behind, and what happens when a process
dies halfway. Python and TypeScript. Poland, open to remote work.

## Selected work

| Project | What it does | Evidence |
|---|---|---|
| [permissioned-rag](https://github.com/WWIntegrations/permissioned-rag) | Question answering where each caller sees only the documents they may read: PostgreSQL row-level security inside hybrid retrieval, every quoted citation checked against the text the model was given | 0 chunks from outside the caller's permissions in 1.94M returned on FiQA (57,638 documents); revocation visible on the first query after commit; Claude Haiku 5.5 87% valid citations and 10/10 refusals on swapped context, against 14% and 0/10 for a local 1.7B model |
| [ww-scraper](https://github.com/WWIntegrations/ww-scraper) | Local scraping framework: request queue, datasets, schemas, tasks and schedules, API with Python and JS clients, web console, browser actions, opt-in MCP server, 21 actors including job boards, OpenStreetMap places, product catalogs and contact details | 200-page crawl in 103 s with 42 MB and no cost, against 105 s with 1.8 GB on a hosted scraping platform's 4 GB tier; product fields checked against known answers in 12 shop markup encodings (71% right before the fixes, 100% after); 458 tests; used to audit 150 local business sites; strict robots.txt, SSRF guard on every hop, personal data masked by default |
| [guard-generalization-study](https://github.com/WWIntegrations/guard-generalization-study) | How often a frozen prompt-injection classifier blocks harmless prompts | Qwen3-1.7B base and a LoRA variant on 339 NotInject prompts: 42.8% and 37.4% false positives in the primary cohort, paired test, Wilson intervals, the negative result reported as found |
| [webhook-reliability-gateway](https://github.com/WWIntegrations/webhook-reliability-gateway) | Signed webhook ingress with a durable inbox and at-least-once delivery that ends in exactly one effect | A demo that kills the delivery worker mid-request; leases with fencing tokens, `Retry-After`, dead letters and replay |
| [agent-audit-ledger](https://github.com/WWIntegrations/agent-audit-ledger) | Hash-chained audit trail for agent runs, verified against a checkpoint someone else kept | Crash tests that kill the writer process and check what survives |
| [mcp-contract-auditor](https://github.com/WWIntegrations/mcp-contract-auditor) | Which MCP tool contracts changed between two server versions and which changes break callers | Reads recorded `tools/list` transcripts; classifies each schema change |
| [realtime-voice-handoff](https://github.com/WWIntegrations/realtime-voice-handoff) | Cutting off live audio and handing conversation state to another role over WebRTC | The handoff counts only after a matching acknowledgement comes back |

## Production work

Client systems I built and run are private. Among them: an LLM product-advice assistant live on
an online store, checked against an exam set and a 28-case red-team suite before release, plus
web applications with row-level security, CSP and automated quality gates.
More at [wiktorwojtarowicz.pl](https://wiktorwojtarowicz.pl).
