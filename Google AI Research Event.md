# Agenda
1. Learn to Spell: **Prompt Engineering** 
	1. Prompts are magic spells
	2. LM are far from perfect
	3. Prompting techniques

## Prompt Engineering
A "prompt" is basically text that goes into a Language Model
*Prompt Engineering* is the art of designing the text
### 1
- Prompts are not new tech. Questions asked on search engines are similar to such prompts
- LMs are statistical models of text.
**Model Training** 
- Pre-training - Self-supervised on a lot of examples. O(Trillion) > GPT3
- Fine tuning - Enhanced for particular interactions. O(1000) to O(M) examples > MedPaLM
- Prompt-tuning - Steered for focused tasks. O(100) examples > Bard, Chat-GPT
- Prompting - Steered for a query
- LLM are large libraries of documents, containing text it saw during training
- Prompting re-weights those documents
## 2
Language models see vectors, not text. The text is represented by tokens
LMs operate better on structured text. eg when given a code template and asked to complete it, it would work better as compared to having to generate the full code