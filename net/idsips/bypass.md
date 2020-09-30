<img width="30%" src="https://i.imgur.com/ULwPfn3.png"></img>

# bypass IDS
Bypass de IDS tem algumas formas de fazer. Não vamos abordar aqui todas elas, até porque são diversas.<br><br>

### bypass NIDS/NIPS
Vamos montar um cenário para essa explicação. Imagine que você esteja tentando pivotar a intranet, porém em qualquer tentativa de injetar um payload, esse NIDS/NIPS alertaria/pararia o seu payload, e aí sua ownada seria comprometida ;(<br><br>
Felizmente, tem uma forma bem simples de evitar esse cenário, ao comprometer um dos servidores, basta enumerar os servidores da intranet, como visto na zine [pivoting](../pivot/pivoting.md).<br><br> Ao enumarar os servidores, você pode fazer um dos (denial of service) nesse servidor. Enquanto esse servidor estiver inativo, você pode injetar seu payload sem o NIDS/NIPS alertar/parar sua penetração 8=D ~~
