<img width="30%" src="https://i.imgur.com/CGV9DU1.png"></img>

# gapz
Para começar a falar de bootkit, vou usar como referência o [Win32/gapz bootkit](https://www.welivesecurity.com/wp-content/uploads/2013/04/gapz-bootkit-whitepaper.pdf).<br>
O Win32/gapz bootkit ficou bem conhecido a alguns anos por trazer um novo conceito em relação aos bootkits que modifica apenas 4 bytes da boot record.

## hooks
Uma das features do Win32/gapz, é a implementação de uma hidden storage, que seria um "buffer" escondido na memória para manter o payload secreto.<br>
Para manter esse "buffer" secreto é utilizado uma `AES (Advanced Encryption Standart)` de 256 bits `CBC (Cipher-text Block Chaining)` para crypt/decrypt.
<br><br><img src="https://i.imgur.com/3IrfYUc.png"><br><br>

É uma `IV (Initialization Value)` diferente pra cada section, ou seja, cada section vai resultar em uma CBC diferente<br><br>
