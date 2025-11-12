# Projeto_ML_Aeroespacial_Deteccao_Falhas
Classificador Random Forest para detecção de anomalias em turbinas aeronáuticas - Dados CMAPSS

# 🚀 Projeto de Machine Learning Aeroespacial: Classificação de Falhas em Componentes

Este repositório contém o desenvolvimento e a análise de um modelo de **Aprendizado Supervisionado (Classificação Binária)** focado na Manutenção Preditiva do setor Aeroespacial.

## 🎯 Objetivo Principal

Desenvolver e avaliar um classificador capaz de identificar se um componente (motor) está em **funcionamento normal (0)** ou apresentando uma **anomalia/pré-falha (1)**, com base em dados de sensores. A prioridade é garantir um alto nível de **Recall** para minimizar o risco de segurança (Falsos Negativos).

## 📊 Metodologia e Dataset

* **Algoritmo:** **Random Forest Classifier** (modelo de baixo código).
* **Linguagem e Bibliotecas:** Python (Pandas, NumPy, scikit-learn).
* **Dataset:** **Aircraft Sensor and Engine Performance (CMAPSS - NASA)**, contido no arquivo `PM_train.txt`.

## ⚙️ Fluxo de Desenvolvimento

O código completo está no notebook `projeto_deteccao_falhas.ipynb`.

1.  **Pré-processamento:**
    * Criação do rótulo binário (Falha/Normal) com base no **RUL (Remaining Useful Life)**, definindo o limiar (Threshold) de 30 ciclos para anomalia.
    * Escalonamento dos dados de sensores usando `StandardScaler`.
2.  **Treinamento:** Modelo Random Forest treinado com os dados escalonados.
3.  **Avaliação:** Análise crítica focada em **Recall** e **Precisão**.

## ✅ Resultados Finais do Modelo Selecionado

O modelo final foi escolhido por priorizar a segurança (Recall), demonstrando um desempenho robusto:

| Métrica | Valor | Análise |
| :---: | :---: | :--- |
| **Acurácia Geral** | 0.9639 | Excelente desempenho geral. |
| **Precisão** (Custo) | 0.8880 | Alto índice de acerto nos alarmes (baixo custo operacional). |
| **Recall** (Segurança) | **0.8694** | **CRUCIAL:** O modelo detecta 86.94% das falhas reais, minimizando o risco de **Falsos Negativos**. |

## ⚠️ Destaque Técnico: Tentativa de Otimização (Análise Crítica)

O notebook (`projeto_deteccao_falhas.ipynb`) contém uma seção dedicada à otimização do modelo através do parâmetro `class_weight='balanced'`.

**Atenção:** Essa tentativa resultou em uma **degradação do desempenho de segurança (Recall)** (de 0.8694 para 0.8565) e, consequentemente, foi **descartada** para o resultado final. Esta análise crítica é mantida no código para demonstrar a capacidade de diagnóstico e tomada de decisão técnica do projeto, priorizando a segurança (menor FN) sobre o custo.

## 🔑 Como Executar o Projeto

1.  **Plataforma:** Recomenda-se o Google Colaboratory (Colab) ou Jupyter Notebook.
2.  **Dependências:** As bibliotecas necessárias são **pandas**, **numpy**, e **scikit-learn**.
3.  **Execução:** Abra o notebook `projeto_deteccao_falhas.ipynb` e execute as células sequencialmente. O código reproduzirá o pré-processamento, treinamento e gerará as métricas finais.
