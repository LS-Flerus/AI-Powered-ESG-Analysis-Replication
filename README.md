# AI-Powered ESG Analysis Replication 📊🌱

[![Python Version](https://img.shields.io/badge/python-3.12-blue.svg)](https://www.python.org/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/github/LS-Flerus/AI-Powered-ESG-Analysis-Replication/blob/main/ESG_Replication_Pipeline.ipynb)

Este repositório contém a reprodução computacional estrita e auditoria científica do pipeline de Processamento de Linguagem Natural (PLN) e Aprendizado de Máquina proposto originalmente por **Magotra et al. (2026)** ((https://doi.org/10.1038/s41598-026-49931-z)). 

O objetivo principal deste projeto é validar de forma independente a consistência, estabilidade e reprodutibilidade do ecossistema técnico projetado para monitorar métricas Ambientais, Sociais e de Governança (ESG) em relatórios corporativos de fábricas de vestuário certificadas pela LEED em Bangladesh.

---

## 🚀 Arquitetura do Pipeline

O fluxo de processamento foi auditado e consolidado nas seguintes etapas:

1. **Pré-processamento de Linguagem Natural (NLP):** Limpeza de ruído textual, tokenização, remoção de stopwords específicas do domínio corporativo e lematização utilizando a biblioteca `SpaCy`.
2. **Modelagem de Tópicos Comparativa:** 
   * Extração de macrotemas utilizando o algoritmo **LDA** (*Latent Dirichlet Allocation*).
   * Extração e separação semântica determinística utilizando o algoritmo **NMF** (*Non-Negative Matrix Factorization*) com inicialização **NNDSVD** (*Non-negative Double Singular Value Decomposition*).
3. **Classificação Supervisionada:** Vetorização densa de palavras-chave usando embeddings pré-treinados do **Word2Vec** integrada a um classificador **Random Forest** sob validação cruzada (**k=5**).
4. **Mapeamento Topológico de Redes:** Modelagem de grafos de coocorrência de termos com força de dispersão baseada no modelo físico de **Fruchterman-Reingold** (Spring Layout) via `NetworkX`.

---

## 📈 Resultados Obtidos na Reprodução

Os experimentos de reexecução confirmaram com exatidão decimal as propriedades estatísticas do pipeline original:

### 1. Coerência de Tópicos (NMF vs. LDA)
O modelo NMF demonstrou superioridade semântica ao isolar com sucesso os quatro eixos temáticos sem sobreposição vocabular, enquanto o LDA apresentou redundâncias estruturais.

| Algoritmo | Métrica de Coerência (C_v) | Estabilidade Semântica |
| :--- | :---: | :---: |
| **LDA** (Latent Dirichlet Allocation) | 0.3 | Baixa |
| **NMF** (Non-Negative Matrix Factorization) | 0.3756 | Alta |

### 2. Desempenho do Classificador (Random Forest + Word2Vec)
Sob validação cruzada robusta (**k=5**), as representações contínuas baseadas na hipótese distribucional garantiram alta acurácia preditiva:

| Métrica | Valor Obtido |
| :--- | :---: |
| **Acurácia Global** | **87.16%** |
| **F1-Score Ponderado** | **86.92%** |

---

## 📁 Estrutura do Repositório

```text
├── Data/                                       # Dados secundários brutos e dicionários ESG
│   ├── Machine Learning Pipeline               # Dados necessários para a execução da pipeline de aprendizagem de máquina
│   │   ├── Keywords Updated Data 01_08.xlsx
│   │   ├── Topic 1 Keywords.xlsx
│   │   ├── Topic 2 Keywords.xlsx
│   │   ├── Topic 3 Keywords.xlsx
│   │   ├── topic_4.xlsx
│   │   
│   └── Topic Modeling                          # Dados necessários para a execução da modelagem de tópicos
│       └── Company_Data__.xlsx
│ 
├── Notebooks                                   # Notebooks interativos utilizados no experimento
│   ├── NMF_Topic_Modeling_Final.ipynb          # Notebook contendo a modelagem de tópicos
│   └── Textile_ML_Pipeline.ipynb               # Noteboom contendo a pipeline de aprendizagem de máquina
│
├── LICENSE                                     # Licença MIT de uso livre
└── README.md                                   # Este documento de apresentação
```

## ⚙️ Ambiente e Instalação

O projeto foi planejado e testado para rodar de forma consistente tanto localmente quanto de maneira isolada no Google Colab.

### Dependências

As versões das bibliotecas foram fixadas para o notebook contendo a pipeline de Aprendizagem de Máquina para ser possível executar o código proveniente do estudo original que o presente trabalho reproduz:
* Python == 3.12
* Gensim == 4.3.2
* SciPy == 1.10
* NetworkX == 3.0
* Pandas == 1.3.0
* Scikit-Learn == 0.24.0

## ✍️ Referências Acadêmicas
Se você utilizar este código ou os dados em sua pesquisa, por favor, cite as seguintes referências fundamentais:

### Estudo Original Auditado:
Magotra, R., et al. (2026). Machine learning and NLP pipeline for ESG analysis in textile industries (LEED-certified apparel factories in Bangladesh). Scientific Reports.

### Inicialização Determinística NNDSVD para NMF:
Boutsidis, C., & Gallopoulos, E. (2008). SVD-based initialization: A head start for nonnegative matrix factorization. Pattern Recognition, 41(4), 1350-1362.

### Métrica de Coerência de Tópicos ($C_v$):
Röder, M., Both, A., & Hinneburg, A. (2015). Exploring the space of topic coherence measures. In Proceedings of the eighth ACM international conference on Web search and data mining (pp. 399-408).

### Embeddings Distribuídos de Palavras (Word2Vec):
Mikolov, T., Chen, K., Corrado, G., & Dean, J. (2013). Efficient estimation of word representations in vector space. arXiv preprint arXiv:1301.3781.

### Layout de Forças Fruchterman-Reingold (Grafos):
Fruchterman, T. M., & Reingold, E. M. (1991). Graph drawing by force-directed placement. Software: Practice and Experience, 21(11), 1129-1164.

## 📄 Licença
Este projeto é licenciado sob a Licença MIT - consulte o arquivo LICENSE para obter mais detalhes.
