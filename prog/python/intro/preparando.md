<img width="30%" src="https://i.imgur.com/VATToY0.png">

Você pode baixar o Python no próprio [site do projeto](https://www.python.org/downloads/). Em caso de você ser usuário Linux ou MacOS (duas distros Unix-based), muito provavelmente o Python já vai vir instalado. 
Para checar a versão, abra o seu terminal e digite `python3 -v`, se a saída tiver algo relacionado a "Python 3.7.x", você já tem a versão configurada. Também tente verificar digitando `python3.7 -v`.
Se nenhum dos dois funcionou, recomendo que você atualize para a versão utilizada aqui (Python v3.7).

Para instalar o Python3.7, comece atualizando a sua lista de pacotes<br>
`$ sudo apt update`<br>
Após isso:<br>
`$ sudo apt install software-properties-common`
Adicione essa ppa ao seu sistema:<br>
`$ sudo add-apt-repository ppa:deadsnakes/ppa`<br>
Quando for questionado se deseja continuar, aperte ENTER<br>
`$ Press [ENTER] to continue or Ctrl-c to cancel adding it.`<br>
Por fim, atualize mais uma vez sua lista de pacotes:<br>
`$ sudo apt update`<br>
Agora você pode finalmente instalar o Python3.7:<br>
`$ sudo apt install python3.7`<br>
<br>
Teste com o seguinte comando:<br>
`$ python3.7 --version`<br>
Você deverá receber de volta:<br>
`Python 3.7.9`
<br>

[Fonte](https://linuxize.com/post/how-to-install-python-3-7-on-ubuntu-18-04/)<br>
Caso receba isso, você oficialmente tem o Python instalado, e agora pode seguir o resto das zines sem problemas.

Para usuários do Windows, apenas baixe o arquivo executável. E lembre-se de ativar a opção de PATH e a instalação do pip — gerenciador de pacotes do Python.


