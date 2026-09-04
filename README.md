# Challenge Sprint 3 — Análise Estatística de Veículos Elétricos

##  Sobre o projeto

Este projeto foi desenvolvido para a **Challenge Sprint 3** da disciplina de **Modelagem Linear para Aprendizado de Máquina**.

O objetivo da atividade é aplicar conceitos de **estatística, probabilidade, distribuição normal e regressão linear** utilizando Python sobre uma base de dados real.

Para esta análise, utilizamos a base **Electric Vehicle Population Data**, também utilizada em uma Sprint anterior, com informações sobre veículos elétricos.

---

## Integrantes

- **Felipe Mitsuo Takahashi Stephano** — RM570692
- **Laura Godoy Callegari** — RM569181
- **Letícia Araújo Espindola** — RM569308
- **Mariana Dreset Carbollan** — RM569207
- **Milena de Aguiar Lopes Cardoso** — RM570599
- **Felipe Perdigão Macedo** — RM570990

---

## Base de dados

Foi utilizada a base:

**Electric Vehicle Population Data**

link: https://www.kaggle.com/datasets/rajkumarpandey02/electric-vehicle-population-data

Para as análises de probabilidade, a principal variável escolhida foi:

`Electric Range`

Essa variável representa a **autonomia elétrica dos veículos em milhas**.

Antes das análises, realizamos um tratamento dos dados para utilizar apenas veículos classificados como:

`Battery Electric Vehicle (BEV)`

Também foram removidos os registros em que `Electric Range = 0`, pois esses valores representam casos em que a autonomia não estava devidamente informada e poderiam distorcer os cálculos estatísticos.

### Quantidade de registros

- Base original: **150.482 registros**
- Após o tratamento: **47.109 registros**

---

# Análises realizadas

## 1. Estatísticas iniciais

Inicialmente foram calculadas algumas medidas estatísticas da variável `Electric Range`, necessárias para os exercícios seguintes.

Resultados obtidos:

| Medida | Resultado |
|---|---:|
| Média | 194,91 milhas |
| Mediana | 215,00 milhas |
| Desvio-padrão | 73,77 milhas |

Essas medidas permitem compreender melhor a distribuição da autonomia dos veículos presentes na base.

---

## 2. Probabilidade acima da mediana

O primeiro exercício solicita a probabilidade de ocorrência de valores acima da mediana da variável escolhida.

Conforme solicitado no enunciado, foi assumido que a variável `Electric Range` segue uma **Distribuição Normal**.

Foi utilizada a função `scipy.stats.norm.sf()` para calcular a probabilidade de uma autonomia ser superior à mediana encontrada.

### Resultados

- **Mediana:** 215 milhas
- **Probabilidade de valor acima da mediana:** 0,393
- **Probabilidade em porcentagem:** aproximadamente **39,27%**

### Classificação

De acordo com os critérios adotados no projeto, o resultado foi classificado como:

**Evento pouco provável**

Ou seja, considerando a distribuição normal construída a partir da média e do desvio-padrão da amostra, existe aproximadamente **39,27% de probabilidade** de um veículo apresentar autonomia superior a 215 milhas.

---

## 3. Probabilidade no intervalo média ± 2 desvios-padrão

No segundo exercício, foi calculada a probabilidade da autonomia elétrica estar dentro do intervalo:

**média ± 2 desvios-padrão**

Os limites encontrados foram:

- **Média:** 194,91 milhas
- **Desvio-padrão:** 73,77 milhas
- **Limite inferior:** 47,37 milhas
- **Limite superior:** 342,45 milhas

A probabilidade foi calculada utilizando a função de distribuição acumulada da Normal, `scipy.stats.norm.cdf()`.

### Resultado

A probabilidade encontrada foi:

**95,45%**

### Classificação

O resultado foi classificado como:

**Evento quase certo**

O valor encontrado também está de acordo com o comportamento esperado de uma Distribuição Normal, em que aproximadamente **95% dos valores se encontram dentro de dois desvios-padrão da média**.

---

# 4. Regressão Linear

Para a etapa de regressão linear foram selecionadas duas variáveis numéricas:

- `Model Year` — ano do modelo do veículo
- `Electric Range` — autonomia elétrica em milhas

O objetivo foi analisar se existe uma relação entre **o ano de fabricação/modelo do veículo e sua autonomia elétrica**.

A hipótese analisada é que veículos mais novos tendem a apresentar maior autonomia devido à evolução das tecnologias relacionadas a baterias e eficiência energética.

---

## Resultados do modelo

Os coeficientes obtidos foram:

| Métrica | Resultado |
|---|---:|
| Inclinação | 22,02 |
| Intercepto | -44.226,85 |
| R² | 0,499 |

### Inclinação

A inclinação encontrada foi de aproximadamente **22,02**.

Isso significa que, segundo o modelo ajustado, a autonomia elétrica tende a aumentar em aproximadamente **22,02 milhas para cada aumento de um ano no ano do modelo do veículo**.

Portanto, existe uma relação positiva entre as duas variáveis.

### Intercepto

O intercepto encontrado foi:

**-44.226,85**

Matematicamente, ele representa a autonomia estimada quando o ano do modelo é igual a zero.

Como esse cenário não possui significado dentro do contexto analisado, o intercepto não apresenta uma interpretação prática relevante para este projeto.

### Coeficiente de determinação — R²

O modelo apresentou:

**R² = 0,499**

Isso indica que aproximadamente **49,9% da variação observada na autonomia elétrica pode ser explicada pelo ano do modelo do veículo**.

Portanto, o ano possui uma influência relevante sobre a autonomia, porém não é a única variável responsável por determinar esse valor.

Outros fatores, como capacidade da bateria, fabricante, modelo, eficiência energética e tecnologia utilizada, também podem influenciar a autonomia de um veículo elétrico.

---

## Visualização da regressão

O projeto também apresenta um gráfico de dispersão contendo:

- os dados reais;
- o ano dos veículos no eixo X;
- a autonomia elétrica no eixo Y;
- a reta de regressão linear ajustada.

A visualização facilita a identificação da tendência positiva entre as variáveis e permite observar que, apesar da relação existente, ainda há uma dispersão significativa entre os registros.

---

# Relação com Aprendizado de Máquina

A regressão linear utilizada nesta Sprint também representa um dos modelos mais básicos de **Aprendizado de Máquina supervisionado**.

Nesse caso, o modelo utiliza a variável `Model Year` para tentar estimar o valor de `Electric Range`.

A partir dos dados existentes, uma reta é ajustada de forma a representar a relação entre as duas variáveis e minimizar os erros entre os valores reais e os valores estimados.

Esse processo demonstra como conceitos estatísticos, como:

- média;
- desvio-padrão;
- probabilidade;
- correlação;
- coeficientes;
- variabilidade;

podem servir como base para a construção e interpretação de modelos de Machine Learning.

---

# Conclusão

A análise permitiu aplicar conceitos estatísticos e de aprendizado de máquina sobre uma base real de veículos elétricos.

Nos exercícios de probabilidade, foi possível observar que:

- a probabilidade de encontrar uma autonomia superior à mediana de **215 milhas** foi de aproximadamente **39,27%**;
- aproximadamente **95,45%** dos valores estão dentro do intervalo de **47,37 a 342,45 milhas**, correspondente à média ± 2 desvios-padrão.

Embora a distribuição real da variável `Electric Range` não seja perfeitamente normal, os cálculos foram realizados considerando a hipótese de **Distribuição Normal**, conforme estabelecido pelo enunciado da atividade.

Na regressão linear, foi identificada uma **relação positiva entre o ano do modelo e a autonomia elétrica**, indicando que veículos mais novos tendem a apresentar maiores autonomias.

O valor de **R² = 0,499** mostra que o ano do modelo explica aproximadamente metade da variação da autonomia, indicando que outros fatores também possuem influência significativa.

Assim, a atividade permitiu relacionar conceitos de **estatística, probabilidade e regressão linear** com fundamentos utilizados em **Aprendizado de Máquina**.

---

## Tecnologias utilizadas

- Python
- Pandas
- NumPy
- Matplotlib
- SciPy
- Jupyter Notebook

---

## Estrutura do repositório

```text
Challenge-Sprint-3/
│
├── Electric_Vehicle_Population_Data.csv
├── sprint3_mlam.ipynb
└──  README.md

```

---

## Como executar

1. Faça o download ou clone este repositório.
2. Certifique-se de que o arquivo da base de dados esteja na mesma pasta do notebook.
3. Abra o arquivo `sprint3_mlam.ipynb` no Jupyter Notebook, JupyterLab ou Google Colab.
4. Instale as bibliotecas necessárias, caso ainda não estejam disponíveis.
5. Execute as células do notebook em ordem.

Bibliotecas utilizadas:

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from scipy import stats
```
