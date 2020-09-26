<img width="30%" src="https://i.imgur.com/ULwPfn3.png"></img>

# cowroot
Com certeza o cowroot é um dos exploits local-root mais conhecidos, ele explora uma falha do linux, na qual falaremos mais pra frente.

### Copy on Write
Antes de começar a falar da exploração, é interessante introduzir esse conceito<br>
Copy on write é uma cópia de uma região de memória para outra região de memória em execução. Para facilitar, imaginem da seguinte forma:
<br><br>

> *Obs: Para ficar claro o conceito de overwrite usado posteriormente, re-veja as zines de buffer overflow, é o mesmo conceito*
<br>

| REGIÃO DE MEMÓRIA A | <- Região de memória em execução<br>
| REGIÃO DE MEMÓRIA B | <br>
<br>
Imagine que todo conteúdo da região de memória B, fosse copiado para a região de memória A, causando um overwrite e executando o conteúdo da região de memória B<br><br>

### escalando privilégio
Dado o conceito de Copy on Write, vamos introduzir a falha que o cowroot explora. Essa falha, permite que a região de memória B, seja Writeable, ou seja, um usuário comum pode escrever nessa região de memória.
Dado isso, o cowroot faz o overwrite dessa região de memória com um payload do metasploit. Veja o payload usado:<br><br>

<img src="https://i.imgur.com/eOJje0V.png"></img><br><br>

Esse payload apenas spawna uma shell uid=0(root), é um [shellcode](../shellcode.md), que foi anteriormente explicado<br>
[demonstração cowroot](https://youtu.be/YoeuGnF_2Qk) by RE AK (Linux Dirty C0W Exploit tutorial (privilege escalation attack root))<br><br>

[pwn](../README.md)<br>
[home](../../README.md)<br><br>
