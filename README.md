# Veridian

Veridian is an AI assistant that answers business data questions using verified, version-controlled metric definitions.

Standard RAG systems retrieve answers from documents using semantic similarity. When the same term is defined differently across documents, the AI returns whichever definition scored highest in the search. It might not necessarily be the correct one. In production evaluations, this causes incorrect answers in nearly 1 in 4 business intelligence queries.

Veridian adds Google's Open Knowledge Format (OKF) as a contract layer. Before retrieving anything, the AI checks the official definition of the metric being asked about. That definition governs what gets retrieved and how the answer is constructed.

## The Problem

AI assistants built on RAG retrieve text using semantic similarity, not correctness. When an organization has multiple, conflicting definitions of the same metric (for example, three different definitions of "revenue" across finance, product, and marketing documents), the AI returns whichever definition is closest in vector space. There is a possibility that it might not be the official one.

This is a documented problem. Research on enterprise RAG deployments shows that when the same term is defined inconsistently, even production-grade systems produce incorrect or conflicting answers. One evaluation of business intelligence queries found a 23% incorrect entity retrieval rate — nearly a quarter of answers referenced the wrong thing entirely.

The root cause is not the AI model. It is missing information architecture. There is no single source that tells the AI which definition is authoritative.