<img width="30%" src="https://i.imgur.com/CGV9DU1.png"></img>

# bof
Vamos ao nosso primeiro bof<br>
Para começar, vamos fazer os challenges do `narnia`, e entendendo mais pra frente como funciona a exploração de buffer overflow<br><br>

## narnia
Conecte-se ao narnia `ssh narnia0@narnia.labs.overthewire.org -p2226`<br>Senha `narnia0`<br><br>
<img src="https://i.imgur.com/yXDlwHN.png" width="60%">
<br><br>
As challenges ficam em `/narnia`, começaremos com o `narnia0`<br>
Você vai reparar, que a source de cada challenge vai estar disponível pra você<br>
Observe o `narnia0.c`, e vamos tentar resolve-lo...<br><br>
<img src="https://i.imgur.com/owrRmxX.png" width="60%"><br><br>
Ao analisar a source, você vai perceber que, temos 2 buffers, um com o valor `0x41414141`, e outro buffer pra receber um input<br>
Você também vai notar que esse há uma comparação de `val (0x41414141)` com `0xdeadbeef`, se val for igual a `0xdeadbeef`, conseguimos uma shell com permissões...<br><br>

### buffer overflow
Ok... Mas o valor dentro de `val`, nunca vai ser `0xdeadbeef`... Né?!<br>
Bom... Tecnicamente sim! Mas se pudermos explorar buffer overflow, podemos alterar esse valor...<br><br>

Como isso funciona?<br>
Buffer overflow, é uma falha que permite com que a gente ultrapasse os limites de um buffer e começe a sobrescrever outras regiões da memória<br>
Sabendo isso, o que podemos fazer é, tentar sobrescrever a região que armazena o valor `0x41414141` para `0xdeadbeef`, e assim então, a comparação seria verdadeira<br>
e retornaria uma shell com permissões pra gente<br><br>

### explorando bof
Como dito antes, buffer overflow é a falha que permite com que ultrapasse os limites do buffer e sobrescreva outras regiões de memória...<br>
Para começar, vamos a um teste simples...<br><br>
<img src="https://i.imgur.com/rei37wL.png" width="60%"></img>
<br><br>
Ok, primeiro, conseguimos sobrescrever a região de memória que guardava o valor de `val`, sobrescrevemos com um `a` que passando pra hex fica `0x61`<br>
Por isso o val ficou com o valor `0x61616161`. Sabendo que conseguimos sobrescrever o val, só precisamos descobrir com quantos bytes chegamos na região de memória<br>
que armazena esse valor, o narnia facilita isso pra gente, se você observar bem, vai ver que tem um delimitador no scanf, com `%24s`, e printa esse valor delimitado<br><br>
<img src="https://i.imgur.com/mlKVM2m.png" width="60%"></img><br><br>
Sabemos que com 24 bytes, sobrescrevemos o valor de val, então precisamos subtrair `4` bytes, porque assim podemos preencher o restante com o valor que a gente quiser, no caso `deadbeef`.<br><br>
Dito isso, vamos enviar o payload `perl -e 'print "a"x20 . "bbbb"'`<br><br>
<img src="https://i.imgur.com/v8yo8Xq.png" width="60%"><br><br>
Veja que o val foi sobrescrito com os b's que nós enviamos, que passando pra hex fica `0x62`, agora só precisamos formatar o `deadbeef` acrescentar um `0x90` para sobrescrever o nullbyte<br>
e teremos a nossa shell...<br><br>
Enviando o payload `perl -e 'print "a"x20 . "\xef\xbe\xad\xde\x90"'`, veja o que acontece...<br><br>
<img src="https://i.imgur.com/1D7cDUW.png" width="60%"><br><br>

## resumo
Resumindo, quando a gente ultrapassou os limites que o buffer permitia, e começou a sobrescrever outras regiões de memória, descobrimos com quantos bytes sobrescreviamos o valor da variável `val`, e assim pudemos sobrescrever com o valor que nós quisessemos, e então sobrescrevemos com o valor que era comparado, e isso spawnou uma shell com permissões de `narnia1`...<br><br>
[home](../pwn.md)
