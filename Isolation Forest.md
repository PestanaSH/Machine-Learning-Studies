# Isolation Forest

## 1. O que é Isolation Forest ?
   
* Isolation Forest é um algoritmo de Machine Learning não supervisionado usado para detecção de anomalias (outliers). Foi proposto por Fei Tony Liu, Kai Ming Ting e Zhi-Hua Zhou em 2008.

* A ideia é simples e elegante: "Anomalias são poucas e diferentes, portanto são mais fáceis de isolar".

## 2. Intuição do algoritmo
Imagine que você tem um conjunto de pontos em um gráfico:
- A maioria dos pontos está agrupada (dados normais)
- Alguns pontos estão distantes do grupo (anomalias)

  Se você tentar "isolar" um ponto fazendo cortes aleatórios no espaço: 
- Ponto NORMAIS: precisam de MUITOS cortes para serem isolados (estão no meio)
- Pontos ANÔMALOS: precisam de POUCOS cortes para serem isolados (estão isolados)

## 3. Como funciona - PASSO A PASSO

### FASE 1:  CONSTRUÇÃO DAS ÁRVORES (Isolation Forest)

 a) Seleciona uma amostra aleatória dos dados
 b) Escolhe uma feature (coluna) aleatoriamente
 c) Escolhe um valor de corte aleatório entre o mínimo e máximo dessa feature
 d) Divide os dados em dois grupos (esquerda e direita)
 e) Repete recursivamente até cada ponto estar isolado ou atingir limite

Exemplo de uma árvore:
   
                    [Feature: Idade < 35?]
                    /                    \
                  Sim                    Não
                  /                        \
        [Salário < 50k?]            [Idade < 55?]
         /          \                 /        \
       ...         ...              ...       ...

### Fase 2: Cálculo do Path LENGTH (Comprimento do Caminho)

- Para cada ponto, conta quantos "cortes" foram necessários para isolá-lo
- Esse número é o "path length" (h)
- Anomalias têm path length MENOR (são isolados mais rápido)

### Fase 3: CÁLCULO DO ANOMALY SCORE

 O score de anomalia é calculado pela fórmula: 

 s(x, n) = 2^(-E(h(x)) / c(n))

 Onde:
 - E(h(x)) = média do path length nas árvores
 - c(n) = path length médio esperado para n amostras
 - s -> 1: alta probabilidade de anomalia
 - s -> 0: baixa probabilidade de anomalia
 - s = 0.5: ponto normal
