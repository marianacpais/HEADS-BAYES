# Lesson 07 - Probability - a quick introduction to Bayesian reasoning

## Incerteza
- Mesmo não podendo ter a certeza de nada, posso ter uma ideia da verosimilhança de um evento.

## Verossimilhança

## MBE
- Uso consciente, explícito e criterioso da melhor evidência disponível para a tomada de decisão clínica. Isso inclui:
  - Experiência clínica pessoal
  - Melhor evidência clínica externa com base em investigação clínica de qualidade
  - Valores, necessidades, expectativas e contexto individual de cada doente

- É necessário representar a incerteza!
  - A probabilidade é muitas vezes a melhor forma

## Raciocínio Bayesiano

- **Definição**: Processo formal que utilizamos para atualizar as nossas crenças sobre o mundo assim que obtemos alguns dados observados. (Kurt, 2019)

## Probabilidade Bayesiana
- Computa a probabilidade de que a hipótese é verdadeira, atualizando a probabilidade a priori sobre a hipótese com base em novos dados.
  - **Probabilidade a priori**: Probabilidade de que a hipótese é verdadeira antes de uma experiência aleatória
  - **Probabilidade a posteriori**: Probabilidade de que a hipótese é verdadeira depois de uma experiência aleatória

## Probabilidade Condicional - P(A|B)
\[ P(A|B) = rac{P(A \cap B)}{P(B)} \]

## Modelo de Conhecimentos Bayesianos
- Os métodos estatísticos Bayesianos permitem que se utilize conhecimento prévio quando se analisam os dados, transformando o processo de análise de dados num processo de atualização do conhecimento prévio com evidência biomédica de cuidados de saúde. (Peter Lucas, 2004)

## Redes Bayesianas
- É necessário ter em consideração as dependências entre os fatores; é diferente pensar na probabilidade de uma doença dado que está presente um sintoma ou dado que está presente um fator de risco.

## Modelo Quantitativo
\[ P(	ext{Disease}|	ext{Symptom}) \]
\[ P(	ext{Disease}|	ext{Risk Factor}) \]

## Representação do Conhecimento
- Redes Bayesianas representadas em grafo onde:
  - Os atributos são representados pelos nós do grafo
  - Os arcos representam as dependências entre os atributos, utilizando probabilidades condicionais

- Aproxima-se à forma de pensar "natural"

## Evaluating Decision Support Methods
- **Sensibilidade** = Recall
- **Valor preditivo positivo** = Precision

## Relembrando...
- **Sensibilidade** (= Recall) -> P(T+ | D+)
- **Especificidade** -> P(T- | D-)
- **Valor preditivo positivo** -> P(D+ | T+)
- **Valor preditivo negativo** -> P(D- | T-)
- **Likelihood Ratio** + -> S / (1-E) = (1)
- **Likelihood Ratio** - -> (1-S) / E = (2)
\[ LR+ = rac{P(T+ | D+)}{P(T+)} \]

## Teorema de Bayes
\[ P(A|B) = rac{P(A) 	imes P(B|A)}{P(B)} \]
- Sensibilidade
- Probabilidade de ter um "teste positivo"
