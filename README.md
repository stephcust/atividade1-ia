# Atividade de Inteligência Articial - Resolução do Problema do Sudoku com heurística

### Equipe A - Integrantes:
 - Alberth Lima
 - Ana Júlia Pereira Corrêa
 - Daniel Gonzalez
 - Guilherme Maciel
 - Stepheson Custódio

### 1. Explicar as regras heurísticas do Sudoku
  ---
  **1. Único Nú (Naked Single)**  

  Se ***|P(r, c)| = 1***, atribua o único candidato a ***S[r, c]***:  
  
  $$
  \exists C(r,c), d \text{ tal que } P(r, c) = \{d\} \implies B_{r,c,d}.
  $$

  **Explicação**: Se uma célula tem somente um candidato possível, então esse número deve estar ali.  
  - Exemplo: Se a célula (2, 3) só pode ser o número 5 (ou seja, o conjunto de possibilidades é {5}), então o resultado único e correto é este.
  
  ---
  
  **2. Único Oculto (Hidden Single)**  
  
  Se um dígito ***d*** aparecer como candidato em apenas uma célula dentro de uma unidade ***U***:  
  
  $$
  \forall U, \forall d : |\{ C \in U \mid d \in P(C) \}| = 1 \implies B_{r,c,d},
  $$  
  
  onde ***C(r, c)*** é a única célula em ***U*** onde $$\( d \in P(r, c) \)$$.

  **Explicação**: Mesmo que uma célula tenha vários candidatos, se um número só aparece como possibilidade em uma única célula dentro de uma linha, coluna ou bloco, então esse número deve estar ali, mesmo que a célula aceite outros valores.  
 - Exemplo: Na linha 1, se o número 7 só aparece como candidato na célula (1, 5), mesmo que (1,5) aceite 4, 6 ou 7, como o 7 tendo apenas uma célula válida, deve-se colocar o mesmo nesta.
  
  ---
  
  **3. Candidatos Bloqueados Tipo 1 (Apontando) (Locked Candidates Type 1 - Pointing)**  
  
  Se todos os candidatos para ***d***em um bloco ***B*** estiverem confinados a uma única linha $$\ R_r \$$ (ou coluna $$\ C_c \$$):  
  
  $$
  \exists B, d, r \text{ tal que } (\forall C(r',c') \in B : d \in P(r',c')) \implies (r' = r) \land (\exists C \in B : d \in P(C)) \implies \forall c'' \text{ tal que } C(r, c'') \notin B : \neg B_{r,c'',d}.
  $$

  **Explicação**: Se todos os candidatos a um número x dentro de um bloco estão na mesma linha ou coluna, então esse número não pode aparecer nessa linha ou coluna fora do bloco.  
  - Exemplo: Imagine que num bloco, o número 9 só pode ir nas células de posições (1,1) e (1,2). Isso fixa o 9 nesta linha dentro do bloco. Então, não pode haver um 9 em outras células     da linha 1 fora desse bloco, como na posição de outros blocos (1,4) ou (1,7).

### 2. Resolver o sudoku considerado o mais dificil da atualidade, utilizando as heurísticas.
![Hardest Sudoku](https://a57.foxnews.com/static.foxnews.com/foxnews.com/content/uploads/2018/09/720/405/Worlds-hardest-sudoku.jpg?ve=1&tl=1)

1. Indicar, em cada passo, que regras heurísticas foi ou foram utilizadas

2. Escolher que última heurística foi usada para iniciar o Sudoku
   ---
   **Resolução passo a passo:
   

### 3. Gerar a representação em CNF do Sudoku
