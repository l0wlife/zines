<img width="30%" src="https://i.imgur.com/ULwPfn3.png"></img>

# Stack
Nesse tópico, tente entender o que é e como funciona a Stack, lembrando que é importante que você estude por fora...<br>

### O que é
A Stack nada mais é que uma pilha de dados, uma estrutura que contem endereços de memória próprios, cada endereço da stack contém um endereço de instrução. A stack é do tipo LIFO (Last In First Out), ou seja, o primeiro endereço da stack, é o primeiro a ser executado...<br>

### Como funciona
A Arquitetura é composta por alguns registradores, `ax`, `bx`, `cx`, `dx`, `ip`, `bp` e `sp`. Sendo o registrador `ip` responsável por apontar a instrução em execução (instruction pointer), `bp` responsável pela instrução na base da stack e `sp` responsável pela instrução no topo da stack (stack pointer), o endereço que aponta pra instrução no topo da stack é conhecido como `endereço de retorno`, porque ele vai retornar pro registrador `ip`.
<br><br>
[pwn](../README.md)<br>
[home](../../README.md)
