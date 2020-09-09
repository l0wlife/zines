<img width="30%" src="https://i.imgur.com/CGV9DU1.png"></img>

# Port Knocking
É uma forma de abrir uma determinada porta pra qualquer conexão externa, porém essa porta só é aberta se for enviado um packet em uma coleção de portas pré-determinadas<br><br>
Normalmente, é usado para SSH, telnet, entre outros serviços como esses...<br><br>

Essa configuração pode ser feita em um daemon chamado `knockd`, veja como ela é feita<br><br>

/etc/knockd.conf:<br>
```
[options]
logfile = /var/log/knockd.log
[openSSH]
sequence = 7000,8000,9000
seq_timeout = 5
command = /sbin/iptables -I INPUT -s %IP% -p tcp --dport 22 -j ACCEPT
tcpflags = syn
[closeSSH]
sequence = 9000,8000,7000
seq_timeout = 5
command = /sbin/iptables -D INPUT -s %IP% -p tcp --dport 22 -j ACCEPT
tcpflags = syn
```
<br>
Essa configuração abre a porta 22 se houver um "knock" nessa sequência 7000,8000,9000<br>
Por outro lado, fecha a porta 22 se houver um "knock" nessa sequência 9000,8000,7000<br><br>

## Resources
[Artigo TCC Port-Knocking](https://www.ppgia.pucpr.br/~jamhour/RSS/TCCRSS11/Diego%20Pereira%20do%20Nascimento%20_%20ArtigoTCC.pdf)
