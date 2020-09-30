<img width="30%" src="https://i.imgur.com/ULwPfn3.png"></img>

# O que é?
Bring in own driver é uma técnica muito utilizada em red teaming. A forma mais comum de encontrar driver não autenticados, é checando a signature dele. A uns anos atrás, a microsoft começou a assinar os drivers permitidos, por conta disso, ao tentar carregar um driver não-assinado, o usuário é alertado na hora.

### bring in own driver
Agora vamos falar sobre a técnica. A microsoft começou a assinar os dll's cerca de Julho de 2015, portanto, todos os dll's feitos antes dessa data, são certificados. Dito isso, a técnica consiste basicamente, em procurar um dll vulnerável em um desses dll's, feito isso, basta carregar esse dll, explorar a vulnerabilidade desse dll, e por meio dessa vulnerabilidade carregar o seu payload.dll. Dessa forma o usuário não é alertado e seu payload é carregado.

### fixing
Infelizmente (ou felizmente hehe), não tem como fixar esse bug, pois isso iria causar um prejuízo muito grande a microsoft, tendo que refazer todos esses dll's e assiná-los. E quando essa função fosse implementada, todos os sistemas com drivers não-assinados (antigos) seriam quebrados. Causando um prejuízo não só a Microsoft, mas a todos os seus usuários.
