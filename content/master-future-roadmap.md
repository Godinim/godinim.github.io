---
publish: true
title: Master Future Roadmap Checklist
created: 2026-05-27T00:45:47.863+08:00
modified: 2026-05-27T00:47:28.399+08:00
---

# [[2025/blog-posts-with-obsidian.md|blog-posts-with-obsidian]]

```
- [ ] Add a clearer content taxonomy for projects, blog posts, and evergreen notes
- [ ] Customize the Quartz theme so the site feels more portfolio-oriented
- [ ] Create a publishing checklist for metadata, tags, and screenshots before syncing
```

# [[2025/private-rag-document-scanner-base.md|private-rag-document-scanner-base]]

```
- [ ] Add reranking stage (FlashRank or bge-reranker-v2-m3) for improved retrieval quality
- [ ] Integrate knowledge graph (LightRAG or Neo4j) for entity-aware multi-hop queries
- [ ] Implement Cog-RAG iterative probing for hard questions
- [ ] Add document classification and routing by document type
- [ ] Build a Streamlit or custom dashboard for collection management
```

# [[2026/llm-model-selection.md|llm-model-selection]]

```
- [ ] Build a cost-tracker dashboard that logs per-model cost, quality, and latency for your actual workloads
- [ ] Implement automatic model routing — small/cheap model for easy queries, escalate to expensive model for hard ones
- [ ] Test Qwen3-Coder-Next's 256K context against Claude's 200K for repository-scale understanding
- [ ] Evaluate new dense/MoE hybrids as they release — the line is blurring (e.g., 80B/3B MoE is practically dense-like for inference)
- [ ] Track the emerging "agentic model" category — models fine-tuned specifically for tool use and multi-step reasoning
```

# [[2026/local-llm-guide-AMD-RX-7800-XT.md|local-llm-guide-AMD-RX-7800-XT]]

```
- [ ] Run real benchmarks on this hardware — publish actual t/s, VRAM usage, and model quality scores
- [ ] Test Qwen3-Coder-Next in hybrid mode (GPU for active experts, CPU for inactive)
- [ ] Compare vLLM vs llama.cpp vs Ollama serving performance on the same models
```

# [[2026/private-rag-document-scanner-upgraded.md|private-rag-document-scanner-upgraded]]

```
- [ ] Implement with the OpenSearch + Neo4j stack (3 search modes, 6 retrieval strategies)
- [ ] Test NexusRAG — combines vector search, KG, cross-encoder in one package
- [ ] Evaluate docpipe SDK — unified pipeline SDK with 6 RAG strategies (naive, hyde, multi_query, parent_document, hybrid, auto)
- [ ] Benchmark: real accuracy comparison on your document collection
- [ ] Add agentic routing — use a small LLM to classify query difficulty and route to base vs upgraded pipeline
```

# [[2026/terminal-coding-agents-showdown.md|terminal-coding-agents-showdown]]

```
- [ ] Real hardware benchmarks on RX 7800 XT (16GB) — compare Qwen3.6-27B, Qwen3-Coder-Next, DeepSeek V4-Flash across agents
- [ ] Test Claude Code sub-agent workflow against OpenCode parallel agent teams
- [ ] Evaluate Codex CLI's cloud sandbox for CI/CD integration vs local-only approaches
- [ ] Monitor OpenCode's ACP protocol adoption as a standard for agent-client communication
- [ ] Track Qwen3-Coder-Next improvements — it's the most rapidly improving local coding model
```
