<img width="30%" src="https://i.imgur.com/ULwPfn3.png"></img>

# gnu debugger
Vamos começar debuggando um hello world...<br><br>

### Source
<b>c.c:</b><br><br>
<img src="https://i.imgur.com/1TpBTUX.png" width="60%"></img><br><br>
 O gdb oferece um disassembler, uma feature para passar o binário para em instruções assembly, facilitando assim o entendimento do programa e oferece também algumas outras features para análise...<br><br>

### Primeiros passos
`gdb -q c` ~ Para iniciar o debugger<br>
`info functions` ~ Lista as funções usadas<br>
`disas (function)` ~ Para usar o disassembler<br>
<br>
Veja o dump:<br><br>
<img src="https://i.imgur.com/nUzTT2D.png" width="60%"></img><br><br>
Observe a montagem do stack frame `push` coloca um valor na stack, `mov %rsp,%rbp` move essa valor para `rsp` e `mov $0x, %edi`, move um valor para o registrador `edi`. Logo após isso, temos uma `call` para `0x2013a0 <puts@plt>`, que seria o endereço da função puts, responsável por fazer um print.<br><br>
Após isso, observe que as seguintes instruções são responsáveis por desmontar o stack frame
<br><br>
[pwn](../README.md)<br>
[home](../../README.md)
