# Aula de Lógica de Predicados com Resolução de Exercícios

## Introdução à Lógica de Predicados

A lógica de predicados é uma extensão da lógica proposicional que permite representar conhecimentos mais complexos, como relações entre objetos e propriedades dos objetos. Ela é essencial para raciocínio formal, inteligência artificial, prova de teoremas e representação de conhecimento.

### Conceitos Fundamentais

#### 1. **Termos**

* **Constantes**: representam objetos específicos (ex: "João", "Maçã").
* **Variáveis**: representam objetos arbitrários (ex: x, y).
* **Funções**: mapeiam objetos para objetos (ex: pai(x)).

#### 2. **Predicados**

Expressam propriedades ou relações entre termos. Exemplos:

* Gosta(João, Maçã) significa que João gosta de Maçã.
* Come(Paulo, y) significa que Paulo come y.

#### 3. **Quantificadores**

* **Universal ($\forall$)**: "para todo"

  * Ex: $\forall x \; P(x)$ → P(x) é verdadeiro para todo x.
* **Existencial ($\exists$)**: "existe ao menos um"

  * Ex: $\exists x \; P(x)$ → Existe ao menos um x para o qual P(x) é verdadeiro.

#### 4. **Conectivos Lógicos**

* $\land$: e
* $\lor$: ou
* $\rightarrow$: implicação
* $\leftrightarrow$: bicondicional ("se e somente se")
* $\lnot$: negação

#### 5. **Forma Normal Conjuntiva (FNC)**

Conjunto de cláusulas (disjunções de literais) que facilita a aplicação de algoritmos como a **Resolução**.

**Exemplo:**
$\forall x (P(x) \rightarrow Q(x))$ se torna $\neg P(x) \lor Q(x)$.

#### 6. **Resolução**

Técnica automática de inferência. Baseia-se na aplicação da regra:
$A \lor C, \; \neg A \lor D \Rightarrow C \lor D$
Utiliza substituição de variáveis (unificação).

#### 7. **Tableaux (Poussinhos)**

Técnica de prova para demonstrar insatisfatibilidade. Assume a negação do que se quer provar e expande as possibilidades até obter uma contradição.

#### 8. **Validade de Argumentos**

Um argumento é válido se, sempre que as premissas forem verdadeiras, a conclusão também for.

---

## Parte 1: Formalização e Validade de Argumentos com Lógica Proposicional

### a)

**Argumento:**
Se Deus existe, então a vida tem significado. Deus existe. Portanto, a vida tem significado.

**Formalização:**

* D: Deus existe
* V: A vida tem significado

1. D → V
2. D
3. ∴ V

**Validade:** Válido (Modus Ponens)

---

### b)

**Argumento:**
Deus não existe. Pois, se Deus existisse, a vida teria significado. Mas a vida não tem significado.

**Formalização:**

* D: Deus existe
* V: A vida tem significado

1. D → V
2. ¬V
3. ∴ ¬D

**Validade:** Válido (Modus Tollens)

---

### c)

**Argumento:**
Se o avião não tivesse caído, teríamos feito contato pelo rádio. Não fizemos contato pelo rádio. Portanto, o avião caiu.

**Formalização:**

* C: O avião caiu
* R: Fizemos contato pelo rádio

1. ¬C → R
2. ¬R
3. ∴ C

**Validade:** Válido (Modus Tollens)

---

### d)

**Argumento:**
Como hoje não é quinta-feira, deve ser sexta-feira. Hoje é quinta-feira ou sexta-feira.

**Formalização:**

* Q: Hoje é quinta-feira
* S: Hoje é sexta-feira

1. Q ∨ S
2. ¬Q
3. ∴ S

**Validade:** Válido (Silogismo Disjuntivo)

---

### e)

**Argumento:**
Se hoje é quinta-feira, então amanhã será sexta-feira. Se amanhã for sexta-feira, então depois de amanhã será sábado. Portanto, se hoje é quinta-feira, depois de amanhã será sábado.

**Formalização:**

* Q: Hoje é quinta-feira
* S1: Amanhã é sexta-feira
* S2: Depois de amanhã é sábado

1. Q → S1
2. S1 → S2
3. ∴ Q → S2

**Validade:** Válido (Silogismo Hipotético)

---

### f)

**Argumento:**
Hoje é fim de semana se e somente se hoje é sábado ou domingo. Portanto, hoje é fim de semana, desde que hoje é sábado.

**Formalização:**

* F: Hoje é fim de semana
* S: Hoje é sábado
* D: Hoje é domingo

1. F ↔ (S ∨ D)
2. S
3. ∴ F

**Validade:** Válido (Eliminação da Bicondicional e Modus Ponens)

---

### g)

**Argumento:**
Hoje é fim de semana se hoje é sábado ou domingo. Mas hoje não é fim de semana. Portanto, hoje não é sábado e hoje não é domingo.

**Formalização:**

* F: Hoje é fim de semana
* S: Hoje é sábado
* D: Hoje é domingo

1. (S ∨ D) → F
2. ¬F
3. ∴ ¬S ∧ ¬D

**Validade:** Válido (Contra positiva)

---

## Parte 2 - Tradução e Resolução em Lógica de Predicados

### Sentenças:

1. **"Joao gosta de todo tipo de comida"**  
2. **"Maçã é comida"**  
3. **"Frango é comida"**  
4. **"Qualquer coisa que alguém come e que não cause sua morte é comida"**  
5. **"Paulo come amendoim e ainda está vivo"**  
6. **"Susana come tudo o que Paulo come"**

---

### a) Tradução para Lógica de Predicados

**Predicados:**

- `Gosta(x, y)`: x gosta de y  
- `Comida(y)`: y é comida  
- `Come(x, y)`: x come y  
- `Morre(x)`: x morre  
- `Vivo(x)`: x está vivo  

**Constantes:**

- `joao`, `paulo`, `susana`: pessoas  
- `maca`, `frango`, `amendoim`: objetos

**Tradução:**

1. `∀y (Comida(y) → Gosta(joao, y))`  
2. `Comida(maca)`  
3. `Comida(frango)`  
4. `∀x ∀y ((Come(x, y) ∧ ¬Morre(x)) → Comida(y))`  
5. `Come(paulo, amendoim) ∧ Vivo(paulo)`  
6. `∀y (Come(paulo, y) → Come(susana, y))`

---

### b) Forma Clausulada (Forma Normal Conjuntiva - FNC)

Convertendo as fórmulas para forma clausal:

1. `∀y (¬Comida(y) ∨ Gosta(joao, y))`  
2. `Comida(maca)`  
3. `Comida(frango)`  
4. `∀x ∀y (¬Come(x, y) ∨ Morre(x) ∨ Comida(y))`  
5. `Come(paulo, amendoim)`  
6. `Vivo(paulo)`  
7. `∀y (¬Come(paulo, y) ∨ Come(susana, y))`

**Forma clausal explícita:**

- C1: `¬Comida(y) ∨ Gosta(joao, y)`  
- C2: `Comida(maca)`  
- C3: `Comida(frango)`  
- C4: `¬Come(x, y) ∨ Morre(x) ∨ Comida(y)`  
- C5: `Come(paulo, amendoim)`  
- C6: `Vivo(paulo)`  
- C7: `¬Come(paulo, y) ∨ Come(susana, y)`

---

### c) Joao gosta de amendoim?

Queremos provar: `Gosta(joao, amendoim)`

**Etapas:**

- De C5: `Come(paulo, amendoim)`  
- De C6: `Vivo(paulo)` → então `¬Morre(paulo)`  
- De C4 (instanciando x = paulo, y = amendoim):  
  `¬Come(paulo, amendoim) ∨ Morre(paulo) ∨ Comida(amendoim)`  
  Como `Come(paulo, amendoim)` e `¬Morre(paulo)` são verdade:  
  ⇒ `Comida(amendoim)`  

- De C1 (instanciando y = amendoim):  
  `¬Comida(amendoim) ∨ Gosta(joao, amendoim)`  
  Sabemos que `Comida(amendoim)` ⇒ `Gosta(joao, amendoim)`

✅ **Conclusão:** Joao gosta de amendoim.

---

### d) O que Susana come?

Queremos provar: `∃x Come(susana, x)`

Sabemos:

- C5: `Come(paulo, amendoim)`  
- C7: `¬Come(paulo, y) ∨ Come(susana, y)`  
  (instanciando y = amendoim)  
  `¬Come(paulo, amendoim) ∨ Come(susana, amendoim)`  
  Como `Come(paulo, amendoim)` é verdadeiro:  
  ⇒ `Come(susana, amendoim)`

✅ **Conclusão:** `Come(susana, amendoim)` ⇒ ∃x Come(susana, x)

