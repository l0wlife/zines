<img width="30%" src="https://i.imgur.com/CGV9DU1.png"></img>

# Pivoting
Pivoting é uma forma de navegar pelos servidores da intranet, normalmente, quando se consegue acesso a um servidor, a ideia é passar para o servidor principal<br><br>

## Primeiros passos
Assim que você obtem acesso a um servidor, mesmo que não seja `root`, você pode começar o pivoting, eu vou usar uma zine que eu escrevi a um tempo sobre pivoting como referência, então me desculpe a má qualidade de algums imagens...<br><br>
Há um tempo atrás, eu peguei um acesso a `unir`, e fiz um redirecionamento de tráfego<br><br>

<img src="https://i.imgur.com/DdQwWo3.png"><br><br>

Repare que, eu spawnei uma shell comum, e dei o comando `route`, uma tabela que exibe o destino dos pacotes e ele exibe também em `destino` o endereço base da rede<br><br>

Usei o `autoroute` e passei o ip base da rede com um range pra intranet `run autoroute -s 10.0.104.0/24`<br><br>

## Tunelando o servidor
Agora que criamos uma route pra intranet, só precisamos fazer desse servidor um tunel pra intranet, pra isso, temos um modulo auxiliary do metasploit chamado `socks4a`<br>
De o comnado `run` no socks4a depois de ter criado a route, e o socks4a vai agir como um proxyserver, agora basta configurar esse `proxy` na sua máquina, pra isso, eu usei o proxychains...<br><br>

proxychains.conf:<br>
```
socks4  127.0.0.1 1080
```
<br>
> 1080 é a porta default do socks4a<br><br>

## Scan na intranet
Agora que configuramos o proxyserver no servidor que tinhamos acesso, vamos rodar um scan na intranet com o nmap<br>
`proxychains nmap -sV -sS -oN .unir.txt 10.0.104.0/24`<br><br>

O resultado foi esse: https://pastebin.com/raw/dg9mPNVC<br><br>

Eu não fui além disso, mas perceba que muitos dos services da intranet são iguais, principalmente os windows servers, o passo seguinte, seria procurar uma forma de explorar esses services e obter acesso aos servers da intranet<br><br>

[net](../README.md)<br>
[home](../../README.md)
