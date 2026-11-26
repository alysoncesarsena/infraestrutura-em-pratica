# Proxmox VE: como preparar uma janela de manutenção de VM?

Uma aplicação interna vai receber uma atualização. A VM pode reiniciar e o painel do Proxmox pode voltar ao normal antes de a aplicação estar pronta para os usuários. A janela precisa reservar tempo para preparar, validar e, se necessário, voltar ao estado anterior.

## Antes de iniciar

- **Identifique o alcance.** Registre a VM, a função afetada, quem depende dela e se a mudança alcança componentes externos, como um banco em outra VM.
- **Combine o teste de aceite.** Escolha uma operação que represente o uso real. Por exemplo, abrir o portal, autenticar com uma conta de teste autorizada e consultar um registro fictício.
- **Confirme o ponto de recuperação.** Verifique o backup disponível, seu escopo e o que já foi testado em uma restauração. Se o processo usar snapshot, confirme o suporte do armazenamento e quais discos e estados ele cobre. Um banco externo precisa de seu próprio plano.
- **Reserve tempo para voltar.** Defina quem decide, qual evidência dispara a reversão e até que horário a decisão precisa ser tomada.

## Exemplo fictício de janela de 60 minutos

| Horário | Atividade |
| --- | --- |
| 20h00 a 20h10 | Confirmar o estado inicial, dependências, ponto de recuperação e teste de referência. |
| 20h10 a 20h25 | Aplicar a mudança documentada. |
| 20h25 a 20h35 | Verificar inicialização, logs e operação de aceite. |
| A partir das 20h35 | Se o aceite falhar, iniciar a reversão prevista. A janela reserva 25 minutos para reversão e nova verificação. |

Os tempos são ilustrativos. Se a reversão conhecida demora mais que a reserva disponível, a janela precisa ser ajustada antes da mudança.

## Como decidir se a mudança terminou

Uma VM em execução prova que o hipervisor a iniciou. Para aceitar a manutenção, repita o teste funcional, confira as dependências e registre o resultado com horário. Em caso de reversão, repita o mesmo teste e documente se houve perda de alterações posteriores ao ponto recuperado. Se a aplicação escreve em mais de um componente, avalie a consistência desses dados antes de retomar o uso normal.

[Proxmox VE — Administração, snapshots e máquinas virtuais](https://pve.proxmox.com/pve-docs/pve-admin-guide.pdf) · [Proxmox VE — Backup e restauração](https://pve.proxmox.com/pve-docs/chapter-vzdump.html)
