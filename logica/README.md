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


## Parte 3 - Clube de Tranca

### Fatos fornecidos:

* Os membros do Clube de Tranca da Rua Etno são: joao, salete, paulo e helena
* joao é casado com salete
* paulo é irmão de helena
* O cônjuge de um membro casado também é membro
* A última reunião do Clube foi na casa do joao

---

### a) Representação em Lógica de Predicados

**Predicados:**

* `Membro(x)`: x é membro do clube
* `CasadoCom(x, y)`: x é casado com y
* `Irmao(x, y)`: x é irmão de y
* `ReuniaoCasa(x)`: a reunião foi na casa de x

**Fatos:**

1. `Membro(joao) ∧ Membro(salete) ∧ Membro(paulo) ∧ Membro(helena)`
2. `CasadoCom(joao, salete)`
3. `Irmao(paulo, helena)`
4. `∀x∀y (CasadoCom(x, y) → (Membro(x) ∧ Membro(y)))`
5. `ReuniaoCasa(joao)`

---

### b) Provas

#### Pergunta 1: A última reunião do Clube foi na casa da salete?

Sabemos que:

* `CasadoCom(joao, salete)`
* `ReuniaoCasa(joao)`

**Hipótese implícita**: Se alguém é casado com outra pessoa e a reunião foi em sua casa, então também pode-se considerar a casa do cônjuge.

Adicionamos:

* `∀x∀y (CasadoCom(x, y) → (ReuniaoCasa(x) → ReuniaoCasa(y)))`

Assim:

* `CasadoCom(joao, salete) ∧ ReuniaoCasa(joao)` ⇒ `ReuniaoCasa(salete)`

✅ **Conclusão:** Sim, a reunião foi na casa da salete.

---

#### Pergunta 2: helena não é casada?

Sabemos:

* `CasadoCom(joao, salete)`
* Nenhuma outra relação de casamento foi declarada

**Suposição**: `¬∃x CasadoCom(helena, x)`

Nada nos fatos contradiz isso.

✅ **Conclusão:** Podemos inferir que helena não é casada.

---

## Parte 4 - Carlos e Cursos

### Fatos:

* `Gosta(carlos, x)` se `Facil(x)`
* `Dificil(ciencias)`
* `∀x (CursoPrendas(x) → Facil(x))`
* `CursoPrendas(bk301)`

---

### Resolução: De que curso Carlos gostaria?

Sabemos:

* `CursoPrendas(bk301)` ⇒ `Facil(bk301)`
* `Facil(x)` ⇒ `Gosta(carlos, x)`

Logo:

* `Gosta(carlos, bk301)`

✅ **Conclusão:** Carlos gostaria de **bk301**

---

## Parte 5 - Exame e Felicidade

### Premissas:

1. `Facil(curso) → ∃x (Estudante(x) ∧ Feliz(x, curso))`
2. `Exame(curso) → ∀x (Estudante(x) → ¬Feliz(x, curso))`

### Objetivo: Mostrar que `Exame(curso) → ¬Facil(curso)`

### Prova por resolução:

1. Suponha `Exame(curso)` e `Facil(curso)`
2. De (1): `∃x Estudante(x) ∧ Feliz(x, curso)`
3. De (2): `∀x (Estudante(x) → ¬Feliz(x, curso))`

Contradição: Existe `x` tal que `Feliz(x, curso)` e `¬Feliz(x, curso)`

✅ **Conclusão:** `Exame(curso) → ¬Facil(curso)`

---

## Parte 6 - Golfinhos e Leitura

### Premissas:

1. `∀x (PodeLer(x) → Alfabetizado(x))`
2. `∃x (Golfinho(x) ∧ Inteligente(x))`
3. `∀x (Golfinho(x) → ¬Alfabetizado(x))`

### Objetivo: Mostrar que existem coisas inteligentes que nao sabem ler

**Plano:**

* De (1) e (3): `Golfinhos não são alfabetizados ⇒ não podem ler`
* De (2): Existe um `x` tal que `Inteligente(x) ∧ Golfinho(x)`
* De (3): `¬Alfabetizado(x)` ⇒ `¬PodeLer(x)`

✅ **Conclusão:** `∃x (Inteligente(x) ∧ ¬PodeLer(x))`

---

## Parte 7 - Velocidade: Cavalos vs Coelhos

### Premissas:

* `∀x (Cavalo(x) → MaisRapido(x, cao))`
* `∀x (Coelho(x) → ¬MaisRapido(fig, x))`
* `Cavalo(centelha)`
* `Coelho(pernalonga)`

### Prova:

1. `Cavalo(centelha)` ⇒ `MaisRapido(centelha, cao)`
2. `Coelho(pernalonga)` ⇒ `¬MaisRapido(fig, pernalonga)` ⇒ `MaisRapido(pernalonga, fig) = false`
3. `MaisRapido(centelha, cao)` e `MaisRapido(fig, coelho)` ⇒ `MaisRapido(centelha, pernalonga)`

✅ **Conclusão:** Centelha é mais rápido que Pernalonga

---
