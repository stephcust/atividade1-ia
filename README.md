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


  2. Cada número aparece exatamente uma vez por linha

  $$
  \forall U, \forall d: \left| \{ C \in U \mid d \in P(C) \} \right| = 1 \implies B_{r,c,d},
  $$ 
  
  onde \(C(r, c)\) é a célula única em \(U\) onde \( d $$\in$$ P(r, c)\).

  3. ach number appears exactly once per column: For each column  Cc  and number  k :

### 2. Resolver o sudoku considerado o mais dificil da atualidade, utilizando as heuristicas.
![Hardest Sudoku](https://a57.foxnews.com/static.foxnews.com/foxnews.com/content/uploads/2018/09/720/405/Worlds-hardest-sudoku.jpg?ve=1&tl=1)

1. Indicar, em cada passo, que regras heurísticas foi ou foram utilizadas

2. Escolher que última heurística foi usada para iniciar o Sudoku

3. Gerar a representação em CNF do Sudoku
