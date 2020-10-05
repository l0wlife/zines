<p align="center"><img width="70%" src="https://i.imgur.com/VYGCgNc.png"></p>

Você pode baixar o Python no próprio [site do projeto](https://www.python.org/downloads/). Em caso de você ser usuário Linux ou MacOS (duas distros Unix-based), muito provavelmente o Python já vai vir instalado. 
Para checar a versão, abra o seu terminal e digite `python3 -v`, se a saída tiver algo relacionado a "Python 3.7.x", você já tem a versão configurada. Também tente verificar digitando `python3.7 -v`.
Se nenhum dos dois funcionou, recomendo que você atualize para a versão utilizada aqui (Python v3.7).

Para instalar o Python3.7, comece atualizando a sua lista de pacotes<br>
`$ sudo apt update`<br><br>
Após isso instale as dependências:<br>
`$ sudo apt install build-essential zlib1g-dev libncurses5-dev libgdbm-dev libnss3-dev libssl-dev libreadline-dev libffi-dev wget`<br><br>
Entre no diretório temporário do sistema, e lá baixe o Python: — a versão baixada aqui é o 3.7.9, você pode checar qual versão é a mais atualizada.<br>
`$ cd /tmp`<br>
`$ wget https://www.python.org/ftp/python/3.7.9/Python-3.7.9.tar.xz`<br><br>
Extraia o conteúdo, entre na pasta e configure o binário (lembre-se da opção `--enable-optimizations`):<br>
`$ tar -xf Python-3.7.9.tar.xz`<br>
`$ cd Python-3.7.9`<br>
`$ ./configure --enable-optimizations`<br><br>
Rode o make, e então o make (lembre-se da opção `altinstall`, caso contário você vai acabar substituindo a versão do Python padrão do seu sistema.):
`$ make -j 1`<br>
`$ sudo make altinstall`<br><br>

Agora você pode finalmente testar o Python:<br>
`$ python3.7 --version`<br>
Você deverá receber de volta:<br>
`Python 3.7.9`<br><br>
Estamos quase lá. Só falta agora instalar o gerenciador de pacotes do Python, o pip. E para isso apenas rode:<br>
`$ python3.7 -m pip install pip`<br><br>
Após a instalação, rode:
`$ pip3.7 --version`<br>
Você deverá receber de volta algo *como*:<br>
`$ pip 20.1.1 from ----`<br><br>
<br>
[Fonte](https://websiteforstudents.com/installing-the-latest-python-3-7-on-ubuntu-16-04-18-04/)<br>
Caso receba isso, você oficialmente tem o *Python* e o *pip* instalado, e agora pode seguir o resto das zines sem problemas.

Para usuários do Windows, apenas baixe o arquivo executável. E lembre-se de ativar a opção de PATH e a instalação do pip — gerenciador de pacotes do Python.


