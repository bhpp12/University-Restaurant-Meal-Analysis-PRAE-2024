# Análise de Refeições dos Comensais do RU — PRAE 2024

Projeto desenvolvido em Python para realizar uma **análise exploratória e estatística dos registros de refeições dos comensais dos Restaurantes Universitários (RU)** da Universidade Federal do Ceará (UFC), utilizando dados referentes ao ano de 2024.

O projeto utiliza técnicas de **estatística descritiva, visualização de dados, teste de normalidade e probabilidade** para investigar o comportamento dos registros de refeições de diferentes perfis de comensais.

## Objetivos

* Analisar os diferentes perfis de comensais;
* Calcular estatísticas descritivas sobre as refeições;
* Identificar a participação de cada perfil no total de refeições;
* Analisar a distribuição da quantidade de refeições por CPF;
* Verificar a normalidade da distribuição utilizando o teste de Shapiro-Wilk;
* Calcular a probabilidade de uma pessoa na fila do almoço ser não pagante;
* Calcular a probabilidade de um docente ter jantado dado que almoçou;
* Utilizar gráficos para facilitar a interpretação dos dados.

## Dataset

O dataset contém registros de comensais e refeições realizadas nos Restaurantes Universitários durante 2024.

**Ano analisado:** 2024

Entre as principais variáveis utilizadas estão:

* `cpf_cnpj`
* `vinculo_comensal`
* `categoria_acesso`
* `tipo_refeicao`
* `quantidade_refeicao`

Dataset utilizado:

https://raw.githubusercontent.com/bhpp12/datasets/refs/heads/main/17_prae_comensais_2024.csv

## Tecnologias utilizadas

* Python
* Pandas
* Matplotlib
* Seaborn
* SciPy

## Análises realizadas

### 1. Análise dos perfis dos comensais

Foi criada uma nova variável chamada `perfil`, combinando três informações:

```text
vínculo do comensal + categoria de acesso + tipo de refeição
```

Por exemplo, um perfil pode representar a combinação entre:

```text
Discente + Não Pagante + Almoço
```

A partir desses perfis, são calculadas estatísticas como:

* Número de CPFs distintos;
* Total de refeições;
* Média de refeições;
* Mediana;
* Desvio padrão;
* Mínimo;
* Máximo;
* Participação percentual no total de refeições.

A participação percentual é calculada considerando o total de refeições registradas no dataset.

## 2. Distribuição das refeições por CPF

Para analisar o comportamento individual dos comensais, é calculado o total de refeições registradas para cada CPF.

A distribuição é apresentada por meio de dois histogramas.

### Histograma completo

O primeiro gráfico apresenta todos os valores de refeições por CPF.

Esse gráfico permite observar a distribuição geral, mas valores muito altos podem comprimir visualmente a maior parte dos dados próximos ao início do eixo.

### Histograma limitado

O segundo histograma considera apenas CPFs com menos de 500 refeições.

Essa limitação permite observar com maior clareza a região de maior concentração dos dados.

## 3. Teste de normalidade

Foi utilizado o teste de **Shapiro-Wilk** para verificar se a distribuição do total de refeições por CPF pode ser considerada aproximadamente normal.

A hipótese é avaliada utilizando nível de significância de 5%.

```text
H₀: os dados seguem uma distribuição normal
H₁: os dados não seguem uma distribuição normal
```

A interpretação utilizada no projeto é:

* `p > 0,05` → não há evidência suficiente para rejeitar a normalidade;
* `p ≤ 0,05` → rejeita-se a hipótese de normalidade.

## 4. Probabilidade de uma pessoa ser não pagante no almoço

Nesta etapa, são considerados somente os registros de **almoço**.

A quantidade de refeições não pagantes é dividida pelo total de refeições de almoço:

```text
P(Não Pagante | Almoço)
=
Refeições de almoço não pagantes
/
Total de refeições de almoço
```

O resultado representa a proporção de refeições de almoço associadas à categoria de acesso **não pagante**.

## 5. Probabilidade condicional para docentes

Também é analisado o comportamento dos docentes que realizaram refeições no RU.

Primeiramente, são identificados:

* CPFs de docentes que almoçaram;
* CPFs de docentes que jantaram.

Em seguida, é calculada a interseção entre esses dois conjuntos.

A probabilidade condicional utilizada é:

```text
P(Jantar | Almoço)
=
P(Jantar ∩ Almoço)
/
P(Almoço)
```

Na implementação, isso corresponde a:

```python
len(docente_interseccao) / len(docente_almoco)
```

Assim, o resultado representa a probabilidade de um docente ter jantado **dado que ele já havia almoçado**.

## Visualizações

O projeto utiliza histogramas para visualizar a distribuição do total de refeições por CPF.

São produzidos:

1. **Distribuição do total de refeições por CPF**
2. **Distribuição do total de refeições por CPF até 500 refeições**

As visualizações são construídas utilizando `Seaborn` e `Matplotlib`.

## Bibliotecas utilizadas

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from scipy.stats import shapiro
```

## Como executar

### 1. Clone o repositório

```bash
git clone URL_DO_SEU_REPOSITORIO
```

### 2. Instale as dependências

```bash
pip install pandas matplotlib seaborn scipy
```

### 3. Execute o código

```bash
python analise.py
```

O código também pode ser executado no **Google Colab**, já que o dataset é carregado diretamente através de uma URL do GitHub.

## Estrutura do projeto

```text
├── analise.py
├── dados/
│   └── 17_prae_comensais_2024.csv
└── README.md
```

## Principais conceitos aplicados

Este projeto utiliza conceitos de:

* Estatística descritiva;
* Média e mediana;
* Desvio padrão;
* Distribuição de frequência;
* Histogramas;
* Teste de normalidade;
* Shapiro-Wilk;
* Probabilidade;
* Probabilidade condicional;
* Operações com conjuntos;
* Agrupamento de dados com Pandas.

## Conclusão

A análise permite explorar o comportamento dos registros de refeições dos comensais dos Restaurantes Universitários em 2024, observando diferenças entre perfis, distribuição do número de refeições por CPF e relações probabilísticas entre diferentes tipos de refeições.

O projeto também demonstra a aplicação prática de conceitos de **estatística e probabilidade utilizando Python**, integrando tratamento de dados, análise exploratória e visualização.

## Autor

**Bruno Henrique Pacheco Prudêncio**

Projeto acadêmico desenvolvido para estudo de **Ciência de Dados, Estatística e Análise Exploratória de Dados**.
