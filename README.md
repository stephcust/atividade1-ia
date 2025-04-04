# Atividade de Inteligência Articial - Resolução do Problema do Sudoku com heurística

### Equipe A - Integrantes:
 - Alberth Lima
 - Ana Júlia
 - Daniel Gonzalez
 - Guilherme Maciel
 - Stepheson Custódio

### 1. Explicar as regras heuristicas do Sudoku
  1. Cada célula contém exatamente um número: Para cada célula  C(r,c):
     
   $$
   \bigvee_{k=1}^{9} B_{r,c,k} \quad \text{(Pelo menos um número na célula)}
   $$

   $$
   \neg (B_{r,c,k_1} \land B_{r,c,k_2}) \quad \forall k_1 \neq k_2 \quad \text{(Sem dois números na mesma célula).}
   $$


  3. Each number appears exactly once per row: For each row  Rr  and number  k:

  4. ach number appears exactly once per column: For each column  Cc  and number  k :

### 2. Resolver o sudoku considerado o mais dificil da atualidade, utilizando as heuristicas.
![Hardest Sudoku](https://a57.foxnews.com/static.foxnews.com/foxnews.com/content/uploads/2018/09/720/405/Worlds-hardest-sudoku.jpg?ve=1&tl=1)
#### 1. Indicar, em cada passo  que regras heuristicas foi ou foram utilizadas

#### 2. Escolher que ultima heuristica foi usada para iniciar o Sudoku

### 3. Gerar a representação em CNF do Sudoku
