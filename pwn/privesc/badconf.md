<img width="30%" src="https://i.imgur.com/ULwPfn3.png"></img>

# bad permissions config
Para introduzir nesse tema, é necessário que você conheça o sistema de permissões do linux, veja [esse link](https://www.alura.com.br/artigos/entendendo-as-permissoes-no-linux) antes de começar essa zine<br><br>

### bad cron
Uma forma muito conhecida de efetuar um privilege escalation é usando o cron. O cron é um serviço que programa a execução de algum script/programa.<br>
Para explorar esse serviço, verifique as permissões do crontab.<br><br>

`ls -hal /etc/crontab`<br>
Caso o resultado seja algo como:<br>
`-rw-rw-rw- root root 722 Nov 16  2017 /etc/crontab`<br><br>

Não perca a oportunidade de rootar esse sistema, isso significa que outros qualquer usuário, idenpendente do uid/gid pode ler e escrever nesse arquivo.<br>
Basta escrever um .sh executando `/bin/bash` em algum diretório com permissões de escrita e configurar o cron para que ele execute esse .sh<br><br>

> *Esse foi só um exemplo de uma permissão mal configurada, existem outras formas de explorar essas má configurações*

[pwn](../README.md)<br>
[home](../../README.md)
