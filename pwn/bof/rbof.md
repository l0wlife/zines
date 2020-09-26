<img width="30%" src="https://i.imgur.com/ULwPfn3.png"></img>

# brainpan
o brainpan é um challenge muito interessante, espero que lendo isso vocês entendam como funciona uma exploração de buffer overflow.<br><br>

## ambiente
Vamos dar uma olhada no ambiente que vamos trabalhar<br>
> *Vou usar o Immunity Debugger para debuggar a aplicação*<br>

<img src="https://i.imgur.com/0xUj5fZ.png" src="40%"></img><br><br>

Veja que a aplicação está bindando a porta 9999 (esperando conexão), veja o que acontece quando interagimos com a aplicação.<br><br>

<img src="https://i.imgur.com/kX5S8Pl.png"></img><br><br>
<img src="https://i.imgur.com/yIoOIzc.png"></img><br><br>
*salve pro meu amigao bky hehe*<br><br>

## overflow + controle EIP
Ok, sabendo que a aplicação copia todos os bytes para um buffer, vamos tentar um overflow, enviando um pattern com uma grande quantidade de bytes.<br><br>

<img src="https://i.imgur.com/NGFi6SX.png"></img>
<br>
<img src="https://i.imgur.com/owFlK1j.png"></img><br><br>

Ocorreu um "Access Violation" que seria o equivalente ao "Segmentation Fault". Vamos pegar o valor em EIP e usar o pattern_offset para descobrir o offset do EIP.<br><br>

<img src="https://i.imgur.com/hFju72g.png"></img><br></br><br>
*perl -e 'print "a"x524 . "kosu"' | ncat 192.168.15.14 9999*<br><br>
<img src="https://i.imgur.com/iAudx9a.png"></img><br><br>
0x75736f6b = usok ("kosu" em little-endian)<br><br>

## find JMP ESP + gen shellcode
Agora que controlamos o EIP, vamos fazer com que EIP aponte para uma instrução que aponte para ESP. Após isso, vamos gerar um shellcode com o msfvenom.

### Find JMP ESP
Para encontrar essa instrução, podemos procurar em qualquer binário/driver que a aplicação chame.<br>

Essa é a lista de drivers que a aplicação utiliza<br><br>
<img src="https://i.imgur.com/v9EBOKd.png"></img><br><br>

Vamos procurar nesses drivers, a instrução que a gente precisa.<br><br>
<img src="https://i.imgur.com/JM8ufJs.png"></img><br><br>

No meu caso, em "kernelbase.dll", consegui encontrar a instrução que precisava. Setei um breakpoint nela, vamos escrever uma poc e enviar para ver se está tudo certo<br><br>

<img src="https://i.imgur.com/p7IiJ56.png"></img><br>
<img src="https://i.imgur.com/NGwyS0d.png"></img><br><br>

Atingido o breakpoint, isso significa que a nossa instrução "JMP ESP" chegou em EIP, Portanto vai ser executada. 

### gen shellcode
Algumas aplicações rejeitam certos bytes, esses bytes são chamados de bad characters, quando a aplicação encontra esses bytes ela crasha, tudo que você tem que fazer é executar uma poc diversas vezes até localizar esses bytes. Não tem nada demais, então resolvi adiantar essa parte<br>
Bad chars: 0x00 0x0a 0x0d<br><br>
<img src="https://i.imgur.com/MWFBPLe.png"></img><br>

## build exploit
Essa parte é simples, basta conduzir um socket ao servidor e enviar o payload.<br>
Veja o [source-code](https://github.com/wtfflya/brainpan/blob/master/brainpan.py) do exploit.<br><br>

<img src="https://i.imgur.com/Wgr2LoY.png"></img><br><br>
<img src="https://i.imgur.com/504bTP3.png"></img><br><br>

## fim
Aqui finalizamos a parte de buffer overflow, espero que tenham entendido como funciona essa falha e a exploração dela.<br><br>

[pwn](../README.md)<br>
[home](../../README.md)
