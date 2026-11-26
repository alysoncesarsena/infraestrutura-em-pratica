# Windows Server: o que registrar antes de reiniciar um serviço?

Um serviço aparece como parado e a equipe recebe um chamado de indisponibilidade. Antes de reiniciá-lo, registrar o estado atual e a linha do tempo ajuda a preservar evidências que podem esclarecer a causa e orientar a próxima ação.

## 1. Confirmar o impacto e o horário

Identifique a função afetada, o horário do primeiro relato e o último momento em que o serviço funcionou. Registre o fuso usado. Se a falha for intermitente, compare ao menos dois períodos com impacto, quando houver registros suficientes.

## 2. Coletar evidências no Windows

No console **Serviços**, confira o nome interno do serviço, o estado e o tipo de inicialização. Examine as dependências declaradas e compare a configuração com o padrão esperado para o servidor. Um serviço parado pode ser normal quando ele é iniciado sob demanda.

No **Visualizador de Eventos**, abra **Logs do Windows → Sistema**. Filtre pelo intervalo do incidente e pela origem **Service Control Manager**. Registre horário, ID e resumo dos eventos pertinentes. Consulte também o log **Aplicativo** ou o log próprio da aplicação quando ela tiver um. Essas fontes ajudam a ordenar os fatos, mas eventos próximos no tempo podem ter causas diferentes.

## 3. Relacionar os sinais antes de agir

| Evidência observada | Próxima verificação |
| --- | --- |
| Serviço parado, sem registro recente de erro | Confirmar a configuração esperada e se ele deveria estar ativo naquele momento. |
| Serviço falhou logo após uma alteração autorizada | Revisar a alteração, as dependências e os eventos relacionados no mesmo intervalo. |
| Serviço em execução, mas o usuário continua sem acesso | Validar a função afetada de ponta a ponta. O estado do processo é apenas um dos sinais. |

## Exemplo fictício de registro

> **09h12, horário de Brasília.** Usuários do laboratório não conseguem usar a aplicação de treinamento. O serviço está parado. Às 09h08, o log do Sistema registra falha ao iniciar uma dependência. Próxima verificação: descobrir por que a dependência falhou e comparar o horário com a última mudança registrada.

Esse registro separa evidência de hipótese. Se uma intervenção for autorizada, anote o horário, o resultado e o teste funcional usado para confirmar a recuperação. Preserve os logs originais no ambiente autorizado. Ao compartilhar um exemplo de aprendizado, substitua nomes e detalhes reais por dados fictícios.

[Referências: consulta a serviços no Windows](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.management/get-service?view=powershell-7.6) · [consulta e filtragem de eventos do Windows](https://learn.microsoft.com/en-us/powershell/module/microsoft.powershell.diagnostics/get-winevent?view=powershell-7.6)
