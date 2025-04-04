# Atividade de Inteligência Articial - Resolução do Problema do Sudoku com heurística

### Equipe A - Integrantes:
 - Alberth Lima
 - Ana Júlia
 - Daniel Gonzalez
 - Guilherme Maciel
 - Stepheson Custódio

### 1. Explicar as regras heuristicas do Sudoku
  ---
  **1. Único Nú (Naked Single)**  

  Se ***|P(r, c)| = 1***, atribua o único candidato a ***S[r, c]***:  
  
  $$
  \exists C(r,c), d \text{ tal que } P(r, c) = \{d\} \implies B_{r,c,d}.
  $$
  
  ---
  
  **2. Único Oculto (Hidden Single)**  
  
  Se um dígito ***d*** aparecer como candidato em apenas uma célula dentro de uma unidade ***U***:  
  
  $$
  \forall U, \forall d : |\{ C \in U \mid d \in P(C) \}| = 1 \implies B_{r,c,d},
  $$  
  
  onde ***C(r, c)*** é a única célula em ***U*** onde $$\( d \in P(r, c) \)$$.
  
  ---
  
  **3. Candidatos Bloqueados Tipo 1 (Apontando) (Locked Candidates Type 1 - Pointing)**  
  
  Se todos os candidatos para ***d***em um bloco ***B*** estiverem confinados a uma única linha $$\ R_r \$$ (ou coluna $$\ C_c \$$):  
  
  $$
  \exists B, d, r \text{ tal que } (\forall C(r',c') \in B : d \in P(r',c')) \implies (r' = r) \land (\exists C \in B : d \in P(C)) \implies \forall c'' \text{ tal que } C(r, c'') \notin B : \neg B_{r,c'',d}.
  $$

### 2. Resolver o sudoku considerado o mais dificil da atualidade, utilizando as heuristicas.
![Hardest Sudoku](https://a57.foxnews.com/static.foxnews.com/foxnews.com/content/uploads/2018/09/720/405/Worlds-hardest-sudoku.jpg?ve=1&tl=1)
#### 1. Indicar, em cada passo  que regras heuristicas foi ou foram utilizadas

#### 2. Escolher que ultima heuristica foi usada para iniciar o Sudoku

### 3. Gerar a representação em CNF do Sudoku
