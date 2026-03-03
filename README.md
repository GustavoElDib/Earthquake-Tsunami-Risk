# 🌍 Earthquake–Tsunami Risk Prediction | Machine Learning

## 📌 Objetivo
Este projeto implementa um modelo de **classificação supervisionada** para estimar a probabilidade de um terremoto gerar um tsunami, com base em características sísmicas e geográficas.

O problema é tratado como uma **classificação binária**:
* **0**: Não gerou tsunami
* **1**: Gerou tsunami

O modelo estima a probabilidade:  
$$P(tsunami = 1 \mid X)$$

---

## 📊 Base de Dados
O dataset contém informações detalhadas sobre eventos sísmicos:

| Variável | Descrição |
| :--- | :--- |
| **magnitude** | Magnitude do terremoto |
| **depth** | Profundidade do hipocentro |
| **mmi** | Intensidade percebida (Modified Mercalli Intensity) |
| **sig** | Significância do evento |
| **nst** | Número de estações que detectaram o evento |
| **dmin** | Distância mínima da estação |
| **gap** | Gap azimutal |
| **latitude/longitude** | Localização geográfica |
| **tsunami** | Variável alvo (Target) |

---

## 🔎 Análise Exploratória (EDA)
Foi construída uma matriz de correlação para avaliar as relações lineares entre as variáveis.

**Principais Observações:**
* **Forte correlação:** Entre `magnitude`, `mmi` e `sig`.
* **Correlação negativa:** Entre `nst` (número de estações) e `tsunami`.
* **Geografia:** Variáveis de localização apresentaram baixa correlação linear direta com o alvo.

> 

⚠️ **Nota Importante:** Correlação não implica causalidade. A correlação negativa de `nst` pode refletir fatores estruturais da rede de monitoramento e não uma relação física direta com a geração de ondas.

---

## 🤖 O Modelo
O fluxo de desenvolvimento seguiu as etapas padrão de Ciência de Dados:

1.  **Pré-processamento:** Tratamento de dados e separação entre treino e teste.
2.  **Treinamento:** Implementação de algoritmos de classificação.
3.  **Avaliação:** Foco em métricas que consideram o desbalanceamento de classes.
4.  **Feature Importance:** Análise de quais variáveis mais impactam a decisão.

---

## 📈 Feature Importance & Interpretação
Os resultados indicam a seguinte hierarquia de relevância:

1.  **Magnitude:** Alta relevância (principal preditor físico).
2.  **Depth (Profundidade):** Influência significativa na propagação de energia.
3.  **Intensidade (mmi, sig):** Contribuem para a precisão do modelo.
4.  **nst:** Apresenta influência, mas exige interpretação cautelar devido ao viés de infraestrutura.

> 

---

## 🌊 Desafios: Raridade do Evento e Viés Estrutural
Tsunamis são eventos raros, o que impõe desafios específicos:

* **Desbalanceamento:** A acurácia (Accuracy) pode ser enganosa. O foco deve estar no **Recall** da classe positiva para evitar falsos negativos perigosos.
* **Viés de Monitoramento:** Regiões com maior infraestrutura (mais estações - `nst`) podem detectar mais eventos menores, enquanto regiões remotas onde tsunamis ocorrem podem ter menos sensores. O modelo pode "aprender" a geografia do monitoramento em vez de apenas a física do evento.

---

## 📊 Avaliação do Modelo
Dada a natureza crítica do problema, utilizamos as seguintes métricas:

* **Precision & Recall:** Equilíbrio entre assertividade e cobertura.
* **F1-score:** Média harmônica para avaliação global.
* **Matriz de Confusão:** Essencial para visualizar falhas na detecção de tsunamis (Falsos Negativos).

---

## ⚠️ Limitações
* Multicolinearidade entre variáveis de intensidade física.
* Dependência da representatividade histórica (dados limitados a regiões monitoradas).

---

## 🎯 Conclusão
O modelo captura padrões físicos relevantes (magnitude e profundidade) com sucesso. Contudo, a análise destaca que variáveis estruturais como o número de estações devem ser interpretadas criticamente, pois refletem a distribuição humana de sensores. O projeto consolida fundamentos de **modelagem preditiva**, **estatística aplicada** e **análise ética de dados**.
