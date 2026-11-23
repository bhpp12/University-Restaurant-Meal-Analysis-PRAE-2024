# University Restaurant Meal Analysis — PRAE 2024

This project was developed in Python to perform an **exploratory and statistical analysis of meal records from customers of the University Restaurants (RUs)** at the Federal University of Ceará (UFC), using data from 2024.

The project applies **descriptive statistics, data visualization, normality testing, and probability analysis** to investigate meal consumption patterns across different customer profiles.

## Objectives

- Analyze different customer profiles;
- Calculate descriptive statistics for meal records;
- Identify the contribution of each profile to the total number of meals;
- Analyze the distribution of meals per CPF (Brazilian individual taxpayer identification number);
- Assess the normality of the distribution using the Shapiro-Wilk test;
- Calculate the probability that a person in the lunch queue belongs to the non-paying category;
- Calculate the probability that a faculty member had dinner given that they had lunch;
- Use visualizations to facilitate data interpretation.

## Dataset

The dataset contains records of customers and meals served at the University Restaurants throughout 2024.

**Year analyzed:** 2024

The main variables used include:

- `cpf_cnpj`
- `vinculo_comensal`
- `categoria_acesso`
- `tipo_refeicao`
- `quantidade_refeicao`

Dataset:

https://raw.githubusercontent.com/bhpp12/datasets/refs/heads/main/17_prae_comensais_2024.csv

## Technologies Used

- Python
- Pandas
- Matplotlib
- Seaborn
- SciPy

## Analysis Performed

### 1. Customer Profile Analysis

A new variable called `perfil` was created by combining three pieces of information:

```text
Customer affiliation + Access category + Meal type
```

For example, a profile may represent the following combination:

```text
Student + Non-Paying + Lunch
```

Based on these profiles, the following statistics are calculated:

- Number of distinct CPFs;
- Total number of meals;
- Average number of meals;
- Median;
- Standard deviation;
- Minimum;
- Maximum;
- Percentage contribution to the total number of meals.

The percentage contribution is calculated based on the total number of meal records in the dataset.

### 2. Meal Distribution per CPF

To analyze individual customer behavior, the total number of meals recorded for each CPF is calculated.

The distribution is presented using two histograms.

**Full Histogram**

The first chart displays all meal counts per CPF.

This visualization provides an overview of the overall distribution, although extremely high values may compress most observations near the beginning of the axis.

**Limited Histogram**

The second histogram considers only CPFs with fewer than 500 recorded meals.

This restriction provides a clearer view of the region where most observations are concentrated.

### 3. Normality Test

The **Shapiro-Wilk test** was used to assess whether the distribution of total meals per CPF can be considered approximately normal.

The hypothesis is evaluated using a 5% significance level.

```text
H₀: The data follows a normal distribution.
H₁: The data does not follow a normal distribution.
```

The interpretation used in the project is:

- `p > 0.05` → There is insufficient evidence to reject the normality assumption.
- `p ≤ 0.05` → The null hypothesis of normality is rejected.

### 4. Probability of a Non-Paying Customer Having Lunch

At this stage, only **lunch** records are considered.

The number of non-paying meals is divided by the total number of lunch meals:

```text
P(Non-Paying | Lunch)
=
Non-paying lunch meals
/
Total lunch meals
```

The result represents the proportion of lunch meals associated with the **non-paying** access category.

### 5. Conditional Probability for Faculty Members

The meal consumption behavior of faculty members at the University Restaurants is also analyzed.

First, the following groups are identified:

- Faculty members who had lunch;
- Faculty members who had dinner.

Next, the intersection between these two sets is calculated.

The conditional probability used is:

```text
P(Dinner | Lunch)
=
P(Dinner ∩ Lunch)
/
P(Lunch)
```

In the implementation, this corresponds to:

```python
len(docente_interseccao) / len(docente_almoco)
```

Therefore, the result represents the probability that a faculty member had dinner **given that they had already had lunch**.

## Data Visualizations

The project uses histograms to visualize the distribution of total meals per CPF.

Two visualizations are generated:

1. **Distribution of total meals per CPF**
2. **Distribution of total meals per CPF, limited to 500 meals**

The visualizations are created using `Seaborn` and `Matplotlib`.

## Libraries Used

```python
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns
from scipy.stats import shapiro
```

## How to Run

### 1. Clone the Repository

```bash
git clone REPOSITORY_URL
```

### 2. Install Dependencies

```bash
pip install pandas matplotlib seaborn scipy
```

### 3. Run the Script

```bash
python analise.py
```

The code can also be executed in **Google Colab**, since the dataset is loaded directly from a GitHub URL.

## Project Structure

```text
├── analise.py
├── dados/
│   └── 17_prae_comensais_2024.csv
└── README.md
```

## Key Concepts Applied

This project applies concepts related to:

- Descriptive Statistics;
- Mean and Median;
- Standard Deviation;
- Frequency Distribution;
- Histograms;
- Normality Testing;
- Shapiro-Wilk Test;
- Probability;
- Conditional Probability;
- Set Operations;
- Data Grouping with Pandas.

## Conclusion

This analysis provides insights into meal consumption records at the University Restaurants throughout 2024, highlighting differences between customer profiles, the distribution of meals per CPF, and probabilistic relationships between different meal types.

The project also demonstrates the practical application of **statistics and probability using Python**, combining data processing, exploratory data analysis, and visualization.

## Author

**Bruno Henrique Pacheco Prudêncio**

Academic project developed as part of studies in **Data Science, Statistics, and Exploratory Data Analysis**.
