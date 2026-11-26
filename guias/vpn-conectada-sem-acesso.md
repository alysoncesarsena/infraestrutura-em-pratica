# VPN conectada: por que o sistema interno ainda não abre?

A VPN indica **Conectada**, mas um portal interno não abre. O estado da VPN informa que a sessão foi estabelecida. Para uma aplicação funcionar, o nome precisa apontar para o destino esperado, o tráfego precisa seguir pela rota correta e a conexão à porta do serviço precisa ser permitida.

## Quatro verificações, na ordem

1. **Nome.** Confira se o endereço informado pelos usuários resolve para o IP previsto para quem está na VPN. Compare com a documentação ou com uma estação de referência autorizada. Se o nome resolve para outro destino, investigar o servidor de aplicação errado vai atrasar o diagnóstico.
2. **Rota.** No cliente, confira qual interface o sistema escolhe para alcançar aquele IP. Em um túnel dividido, os prefixos definidos no perfil devem seguir pelo túnel. Uma rede local com o mesmo prefixo ou uma rota específica inadequada pode mudar o caminho escolhido.
3. **Porta.** Verifique a conexão TCP somente para o destino e a porta conhecidos do serviço, como HTTPS na porta 443. Um ping pode ser bloqueado. Se o teste TCP falhar, revise o caminho de ida e volta, as regras e se o serviço está escutando. O resultado do teste não informa sozinho qual componente bloqueou ou rejeitou a conexão.
4. **Aplicação.** Se a conexão TCP funcionar, repita a operação no cliente normal. Um erro de certificado, autenticação ou autorização pede uma investigação própria. Registre o texto exato do erro, sem dados sensíveis.

## Exemplo fictício

A estação resolve o portal para o endereço esperado. Na análise de rota, porém, o Windows seleciona a interface Wi-Fi. O portal deveria estar em um prefixo encaminhado pela VPN. Nesse cenário, o primeiro passo é comparar a rota selecionada com o perfil aprovado e com uma estação funcional. Só faz sentido alterar a configuração após identificar a divergência e confirmar a política para aquele prefixo.

Se o cliente seleciona o túnel e a conexão TCP funciona, mas o portal retorna **HTTP 403**, já há uma resposta HTTP no caminho. Consulte então as políticas de acesso e, conforme o ambiente, os registros do proxy ou da aplicação para entender quem retornou a recusa.

## Registro mínimo para escalar

Anote horário, função afetada, resultado de resolução, interface escolhida, porta testada e erro da aplicação. Na estação Windows, o diagnóstico de rota e o teste TCP de `Test-NetConnection` são operações separadas. Em um chamado real, armazene as evidências nos canais autorizados.

[Microsoft Learn — Roteamento de VPN no Windows](https://learn.microsoft.com/en-us/windows/security/operating-system-security/network-security/vpn/vpn-routing) · [Microsoft Learn — Test-NetConnection](https://learn.microsoft.com/en-us/powershell/module/nettcpip/test-netconnection?view=windowsserver2025-ps)
