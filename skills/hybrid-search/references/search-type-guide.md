# Search Type Selection Guide

## Vector Search Only (`SearchType.VECTOR`)
Best for semantic/conceptual queries, cross-lingual search, and synonym matching.
**Strong at:** synonym matching ("AI" → "machine learning"), paraphrasing, conceptual similarity.
**Weak at:** specific keywords, exact phrases, error codes, technical terms.

## Text Search Only (`SearchType.TEXT`)
Best for exact keyword matching, error messages, code search, and structured data.
**Strong at:** exact keywords, technical terms, error codes.
**Weak at:** synonyms, paraphrasing, conceptual queries.

## Hybrid Search (`SearchType.HYBRID`) — Recommended
Combines both vector and text search for best overall retrieval quality.
**Strong at:** general-purpose search, mixed keyword + semantic needs, unknown query patterns.
