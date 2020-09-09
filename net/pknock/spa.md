<img width="30%" src="https://i.imgur.com/CGV9DU1.png"></img>

# Single Packet Authrozation
Sigle Packet Authrozation é uma outra forma de realizar um port-knocking, e é normalmente a forma utilizada para os rootkits<br><br>

Em SPA, basicamente, o knock é feito por apenas um packet, assim que esse packet for autenticado, uma determinada porta será aberta...<br><br>
Uma forma bastante conhecida de realizar essa técnica é com `fwknop`, vamos falar sobre o fwknop no próximo módulo, mas basicamente, o fwknop recebe esse packet, autentica e abre uma pré-determinada porta...<br><br>
