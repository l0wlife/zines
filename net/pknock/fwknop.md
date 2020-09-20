<img width="30%" src="https://i.imgur.com/ULwPfn3.png"></img>

# fwknop
O fwknop é um operador bastante utilizado quando se trata de `port-knocking SPA`, ele facilita bastante o processo<br>
O fwknop funciona como um daemon, tanto que nome do client é `fwknopd`<br><br>

Você pode configurar o fwknop em `/usr/local/etc/fwknop/access.conf`, lá você configura as keys, a porta que vai ser aberta, e o username<br><br>

## fwknop server-side
Com o fwknop configurado, basta startar ele com `sudo fwknopd -f -vv`<br>
Agora, que o fwknop já foi configurado no server, vamos a parte do client<br><br>

## fwknop client-side
Agora, no client-side com o fwknop ativo, basta enviar o packet e se conectar a porta<br>
Envie o packet com `fwknop -D (ip server) -s -A tcp/(porta)`, em seguida, será requisitada a key, previamente configurada no server<br>
Assim que a key for autenticada, você pode se conectar a porta sem problemas<br><br>

## Resources
[fwknop](https://youtu.be/QVpgDCsqr0U) ~ Single Packet Authorization using fwknop by Security Generation<br>
[fwknop2](https://xnwm0.github.io/pdfs/spa_fwknop.pdf) ~ Como um rootkit mantem acesso ao servidor? by kosu<br><br>

[net](../README.md)<br>
[home](../../README.md)
