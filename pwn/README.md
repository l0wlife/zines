<img width="30%" src="https://i.imgur.com/ULwPfn3.png"></img>

## Introdução
Pra você que ainda não entende muito sobre exploitation e afins, vamos a uma breve introdução... É essencial que você estude por fora para poder seguir o resto do conteúdo<br>

### Stack e Stack Frame
* [Stack](intro/stack.md) ~ Introdução a stack<br>
* [Stack Frame](intro/stackf.md) ~ Entendendo o Stack Frame

### GDB (Gnu Debugger)
* [gdb](dbg/gdb.md) ~ Conhecendo o gdb<br>

### Buffer Overflow
* [bof](bof/bof.md) ~ Primeiro buffer overflow<br>
* [depbof](bof/depbof.md) ~ Exploração depurada com gdb<br>
* [insidebof](bof/insidebof.md) ~ Controlando endereço de retorno<br>
* [shellcode](shellcode.md) ~ Entendendo o que é um shellcode<br>
* [environment overwrite](bof/env.md) ~ Exploração por meio de variáveis de ambiente, e execução de shellcode<br>
* [nx-bit bypass](bof/nx.md) ~ Bypass da Proteção NX-Bit<br>
* [aslr-32bits](bof/aslr32.md) ~ Bypass de NX + ASLR 32 bits<br>
* [pwntools](bof/pwnt.md) ~ Library pwntools - Escrevendo simples exploit<br>
* [remote bof](bof/rbof.md) ~ Remote Buffer Overflow - brainpan (windows x86)<br>

### PrivEsc
* [sys info](privesc/sysinf.md) ~ operational system information gathering<br>
* [bad permissions config](privesc/badconf.md) ~ Explorando permissões mal configuradas<br>
* [cowroot](privesc/cowroot.md) ~ Explicando cowroot<br>

### Rootkit
* [hook](rk/hook.md) ~ demonstração de um hooking na driver list<br>
* [hook2](rk/hook2.md) ~ demonstração de um hooking na port list<br>
* [port-knocking](../net/pknock/pkn.md) ~ Port-Knocking para rootkits<br>
* [single packet authorization](../net/pknock/spa.md) ~ Port-Knocking Single Packet Authorization<br>
* [fwknop](../net/pknock/fwknop.md) ~ FireWall KNock OPerator para SPA<br>

### Bootkit
* [bios](bios.md) ~ BIOS<br>
* [bootloader](bk/bld.md) ~ o que é um bootloader<br>
* [bootkit-1](bk/bk1.md) ~ Introdução a bootkit<br>
* [bootkit-2](bk/bk2.md) ~ hooks do gapz-bootkit<br>
* [bootkit-3](bk/bk3.md) ~ Payload injection<br><br>

### Others
* [bring in own driver](biodll.md) ~ Técnica bring in own driver<br>
* [mimikatz password dump](mkpdump.md) ~ password windows dump com mimikatz
