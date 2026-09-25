# Backup e restauração: planejar a validação

Ter arquivos de backup é uma etapa da continuidade operacional. A recuperação exige saber **o que restaurar**, **em qual ordem**, **com qual objetivo de tempo** e **como confirmar que o serviço voltou a funcionar**.

Este guia é um roteiro de planejamento para um laboratório com dados fictícios. Ele não registra uma restauração já executada.

## Antes do exercício

| Pergunta | Por que importa |
| --- | --- |
| Qual serviço precisa voltar primeiro? | Dependências podem impedir a validação de serviços posteriores. |
| Qual é a última cópia íntegra disponível? | O ponto de recuperação precisa estar claro antes de iniciar. |
| Quem autoriza e executa o procedimento? | Reduz improviso e lacunas de responsabilidade. |
| Onde o teste será feito? | Um ambiente isolado evita sobrescrever dados de produção. |
| Quais são os critérios de sucesso? | “Arquivo copiado” não equivale a aplicação utilizável. |

## Exemplo fictício de validação

Considere uma aplicação de laboratório com banco de dados e arquivos de exemplo. Um exercício poderia verificar:

1. Se os arquivos e o banco foram restaurados a partir do ponto escolhido.
2. Se a aplicação inicia no ambiente isolado e consegue consultar dados fictícios esperados.
3. Se as dependências necessárias estão disponíveis.
4. Se o tempo observado e qualquer falha foram registrados para revisão do procedimento.

Os passos concretos, ferramentas e ordem exata dependem da arquitetura testada. Só se deve declarar que a restauração funciona depois de executar o ensaio e validar dados e funcionalidades. Em produção, o plano ainda precisa prever comunicação, autorização e retorno à operação normal.

## Referência

- [NIST SP 800-34 Rev. 1 — Contingency Planning Guide for Federal Information Systems](https://nvlpubs.nist.gov/nistpubs/legacy/sp/nistspecialpublication800-34r1.pdf), especialmente os exemplos de procedimentos de recuperação e validação após a restauração.
