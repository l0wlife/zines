<img width="30%" src="https://i.imgur.com/CGV9DU1.png"></img>

# aslr
ASLR (Address System Layout Randomization), é uma proteção do sistema que randomiza os endereços da stack/libc<br><br>
[demo bypass nx and aslr i386](https://youtu.be/6Eegz3b6PTU) ~ Assista esse vídeo que eu gravei a um tempo atrás<br><br>

## bypass aslr 32 bits
No vídeo, eu explorava um binário de 32 bits com a proteção NX habilitada, e por conta do ASLR, não era possível fazer um ret2libc convencional<br>
Porém, o aslr de 32 bits, tem um range limitado de randomização, então tudo que precisamos fazer é um bruteforce, até que o endereço da system seja alinhado...<br><br>

[pwn](../README.md)<br>
[home](../../README.md)
