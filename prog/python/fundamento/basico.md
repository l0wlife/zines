# Começando com expressões no shell interativo

É importante que você se acostume a usar o shell interativo, pois enquanto você absorve o conteúdo é de extrema importância testar tudo o que você consome.
Começaremos com algumas expressões matemáticas no shell:
```
>>> 2 + 2
4
>>>
```
Acima nós temos uma expressão simples. No Python — e similarmente em outras linguagens — 2 + 2 é uma *expressão*; e uma expressão é formada de valores (como o 2) e operadores (como o +), e como toda expressão, eles evaluam (reduzem) até um valor.
No exemplo citado, 2 + 2 evaluam até um único valor, o 4. No Python um único valor *também* é uma *expressão*. Com a única diferença é que ele se reduz a si mesmo.
```
>>> 2
2
```
No python existem outros diversos operadores que você pode usar, alguns deles são esses:

| Operador | Operação        | Exemplo | Se evalua á |
| -------- | --------------- | ------- | ----------- |
|    **    | Exponenciação   | 2 ** 3  | 8           |
|    %     | Modulo/Restante | 22 % 8  | 6           |
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

Essas regras de ordens são importantes, pois, o Python — uma linguagem de programação — assim como uma linguagem qualquer tem suas regras de gramática. E desrespeitar essas regras resulta no que é chamado de um *SyntaxError*.
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
