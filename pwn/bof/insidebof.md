<img width="30%" src="https://i.imgur.com/CGV9DU1.png"></img>

# bof
Vamos usar os challs do `picoCTF 2018` para entender como funciona de fato uma exploração de buffer overflow<br>
Ambiente: `/problems/buffer-overflow-1_0_787812af44ed1f8151c893455eb1a613/vuln`<br><br>

<img src="https://i.imgur.com/ZNJoAdz.png" width="60%"><br><br>

Fazendo um simples teste de floodar o buffer, podemos ver que, ele da um erro de `segmentation fault`, que vamos entender mais pra frente, e aparece uma mensagem `Jumping to 0x61616161`<br>
Dando um `info functions`, você vai notar a function "vuln", vamos disassemblar ela...<br><br>

<img src="https://i.imgur.com/2BREr9i.png" width="60%"><br><br>

Coloque um breakpoint na instrução "ret", pois essa é a instrução responsável por retornar a função main, assim que a execução terminar<br>`gdb-peda$ b * 0x0804865c`<br><br>

Vamos enviar um pattern de 100 bytes, e observe a stack...<br><br>

<img src="https://i.imgur.com/QVFPHmH.png" width="60%"><br><br>

Note que, a stack está toda sobrescrita pelo nosso pattern, e como vocês devem lembrar, os endereços da stack armazenam os endereços de instrução, que seria executados...<br>
Por isso assim que damos sequência ao programa, ele retorna erro de `segmentation fault`, execute o comando `s`, para passar para a próxima etapa...<br><br>

<img src="https://i.imgur.com/oCXDdb3.png" width="60%"><br><br>

É muito importante que você perceba uma coisa, os primeiros 4 bytes que estavam no topo da stack (AFAA), o que seria o endereço de retorno, foi enviando para o registrador `eip`, que como foi explicado anteriormente, é o registrador que aponta para a próxima instrução a ser executada...<br>
Agora vamos usar a feature `pattern offset` no valor em EIP, para descobrirmos o offset do endereço de retorno, e assim controlarmos o EIP<br><br>

<img src="https://i.imgur.com/10YpKIL.png" width="60%"><br><br>

E aí está, o offset do `EIP`...<br>
Se você der um `info functions`, vai encontrar uma função chamada `win`, se você disassemblar ela, vai perceber que ela abre um arquivo, printa o conteúdo e finaliza a execução<br>
Vamos enviar essa função pro EIP, sobrescrevendo o endereço de retorno, ai quando a instrução `ret` for executada, em vez de retornar para a função `main`, retornará para a função `win`<br><br>

<img src="https://i.imgur.com/pyJ7438.png" width="60%"><br><br>

Formate o endereço da win em little-endian (do menos significante ao mais significante) ficando assim `\xcb\x85\x04\x08`<br>
Ok, payload montado `perl -e 'print "a"x44 . "\xcb\x85\x04\x08"' | ./vuln`<br><br>

<img src="https://i.imgur.com/DSqcNrz.png" width="60%"><br><br>

## Resumo
O endereço de retorno, é sempre aquele que fica no topo da stack, ele será enviado para o registrador `ip` que aponta para a seguinte instrução, o que nós fizemos, foi explorar uma vulnerabilidade de buffer overflow, para que pudessmos sobrescrever esse endereço com o endereço da function `win`.<br><br>

[pwn](README.md)
[home](../README.md)
