<img width="30%" src="https://i.imgur.com/CGV9DU1.png"></img>

# Environment Overwrite
O ambiente que vamos trabalhar é o `narnia`, novamente, e dessa vez, vamos fazer o desafio 1<br>
Conecte-se ao narnia `ssh narnia1@labs.overthewire.org -p2226` Senha `efeidiedae`<br><br>

## shellcode
Antes de começar a exploração, é importante que você separe um shellcode... `\x31\xc0\x50\x68\x2f\x2f\x73\x68\x68\x2f\x62\x69\x6e\x89\xe3\x50\x53\x89\xe1\x31\xd2\xb0\x0b\xcd\x80`<br>
Você pode usar esse shellcode<br><br>

## Exploração

<img src="https://i.imgur.com/j3nrpwb.png" width="60%"><br><br>

Ao tentar executar, você vai encontrar essa mensagem, isso acontece, porque tem uma função chamada `getenv` sendo chamada, você pode confirmar isso na source do narnia1.<br>
Como essa variável está vazia, o narnia1 retorna essa mensagem, porém se você exportar algum valor pra ela, veja o que acontece...<br><br>

<img src="https://i.imgur.com/oZaCVjF.png" width="60%"><br><br>

A mensagem retornada é `Trying to **EXECUTE** EGG!`<br>
Sabendo isso, basta exportar um shellcode para essa variável, e ele será executado<br><br>

<img src="https://i.imgur.com/PA5eSNq.png" width="60%"><br><br>
Feito!!<br><br>

## Resumo
Como é feita a execução de um valor tirado de uma variável de ambiente, criamos essa variável e atribuimos um shellcode a ela, esse shellcode spawna uma shell pra gente<br><br>

[pwn](../README.md)<br>
[home](../../README.md)
