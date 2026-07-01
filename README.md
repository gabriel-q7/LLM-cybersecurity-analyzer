# Cybersecurity Incident Analyzer

Projeto de apoio à triagem de incidentes de segurança da informação com foco em experimentos de NLP e LLMs aplicados à cibersegurança.

Este repositório usa **exclusivamente modelos open source disponíveis no Hugging Face**. Esse requisito vale para todas as fases do projeto. Não fazem parte do escopo modelos proprietários ou APIs fechadas de terceiros.

## Política de modelos

- Apenas modelos **open source** hospedados ou distribuídos via **Hugging Face** serão utilizados neste projeto.
- A Fase 1 usa modelos clássicos de NLP do ecossistema Hugging Face.
- A Fase 2 usa um modelo instruído open source do Hugging Face para os experimentos de prompt engineering.
- O projeto não depende de Anthropic, Claude, OpenAI nem qualquer outro modelo proprietário.

## Estrutura do projeto

```text
project/
│
├── data/
│   └── incidents.json                                 # Dataset compartilhado entre as fases
│
├── notebooks/
│   ├── phase1_cybersecurity_incident_analyzer.ipynb   # Notebook principal da Fase 1
│   └── phase2_prompt_engineering.ipynb                # Notebook principal da Fase 2
│
├── docs/
│   └── recommended_corpus.md                          # Materiais recomendados para a futura fase de RAG
│
├── requirements.txt
└── README.md
```

## Fases atuais

### Fase 1

Sistema inicial para triagem de incidentes com modelos pré-treinados do Hugging Face, focado em sumarização e extração estruturada, sem RAG, embeddings ou recuperação documental.

Entregas da Fase 1:

1. **Sumarização** de relatos de incidentes com `facebook/bart-large-cnn`
2. **Extração com NER** retornando diretamente as entidades reconhecidas pelo modelo pré-treinado
3. Demonstração de **tokenização** e explicação das arquiteturas relevantes ao escopo
4. Inspeção dos tipos de entidades reconhecidos ao longo do dataset
5. Discussão de limitações observadas, motivando as fases futuras

### Fase 2

Notebook voltado a **prompt engineering** e saídas estruturadas em JSON para triagem de incidentes, agora usando **somente modelo open source do Hugging Face**.

Entregas da Fase 2:

1. Comparação entre **RCTOF**, **Guided Chain of Thought** e **Meta Prompting**
2. Geração de respostas estruturadas em JSON
3. Validação rígida com **Pydantic**
4. Comparação de consistência e uso de tokens entre as técnicas

## Como executar

### Opção recomendada: Google Colab

1. Clone o repositório dentro do runtime do [Google Colab](https://colab.research.google.com/) ou faça upload do notebook junto com `data/incidents.json`.
2. Ative o runtime com GPU: `Ambiente de execução > Alterar o tipo de ambiente de execução > GPU (T4 ou superior)`.
3. Execute as células em sequência, de cima para baixo (`Ambiente de execução > Executar tudo`).

Exemplo:

```python
!git clone https://github.com/gabriel-q7/LLM-cybersecurity-analyzer.git
%cd /content/LLM-cybersecurity-analyzer
!pip install -r requirements.txt
```

> A Fase 2 baixa um modelo open source do Hugging Face na primeira execução. Em CPU, o notebook continua funcional, mas a geração pode ficar significativamente mais lenta.

### Opção alternativa: ambiente local

```bash
# Crie e ative um ambiente virtual (recomendado)
python3 -m venv venv
source venv/bin/activate  # Linux/Mac
# venv\Scripts\activate   # Windows

# Instale as dependências
pip install -r requirements.txt

# Inicie o Jupyter
jupyter notebook
```

Abra então o notebook de interesse:

- `notebooks/phase1_cybersecurity_incident_analyzer.ipynb`
- `notebooks/phase2_prompt_engineering.ipynb`

## Dataset

O projeto utiliza um dataset local de **10 incidentes fictícios** em linguagem natural, centralizado em `data/incidents.json`. Todos os dados são fictícios e foram criados exclusivamente para este repositório.

## Diretriz de evolução

As próximas fases continuarão seguindo a mesma restrição arquitetural: **somente modelos open source do Hugging Face** serão adotados no projeto.
