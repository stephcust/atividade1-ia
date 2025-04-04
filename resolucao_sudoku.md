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

  Se **|P(r, c)| = 1**, atribua o único candidato a **S[r, c]**:  
  
  $$
  \exists C(r,c), d \text{ tal que } P(r, c) = \{d\} \implies B_{r,c,d}.
  $$

  **Explicação**: Essa técnica é aplicada quando uma célula no tabuleiro possui apenas um único candidato possível. Isso ocorre porque todas as outras possibilidades foram eliminadas com base nas restrições do Sudoku (linha, coluna e bloco).
  - Exemplo: Se a célula (2, 3) só pode ser o número 5 (ou seja, o conjunto de possibilidades é {5}), então o resultado único e correto é este.
  
  ---
  
  **2. Único Oculto (Hidden Single)**  
  
  Se um dígito **d** aparecer como candidato em apenas uma célula dentro de uma unidade **U**:  
  
  $$
  \forall U, \forall d : |\{ C \in U \mid d \in P(C) \}| = 1 \implies B_{r,c,d},
  $$  
  
  onde **C(r, c)** é a única célula em ***U*** onde $$\( d \in P(r, c) \)$$.

  **Explicação**: Essa técnica identifica um número que só pode aparecer em uma única célula dentro de uma unidade (linha, coluna ou bloco), mesmo que essa célula tenha outros candidatos.
 - Exemplo: Na linha 1, se o número 7 só aparece como candidato na célula (1, 5), mesmo que (1,5) aceite 4, 6 ou 7, como o 7 tendo apenas uma célula válida, deve-se colocar o mesmo nesta.
  
  ---
  
  **3. Candidatos Bloqueados Tipo 1 (Apontando) (Locked Candidates Type 1 - Pointing)**  
  
  Se todos os candidatos para **d** em um bloco **B** estiverem confinados a uma única linha $$\ R_r \$$ (ou coluna $$\ C_c \$$):  
  
  $$
  \exists B, d, r \text{ tal que } (\forall C(r',c') \in B : d \in P(r',c')) \implies (r' = r) \land (\exists C \in B : d \in P(C)) \implies \forall c'' \text{ tal que } C(r, c'') \notin B : \neg B_{r,c'',d}.
  $$

  **Explicação**: Essa técnica é usada quando todos os candidatos de um número d em um bloco estão confinados a uma única linha ou coluna dentro do bloco. Isso implica que o número d não pode aparecer em outras células dessa linha ou coluna fora do bloco.  
  - Exemplo: Imagine que num bloco, o número 9 só pode ir nas células de posições (1,1) e (1,2). Isso fixa o 9 nesta linha dentro do bloco. Então, não pode haver um 9 em outras células     da linha 1 fora desse bloco, como na posição de outros blocos (1,4) ou (1,7).

### 2. Resolver o sudoku considerado o mais dificil da atualidade, utilizando as heurísticas.
![Hardest Sudoku](https://a57.foxnews.com/static.foxnews.com/foxnews.com/content/uploads/2018/09/720/405/Worlds-hardest-sudoku.jpg?ve=1&tl=1)

1. Indicar, em cada passo, que regras heurísticas foi ou foram utilizadas

2. Escolher que última heurística foi usada para iniciar o Sudoku
    
---

   **Resolução passo a passo**:
   
   célula (2,5) &rarr; 2. Hidden Single (n5)  
   célula (5,6) &rarr; 2. Hidden Single (n3)  
   célula (7,8) &rarr; 15. Alternating Inference Chains (n1)  
   célula (4,8) &rarr; 16. Forcing Chains (n7)  
   célula (4,3) &rarr; 1. Naked Single (n6)  
   célula (7,3) &rarr; 2. Hidden Single (n7)  
   célula (4,8) &rarr; 16. Forcing Chains (n7)  
   célula (1,2) &rarr; 16. Forcing Chains (n4)  
   célula (2,2) &rarr; 2. Hidden Single (n3)  
   célula (3,9) &rarr; 2. Hidden Single (n3)  
   célula (7,1) &rarr; 16. Forcing Chains (n3)  
   célula (9,5) &rarr; 2. Hidden Single (n3)  
   célula (4,9) &rarr; 16. Forcing Chains (n2)  
   célula (4,4) &rarr; 2. Hidden Single (n1)  
   célula (8,6) &rarr; 2. Hidden Single (n1)  
   célula (8,4) &rarr; 2. Hidden Single (n7)  
   célula (9,2) &rarr; 2. Hidden Single (n2)  
   célula (6,6) &rarr; 7. Naked Subset e 16. Forcing Chains (n6)  
   célula (4,2) &rarr; 2. Hidden Single (n9)  
   célula (4,5) &rarr; 2. Hidden Single (n8)  
   célula (6,2) &rarr; 2. Hidden Single (n5)  
   célula (8,2) &rarr; 2. Hidden Single (n8)  
   célula (5,1) &rarr; 2. Hidden Single (n2)  
   célula (5,3) &rarr; 2. Hidden Single (n8)  
   célula (9,3) &rarr; 2. Hidden Single (n1)  
   célula (2,3) &rarr; 2. Hidden Single (n9)  
   célula (3,3) &rarr; 2. Hidden Single (n2)  
   célula (3,1) &rarr; 2. Hidden Single (n6)  
   célula (1,1) &rarr; 2. Hidden Single (n1)  
   célula (9,1) &rarr; 2. Hidden Single (n5)  
   célula (8,1) &rarr; 2. Hidden Single (n9)  
   célula (8,9) &rarr; 2. Hidden Single (n5)  
   célula (5,8) &rarr; 2. Hidden Single (n5)  
   célula (2,4) &rarr; 3. Locked Candidates, 16. Forcing Chains e 2. Hidden Single (n6)  
   célula (9,8) &rarr; 2. Hidden Single (n6)  
   célula (1,8) &rarr; 2. Hidden Single (n9)  
   célula (3,8) &rarr; 2. Hidden Single (n4)  
   célula (3,6) &rarr; 2. Hidden Single (n8)  
   célula (3,4) &rarr; 2. Hidden Single (n9)  
   célula (5,4) &rarr; 2. Hidden Single (n4)  
   célula (5,7) &rarr; 2. Hidden Single (n9)  
   célula (6,5) &rarr; 2. Hidden Single (n9)  
   célula (9,4) &rarr; 2. Hidden Single (n8)  
   célula (9,9) &rarr; 2. Hidden Single (n4)  
   célula (6,9) &rarr; 2. Hidden Single (n1)  
   célula (6,7) &rarr; 2. Hidden Single (n4)  
   célula (2,9) &rarr; 2. Hidden Single (n7)  
   célula (1,9) &rarr; 2. Hidden Single (n8)  
   célula (1,7) &rarr; 2. Hidden Single (n6)  
   célula (2,7) &rarr; 2. Hidden Single (n1)  
   célula (2,6) &rarr; 2. Hidden Single (n4)  
   célula (1,5) &rarr; 2. Hidden Single (n2)  
   célula (1,6) &rarr; 2. Hidden Single (n7)  
   célula (7,6) &rarr; 2. Hidden Single (n2)  
   célula (7,5) &rarr; 2. Hidden Single (n4)  
   célula (7,7) &rarr; 2. Hidden Single (n8)  
   célula (8,5) &rarr; 2. Hidden Single (n6)  
   célula (8,7) &rarr; 2. Hidden Single (n2)  

  **Sudoku Resolvido**:  
  
  ![Sudoku Resolvido](https://github.com/user-attachments/assets/a8d4b7fc-9675-42a8-a05a-a03ee0962e34)


### 3. Gerar a representação em CNF do Sudoku

```bash
def generate_cnf(sudoku, size=9):
    """
    Gera a representação CNF para um Sudoku dado, considerando a configuração e regras de unicidade.
    :param sudoku: Uma matriz 2D (lista de listas) representando o Sudoku, com números ou zeros (vazio).
    :param size: Tamanho do Sudoku (padrão 9x9).
    :return: Lista de cláusulas CNF.
    """
    cnf_clauses = []
    
    # Função auxiliar para garantir que cada célula tenha exatamente um número entre 1 e 'size'
    def add_cell_constraint(r, c):
        # Para uma célula (r, c), ela pode ter qualquer número entre 1 e 'size'
        clause = [f"x_{r}_{c}_{n}" for n in range(1, size + 1)]
        cnf_clauses.append(clause)  # A célula deve ter um número de 1 a 'size'
        
        # Exclusões para garantir que apenas um número seja colocado na célula
        for n1 in range(1, size + 1):
            for n2 in range(n1 + 1, size + 1):
                cnf_clauses.append([f"-x_{r}_{c}_{n1}", f"-x_{r}_{c}_{n2}"])
    
    # Função auxiliar para garantir a unicidade dos números por linha, coluna e bloco
    def add_unique_constraints():
        # Unicidade nas linhas, colunas e blocos
        for r in range(1, size + 1):
            for n in range(1, size + 1):
                # Linha
                for c1 in range(1, size + 1):
                    for c2 in range(c1 + 1, size + 1):
                        cnf_clauses.append([f"-x_{r}_{c1}_{n}", f"-x_{r}_{c2}_{n}"])
                
                # Coluna
                for c1 in range(1, size + 1):
                    for c2 in range(c1 + 1, size + 1):
                        cnf_clauses.append([f"-x_{c1}_{r}_{n}", f"-x_{c2}_{r}_{n}"])
                
                # Bloco (3x3)
                block_r = (r - 1) // 3 * 3 + 1
                block_c = (r - 1) % 3 * 3 + 1
                for dr in range(0, 3):
                    for dc in range(0, 3):
                        for dr2 in range(dr + 1, 3):
                            for dc2 in range(dc + 1, 3):
                                cnf_clauses.append([f"-x_{block_r + dr}_{block_c + dc}_{n}", f"-x_{block_r + dr2}_{block_c + dc2}_{n}"])

    # Função para adicionar restrições para células já preenchidas
    def add_initial_values():
        for r in range(1, size + 1):
            for c in range(1, size + 1):
                if sudoku[r-1][c-1] != 0:  # Se a célula não está vazia
                    n = sudoku[r-1][c-1]
                    cnf_clauses.append([f"x_{r}_{c}_{n}"])
                    # Elimina outros números para essa célula
                    for num in range(1, size + 1):
                        if num != n:
                            cnf_clauses.append([f"-x_{r}_{c}_{num}"])
    
    # Gerar as cláusulas CNF
    add_initial_values()
    add_unique_constraints()
    
    return cnf_clauses

# Exemplo de uso com um Sudoku 9x9:
sudoku_9x9 = [
    [0, 0, 5, 3, 0, 0, 0, 0, 0],
    [8, 0, 0, 0, 0, 0, 0, 2, 0],
    [0, 7, 0, 0, 1, 0, 5, 0, 0],
    [4, 0, 0, 0, 0, 5, 3, 0, 0],
    [0, 1, 0, 0, 7, 0, 0, 0, 6],
    [0, 0, 3, 2, 0, 0, 0, 8, 0],
    [0, 6, 0, 5, 0, 0, 0, 0, 9],
    [0, 0, 4, 0, 0, 0, 0, 3, 0],
    [0, 0, 0, 0, 0, 0, 9, 7, 0]
]

cnf_clauses = generate_cnf(sudoku_9x9)

# Imprimir as cláusulas CNF
for clause in cnf_clauses[:208]:  # Exibindo apenas as primeiras 50 cláusulas
    print(clause)
```

**Terminal**

```bash 
['x_1_3_5']
['-x_1_3_1']
['-x_1_3_2']
['-x_1_3_3']
['-x_1_3_4']
['-x_1_3_6']
['-x_1_3_7']
['-x_1_3_8']
['-x_1_3_9']
['x_1_4_3']
['-x_1_4_1']
['-x_1_4_2']
['-x_1_4_4']
['-x_1_4_5']
['-x_1_4_6']
['-x_1_4_7']
['-x_1_4_8']
['-x_1_4_9']
['x_2_1_8']
['-x_2_1_1']
['-x_2_1_2']
['-x_2_1_3']
['-x_2_1_4']
['-x_2_1_5']
['-x_2_1_6']
['-x_2_1_7']
['-x_2_1_9']
['x_2_8_2']
['-x_2_8_1']
['-x_2_8_3']
['-x_2_8_4']
['-x_2_8_5']
['-x_2_8_6']
['-x_2_8_7']
['-x_2_8_8']
['-x_2_8_9']
['x_3_2_7']
['-x_3_2_1']
['-x_3_2_2']
['-x_3_2_3']
['-x_3_2_4']
['-x_3_2_5']
['-x_3_2_6']
['-x_3_2_8']
['-x_3_2_9']
['x_3_5_1']
['-x_3_5_2']
['-x_3_5_3']
['-x_3_5_4']
['-x_3_5_5']
['-x_3_5_6']
['-x_3_5_7']
['-x_3_5_8']
['-x_3_5_9']
['x_3_7_5']
['-x_3_7_1']
['-x_3_7_2']
['-x_3_7_3']
['-x_3_7_4']
['-x_3_7_6']
['-x_3_7_7']
['-x_3_7_8']
['-x_3_7_9']
['x_4_1_4']
['-x_4_1_1']
['-x_4_1_2']
['-x_4_1_3']
['-x_4_1_5']
['-x_4_1_6']
['-x_4_1_7']
['-x_4_1_8']
['-x_4_1_9']
['x_4_6_5']
['-x_4_6_1']
['-x_4_6_2']
['-x_4_6_3']
['-x_4_6_4']
['-x_4_6_6']
['-x_4_6_7']
['-x_4_6_8']
['-x_4_6_9']
['x_4_7_3']
['-x_4_7_1']
['-x_4_7_2']
['-x_4_7_4']
['-x_4_7_5']
['-x_4_7_6']
['-x_4_7_7']
['-x_4_7_8']
['-x_4_7_9']
['x_5_2_1']
['-x_5_2_2']
['-x_5_2_3']
['-x_5_2_4']
['-x_5_2_5']
['-x_5_2_6']
['-x_5_2_7']
['-x_5_2_8']
['-x_5_2_9']
['x_5_5_7']
['-x_5_5_1']
['-x_5_5_2']
['-x_5_5_3']
['-x_5_5_4']
['-x_5_5_5']
['-x_5_5_6']
['-x_5_5_8']
['-x_5_5_9']
['x_5_9_6']
['-x_5_9_1']
['-x_5_9_2']
['-x_5_9_3']
['-x_5_9_4']
['-x_5_9_5']
['-x_5_9_7']
['-x_5_9_8']
['-x_5_9_9']
['x_6_3_3']
['-x_6_3_1']
['-x_6_3_2']
['-x_6_3_4']
['-x_6_3_5']
['-x_6_3_6']
['-x_6_3_7']
['-x_6_3_8']
['-x_6_3_9']
['x_6_4_2']
['-x_6_4_1']
['-x_6_4_3']
['-x_6_4_4']
['-x_6_4_5']
['-x_6_4_6']
['-x_6_4_7']
['-x_6_4_8']
['-x_6_4_9']
['x_6_8_8']
['-x_6_8_1']
['-x_6_8_2']
['-x_6_8_3']
['-x_6_8_4']
['-x_6_8_5']
['-x_6_8_6']
['-x_6_8_7']
['-x_6_8_9']
['x_7_2_6']
['-x_7_2_1']
['-x_7_2_2']
['-x_7_2_3']
['-x_7_2_4']
['-x_7_2_5']
['-x_7_2_7']
['-x_7_2_8']
['-x_7_2_9']
['x_7_4_5']
['-x_7_4_1']
['-x_7_4_2']
['-x_7_4_3']
['-x_7_4_4']
['-x_7_4_6']
['-x_7_4_7']
['-x_7_4_8']
['-x_7_4_9']
['x_7_9_9']
['-x_7_9_1']
['-x_7_9_2']
['-x_7_9_3']
['-x_7_9_4']
['-x_7_9_5']
['-x_7_9_6']
['-x_7_9_7']
['-x_7_9_8']
['x_8_3_4']
['-x_8_3_1']
['-x_8_3_2']
['-x_8_3_3']
['-x_8_3_5']
['-x_8_3_6']
['-x_8_3_7']
['-x_8_3_8']
['-x_8_3_9']
['x_8_8_3']
['-x_8_8_1']
['-x_8_8_2']
['-x_8_8_4']
['-x_8_8_5']
['-x_8_8_6']
['-x_8_8_7']
['-x_8_8_8']
['-x_8_8_9']
['x_9_7_9']
['-x_9_7_1']
['-x_9_7_2']
['-x_9_7_3']
['-x_9_7_4']
['-x_9_7_5']
['-x_9_7_6']
['-x_9_7_7']
['-x_9_7_8']
['x_9_8_7']
['-x_9_8_1']
['-x_9_8_2']
['-x_9_8_3']
['-x_9_8_4']
['-x_9_8_5']
['-x_9_8_6']
['-x_9_8_8']
['-x_9_8_9']
['-x_1_1_1', '-x_1_2_1']
```
