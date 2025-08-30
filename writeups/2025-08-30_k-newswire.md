TEMPLATE


**Título:** [web] - K-Newswire

**Autor(es):** @thadeu_rodrigues

**CTF:** Kaspersky CTF

**Categoria:** web

**Resumo (1–2 linhas):**

O desafio consistia em encontrar a flag em uma aplicação web moderna que usava Socket.IO, explorando a comunicação entre cliente e servidor com o Burp Suite para se conectar a um canal secreto.

**Passo a passo (solução):**

1)Análise do Código-Fonte: A primeira etapa foi analisar o código JavaScript da aplicação. Nele, foi encontrada uma constante que definia o nome de um canal secreto no Socket.IO: secret_announcements. A aplicação padrão usava apenas o canal public.  2)Configuração do Proxy: O Burp Suite foi configurado como um proxy para inspecionar e manipular todo o tráfego da rede, incluindo as comunicações do WebSocket, que não são facilmente acessíveis pelo console do navegador. 3) Localização da Mensagem de "join": Na seção WebSocket history do Burp Suite, foi identificada a mensagem que a aplicação envia para se juntar ao canal público. Essa mensagem tinha o formato 42["join",{"room":"public"}]. 4) Modificação e Envio do Payload: A mensagem de "join" foi modificada para apontar para o canal secreto. No Repeater do Burp Suite, o payload foi alterado para 42["join",{"room":"secret_announcements"}] e enviado ao servidor. 5) Obtenção da Flag: O servidor aceitou a requisição e, em resposta, enviou uma mensagem com a flag no formato 42["announcement",{"flag":"kaspersky{h07_n3ws_fr0m_unl0ck3d_s3cre7_ch4nn3ls}"}]

**Arquivo(s):** 