# Cybersecurity Incident Analyzer — Fase 1

Sistema de apoio à triagem de incidentes de segurança da informação utilizando modelos de NLP pré-treinados (Hugging Face). Este repositório contém a **Fase 1** do projeto, focada em sumarização, classificação zero-shot e geração de recomendações — sem RAG, embeddings ou recuperação documental, que serão introduzidos em fases futuras.

## Estrutura do projeto

```text
project/
│
├── notebooks/
│   └── phase1_cybersecurity_incident_analyzer.ipynb   # Notebook principal da Fase 1
│
├── docs/
│   └── recommended_corpus.md                          # Materiais recomendados para a Fase de RAG
│
├── requirements.txt
└── README.md
```

## O que esta fase entrega

1. **Sumarização** de relatos de incidentes (`facebook/bart-large-cnn`)
2. **Classificação Zero-Shot** da categoria do incidente (`facebook/bart-large-mnli`)
3. **Geração de recomendações** de resposta inicial (`google/flan-t5-large`)
4. Demonstração de **tokenização** e explicação de **arquiteturas** de modelos de linguagem (encoder-only, decoder-only, encoder-decoder)
5. Experimentos com parâmetros de geração (`temperature`, `max_new_tokens`)
6. Discussão de limitações observadas, motivando a Fase 2 (RAG)

> **Nota sobre o modelo de geração:** a especificação original sugeria `microsoft/Phi-3-mini-4k-instruct` para a Tarefa 3. Neste notebook, optamos por `google/flan-t5-large` como alternativa mais leve, adequada a GPUs de menor porte (ex: T4 no Google Colab). Para usar o Phi-3-mini, basta trocar o nome do modelo na célula correspondente e ajustar o pipeline para `text-generation` com `AutoModelForCausalLM`.

## Como executar

### Opção recomendada: Google Colab

1. Faça upload do notebook `notebooks/phase1_cybersecurity_incident_analyzer.ipynb` para o [Google Colab](https://colab.research.google.com/).
2. Ative o runtime com GPU: `Ambiente de execução > Alterar o tipo de ambiente de execução > GPU (T4 ou superior)`.
3. Execute as células em sequência, de cima para baixo (`Ambiente de execução > Executar tudo`).

### Opção alternativa: ambiente local

```bash
# Crie e ative um ambiente virtual (recomendado)
python3 -m venv venv
source venv/bin/activate  # Linux/Mac
# venv\Scripts\activate   # Windows

# Instale as dependências
pip install -r requirements.txt

# Inicie o Jupyter
jupyter notebook notebooks/phase1_cybersecurity_incident_analyzer.ipynb
```

> Em CPU, a Tarefa 3 (geração com `flan-t5-large`) pode ser mais lenta. Caso necessário, troque para `google/flan-t5-base`, mais leve.

## Dataset

O notebook utiliza um dataset local de **10 incidentes fictícios**, cobrindo as categorias: Phishing, Ransomware, Malware, Credential Theft, Insider Threat, Brute Force Attack e DDoS. Todos os dados são fictícios, criados exclusivamente para fins didáticos.
