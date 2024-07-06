# Lesson 09 - Probabilistic principles - The core engine of Bayesian networks


## Porque utilizam Redes Bayesianas?
- São modelos probabilísticos gráficos, pelo que são os formalismos de incerteza mais populares porque:
  - Conseguem lidar com ruído, informação em falta (missing) e relação probabilística.
  - Aprendem com os dados e conseguem incorporar conhecimento de domínio.
  - Oferecem flexibilidade de pensamento/razoamento.
  - Apresentam uma interface de representação gráfica compacta.
  - Assentam em princípios probabilísticos.
  - Aceitam princípios de engenharia: aquisição de conhecimento, machine learning e estatística.

## Nota 8
- Variável estocástica (= estatística = random) -> letra maiúscula ou string maiúscula (ex: X ou FEVER)
- Valores -> as variáveis podem assumir valores (ex: X=x; FEVER=yes)
- Variáveis binárias -> podem assumir 2 valores
- Variáveis discretas -> podem assumir um de um conjunto finito de valores (ex: TEMP ∈ {low, medium, high})
- Variáveis contínuas -> podem assumir qualquer valor num intervalo ou intervalo de valores reais (ex: TEMP ∈ [-50, 50])

## Nota abreviada
- Variáveis binárias: X=true -> x; X=false -> x
- Variáveis não binárias: X=x -> x, CITY=tokyo -> tokyo (se não for ambíguo!)
- Conjuntos de variáveis análogas:
  X_1=x_1
  X_2=x_2
  ...
  X_n=x_n
  -> X = (X_1, X_2, ..., X_n)
  -> x = (x_1, x_2, ..., x_n)

### Conjugação:
(X=x) ∧ (Y=y) -> (X=x, Y=y)

### Templates:
(X,Y) <- ∀_x,y (X=x, Y=y)

### Exemplos:
P(X=x, Y=y) <=> P(X=x ∧ Y=y)
P(X,Y) <=> P(X=x, Y=y) ∀_x,y

### Para binárias:
∑ P(X) = P(x) + P(¬x)

## Distribuição de Probabilidade Conjunta

Sejam \( X \) e \( Y \) variáveis aleatórias com domínios

\[dom(X) = \{x_1, x_2, \ldots, x_n\}\]

\[dom(Y) = \{y_1, y_2, \ldots, y_m\}\]

O conjunto produto

\[dom(X) \times dom(Y)\]

é transformado em um espaço de probabilidade definindo

\[P(X = x_i, Y = y_j)\]

onde \( P \) é uma distribuição de probabilidade conjunta de \( X \) e \( Y \).


Aqui, estamos a definir as variáveis aleatórias \( X \) e \( Y \) com seus respectivos domínios, que são os conjuntos de todos os possíveis valores que essas variáveis podem assumir. O conjunto produto \( dom(X) \times dom(Y) \) representa todas as combinações possíveis dos valores de \( X \) e \( Y \). Para transformar esse conjunto em um espaço de probabilidade, definimos uma função de probabilidade conjunta \( P(X = x_i, Y = y_j) \), que fornece a probabilidade de \( X \) e \( Y \) assumirem valores específicos simultaneamente.

## Marginalização

Suponha que a distribuição de probabilidade conjunta de duas variáveis \( X \) e \( Y \) é dada; então

\[
P(x) = P(X = x) = P(x \land \top)
\]
\[
= P(x \land (y \lor \neg y))
\]
\[
= P((x \land y) \lor (x \land \neg y))
\]

Como

\[
P(a \lor b) = P(a) + P(b), \text{se} \ a \land b = \bot
\]

\[
= P(x \land y) + P(x \land \neg y)
\]

A distribuição de probabilidade marginal de \( X \) é

\[
P(x) = \sum_Y P(x, Y)
\]


Neste contexto, a marginalização refere-se ao processo de encontrar a distribuição de probabilidade de uma variável ao somar (ou integrar) sobre as possíveis valores de outra variável. Aqui, começamos com a distribuição de probabilidade conjunta de \( X \) e \( Y \) e mostramos que a probabilidade marginal de \( X \), \( P(X=x) \), pode ser encontrada somando todas as probabilidades conjuntas \( P(X=x, Y=y) \) para todos os valores possíveis de \( Y \). Isto é feito utilizando a regra da soma das probabilidades para eventos mutuamente exclusivos.

- Se eu tenho a distribuição de probabilidade conjunta (e, portanto, a distribuição de todas as combinações possíveis), eu posso calcular uma determinada probabilidade marginal à custa de todas as combinações possíveis das outras variáveis.
- Ou seja, o que queremos fazer quando vamos marginalizar é calcular a probabilidade de uma variável em particular tomar um determinado valor qualquer que seja o valor das restantes variáveis.

## Regra da cadeia (Chain rule, derivation)

- Para calcular esta probabilidade conjunta (com todos os valores possíveis para cada variável), ter que saber todas as probabilidades, quando o número de variáveis começa a ser muito grande, torna-se muito difícil. É aqui que surge a regra da cadeia.

Da definição de **probabilidade condicional**...

\[
P(A|B) = \frac{P(A, B)}{P(B)}
\]

\[
P(X_1 | X_2, \ldots, X_n) = \frac{P(X_1, X_2, \ldots, X_n)}{P(X_2, \ldots, X_n)}
\]

\[
\Rightarrow P(X_1, X_2, \ldots, X_n) = P(X_1 | X_2, \ldots, X_n) P(X_2, \ldots, X_n)
\]

\[
P(X_2, \ldots, X_n) = P(X_2 | X_3, \ldots, X_n) P(X_3, \ldots, X_n)
\]

\[
\vdots
\]

\[
P(X_{n-1}, X_n) = P(X_{n-1} | X_n) P(X_n)
\]

\[
P(X_n) = P(X_n)
\]

\[
P(X_1, X_2, \ldots, X_n) = P(X_1 | X_2, \ldots, X_n) \cdot P(X_2 | X_3, \ldots, X_n) \cdot P(X_3 | X_4, \ldots, X_n) \cdot \ldots \cdot P(X_{n-1} | X_n) P(X_n)
\]

\[
= \prod_{i=1}^{n-1} P(X_i | X_{i+1}, \ldots, X_n) P(X_n)
\]

Uma **rede Bayesiana** é um par \((G, P)\), onde:

- \(G = (V(G), A(G))\) é um grafo direcionado acíclico, com
  - \(V(G) = \{v_1, v_2, \ldots, v_n\}\), um conjunto de vértices
  - \(A(G) \subseteq V(G) \times V(G)\), um conjunto de arcos

- \(P: V(G) \to [0, 1]\) é uma distribuição de probabilidade conjunta:

\[
P(V(G)) = \prod_{i=1}^{n} P(v_i | \pi_G(v_i))
\]

onde \(\pi_G(v_i)\) denota o conjunto de ancestrais imediatos (pais) do vértice \(v_i\) em \(G\).

- A probabilidade condicional é a probabilidade de um evento ocorrer dado que outro evento já ocorreu. A fórmula básica é \(P(A|B) = \frac{P(A, B)}{P(B)}\), onde \(P(A, B)\) é a probabilidade conjunta dos eventos \(A\) e \(B\), e \(P(B)\) é a probabilidade do evento \(B\).

- Nas redes Bayesianas, utilizamos a probabilidade condicional para definir a relação entre as variáveis. A rede Bayesiana é um grafo direcionado acíclico que representa um conjunto de variáveis e suas relações condicionais. Cada vértice no grafo representa uma variável, e os arcos direcionados entre os vértices indicam dependências condicionais.

- A distribuição de probabilidade conjunta de todas as variáveis na rede pode ser decomposta em um produto de probabilidades condicionais, utilizando a regra da cadeia (chain rule). Isto é útil para simplificar o cálculo das probabilidades conjuntas em sistemas complexos com muitas variáveis, facilitando a inferência e a aprendizagem de padrões a partir dos dados.

- A fórmula final para a probabilidade conjunta de todas as variáveis \(X_1, X_2, \ldots, X_n\) é um produto das probabilidades condicionais de cada variável, dado as suas variáveis parentais na rede.

- Quando algumas independências são declaradas entre as variáveis, a quantidade de informação necessária para calcular as probabilidades pode ser, então, reduzida. Em redes Bayesianas, isso é representado pela ausência de arcos diretos entre certos vértices, indicando que essas variáveis são independentes condicionalmente a outras variáveis. Por exemplo, se \(X\) e \(Y\) são independentes condicionalmente a \(Z\), então podemos escrever \(P(X, Y | Z) = P(X | Z) P(Y | Z)\).

- Essas independências permitem decompor a distribuição de probabilidade conjunta de uma maneira mais simples e eficiente. Em contraste, se todas as variáveis tivessem relações diretas entre si, não poderíamos simplificar a decomposição e precisaríamos conhecer a probabilidade conjunta completa de todas as combinações de variáveis, o que é impraticável para um grande número de variáveis.

- Portanto, o poder das redes Bayesianas reside na sua capacidade de representar e explorar essas independências condicionais, reduzindo a complexidade do problema de inferência de probabilidades em sistemas com muitas variáveis interrelacionadas.
