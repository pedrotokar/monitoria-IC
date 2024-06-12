# Simulado para A2 de IC - Turma do Flávio

## Questão 1

Você estava estudando, como todo bom estudante, e encontrou o seguinte código que converte números no sistema decimal para números romanos no GitHub do professor Flávio:

```python
def num_romanos(num):
    if 3 < num <= 5:
        res = (5 - num) * 'I' + 'V'
    elif  num > 5:
        res = 'V' + (num-5) * 'I'
    elif 1 <= num <= 3:
        res = num * 'I'
    else:
        print(f"não sei converter {num}!")
    return res
```

Essa implementacao é bacana e bem fácil de entender, mas só funciona com números até 8. Depois disso, ele converte incorretamente os números. 

**Item a)**
Adicione mais uma condicional na função, para tratar o caso do número nove. Também faca a função não converter números acima de 9, (atualmente, ela só não tenta converter números menores que 1).

```python
def num_romanos(num):
    if #_________________:
        print(f"não sei converter {num}!")
        res = ""
    elif 1 <= num <= 3:
        res = num * 'I'
    if 3 < num <= 5:
        res = (5 - num) * 'I' + 'V'
    elif  #_________________:
        res = 'V' + (num-5) * 'I'
    #_________________
        #_________________
    return res
```

Agora, seu código funciona para números de 1 a 9. Mas você e um espírito incansável e quer fazer ele funcionar para *todos* os números de 1 a 3999 (depois disso, a representação em romanos precisa de barras acima dos números, o que é muita dor de cabeça de fazer). Observando o algorítmo (e o funcionamento do sistema de numeração romano), você percebe que é possível fazer uma implementação que processe diferentes casas decimais independentemente das outras. Para comecar a implementar essa ideia, você resolve usar um dicionário (que você também encontrou no GitHub do professor Flávio):

```python
val = {"I": 1,
       "V": 5,
       "X": 10,
       "L": 50,
       "C": 100,
       "D": 500,
       "M": 1000}
```

**Item b)**
Faça, do jeito que preferir, com que o dicionário fornecido seja invertido (sem declará-lo de novo manualmente!).

Agora, você quer ter uma forma de saber qual o algarismo presente em determinada casa decimal de um número. 

**Item c)**
Faça um código que, dado um número e qual casa decimal se quer ver o algarismo, retorne ele como inteiro (exemplo: dado o número 3247 e a casa decimal 100, retorna 4 (a casa das centenas)). Obs: você deve fazer isso usando apenas operações básicas do python (soma, subtração, multiplicação, divisão, divisão inteira e divisão modular).

Com essas ferramentas em mãos, esta na hora de fazer a função desejada. 

**Item d)**
Complete com o que for necessário para fazer a conversão de todos os números entre 1 e 3999 para forma romana:

```python
def numeros_romanos_melhorado(num):
    if #________________________:
        print(f"nao sei converter {num}!")
    else:
        resultado = ""
        for casa_decimal in [1000, 100, 10, 1]:
            ordem = #______________________________________
            if ordem == 0:
                continue
            elif 1 <= ordem <= 3:
                resultado += ordem * dict_inv[casa_decimal]
            elif 4 <= ordem <= 5:
                resultado += (5 - ordem) * dict_inv[casa_decimal] + dict_inv[casa_decimal * 5]
            #______________________________________:
                #__________________________________________________
            #______________________________________:
                resultado += dict_inv[casa_decimal] + dict_inv[casa_decimal * 10]
        return resultado
```

## Questão 2

Você está fazendo um trabalho da matéria mais legal do 3º período, TACD, e a parte mais difícil envolve multiplicar duas matrizes definidas com numpy. O maior problema é que, enquanto uma das matrizes é fornecida já com dois eixos, a outra deve ser feita manipulando uma array unidimensional do numpy. Para entregar o trabalho, você deve fazer a manipulação pertinente usando o método `reshape`.

Abaixo, está o trecho de código e com a matriz, a array unidmensional, e a linha para fazer a multiplicação entre elas.

```python
matriz = np.asarray(
    ((0, 1, 2, 4, 6, 8),
     (9, 4, 5, 3, 2, 6),
     (0, 2, 6, 7, 3, 4),
     (1, 1, 1, 1, 1, 1))
)

array = np.arange(n)

resultado = np.dot(matriz, array.reshape(tupla))
```

Para que sua multiplicação dê certo, quais condições devem ser cumpridas?

**a)** o número n tem que ser multiplo de 4, e a tupla deve conter os valores (4, 6)

**b)** o número n tem que ser multiplo de 6, e a tupla deve conter os valores (n/4, n) 

**c)** o número n tem que ser especificamente 6, e a tupla deve ter apenas um elemento, 6

**d)** o número n tem que ser especificamente 4, e a tupla deve ser (4, -1)

**e)** o número n tem que ser multiplo de 6, e a tupla deve conter os valores (6, n/6)

## Questão 3

No python, existem diversos tipos de estruturas que guardam mais de um elemento, tanto padrões da lingugagem tanto quanto em bibliotecas padrão. Marque as estruturas que guardam informações de ordenação dos elementos inseridos nelas:

- [ ] Dicionário (`dict`)
- [ ] Lista (`list`)
- [ ] Conjunto (`set`)
- [ ] Tupla (`tuple`)
- [ ] Dicionário ordenado (`OrderedDict`)
- [ ] String (`str`)
- [ ] Dicionário com valor padrão (`defaultdict`)

## Questão 4

Você precisa fazer uma função que age como uma fábrica de funções para resolver polinômios. Para isso, sua função deve receber uma lista de números $\[n_1,n_2,n_3,...]$ e o retorno dela deverá ser outra função, que recebe qualquer número real e retorna o valor do polinômio $n_1+n_2x+n_3x^2+n_4x^3+...$ . Complete as lacunas para que isso seja possível:

```python
def gera_funcao_polinomial(lista_coeficientes):
    
    def func_polinomio(x):
        #_____________________
        #_____________________
        #_____________________
        #_____________________

    return #_____________________
```

Se quiser se desafiar, faça a função `gera_funcao_polinomial` receber um dicionário, com a chave sendo um inteiro representando a potência de x, e o valor sendo o coeficiente.

## Questão 5

João trabalha com problemas muito difíceis de álgebra linear e precisa programar um gerador de matrizes de três eixos. Esse gerador deve ter um parâmetro n, representando o tamanho da primeira dimensão, e deve gerar uma matriz $n \cross \floor{\frac{n}{2}} \cross 3n$, sendo que um elemento $i,j,k$ deve ser igual à $i^{j - k} + 3$. Ele programou da seguinte forma:

```python
def gera_matriz(n):
    matriz_3_eixos = [[[i ** j - k + 3 for k in range(j * 3)] for j in range(i//2)] for i in range(n)]
    return matriz_3_eixos
```

Corrija o código para funcionar como deveria.

## Questão 6

Imagine que exista uma função python que recebe um número k e uma lista, e itera k vezes, realizando as seguintes instruções em cada uma das vezes:
    1 - multiplica cada elemento com índice ímpar da lista por (número da iteração + 2, numero da iteração começa em 0);
    2 - subtrai de cada elemento com índice par da lista o elemento de indíce ímpar que vem antes dele;
    3 - para cada par de elementos da lista (começando com o par de elementos de índices 0 e 1, depois partindo para os de índice 1 e 2, etc), os modifica, fazendo o primeiro ser a soma dos dois e o segundo ser o módulo da diferença.
Qual será a saída dessa função, se alimentada com k = 5 e com a lista [1, 4, 2, 9, 4, 6, 8]?

**a)** [-29, 1214, -394, 806, 1064, 778, 478];

**b)** [1214, -802, 7096, 7140, 22, 14102, 8366];

**c)** [301, 561, 31, 806, 130, 1543, 693];

**d)** [110, 90, 247, 237, 166, 66, 960];

**e)** [-5, -955, 1253, -902, -1088, 25013, 13477],

## Questão 7

Qual das alternativas melhor descreve a lingugagem de programção Python?

**a)** Python é uma lingugagem interpretada, de paradigma procedural, dinamicamente tipada, e todos os tipos são objetos;

**b)** Python é uma lingugagem compilada, com paradigma imperativo, fracamente e dinamicamente tipada;

**c)** Python tem tipagem estática, é uma lingugagem compilada e de paradigma funcional, que não aceita programação voltada a objetos;

**d)** Python tem tipagem dinamica e fraca, é uma lingugaem compilada e tem suporte a programação voltada a objetos;

**e)** Python é uma linguagem interpretada, de paradigma imperativo, que tem tipagem estática.
