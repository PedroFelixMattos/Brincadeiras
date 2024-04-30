Programa pra calcular a probabilidade de cada valor que pode sair ao se rolar alguns dados de alguns lados
A quantidade de dados, o lado dos dados deve ser indicado
Caso não seja, os valores default são 1 para ambos
Durante a verificação dos resultados podemos filtrar por uma faixa de valores minimas a maximas,
além de pedir entre o valro de cada resultado ou a soma dos valores da faixa
Os resultados podem ser apresentados de forma aritmetica ou de porcentagem

Os resultados são apresentados em um vetor que vai do 0 até o valor maximo
que é: numero de dados * tamanho dos dados

Durante o seu calculo é feita uma matriz cuja coluna são os tamanhos dos dados e as linhas
a quantidade de dados

Por exemplo: 3 dados de 4 lados

[1 1 1]
[2 2 2]
[3 3 3]
[4 4 4]

e então é adicionada uma linha de controle com apenas zeros no seu fim, ficando

[1 1 1]
[2 2 2]
[3 3 3]
[4 4 4]
[0 0 0]

Essa linha de controle é atualizada ao longo dos código e vai de 0 até (tamanho dos dado) * -1
ela se atualiza a cada passagem do sistema começando pela ultima coluna, a coluna anterior só
atualiza caso todas as outras estejama atualizadas:

Por exemplo:

[1 1 1]
[2 2 2]
[3 3 3]
[4 4 4]
[0 0 0]
vira
[1 1 1]
[2 2 2]
[3 3 3]
[4 4 4]
[0 0 -1]
vira
[1 1 1]
[2 2 2]
[3 3 3]
[4 4 4]
[0 0 -2]
vira
[1 1 1]
[2 2 2]
[3 3 3]
[4 4 4]
[0 0 -3]
vira
[1 1 1]
[2 2 2]
[3 3 3]
[4 4 4]
[0 0 -4]
vira
[1 1 1]
[2 2 2]
[3 3 3]
[4 4 4]
[0 -1 0]

Até o seu ultimo lçao, que seria

[1 1 1]
[2 2 2]
[3 3 3]
[4 4 4]
[-3 -4 -4]
vira
[1 1 1]
[2 2 2]
[3 3 3]
[4 4 4]
[-4 -4 -4]

Essa linha serve para indicar quais valores serão utilizados nas
somas

A soma é cada elemento da coluna na linha indicada pelo controle*-1
Por exemplo

[1 1 1]
[2 2 2]
[3 3 3]
[4 4 4]
[-1 0 -3]

indica a soma dos elementos [0,1]+[1,0]+[2,3]=2+1+4=7
e então o vetor valores_possiveis na posição [7] é acrssido em 1

Devido ao tamanho crescente uma vez que mais dados são rolados o codigo começa a ficar lento
logo na versão 2 o codigo foi alterado para calcular uma tabela que englobe todos os valores
em uma faixa maxima de tamanhos de dados e numero de dados.

Cada vetor calculado é tageado para representar o numero de dados tamanho de dados e possiveis somas:
por exemplo:

Com 3 dados de 4 lados
[3, 4, vetor com a chance de cada resultado]

em uma tabela que avalie até 4 dados de 4 lados a tabela seria:

[[1, 1, vetor com a chance de cada resultado]


[1, 2, vetor com a chance de cada resultado]

[1, 3, vetor com a chance de cada resultado]

[1, 4, vetor com a chance de cada resultado]

[2, 1, vetor com a chance de cada resultado]

[2, 2, vetor com a chance de cada resultado]

[2, 3, vetor com a chance de cada resultado]

[2, 4, vetor com a chance de cada resultado]

[3, 1, vetor com a chance de cada resultado]

[3, 2, vetor com a chance de cada resultado]

[3, 3, vetor com a chance de cada resultado]

[3, 4, vetor com a chance de cada resultado]

[4, 1, vetor com a chance de cada resultado]

[4, 2, vetor com a chance de cada resultado]

[4, 3, vetor com a chance de cada resultado]

[4, 4, vetor com a chance de cada resultado]]

Uma vez tendo a tabela criada ela é salva e pode ser carregada novamente
caso então desejemos saber a conta de 2 dados de 4 lados o codigo ira 
rapiamente para o ponto tageado por [2,4] e os calculos são feitos



