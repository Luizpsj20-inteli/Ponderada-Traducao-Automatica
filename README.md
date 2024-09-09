# Ponderada-Traducao-Automatica

### Pergunta 1:
**Tente valores diferentes do argumento `num_examples` na função `load_data_nmt`. Como isso afeta os tamanhos do vocabulário do idioma de origem e do idioma de destino?**

**Resposta:**
Ao variar o valor de `num_examples`, podemos observar um impacto direto nos tamanhos dos vocabulários de origem e destino. Os resultados do teste mostram:

- **Num examples: 100**
  - Tamanho do vocabulário da origem: 40
  - Tamanho do vocabulário do destino: 40

- **Num examples: 500**
  - Tamanho do vocabulário da origem: 159
  - Tamanho do vocabulário do destino: 163

- **Num examples: 1000**
  - Tamanho do vocabulário da origem: 266
  - Tamanho do vocabulário do destino: 321

- **Num examples: 2000**
  - Tamanho do vocabulário da origem: 454
  - Tamanho do vocabulário do destino: 585

Esses resultados indicam que, à medida que o valor de `num_examples` aumenta, mais frases são processadas, e o tamanho dos vocabulários de origem e destino aumenta proporcionalmente. Isso acontece porque mais exemplos expõem o modelo a uma maior variedade de palavras, resultando em um vocabulário mais extenso.

---

### Pergunta 2:
**O texto em alguns idiomas, como chinês e japonês, não tem indicadores de limite de palavras (por exemplo, espaço). A tokenização em nível de palavra ainda é uma boa ideia para esses casos? Por que ou por que não?**

**Resposta:**
A tokenização em nível de palavra não é eficaz para idiomas como o chinês, onde não há separadores explícitos (como espaços) entre palavras. Os resultados da comparação de tokenização no notebook são:

- **Tokenização por palavras:**
  - `[['我喜欢学习深度学习'], ['深度学习改变了世界']]`
  
  Aqui, toda a frase é considerada uma única "palavra", o que não é útil para modelagem, pois não identifica corretamente as unidades semânticas menores.

- **Tokenização por caracteres:**
  - `[['我', '喜', '欢', '学', '习', '深', '度', '学', '习'], ['深', '度', '学', '习', '改', '变', '了', '世', '界']]`

  A tokenização por caracteres separa cada caractere, o que é muito mais adequado para o chinês, onde cada caractere pode representar uma palavra ou parte de uma palavra.

Portanto, para idiomas como chinês ou japonês, a tokenização em nível de caractere é mais apropriada, pois a tokenização em nível de palavra falha em capturar corretamente as unidades semânticas nesses idiomas.
