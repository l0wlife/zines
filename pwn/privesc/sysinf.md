<img width="30%" src="https://i.imgur.com/CGV9DU1.png"></img>

# sys info gathering
Antes de começar um privesc, você precisa de informações do sistema que está explorando. Abaixo, algumas formas de colher essas informações.
> *Lembrando, que nessas zines falaremos sobre Linux Privilege Escalation.*<br>

* `$ uname -srvin` ~ os info<br>
* `$ env` ~ Cheque as variáveis de ambiente, veja se há algum conteúdo interessante<br>
* `$ uname -r` ~ verifique se existe algum exploit público para o kernel do sistema<br><br>

### Extraindo kernel's vulneráveis
* `$ curl https://raw.githubusercontent.com/lucyoa/kernel-exploits/master/README.md 2>/dev/null | grep "Kernels: " | cut -d ":" -f 2 | cut -d "<" -f 1 | tr -d "," | tr ' ' '\n' | grep -v "^\d\.\d$" | sort -u -r | tr '\n' ' '`<br><br>
<img src="https://i.imgur.com/yI1BXjF.png"></img><br><br>
