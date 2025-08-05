# 🩺 Predição de Diabetes com Machine Learning (Pima Indians Dataset)

Este projeto tem como objetivo aplicar **ciência de dados e aprendizado de máquina** para prever o risco de diabetes em mulheres, utilizando a base **Pima Indians Diabetes Dataset**. O pipeline inclui limpeza, categorização clínica, modelagem com Regressão Logística e Random Forest, além de análises visuais com **Power BI** e integração com **Databricks Delta Table**.

---

## 🎯 Objetivo

- Identificar os principais fatores de risco associados ao diagnóstico de diabetes
- Criar um modelo preditivo utilizando algoritmos supervisionados
- Preparar a base para visualização com filtros e KPIs clínicos no Power BI
- Registrar a base tratada como **tabela SQL Delta** no Databricks para consultas futuras

---

## 🧪 Pipeline do Projeto

### 1. 📥 Importação de Dados

- Leitura do arquivo `diabetes.csv`
- Análise inicial com `df.info()`, `describe()`, e verificação de valores nulos ou atípicos

### 2. 🛠️ Tratamento de Dados

- Substituição de valores **clinicamente inválidos** (como 0 em `Glucose`, `BMI`, etc.) por `NaN`
- Imputação dos valores ausentes com **mediana** (mais robusta aos outliers)

### 3. 🧠 Categorização Clínica

- Criação de variáveis categóricas com base em faixas clínicas:
  - Faixa Etária (`Age_Low`, `Age_Med`, `Age_Risk`)
  - Pressão Arterial (`BP_Low`, `BP_Nor`, `BP_High`)
  - Hereditariedade (`Her_Low`, `Her_Med`, `Her_Risk`)
  - IMC (`BMI_Low`, `BMI_Med`, `BMI_Risk`)
  - Glicose (`Low_Gluc`, `Med_Gluc`, `High_Gluc`)
  - Insulina (`Ins_Low`, `Ins_Med`, `Res_Ins`)
- Geração de dummies para cada categoria

### 4. 📊 Análise Exploratória

- Criação de um **Heatmap de Correlação** para entender as relações entre variáveis
  ![heatmap](inserir-caminho-ou-link-da-imagem-aqui)

---

## 🤖 Modelagem Preditiva

### 🔷 Regressão Logística

- Accuracy: **0.77**
- Recall: **0.65**
- F1-score: **0.67**
- AUC: **0.82**

### 🌲 Random Forest

- Accuracy: **0.79**
- Recall: **0.71**
- F1-score: **0.70**
- AUC: **0.82**

### 📈 Comparação Visual das Curvas ROC

![roc_comparacao](inserir-caminho-ou-link-da-imagem-aqui)

---

## 📊 Painel Power BI (Resumo Visual)

Painel com KPIs, segmentações e gráficos por faixa etária, glicose, IMC e diagnóstico.  
Os principais indicadores:

- `% com Diabetes`
- `% em Risco por Glicose`
- `Média de Idade`
- `% com IMC Elevado`

🎯 O painel foi construído usando a base final `diabetes_completo_para_BI.csv`, exportada do Databricks.

---

## 💾 Integração com Databricks (Delta Table)

Exportação final do DataFrame como tabela Delta SQL:

spark.createDataFrame(df).write \
    .format("delta") \
    .mode("overwrite") \
    .saveAsTable('base_diabete')

📁 Estrutura dos Arquivos
| Arquivo                           | Descrição                            |
| --------------------------------- | ------------------------------------ |
| `Projeto_Predicao_Diabetes.ipynb` | Notebook com todo o pipeline         |
| `diabetes_completo_para_BI.csv`   | Base tratada e categorizada para BI  |
| `README.md`                       | Documentação do projeto              |
| `base_diabete` (Databricks)       | Tabela Delta SQL com os dados finais |

📚 Dataset Original
    Fonte: Kaggle – Pima Indians Diabetes Dataset
    Atributos: glicose, pressão, idade, IMC, hereditariedade, número de gestações

👨‍💻 Autor
Erick Martinuci
[GitHub](https://github.com/ErickMartinuci/Portfolio-Erick)
[LinkedIN](https://www.linkedin.com/in/erickmartinuci/)
