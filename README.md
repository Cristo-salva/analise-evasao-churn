# Análise de Evasão de Clientes - Telecom X

## 1. Visão Geral do Projeto
Este projeto realiza uma análise exploratória sobre a evasão de clientes (Churn) na empresa de telecomunicações Telecom X. O principal objetivo é identificar os fatores que mais influenciam o cancelamento de serviços pelos clientes, a fim de gerar insights e recomendações que possam ajudar a reduzir essa taxa. A análise aborda desde o tratamento e limpeza dos dados até a visualização e interpretação dos principais indicadores de Churn.

## 2. Fonte dos Dados
A análise foi conduzida utilizando um conjunto de dados em formato JSON, disponibilizado por uma API da Telecom X. O arquivo contém informações demográficas dos clientes, detalhes dos serviços contratados (telefone, internet), informações de conta (tipo de contrato, método de pagamento, cobranças) e o status de evasão.

* **URL dos dados:** `https://raw.githubusercontent.com/alura-cursos/challenge2-data-science/refs/heads/main/TelecomX_Data.json`

## 3. Metodologia

O projeto foi estruturado seguindo as etapas clássicas de uma análise de dados:

### Limpeza e Tratamento dos Dados
1.  **Importação:** Os dados foram carregados utilizando a biblioteca `pandas`.
2.  **Normalização:** As colunas aninhadas no formato JSON (`customer`, `phone`, `internet`, `account`) foram desmembradas e normalizadas para um formato tabular usando `json_normalize`.
3.  **Tratamento de Inconsistências:** Foram identificados e removidos registros com dados inconsistentes ou ausentes, como strings vazias na coluna `Churn` e valores não numéricos na coluna de cobranças totais (`Charges.Total`).
4.  **Conversão de Tipos:** A coluna `Charges.Total` foi convertida para o tipo numérico (float) para possibilitar cálculos estatísticos.
5.  **Engenharia de Features:** Foram criadas novas colunas para enriquecer a análise, como `tempo_contrato_ano` (agrupando a permanência em faixas anuais) e `gasto_total_cliente` (agrupando os gastos totais em faixas de valor).

### Análise Exploratória de Dados (AED)
Foram geradas estatísticas descritivas e visualizações para entender a relação entre as variáveis e a evasão de clientes. Os principais fatores analisados foram:
* Distribuição geral do Churn.
* Churn por Gênero.
* Churn por Tipo de Contrato.
* Churn por Método de Pagamento.
* Churn por Tempo de Contrato.
* Churn por Faixa de Gasto Total.

## 4. Principais Descobertas (Key Findings)

A análise revelou que a taxa de evasão geral é de **26,6%**. Os fatores com maior impacto no Churn foram:

* **Tipo de Contrato:** Clientes com contrato **Mês a Mês** têm uma taxa de evasão altíssima (**42,7%**), enquanto clientes com contratos de **Um Ano (11,3%)** e **Dois Anos (2,8%)** são significativamente mais leais.
* **Método de Pagamento:** O pagamento via **Cheque Eletrônico** está associado a uma taxa de Churn de **45,3%**, muito superior a outros métodos como cartão de crédito (15,3%) e transferência bancária (16,7%).
* **Tempo de Contrato (Tenure):** A evasão é muito mais alta entre clientes novos. Clientes com **0-1 ano** de contrato apresentam **47,7%** de Churn, taxa que cai drasticamente com o aumento do tempo de permanência.
* **Gasto Total:** Clientes que gastaram menos no total com a empresa tendem a cancelar mais. A faixa de **R$ 0 a R$ 3.000** em gastos totais concentra a maior taxa de evasão (**31,5%**).
* **Gênero:** Não foi observada uma diferença relevante na taxa de Churn entre homens e mulheres.

## 5. Conclusões e Recomendações

### Conclusões
O perfil do cliente com maior risco de evasão é aquele com **contrato mensal**, que paga via **cheque eletrônico**, possui **pouco tempo de casa** (menos de 2 anos) e tem um **histórico de gastos totais mais baixo**. A flexibilidade do contrato mensal e a possível complexidade do pagamento eletrônico parecem ser os principais impulsionadores do Churn.

### Recomendações
1.  **Fidelizar Clientes de Contrato Mensal:** Criar campanhas e oferecer incentivos (descontos, benefícios exclusivos) para que clientes do plano Mês a Mês migrem para contratos de 1 ou 2 anos.
2.  **Otimizar a Experiência de Pagamento:** Investigar os problemas relacionados ao "Cheque Eletrônico" e incentivar a adesão a métodos de pagamento automáticos, que possuem taxas de evasão menores.
3.  **Ações de Retenção para Novos Clientes:** Desenvolver um programa de *onboarding* e acompanhamento próximo para clientes nos primeiros 12 meses, garantindo que percebam valor no serviço desde o início.
4.  **Desenvolver um Modelo Preditivo:** Como próximo passo, utilizar os insights gerados para construir um modelo de Machine Learning que identifique proativamente os clientes com alta probabilidade de Churn, permitindo ações de retenção direcionadas.

## 6. Ferramentas Utilizadas
* **Linguagem:** Python
* **Bibliotecas:**
    * `pandas`
    * `matplotlib`
    * `seaborn`
    * `numpy`

## 7. Como Executar

Para executar este projeto, siga os passos abaixo:

1.  Clone este repositório:
    ```bash
    git clone [https://github.com/seu-usuario/seu-repositorio.git](https://github.com/seu-usuario/seu-repositorio.git)
    ```
2.  Navegue até o diretório do projeto:
    ```bash
    cd seu-repositorio
    ```
3.  Instale as dependências necessárias:
    ```bash
    pip install pandas matplotlib seaborn numpy jupyter
    ```
4.  Abra o Jupyter Notebook:
    ```bash
    jupyter notebook "Challenge_Telecom_X_análise_de_evasão_de_clientes.ipynb"
    ```
