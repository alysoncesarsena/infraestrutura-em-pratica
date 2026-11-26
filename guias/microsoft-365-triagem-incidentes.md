# Microsoft 365: como delimitar um incidente no Teams?

Algumas pessoas relatam que não conseguem enviar mensagens no aplicativo do Teams. Outras continuam trabalhando normalmente. Antes de tratar o chamado como indisponibilidade geral, identifique qual função falhou, quem foi afetado e em quais condições.

## 1. Delimite o impacto

Registre a operação que falha, a mensagem exibida e o horário com fuso. Diferencie abrir o aplicativo, entrar na conta, enviar mensagens e participar de uma reunião. São sintomas que podem aparecer em momentos e componentes diferentes.

Com uma conta autorizada, repita **a mesma operação** em condições que mudem uma variável por vez. Use apenas dispositivos, redes e métodos aprovados pela organização.

| Comparação | O que a observação ajuda a investigar |
| --- | --- |
| A mesma conta consegue realizar a operação no navegador, mas não no aplicativo | Comece pelo cliente, pela versão e pela sessão. Confira se a operação é suportada da mesma forma nas duas interfaces. |
| A mesma conta falha em mais de um dispositivo, enquanto outra conta autorizada funciona | Verifique se há diferenças de licença, configuração ou política aplicável à primeira conta. |
| Várias contas falham na mesma operação, em diferentes dispositivos e redes autorizadas | Confira a saúde do serviço e mudanças recentes que afetem mais de um grupo. |

Esses sinais ajudam a escolher o próximo teste. Nenhum deles, sozinho, identifica a causa.

## 2. Confira a saúde do serviço

No centro de administração do Microsoft 365, abra **Integridade → Integridade do serviço** com uma função autorizada. Procure incidentes e avisos que correspondam ao produto, à funcionalidade afetada e à janela do chamado. Se encontrar uma ocorrência compatível, registre seu identificador e o horário da última atualização.

Se o painel não mostrar um incidente correspondente, continue a investigação com as evidências coletadas. Quando houver impacto recorrente ou amplo, use o canal de suporte previsto pela organização. A ausência de um aviso não descarta um problema no serviço.

## Exemplo fictício de atualização para o chamado

> **09h40, horário de Brasília.** Três pessoas relatam que não conseguem enviar mensagens pelo aplicativo do Teams. Duas repetiram a mesma operação com sucesso pelo navegador. O painel do Microsoft 365 não mostra um aviso compatível até o momento. O próximo passo é comparar as versões dos clientes afetados e revisar o erro observado.

Encerre a triagem quando houver um caminho de investigação e alguém responsável pelo próximo passo. Confirme a recuperação repetindo a operação que originalmente falhou, quando aplicável.

[Microsoft Learn — Como verificar a integridade do serviço do Microsoft 365](https://learn.microsoft.com/pt-br/microsoft-365/enterprise/view-service-health?view=o365-worldwide)
