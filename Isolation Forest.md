# Isolation Forest

1. O que é Isolation Forest ?
Isolation Forest é um algoritmo de Machine Learning não supervisionado usado para detecção de anomalias (outliers). Foi proposto por Fei Tony Liu, Kai Ming Ting e Zhi-Hua Zhou em 2008.

A ideia é simples e elegante: "Anomalias são poucas e diferentes, portanto são mais fáceis de isolar".

2. Intuição do algoritmo
Imagine que você tem um conjunto de pontos em um gráfico:
- A maioria dos pontos está agrupada (dados normais)
- Alguns pontos estão distantes do grupo (anomalias)

Se você tentar "isolar" um ponto fazendo cortes aleatórios no espaço: 
- Ponto NORMAIS: precisam de MUITOS cortes para serem isolados (estão no meio)
- Pontos ANÔMALOS: precisam de POUCOS cortes para serem isolados (estão isolados)



