# Análise de Corridas de Táxi em Chicago

## Sobre o projeto

Este projeto tem como objetivo analisar dados de corridas de táxi em Chicago para identificar padrões de demanda entre empresas, regiões com maior volume de desembarques e possíveis diferenças na duração das viagens de acordo com as condições climáticas.

A análise utiliza dados obtidos por meio de consultas SQL e técnicas de análise exploratória e estatística com Python, buscando gerar informações relevantes para a compreensão do transporte urbano.

## Objetivos

- Analisar o volume de corridas por empresa de táxi.
- Identificar os bairros de Chicago com maior média de desembarques.
- Explorar e validar os conjuntos de dados.
- Comparar a duração das viagens em condições climáticas boas e ruins.
- Aplicar testes de hipóteses para avaliar diferenças estatísticas na duração das corridas.

## Tecnologias utilizadas

- Python
- Pandas
- Matplotlib
- SciPy
- Jupyter Notebook
- SQL — consultas utilizadas para obtenção dos dados

## Conjuntos de dados

O projeto utiliza três arquivos CSV:

| Arquivo | Descrição | Registros iniciais |
|---|---|---:|
| `project_sql_result_01.csv` | Empresas de táxi e quantidade de corridas | 64 |
| `project_sql_result_04.csv` | Bairros e média de desembarques | 94 |
| `project_sql_result_07.csv` | Horário de início, condições climáticas e duração das viagens | 1.068 |

Os dois primeiros conjuntos apresentam dados agregados. O terceiro é utilizado para investigar a relação entre as condições climáticas e a duração das viagens do Loop até o Aeroporto Internacional O'Hare, aos sábados.

## Etapas da análise

### 1. Exploração e validação dos dados

Inicialmente, foram analisadas a estrutura dos conjuntos de dados, as colunas, os tipos de dados, as estatísticas descritivas e a presença de registros duplicados.

Principais verificações:

- O conjunto de empresas de táxi contém 64 registros e 2 colunas.
- O conjunto de bairros contém 94 registros e 2 colunas.
- O conjunto utilizado no teste estatístico contém inicialmente 1.068 registros e 3 colunas.
- Não foram encontrados registros duplicados nos dois primeiros conjuntos.
- Foram identificados e removidos 197 registros duplicados do conjunto utilizado na análise estatística.

Essa etapa contribuiu para preparar os dados para as análises seguintes.

### 2. Análise das empresas de táxi

Foi analisada a quantidade de corridas realizadas pelas empresas presentes no conjunto de dados.

A **Flash Cab** apresentou o maior volume, com 19.558 corridas. Entre as demais empresas com volumes expressivos estão Taxi Affiliation Services, Medallion Leasing, Yellow Cab e Taxi Affiliation Service Yellow.

Os resultados demonstram diferenças no volume de corridas entre as empresas analisadas.

### 3. Análise dos bairros com maior média de desembarques

Foram avaliadas 94 regiões de Chicago, considerando a média de desembarques, com o objetivo de identificar as áreas de maior demanda.

Os dez bairros com as maiores médias foram:

| Posição | Bairro | Média de desembarques |
|---:|---|---:|
| 1 | Loop | 10.727,47 |
| 2 | River North | 9.523,67 |
| 3 | Streeterville | 6.664,67 |
| 4 | West Loop | 5.163,67 |
| 5 | O'Hare | 2.546,90 |
| 6 | Lake View | 2.420,97 |
| 7 | Grant Park | 2.068,53 |
| 8 | Museum Campus | 1.510,00 |
| 9 | Gold Coast | 1.364,23 |
| 10 | Sheffield & DePaul | 1.259,77 |

O bairro Loop apresentou a maior média de desembarques, seguido por River North e Streeterville.

Esses resultados indicam uma concentração de desembarques em determinadas regiões da cidade.

### 4. Análise das condições climáticas e da duração das viagens

A etapa final investigou se a duração média das viagens do Loop até o Aeroporto Internacional O'Hare apresentava diferenças entre sábados com condições climáticas boas e ruins.

Após o tratamento dos registros duplicados, foram calculadas as médias de duração para cada condição climática.

| Condição climática | Duração média | Aproximadamente |
|---|---:|---:|
| Boa | 2.032,25 segundos | 33,87 minutos |
| Ruim | 2.409,23 segundos | 40,15 minutos |

A duração média das viagens em condições climáticas ruins foi aproximadamente 376,98 segundos, ou 6,28 minutos, maior do que em condições boas.

### 5. Teste de hipóteses estatísticas

Para verificar se a diferença observada nas durações médias era estatisticamente significativa, foi aplicado um teste t para duas amostras independentes, utilizando a função `ttest_ind` da biblioteca SciPy, com a opção `equal_var=False`.

**Hipótese nula (H₀):** não existe diferença entre a duração média das viagens do Loop até O'Hare em sábados com condições climáticas boas e ruins.

**Hipótese alternativa (H₁):** existe diferença entre as durações médias das viagens nas duas condições climáticas.

Foi adotado um nível de significância de 5% (`α = 0,05`).

| Indicador | Resultado |
|---|---:|
| Nível de significância | 0,05 |
| Valor-p | Aproximadamente 9,13 × 10⁻⁸ |
| Decisão | Rejeitar a hipótese nula |

Como o valor-p é inferior ao nível de significância estabelecido, a hipótese nula foi rejeitada.

**Conclusão estatística:** há evidências de uma diferença significativa na duração média das viagens entre as duas condições climáticas analisadas. No conjunto de dados, as viagens foram mais longas, em média, quando as condições climáticas eram ruins.

## Principais conclusões

A análise identificou diferenças no volume de corridas entre as empresas de táxi e mostrou que regiões como Loop, River North e Streeterville apresentam as maiores médias de desembarques.

Na análise estatística, foi identificada uma diferença significativa entre as durações médias das viagens em condições climáticas boas e ruins. As viagens em condições ruins duraram, em média, aproximadamente 6,28 minutos a mais.

Os resultados demonstram como técnicas de análise exploratória, visualização de dados e testes estatísticos podem ajudar a identificar padrões no transporte urbano e apoiar a tomada de decisões baseada em dados.

## Competências desenvolvidas

- Análise exploratória de dados (EDA).
- Inspeção e validação de conjuntos de dados.
- Tratamento e remoção de registros duplicados.
- Manipulação de dados com Pandas.
- Visualização de dados com Matplotlib.
- Estatística descritiva.
- Formulação e teste de hipóteses.
- Interpretação de resultados estatísticos com SciPy.
- Comunicação de resultados analíticos.