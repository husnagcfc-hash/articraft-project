**Selected retriever: `mmr`** (MRR 0.938, Hit@3 1.00, Prec@3 0.38, 157 ms/query).
- Automatic winner by MRR was `mmr` (MRR 0.938).
- vs. dense baseline: MRR +0.000, latency x1; paired 95% interval [+0.000, +0.000] -> NOT distinguishable from dense retrieval on this dev set: a cost/benefit judgement.
- Plain hybrid (RRF) scored MRR 0.917 vs dense 0.938: fusing BM25 only helps when the lexical ranking is competitive; the cross-encoder is what re-sorts the fused pool.
- Multi-query adds an LLM call per question (see latency); paraphrases from a small model are often near-duplicates, so its recall benefit is small relative to its cost.
- Precision@3 is bounded above by design: only chunks within +-1 page of the gold page count as relevant.
- Caveat: dev questions are partly synthetic and favour lexical overlap; differences of a few MRR points should not be over-read.