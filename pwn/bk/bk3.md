<img width="30%" src="https://i.imgur.com/ULwPfn3.png"></img>

# payload injection
Para essa fase, o Win32/gapz aloca um buffer em um space address e copia o payload `overlord32(64).dll` pra esse space address, feito isso é criada uma thread pra rodar um loader, que vai carregar esse space address. O loader localiza o payload no space address e executa isso em user-mode<br><br>

Para isso, esse loader carrega um `DLL Loader` responsável por carregar os dll's, que mapeiam o payload em user-mode no space address. O payload cria uma função de command execution. O loader também carrega um `exe loader` que baixa os executáveis no sistema infectado<br><br>

[pwn](../README.md)<br>
[home](../../README.md)
