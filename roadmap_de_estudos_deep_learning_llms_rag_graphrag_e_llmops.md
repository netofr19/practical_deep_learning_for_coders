# Roadmap de Engenharia: Deep Learning, LLMs, RAG, GraphRAG e LLMOps

Este documento define o pipeline sequencial de estudos e implementação prática. O objetivo é evitar a dispersão entre múltiplos materiais, mantendo **apenas uma referência principal por etapa** e consolidando cada módulo em um único repositório evolutivo.

---

## Regras de Execução
- **Foco Único:** Não inicie a leitura ou implementação da próxima etapa antes de concluir o entregável prático da etapa atual.
- **Código Replicável:** Todo conceito estudado deve ser implementado localmente em ambiente isolado (Conda/venv) e versionado neste repositório.
- **Evolução Contínua:** Cada etapa aproveita os componentes construídos na anterior.

---

## Etapa 1: Fundações de Deep Learning e PyTorch (Semanas 1 a 3)
**Objetivo:** Dominar tensores, autograd, loops de treinamento customizados e arquiteturas neurais sem abstrações excessivas.

### Material de Referência
- **Livro Principal:** *Deep Learning with PyTorch* (Eli Stevens, Luca Antiga, Thomas Viehmann)

### Checklist de Progresso
- [ ] Configurar ambiente Conda dedicado com suporte a GPU/CPU e estrutura base do repositório.
- [ ] Dominar manipulação de tensores, *broadcasting* e mecânica de *autograd*.
- [ ] Implementar `Dataset` e `DataLoader` customizados para ingestão de dados.
- [ ] Construir e treinar uma arquitetura neural do zero em PyTorch (loop de treino/validação manual).
- [ ] **Entregável:** Pipeline de treinamento funcional com logging de métricas, *checkpointing* e avaliação reproduzível.

---

## Etapa 2: Arquitetura de LLMs e Transformers por Dentro (Semanas 4 a 6)
**Objetivo:** Compreender o funcionamento interno dos Transformers para diagnosticar falhas de contexto, atenção, tokenização e custos de memória/inferência.

### Material de Referência
- **Livro Principal:** *Build a Large Language Model (From Scratch)* (Sebastian Raschka)
- **Apoio Aplicado:** *Hands-On Large Language Models* (Jay Alammar & Maarten Grootendorst)

### Checklist de Progresso
- [ ] Implementar tokenização (BPE) e camadas de embeddings posicionais.
- [ ] Codificar o mecanismo de *Causal Multi-Head Self-Attention* do zero.
- [ ] Montar a arquitetura completa estilo GPT e executar um loop de pré-treino em escala reduzida.
- [ ] Aplicar técnicas de ajuste fino eficiente em parâmetros (LoRA / QLoRA) em um modelo *open-weights*.
- [ ] **Entregável:** Módulo funcional de Transformer implementado do zero + script de fine-tuning (LoRA) documentado.

---

## Etapa 3: RAG Avançado e Engenharia de Contexto (Semanas 7 a 9)
**Objetivo:** Evoluir de pipelines vetoriais simples para sistemas híbridos resilientes a documentos densos, tabelas e referências cruzadas.

### Material de Referência
- **Livro Principal:** *The Architecture of AI Agents and LLM Systems* (Aleksandr Drobiazkin)
- **Apoio Técnico:** Artigos práticos do *Daily Dose of Data Science* (foco em *Hybrid Search*, *Reranking* e *Contextual Retrieval*)

### Checklist de Progresso
- [ ] Implementar estratégias avançadas de *chunking* (semântico / contextual) preservando metadados estruturais.
- [ ] Construir pipeline de **Busca Híbrida** combinando busca densa (vetorial) e busca esparsa (BM25).
- [ ] Integrar um modelo de *Cross-Encoder Reranker* para reordenação dos documentos recuperados.
- [ ] Estruturar suíte de avaliação automatizada medindo *Context Precision*, *Context Recall* e *Faithfulness* (ex.: Ragas ou DeepEval).
- [ ] **Entregável:** Pipeline de RAG Híbrido com Reranking e relatório quantitativo de avaliação de recuperação.

---

## Etapa 4: GraphRAG e Bancos Orientados a Grafos (Semanas 10 a 12)
**Objetivo:** Resolver problemas de raciocínio *multi-hop* (múltiplos saltos entre entidades) e síntese global onde a busca vetorial perde o vínculo estrutural.

### Material de Referência
- **Documentação & Guias:** *Neo4j GraphRAG Python Package* (`neo4j-graphrag-python`) e guias oficiais de padrões arquiteturais de GraphRAG (*Schema Injection*, *Text2Cypher* e *Hybrid Vector + Graph*).

### Checklist de Progresso
- [ ] Subir instância local do Neo4j (via Docker) e modelar a ontologia/schema inicial do domínio.
- [ ] Construir pipeline de extração de entidades e relacionamentos via LLM (com resolução de entidades duplicadas) para popular o grafo.
- [ ] Implementar recuperadores baseados em grafo (*Text2Cypher* com *Schema Injection* e travessia por vizinhança).
- [ ] Criar um roteador de consultas (*Query Router*) que decide entre busca vetorial, busca em grafo ou abordagem híbrida paralela.
- [ ] **Entregável:** Sistema GraphRAG funcional integrando Neo4j + busca vetorial com roteamento dinâmico de consultas.

---

## Etapa 5: LLMOps, Inferência e Sistemas em Produção (Semanas 13 a 16)
**Objetivo:** Transicionar o sistema do ambiente de desenvolvimento para arquitetura de produção com foco em latência, gerenciamento de memória, observabilidade e avaliação contínua.

### Material de Referência
- **Arquitetura Sistêmica:** *Designing Machine Learning Systems* (Chip Huyen)
- **Engenharia de Inferência:** *Inference Engineering* (Philip Kiely)

### Checklist de Progresso
- [ ] Otimizar o *serving* de modelos locais avaliando quantização, *KV-cache*, *throughput* vs. latência (ex.: vLLM ou Ollama).
- [ ] Expor o pipeline GraphRAG/RAG através de uma API padronizada e empacotar todos os serviços via `docker-compose`.
- [ ] Instrumentar observabilidade e *tracing* ponta a ponta (ex.: Langfuse ou Arize Phoenix) para rastrear latência por etapa, consumo de tokens e qualidade das respostas.
- [ ] Implementar testes de regressão e guardrails de entrada/saída no fluxo de CI/CD.
- [ ] **Entregável:** Aplicação completa conteinerizada em Docker com inferência otimizada, painel de observabilidade e testes automatizados.

---

## Log de Progresso
| Etapa | Data Início | Data Conclusão | Branch / Tag no Repo | Notas e Aprendizados |
| :--- | :---: | :---: | :---: | :--- |
| 1. PyTorch & DL | - | - | - | - |
| 2. LLMs & Transformers | - | - | - | - |
| 3. RAG Avançado | - | - | - | - |
| 4. GraphRAG & Neo4j | - | - | - | - |
| 5. LLMOps & Produção | - | - | - | - |