# Query Variant Generation Strategies

Multi-query uses heuristic rules to generate query variants (no LLM required by default).

## Keyword Variant (Stopword Removal)

Removes common stopwords (`a, an, the, for, from, in, is, of, on, to, was, with...`) to focus on key terms. Enabled by default via `config.search.include_keyword_variant = True`.

**Example:** `"how to improve the customer satisfaction"` → `"how improve customer satisfaction"`

## OR Variant (Boolean Expansion)

Creates Boolean OR of non-stopword terms. Only generated for multi-word queries.

**Example:** `"customer retention strategies"` → `"customer OR retention OR strategies"`

## Quoted Phrase Variant (Exact Match)

Wraps query in quotes for exact phrase matching. Only generated for multi-word queries.

**Example:** `"machine learning deployment"` → `"\"machine learning deployment\""`

## Custom LLM-Based Expansion

Provide a custom callback for semantic query diversity:

```python
from llmemory.query_expansion import QueryExpansionService

async def my_llm_expander(query: str, max_variants: int) -> list[str]:
    variants = await my_llm.generate_variants(query, max_variants)
    return variants

service = QueryExpansionService(
    search_config=config.search,
    llm_callback=my_llm_expander  # Tried first; heuristics used as fallback
)
```
