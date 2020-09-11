<img width="30%" src="https://i.imgur.com/CGV9DU1.png"></img>

## Introdução
Pra você que ainda não entende muito sobre exploitation e afins, vamos a uma breve introdução... É essencial que você estude por fora para poder seguir o resto do conteúdo<br>

### Stack e Stack Frame
[Stack](intro/stack.md) ~ Introdução a stack<br>
[Stack Frame](intro/stackf.md) ~ Entendendo o Stack Frame

### GDB (Gnu Debugger)
[gdb](dbg/gdb.md) ~ Conhecendo o gdb<br>

### Buffer Overflow
[bof](bof/bof.md) ~ Primeiro buffer overflow<br>
[depbof](bof/depbof.md) ~ Exploração depurada com gdb<br>
[insidebof](bof/insidebof.md) ~ Controlando endereço de retorno<br>
[shellcode](shellcode.md) ~ Entendendo o que é um shellcode<br>
[environment overwrite](bof/env.md) ~ Exploração por meio de variáveis de ambiente, e execução de shellcode<br><br>

[nx-bit bypass](bof/nx.md) ~ Bypass da Proteção NX-Bit<br>
[aslr-32bits](bof/aslr32.md) ~ Bypass de NX + ASLR 32 bits<br><br>

[pwntools](bof/pwnt.md) ~ Library pwntools - Escrevendo simples exploit<br>

### Rootkit
[hook](rk/hook.md) ~ demonstração de um hooking na driver list<br>
[hook2](rk/hook2.md) ~ demonstração de um hooking na port list<br>
[port-knocking](../net/pknock/pkn.md) ~ Port-Knocking para rootkits<br>
[single packet authorization](../net/pknock/spa.md) ~ Port-Knocking Single Packet Authorization<br>
[fwknop](../net/pknock/fwknop.md) ~ FireWall KNock OPerator para SPA<br>

### Bootkit
[bootloader](bk/bld.md) ~ o que é um bootloader<br>
