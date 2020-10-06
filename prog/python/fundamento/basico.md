# Começando com expressões no shell interativo

É importante que você se acostume a usar o shell interativo, pois enquanto você absorve o conteúdo é de extrema importância testar tudo o que você consome.
Começaremos com algumas expressões matemáticas no shell:
```
>>> 2 + 2
4
>>>
```
Acima nós temos uma expressão simples. No Python — e similarmente em outras linguagens — `2 + 2` é uma *expressão*; e uma expressão é formada de valores (como o 2) e operadores (como o +), e como toda expressão, eles evaluam (reduzem) até um valor.
No exemplo citado, `2 + 2` evaluam até um único valor, o 4. No Python um único valor *também* é uma *expressão*. Com a única diferença é que ele se reduz a si mesmo.
```
>>> 2
2
```

| Operador | Operação        | Exemplo | Se evalua á |
| -------- | --------------- | ------- | ----------- |
|    **    | Exponenciação   | 2 ** 3  | 8           |
|    %     | Módulo/Restante | 22 % 8  | 6           |
|    //    | Divisão inteira | 22 // 8 | 2           |
|    /     | Divisão         | 22 / 8  | 2.75        |
|    *     | Multiplicação   | 3 * 5   | 15          |
|    -     | Subtração       | 5 - 2   | 3           |
|    +     | Adição          | 2 + 2   | 4           |

A precedência dos operadores no Python obedecem a matemática. Isso é o `**` é o primeiro; depois o `%`, `//`, `/`, `*` (nessa mesma ordem).
Com os parenteses você pode editar a precedência, assim como em uma expressão matemática comum.
Como é demonstrado nesse teste no shell interativo.
```
>>> 2 + 3 * 6
20
>>> (2 + 3) * 6
30
>>> 48565878 * 578453
28093077826734
>>> 2 ** 8
256
>>> 23 / 7
3.2857142857142856
>>> 23 // 7
3
>>> 23 % 7
2
>>> 2      +           2
4
>>> (5 - 1) * ((7 + 1) / (3 - 1))
16.0
```
<img src="https://automatetheboringstuff.com/2e/images/000066.jpg">

Essas regras de ordem são importantes, pois, o Python — uma linguagem de programação — assim como uma linguagem qualquer tem suas regras de gramática, e desrespeitar essas regras resulta no que é chamado de um *SyntaxError*.<br>
Como visto a seguir:
```
>>> 5 +
  File "<stdin>", line 1
    5 +
      ^
SyntaxError: invalid syntax
>>> 42 + 5 + * 2
  File "<stdin>", line 1
    42 + 5 + * 2
             ^
SyntaxError: invalid syntax
```
É bom já ir se acostumando com o nome dos erros, pois é com esses nomes que você vai identificar mais rapidamente o que o erro no seu programa se trata.


# Os data-tipos: Inteiro, Float e String.


Sempre se lembre que uma *expressão* é apenas **valores combinados com operadores** que sempre **se reduzem a um único valor**. "Data-tipo" é uma categoria para valores, e todo valor pertence a um data-tipo. Os valores mais comuns no Python estão listados na tabela abaixo. Os valores `-2` e `30`, por exemplo, são valores do data-tipo *inteiro*. O data-tipo inteiro (ou *int*) indica valores que são números inteiros. Números com casas decimais — como por exemplo, 3.14 — são conhecidos como *números flutuantes* (*números de ponto flutuante*) ou, simplesmente, *floats*. É importante você saber que, mesmo que o valor `42` seja um *inteiro*, o valor `42.0` já seria considerado um *float* — note o ponto (.), similarmente como nós consideramos com a virgula (42,0), a partir daquele ponto, é uma casa decimal.

| Data-tipo | Exemplos                               |
| --------- | -------------------------------------- |
| Inteiros  | -2, -1, 0, 1, 2, 3, 4, 5               |
| Floats    | -1.25, -1.0, -0.5, 0.0, 0.5, 1.0, 1.25 |
| Strings   | 'a', 'aa', 'aaa', 'Hello!', '11 cats'  |

É muito comum nos programas termos valores de texto, que chamamos de *strings*, ou *strs*. Strings são indicadas por serem rodeadas por aspas simples (') ou aspas duplas ("). Entraremos em detalhes com strings em zines futuras. Por agora, esses exemplos devem ser o suficiente para entender a natureza básica:
```
>>> "O voto feminino foi um erro"
'O voto feminino foi um erro'
>>> 'Hitler não fez nada de errado'
'Hitler não fez nada de errado'
>>> 'Stalin tinha mais de 1,62 de altura.
  File "<stdin>", line 1
    'Stalin tinha mais de 1,62 de altura.
                                        ^
SyntaxError: EOL while scanning string literal
```
Como foi demonstrado, as strings funcionam tanto com aspas simples como com aspas duplas. Porém é necessário que as mesmas sejam fechadas ao fim da string, dessa forma o interpretador entende onde ela acaba. Caso essa necessidade não seja satisfeita, temos um erro. Nesse caso mais um `SyntaxError`, por ser um erro na *expressão* que forma a string. De forma semelhante com o nosso caso anterior.

# Concatenação e replicação de strings

O significado de um operador pode mudar baseado no data-tipo do valor em que ele é aplicado. Por exemplo, o `+` é um operador que soma dois ou mais inteiros ou floats. Porém, quando o `+` é usado com duas — ou mais — strings, o resultado é a junção dos dois textos, processo conhecido como *concatenação*.
```
>>> 'Alice' + 'Bob'
'AliceBob'
```
Como já é do conceito, a expressão de strings é reduzida a apenas um valor. Porém, se você tentar fazer o mesmo com uma string e um inteiro — ou um float —, um erro será gerado, pois são de data-tipos diferentes.
```
>>> 'Alice' + 42
Traceback (most recent call last):
  File "<pyshell#0>", line 1, in <module>
    'Alice' + 42
TypeError: can only concatenate str (not "int") to str
```
É gerado um `TypeError`, pela incompatibilidade nos tipos. Como já foi citado anteriomente, com *inteiros* o `+` é usado para somas, e com `strings`, para concatenação. Se os dois forem usados ao mesmo tempo, ocorre uma confusão no interpretador, e um erro de *tipos* é gerado.
Porém, é possível converter os valores antes da expressão ser evaluada. Futuramente ainda nessa zine aprenderemos a como fazer isso.<br>
O operador `*` se usado em inteiros e/ou floats, gera um valor multiplicado, se usado em uma string e um valor inteiro é conhecido como *replicação*.<br>
Por exemplo:
```
>>> 'Alice' * 5
'AliceAliceAliceAliceAlice'
>>> 'Zoi de Gato ' * 7
'Zoi de Gato Zoi de Gato Zoi de Gato Zoi de Gato Zoi de Gato Zoi de Gato Zoi de Gato '
```
A expressão é reduzida a um único valor, que se repete o mesmo número de vezes que o inteiro usado na operação.

O operador `*` pode ser usado apenas com dois valores númericos (multiplicação), ou um valor de string e um valor inteiro (replicação).
Caso contrário, você irá receber uma mensagem de erro — muito provavelmente de tipo —. Como demonstrado:
```
>>> 'Alice' * 'Bob'
Traceback (most recent call last):
  File "<pyshell#32>", line 1, in <module>
    'Alice' * 'Bob'
TypeError: can't multiply sequence by non-int of type 'str'
>>> 'Alice' * 5.0
Traceback (most recent call last):
  File "<pyshell#33>", line 1, in <module>
    'Alice' * 5.0
TypeError: can't multiply sequence by non-int of type 'float'
```
É normal que o intepretador não entenda essas operações. Você não pode multiplicar duas palavras, e é extremamente complexo multiplicar um texto por um número fracionário de vezes.
