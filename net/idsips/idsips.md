<img width="30%" src="https://i.imgur.com/ULwPfn3.png"></img>

# IDS/IPS
As IDS/IPS, são servidores na rede que checam as signature do tráfego da rede, nesse processo, ele faz uma comparação com as signatures da ataques conhecidos. Se a comparação for verdadeira, um IDS faria um alerta, já um IPS, alerta e interrompe esse pacote. Ou seja, o IDS é um sistema pra monitorar a rede e o IPS é um sistema para previnir um ataque a rede.

## HIDS/NIDS/HIPS/NIPS
Existem diferentes tipos de IDS/IPS. Vamos ver quais são agora.<br>

### HIDS/HIPS
o HIDS/HIPS (Host-based IDS/IPS) é instalado em todos os servidores na rede e e capaz de analisar os logs do sistema. Além disso o HIDS pode analisar uso excessivo da memória e processos/conexões suspeitas.

### NIDS/NIPS
o NIDS/NIPS (Network-based IDS/IPS) faz o que eu havia dito, é um servidor separado para monitorar a rede inteira. É constituído por 2 componentes principais. Sendo eles os sensores e a estação de gerenciamento.<br>

* Sensores: São devices instalados para monitorar a rede.<br>
* Estação de Gerenciamento: Responsável por gerenciar todos os sensores da rede<br>

[net](../README.md)<br>
[home](../../README.md)
