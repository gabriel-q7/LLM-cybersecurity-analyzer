# Cybersecurity Incident Analyzer — Fase 1

Sistema de apoio à triagem de incidentes de segurança da informação utilizando modelos de NLP pré-treinados (Hugging Face). Este repositório contém a **Fase 1** do projeto, focada em sumarização e extração estruturada de informações, sem RAG, embeddings ou recuperação documental, que serão introduzidos em fases futuras.

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
2. **Extração com NER** retornando diretamente as entidades reconhecidas pelo modelo pré-treinado
3. Demonstração de **tokenização** e explicação das arquiteturas relevantes ao novo escopo
4. Inspeção dos tipos de entidades reconhecidos ao longo do dataset
5. Discussão de limitações observadas, motivando as fases futuras

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

> Em CPU, a execução continua possível, mas a sumarização e a extração com NER podem levar mais tempo ao processar todo o dataset.

## Dataset

O notebook utiliza um dataset local de **10 incidentes fictícios** em linguagem natural. Todos os dados são fictícios, criados exclusivamente para esse projeto.
