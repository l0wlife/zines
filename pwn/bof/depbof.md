<img width="30%" src="https://i.imgur.com/CGV9DU1.png"></img>

# depurando um bof
Vamos começar falando sobre a exploração depurada de buffer overflow, usaremos o mesmo ambiente de antes, o `narnia0`.<br>
Então conecte-se ao narnia `ssh narnia0@narnia.labs.overthewire.org -p2226` Senha `narnia0`<br><br>

Basicamente o que vai ser falado aqui é como o debugger auxilia na exploração de bof, para isso, vamos usar o `gdb`.<br>
Felizmente, o narnia oferece a opção de usar o `gdb-peda`, assim que entrar no debugger, insira o comando `source /usr/local/peda/peda.py`<br><br>

<img width="60%" src="https://i.imgur.com/DXhN7Bw.png"></img><br><br>

O peda é uma extensão do gdb, que nos permite usar algumas features que vão auxiliar na exploração.<br><br>

Algumas features que podem ser interessantes:<br>
* **checksec** (verifica quais proteções estão habilitadas)
* **pattern create** (gera um padding com quantos bytes você definir)
* **pattern offset** (verifica qual o offset do pattern gerado. Obs.: Entenderão melhor mais pra frente)
* **colored register/stack** (exibe os registradores e a stack colorida, para podermos identificar melhor algumas coisas)

## Exploração depurada

<img src="https://i.imgur.com/AdCWUrb.png" width="60%"></img><br><br>

Comecei gerando um pattern de 100 bytes, e executei o narnia0 com esse pattern<br>
Logo após isso, peguei o valor de `val` e usei o pattern offset para pegar o offset<br><br>

<img src="https://i.imgur.com/3KRdR6v.png" width="60%"></img><br><br>
Viu como a exploração com um debugger é mais fácil?<br>
O resto da exploração vocês já conhessem, é a mesma de antes<br><br>

[home](../README.md)
