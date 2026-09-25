# Diagnóstico inicial de DNS e conectividade no Windows

Quando uma aplicação “não abre”, há várias causas possíveis: configuração de IP, DNS, rota, firewall, serviço indisponível ou credenciais. Uma sequência curta de testes ajuda a localizar a falha antes de alterar a configuração.

## Sequência de investigação

1. **Delimite o problema.** O erro ocorre em uma estação, em um grupo de usuários ou em todos? Afeta um nome específico ou qualquer destino? Registre horário, mensagem e mudanças recentes.
2. **Confira a configuração do cliente.** `ipconfig /all` mostra endereço, máscara, gateway, servidores DNS e sufixo. Compare com o desenho esperado para o ambiente. Não publique a saída real do comando sem revisão.
3. **Separe nome de conectividade.** Consulte o nome completo do serviço com `Resolve-DnsName <nome-completo-do-servico>` ou `nslookup <nome-completo-do-servico>`. Compare a resposta com o endereço esperado. Um nome curto pode depender do sufixo DNS da estação.
4. **Teste a porta do serviço.** No PowerShell, `Test-NetConnection <nome-completo-do-servico> -Port <porta>` verifica a tentativa de conexão TCP. Uma consulta DNS bem-sucedida não prova que a aplicação está atendendo.
5. **Avalie dependências.** Se a resolução e a conexão estiverem corretas, verifique estado do serviço, autenticação, regras de acesso e logs disponíveis ao responsável.

Um `ping` sem resposta, isoladamente, não demonstra que o destino está indisponível: o tráfego ICMP pode estar bloqueado. Da mesma forma, `nslookup` consulta o servidor DNS configurado e pode produzir resultado diferente do comportamento de uma aplicação que usa o cache e outros mecanismos do cliente.

## Registro mínimo do diagnóstico

Anote o sintoma, o teste feito, o resultado esperado e o resultado observado. Esse registro ajuda outra pessoa da equipe a continuar a investigação. Remova nomes internos, endereços, credenciais e dados de usuários antes de transformar qualquer caso real em conteúdo público.

## Referências

- [Microsoft Learn — Solução de problemas de clientes DNS](https://learn.microsoft.com/windows-server/networking/dns/troubleshoot/troubleshoot-dns-client)
- [Microsoft Learn — Test-NetConnection](https://learn.microsoft.com/en-us/powershell/module/nettcpip/test-netconnection?view=windowsserver2025-ps)
- [Microsoft Learn — Consultas e resolução DNS](https://learn.microsoft.com/en-us/windows-server/networking/dns/queries-lookups)
