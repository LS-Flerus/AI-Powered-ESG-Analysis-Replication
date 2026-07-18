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

## ⚙️ Ambiente e Execução

O projeto foi planejado e testado para rodar de forma consistente tanto localmente quanto de maneira isolada no Google Colab.

### Dependências

As versões das bibliotecas foram fixadas para o notebook contendo a pipeline de Aprendizagem de Máquina para ser possível executar o código proveniente do estudo original que o presente trabalho reproduz:
* Python == 3.12
* Gensim == 4.3.2
* SciPy == 1.10
* NetworkX == 3.0
* Pandas == 1.3.0
* Scikit-Learn == 0.24.0

### Como executar o experimento

O experimento foi idealizado para ser de fácil reprodução. Seguem adiante instruções para auxiliar isso:

1. Clonar o repositório;

2. Fazer upload do repositório para o seu drive pessoal;

3. Abrir os Jupyter Notebooks no Google Colab

   3.1. Para executar o notebook NMF_Topic_Modeling_Final.ipynb responsável pela modelágem de tópicos, use a opção "executar tudo" no menu de "Tempo de execução";
   3.2. Para executar o notebook Textile_ML_Pipeline.ipynb responsável pelo pipeline de aprendizagem de máquina, use a opção "executar tudo" no menu de "Tempo de execução". A primeira execução irá falhar logo           após a primeira célula (instalação de dependências específicas). Após essa falha, acesse novamente o menu "Tempo de execução" no Colab e selecione "Reiniciar sessão e executar tudo". Desta forma, o notebook inteiro será executado sem mais problemas.

Vale destacar que o notebook Textile_ML_Pipeline.ipynb chega muito próximo ao limite de RAM utilizado pelo Google Colab (12,7GB), logo é extremamente recomendado que ao rodá-lo você não esteja com nenhuma outra sessão do Google Colab ativa.

## ✍️ Referências Acadêmicas
Se você utilizar este código ou os dados em sua pesquisa, por favor, cite as seguintes referências fundamentais:

* Christos Boutsidis and Efstratios Gallopoulos. 2008. SVD-based initialization: A head start for nonnegative matrix factorization. Pattern Recognition 41, 4 (2008), 1350–1362.
* Julian Eggert and Edgar Körner. 2004. Sparse coding and NMF. In Proceedings of the 2004 IEEE International Joint Conference on Neural Networks, Vol. 4. IEEE, 2529–2533.
* International Labour Organization. 2023. The Rana Plaza disaster ten years on: What has changed? InfoStories. Acessado em: 25 mai. 2026. https://webapps.ilo.org/infostories/en-GB/Stories/Country-Focus/rana-plaza.html
* Md. Saiful Islam, Md. Abdur Rakib, and Atm Adnan. 2016. Ready-made garments sector of Bangladesh: Its contribution and challenges towards development. Stud 5 (2016), 02–12.
* Agraj Magotra, Md. Rafiqul Islam Rana, Shishir, Fairuz Shadmani Shishir, and Sumaiya Shomaji. 2026. A machine learning and NLP pipeline for analyzing ESG and sustainability disclosures in the textile and apparel industry. Scientific Reports (apr 2026). doi:10.1038/s41598-026-49931-z
* Aijaz Panhwar, Abdul Sattar Jatoi, Shaukat Ali Mazari, Aftab Kandhro, Uzma Rashid, and Sofia Qaisar. 2024. Water resources contamination and health hazards by textile industry effluent and glance at treatment techniques: A review. Waste Management Bulletin 1, 4 (mar 2024), 158–163. doi:10.1016/j.wmb.2023.09.002

## 📄 Licença
Este projeto é licenciado sob a Licença MIT - consulte o arquivo LICENSE para obter mais detalhes.
