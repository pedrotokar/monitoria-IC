# Gabarito

Não se esqueçam que esse gabarito contém possíveis soluções para as questões, mas que nada é absoluto ou apenas o que está aqui é certo. 
Se sua solução funciona para todos os casos que deveriam funcionar, ela está certa (por mais que possa não ser a mais otimizada, mas 
até aí as minhas não necessariamente são :D). Se não entender alguma ou divergir, me mande um zapzap para conversarmos.

## Questão 1 

**Item a)**

```python
def num_romanos(num):
    if num <= 0 or num >= 10:
        print(f"não sei converter {num}!")
        res = ""
    elif 1 <= num <= 3:
        res = num * 'I'
    if 3 < num <= 5:
        res = (5 - num) * 'I' + 'V'
    elif  6 <= num  <= 8:
        res = 'V' + (num-5) * 'I'
    else:  
        res = 'IV'
    return res
```

**Item b)**

```python
dict_inv = dict()
for key, value in val.items():
    dict_inv[value] = key
```

**Item c)**

```python
def retorna_algarismo(numero, grandeza):
	return int((numero % (grandeza*10)) // (grandeza))
```

**Item d)**

```python
def numeros_romanos_melhorado(num):
    if num >= 4000 or num < 0:
        print(f"nao sei converter {num}!")
    else:
        resultado = ""
        for casa_decimal in [1000, 100, 10, 1]:
            ordem = retorna_algarismo(num, casa_decimal)
            if ordem == 0:
                continue
            elif 1 <= ordem <= 3:
                resultado += ordem * dict_inv[casa_decimal]
            elif 4 <= ordem <= 5:
                resultado += (5 - ordem) * dict_inv[casa_decimal] + dict_inv[casa_decimal * 5]
            elif 6 <= ordem <= 8:
                resultado += dict_inv[casa_decimal * 5] + (ordem - 5) * dict_inv[casa_decimal]
            else:
                resultado += dict_inv[casa_decimal] + dict_inv[casa_decimal * 10]
        return resultado
```

## Questão 2
Resposta: item e)

O método `dot`, quando usado em arrays numpy de duas dimensões, age como uma multiplicação de matrizes. Logo, o número de elementos da 
segunda dimensão da primeira array (6) tem que ser igual ao número de elementos da primeira dimensão da segunda array. Como o método
`reshape` precisa receber uma tupla com o número de elementos de cada dimensão, o primeiro elemento deve ser 6, e por consequência o segundo
deve ser `n`/6. Para a conta fechar, `n` tem que ser múltiplo de 6.

## Questão 3
- [X] Dicionário (`dict`)
- [X] Lista (`list`)
- [ ] Conjunto (`set`)
- [X] Tupla (`tuple`)
- [X] Dicionário ordenado (`OrderedDict`)
- [X] String (`str`)
- [ ] Dicionário com valor padrão (`defaultdict`)

Sobre a opção de dicionários: Antes da versão 3.6, não havia nenhuma garantia de que os dicionários deveriam ser ordenados. Na versão 3.6, uma 
otimização para eles foi feita, e um efeito colateral foi eles serem ordenados, mas ainda assim isso não era estritamente uma regra da linguagem.
Na versão 3.7, essa característica foi incorporada na linguagem, e a paritr daí havia garantia de que os dicionários seriam ordenados, o que fez
o objeto `OrderedDict` se tornar mais redundante, já que agora o seu único diferencial são poucos métodos para mudar a ordenação. Logo, é possível
marcar como ordenado, já que nas versões mais recentes essa característica é garantida. Ainda assim, não marcar não é totalmente errado. 

Se por um acaso uma questão dessa cair na prova, provavelmente será possível negociar (e por via das dúvidas, é legal considerar que é ordenado, tendo em
vista as versões mais recentes.)

## Questão 4
```python
def gera_funcao_polinomial(lista_coeficientes):
    
    def func_polinomio(x):
        resultado = 0
        for index, elemento in enumerate(lista_coeficientes):
            resultado += elemento * (x**(index))
        return resultado

    return func_polinomio
```

## Questão 5
```python
def gera_matriz(n):
    matriz_3_eixos = [[[(i**(j - k)) + 3 for k in range(n * 3)] for j in range(n//2)] for i in range(n)]
    return matriz_3_eixos
```

## Questão 6
Resposta: item b)

Implementação:
```python
def bagunca_lista(k, lista):
    for i in range(k):
        for j in range(0, len(lista), 2):
            lista[j] *= (i + 1)
        for j in range(1, len(lista), 2):
            lista[j] -= lista[j - 1]
        for j in range(1, len(lista)):
            a = lista[j]
            b = lista[j-1]
            lista[j-1] = a + b
            lista[j] = abs(a - b)
    return lista
```

## Questão 7
Resposta: item a)
