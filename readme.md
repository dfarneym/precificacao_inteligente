# 🚀 Projeto Precificação Inteligente: Transformação e Limpeza de Dados

![Python](https://img.shields.io/badge/Python-3.9%2B-blue?style=flat&logo=python)
![Pandas](https://img.shields.io/badge/Pandas-orange?style=flat&logo=pandas)
![Numpy](https://img.shields.io/badge/Numpy-informational?style=flat&logo=numpy)
![Google Colab](https://img.shields.io/badge/Google%20Colab-F9AB00?style=flat&logo=googlecolab&logoColor=white)
![Jupyter Notebook](https://img.shields.io/badge/Jupyter%20Notebook-F37626?style=flat&logo=jupyter)

## 📄 Descrição do Projeto

Este projeto foca intensivamente na **análise e tratamento de dados** para o desenvolvimento de um futuro sistema de precificação inteligente no setor de hospedagem/aluguel de imóveis. O objetivo principal foi realizar uma limpeza, transformação e preparação robustas de um conjunto de dados complexos, originalmente extraídos de arquivos JSON aninhados, para que possam ser utilizados em análises mais aprofundadas e modelagem preditiva.

A etapa de tratamento de dados é fundamental, pois lida com a complexidade de dados semi-estruturados, garantindo que o conjunto de dados final seja limpo, padronizado e adequado para algoritmos de Machine Learning.

## 📁 Estrutura do Repositório
```
Projeto-transformacao/
├── Projeto-transformacao.ipynb       # Notebook Jupyter com todo o processo de ETL e limpeza
├── dados_hospedagem.json             # Conjunto de dados original com informações dos imóveis (entrada)
├── moveis_disponiveis.json           # Conjunto de dados original com informações de disponibilidade e preço (entrada)
└── readme.md                         # Este arquivo README
```
## 📋 Etapas e Técnicas de Transformação de Dados

O processo de tratamento dos dados envolveu diversas etapas cruciais, demonstrando proficiência em manipulação de dados com `pandas`:

* **Extração e Normalização de Dados JSON:**
    * Leitura e processamento de dados brutos a partir de arquivos `.json`.
    * Utilização de `pd.json_normalize()` para achatar estruturas JSON aninhadas e converter dados de dicionários em um formato tabular (`DataFrame`).

* **Desacoplamento de Dados (`explode`):**
    * Aplicação do método `explode()` para transformar elementos de listas dentro de colunas (como `quantidade_banheiros`, `preco`, `comodidades`, `descricao_local`, etc.) em linhas separadas, aumentando a granularidade e a usabilidade dos dados.

* **Transformação de Tipos de Dados:**
    * Conversão de colunas textuais (como `max_hospedes`, `quantidade_banheiros`, `quantidade_quartos`, `quantidade_camas`) para tipos numéricos inteiros (`int64`).
    * Conversão da `avaliacao_geral` para ponto flutuante (`float64`).
    * Limpeza e conversão de colunas monetárias (`preco`, `taxa_deposito`, `taxa_limpeza`): remoção de símbolos de moeda ('$') e vírgulas (',') utilizando `str.replace()` e `apply(lambda x: x.replace(...))`, seguida da conversão para `float64`.
    * Tratamento de valores ausentes (`None`) na coluna `preco` com `fillna('0.0')` antes da conversão para numérico.

* **Limpeza e Tokenização de Texto (`Regex`):**
    * Conversão de textos para minúsculas (`str.lower()`).
    * Remoção de caracteres especiais e pontuações indesejadas utilizando Expressões Regulares (`regex=True`) para padronizar os campos textuais (`descricao_local`, `descricao_vizinhanca`).
    * Remoção de hífens soltos que não fazem parte de palavras compostas.
    * Tokenização simples: quebra de strings em listas de palavras (`str.split()`) para facilitar futuras análises de texto.

* **Manipulação de Dados Temporais (`datetime`):**
    * Conversão da coluna `data` para o formato `datetime` utilizando `pd.to_datetime()`, permitindo extrair componentes temporais como ano e mês.
    * Agrupamento de dados por mês (`dt.strftime('%Y-%m')`) para analisar a disponibilidade de vagas ao longo do tempo.

## 🛠️ Ferramentas e Bibliotecas

As seguintes ferramentas e bibliotecas foram essenciais na construção do projeto:

* **Ambiente:** Google Colab
* **Linguagem:** Python
* **Bibliotecas:**
    * **Pandas:** Para todas as operações de manipulação, limpeza e transformação de dados.
    * **Numpy:** Para operações numéricas e suporte a tipos de dados.

## ⚙️ Como Executar o Notebook

1.  **Clone o Repositório:**
    ```bash
    git clone [https://github.com/dfarneym/precificacao_inteligente](https://github.com/dfarneym/precificacao_inteligente)
    cd NomeDoSeuRepositorio
    ```
   

2.  **Instale as Dependências:**
    Certifique-se de ter Python instalado. Em seguida, instale as bibliotecas necessárias:
    ```bash
    pip install pandas numpy jupyter nbformat
    ```

3.  **Abra o Notebook:**
    Você pode abrir o notebook localmente ou no Google Colab:
    * **Localmente:** `jupyter notebook Projeto-transformacao.ipynb`
    * **Google Colab:** Faça o upload do arquivo `Projeto-transformacao.ipynb` e dos arquivos `.json` diretamente para o ambiente do Google Colab.

4.  **Execute as Células:**
    Execute as células do notebook sequencialmente para observar todas as etapas de transformação e limpeza dos dados.

## 🎓 Origem

Este projeto foi desenvolvido durante a formação de **Data Science** da [Alura](https://www.alura.com.br/) em parceria com o programa **Oracle Next Education (ONE)**.
