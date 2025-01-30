# SCRIPT

"Sobrescrevendo navigator.mediaDevices.getUserMedia"

![image](https://github.com/user-attachments/assets/8fa3691d-b2cd-4776-8895-5ebb35f6b856)

if (navigator.mediaDevices && navigator.mediaDevices.getUserMedia): Verifica se o objeto navigator.mediaDevices e a função getUserMedia existem. Isso é importante para garantir que o código só tente sobrescrever a função se ela realmente existir.
Armazenar a Função Original:

const originalGetUserMedia = navigator.mediaDevices.getUserMedia.bind(navigator.mediaDevices);: Armazena a função original getUserMedia para que ainda possamos chamar a funcionalidade original se necessário.
Sobrescrever a Função:

navigator.mediaDevices.getUserMedia = function (constraints) {...}: Sobrescreve a função getUserMedia com uma nova função que verifica os constraints (restrições) passados para a função.
Bloquear Acesso à Câmera:

if (constraints && constraints.video) { return Promise.reject(new Error('Acesso à câmera bloqueado.')); }: Se as restrições incluem video, a função retorna uma Promise rejeitada com a mensagem "Acesso à câmera bloqueado.".
return originalGetUserMedia(constraints);: Se as restrições não incluem video, a função original getUserMedia é chamada com as mesmas restrições.

Esse userscript bloqueia qualquer tentativa de acessar a câmera do computador sobrescrevendo a função navigator.mediaDevices.getUserMedia. Se um site tentar acessar a câmera, a função modificada rejeitará a tentativa e retornará um erro.

O script oferece vantagens significativas para usuários preocupados com a privacidade e a segurança de suas câmeras nos computadores.
