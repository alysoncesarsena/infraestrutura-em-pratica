# Proxmox VE: há capacidade para mais uma máquina virtual?

O painel mostra CPU folgada e espaço livre. A nova VM tem disco virtual de 120 GiB, mas começa ocupando só 40 GiB. Ainda assim, aprová-la olhando apenas o consumo do momento pode deixar o ambiente sem margem em uma semana de pico.

## O que medir antes de criar a VM

| Recurso | O que comparar | Pergunta para decidir |
| --- | --- | --- |
| CPU | Utilização do host nos picos e comportamento das VMs durante essas janelas | A carga nova coincide com o horário mais ocupado? |
| Memória | Memória disponível no host durante o pico e necessidade da VM nova | Há margem para a VM, o próprio host e o crescimento esperado? |
| Armazenamento | Espaço físico usado, crescimento previsto, latência e atividade de escrita | O pool suporta crescimento e operações que se sobrepõem, como backups? |

Em um armazenamento com *thin provisioning*, o tamanho visível dentro da VM pode ser maior que o espaço físico consumido naquele momento. Conforme o convidado escreve novos blocos, esse consumo cresce. Snapshots também podem reter blocos que o ambiente ainda precisa manter. Uma projeção deve usar o pool real e distinguir capacidade de desempenho.

## Avaliação fictícia do armazenamento

| Item | Valor |
| --- | ---: |
| Capacidade utilizável do pool | 500 GiB |
| Uso atual | 350 GiB |
| Crescimento estimado das VMs existentes | 50 GiB |
| Consumo físico inicial esperado da nova VM | 40 GiB |
| Consumo físico estimado da nova VM ao fim da janela | 75 GiB |
| Reserva mínima definida para este cenário | 80 GiB |

Logo após incluir a VM, a folga prevista é de **110 GiB**. Ao fim da janela, a projeção cai para **25 GiB** (`500 − 350 − 50 − 75`). A comparação usa 75 GiB no cenário futuro porque esse valor já inclui os 40 GiB iniciais. Mesmo que a VM caiba hoje, o cenário previsto fica abaixo da reserva de 80 GiB.

## Como transformar a estimativa em uma decisão

- **Registrar a janela da projeção.** Por exemplo, os próximos 30 dias. Usar períodos comparáveis e documentar quais operações já estão incluídas na estimativa.
- **Resolver a restrição encontrada.** Neste caso, avaliar expansão do pool, redistribuição de carga ou adiamento da VM. Confirmar CPU, RAM e desempenho do armazenamento antes da aprovação.
- **Definir quem acompanha.** Registrar a métrica, a margem mínima, a frequência de revisão e quem recebe o alerta. Em cluster, considerar também o cenário de manutenção ou perda de um nó quando ele fizer parte do requisito.

Os números servem para praticar a decisão. Reservas de capacidade dependem do histórico, do tipo de armazenamento, da carga e da tolerância a falhas do ambiente.

[Referência: guia de administração do Proxmox VE, capítulos de armazenamento e máquinas virtuais](https://pve.proxmox.com/pve-docs/pve-admin-guide.pdf)
