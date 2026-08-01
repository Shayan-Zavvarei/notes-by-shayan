# 1: First phase: Data Extraction 

Customer
   |
Channel Adapter
   |
Persian NLP (Natural Language Processing) Layer
   |
Entity Extraction
   |
Intent + Emotion + Urgency
   |
Orchestrator
   |
--------------------------------
# 2: Second Phase: Process data with agents/sub-agents

| Order Agent                 |
| Product Agent               |
| Payment Agent               |
| Complaint Agent             |
| Human Escalation Agent      |

--------------------------------
# 3: Third Phase: Generate answers

   |
Guardrails
   |
WooCommerce API
   |
Persian Response Generator

---
The existing pipeline is well-suited for a standard RAG architecture, but supporting Iranian users introduces additional challenges due to multilingual input patterns. Users may communicate in Persian script, Finglish, or a mixture of both, often with informal language, spelling variations, and non-standard writing styles.

To address this, the message-processing workflow should be extended with a Persian NLP preprocessing layer. This layer should include language identification, Persian/Finglish normalization, transliteration handling, typo correction, intent extraction, and entity recognition. The normalized and structured output can then be passed to the RAG pipeline, enabling more accurate retrieval, better context understanding, and higher-quality responses.