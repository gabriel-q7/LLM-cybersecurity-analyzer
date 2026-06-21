# Corpus Recomendado para Fases Futuras (RAG)

## Objetivo deste documento

Este documento lista os materiais de referência recomendados para compor a base de conhecimento externa do **Cybersecurity Incident Analyzer** nas fases futuras do projeto. Esses documentos não são utilizados na Fase 1 — nesta etapa, os modelos de NLP operam exclusivamente com seu conhecimento pré-treinado, sem nenhuma forma de recuperação documental.

A partir da Fase 2, esses materiais servirão de base para:

- geração de **embeddings** e indexação em um **banco de dados vetorial**;
- **busca semântica** (semantic search) sobre o conteúdo dos documentos;
- arquitetura **RAG (Retrieval-Augmented Generation)**, na qual trechos relevantes desses documentos são recuperados dinamicamente e fornecidos como contexto ao modelo generativo;
- produção de respostas **fundamentadas (grounded)** em fontes reconhecidas pela indústria, reduzindo o risco de alucinação observado na Fase 1.

---

## NIST

**Documentos recomendados:**

- **NIST Cybersecurity Framework (CSF)** — framework de referência amplamente adotado para gestão de risco de segurança cibernética, organizado em funções centrais (Identify, Protect, Detect, Respond, Recover).
- **NIST SP 800-61 — Computer Security Incident Handling Guide** — guia detalhado com o ciclo de vida de resposta a incidentes (preparação, detecção e análise, contenção/erradicação/recuperação, atividades pós-incidente).

**Por que são relevantes:**
Esses documentos fornecem a estrutura conceitual e a terminologia padrão para classificar incidentes e definir ações de resposta apropriadas. O SP 800-61, em particular, é a referência mais citada na indústria para procedimentos passo a passo de tratamento de incidentes — exatamente o tipo de conhecimento que faltou nas recomendações geradas na Fase 1.

---

## OWASP

**Documentos recomendados:**

- **OWASP Top 10** — lista das vulnerabilidades de segurança mais críticas em aplicações web, atualizada periodicamente pela comunidade.
- **OWASP Cheat Sheets** — guias práticos e objetivos sobre temas específicos (autenticação, validação de entrada, gestão de sessão, etc.).

**Por que são relevantes:**
Grande parte dos incidentes analisados no notebook (phishing, credential theft, brute force) está diretamente relacionada a vulnerabilidades de aplicação cobertas pelo OWASP. Esse corpus ajuda o sistema a sugerir mitigações técnicas específicas, não apenas genéricas.

---

## MITRE ATT&CK

**Documentos recomendados:**

- **ATT&CK Enterprise Matrix** — matriz de táticas e técnicas adversárias observadas em ambientes corporativos reais.
- **ATT&CK Techniques** — descrições detalhadas de técnicas individuais, incluindo exemplos de uso por grupos de ameaça conhecidos.

**Por que são relevantes:**
O MITRE ATT&CK fornece uma taxonomia padronizada da indústria para descrever **como** um ataque ocorre (táticas e técnicas), complementando a classificação por categoria já feita na Fase 1. Em fases futuras, isso permitirá mapear um incidente reportado em linguagem natural para técnicas ATT&CK específicas (ex: T1566 — Phishing).

---

## CISA

**Documentos recomendados:**

- **Incident Response Playbooks** (CISA) — playbooks oficiais com fluxos de resposta passo a passo para diferentes tipos de incidente.
- **Cybersecurity Advisories** — boletins regulares sobre ameaças ativas, vulnerabilidades exploradas e recomendações de mitigação.

**Por que são relevantes:**
Os playbooks da CISA são documentos práticos, orientados à ação — ideais para alimentar a etapa de geração de recomendações (Tarefa 3), substituindo o conhecimento genérico do modelo por procedimentos reconhecidos oficialmente por uma agência governamental de referência.

---

## CVE (Common Vulnerabilities and Exposures)

**Dados recomendados:**

- **Descrições de vulnerabilidades** — texto descritivo de cada CVE, incluindo componente afetado e natureza da vulnerabilidade.
- **Feeds CVE** (ex: NVD — National Vulnerability Database) — dados estruturados e atualizados continuamente, incluindo score CVSS e referências.

**Por que são relevantes:**
Incidentes de malware e exploração geralmente referenciam vulnerabilidades específicas. Ter acesso a um corpus atualizado de CVEs permite que o sistema correlacione um incidente reportado com vulnerabilidades conhecidas e sua severidade — informação que nenhum modelo pré-treinado pode garantir estar atualizada, já que novos CVEs são publicados diariamente.

---

## Resumo

| Fonte | Tipo de conhecimento agregado |
|---|---|
| NIST | Processo e estrutura de resposta a incidentes |
| OWASP | Vulnerabilidades e mitigações de aplicação |
| MITRE ATT&CK | Taxonomia de táticas e técnicas de ataque |
| CISA | Playbooks práticos e alertas oficiais |
| CVE/NVD | Vulnerabilidades específicas e atualizadas |

Esses cinco corpora, combinados, formam uma base de conhecimento abrangente — cobrindo desde o **processo** de resposta a incidentes até o **detalhe técnico** de vulnerabilidades específicas — que será explorada na arquitetura RAG da Fase 2.
