# Lesson 08 - Inference in Bayesian nets - an implementation of Bayesian reasoning

## Redes Bayesianas - Modelo qualitativo

### Definido por Experts

- São incluídas variáveis categóricas (as únicas que vamos falar nesta unidade curricular), considerando 3 grupos:
  - Teorias: fatores de risco ou condicionantes (ex: se é fumador)
  - Hipóteses: outcomes de estudos (ex: diagnóstico de SARS)
  - Observações: sintomas ou medição (ex: febre)

- Dependências são definidas pelo expert, atendendo à causalidade:
  - Exposição → Outcome (ex: tabagismo "provoca" um enfarte)
  - Outcome → Sintome (ex: SARS "provoca" dispneia)

### Definido pelos dados (hill-climbing)

1. Começa sem dependências
2. Calcula a verossimilhança de uns dados observados dado um modelo
3. Testa todas as possíveis dependências individualmente, reavaliando a verossimilhança dos dados
4. Se a verossimilhança aumenta acima de um certo limiar, insere essa dependência no modelo
5. Volta ao 3º, até que o limiar não seja atingido para nenhuma dependência adicional

Os modelos assim obtidos correspondem a redes facilmente relativamente simples de interpretar, uma vez que, como se trata de DAGs, não podem ser cíclicos e portanto acabam por ficar com relativamente poucos dados.

Não pode ser interpretado como um modelo causal!! As setas indicam se é que há informação sobre uma variável nos dá mais informação sobre uma outra variável. Corresponde a associação e não causalidade.

## Redes Bayesianas - Modelo quantitativo

- Definido por:
  - Experts (subjetivamente)
  - Teorias (da literatura, como por ex. meta-análises)
  - Dados (de um estudo original)

- Interpretação do modelo quantitativo:
  - Quando definido por um expert, é baseado num baixo nível de evidência
  - Quando definido em meta-análises, é baseado num elevado nível
  - Quando baseado num estudo original, vai depender do desenho:
    - Coorte → representa risco quando a variável condicionada não foi controlada (incluindo outcome), caso contrário é uma associação
    - Caso-controle → mesmo que o anterior mas excluindo outcome
    - Ensaios clínicos → representa risco de acordo com a randomização ou a informação é interpretável como uma associação

## Redes Bayesianas - Considerações adicionais

- Modelo qualitativo de representação de conhecimento
- Modelo quantitativo de associação
- Podem ser utilizados como modelo final de:
  - Estudos originais - expressando as associações encontradas
  - Meta-análise - expressando evidência agregada
  - Sistemas de suporte à decisão - expressando risco à posteriori de um dado evento
