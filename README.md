# Infraestrutura de TI em prática

Notas técnicas sobre administração de sistemas, redes e continuidade operacional. O conteúdo é educativo, usa exemplos fictícios e foi escrito para compartilhar raciocínio técnico sem expor ambientes de produção.

## Guias

### Redes e identidades

- [VPN conectada sem acesso](guias/vpn-conectada-sem-acesso.md). Separar falhas de DNS, rota, porta e acesso à aplicação.
- [VLAN na prática](guias/vlan-access-trunk.md). Diagnosticar a perda de acesso ao gateway em um caminho com portas de acesso e trunk 802.1Q.
- [Diagnóstico inicial de DNS e conectividade](guias/diagnostico-dns-conectividade.md). Distinguir resolução de nomes e falhas de conectividade.
- [AD DS e identidades centralizadas](guias/ad-ds-identidades.md). Entender controladores de domínio, OUs, grupos e GPOs.

### Servidores e virtualização

- [Janela de manutenção no Proxmox VE](guias/proxmox-janela-manutencao.md). Planejar aceite, horário limite e reversão da mudança em uma VM.
- [Triagem de serviços no Windows Server](guias/windows-server-triagem-servicos.md). Registrar estado, dependências e eventos antes de intervir.
- [Capacidade para uma nova VM no Proxmox VE](guias/proxmox-capacidade-vm.md). Avaliar CPU, memória e armazenamento com um exercício de dimensionamento.

### Continuidade

- [Triagem de incidentes no Microsoft 365](guias/microsoft-365-triagem-incidentes.md). Delimitar o impacto e consultar a saúde do serviço com um exemplo no Teams.
- [Planejamento de restauração](guias/planejamento-restauracao.md). Definir o que recuperar e como validar o resultado em laboratório.

## Escopo

- Os nomes de empresas, usuários e domínios são fictícios.
- Os guias descrevem conceitos e procedimentos de análise; não afirmam ter executado um laboratório ou medido resultados.
- Configurações de produção dependem do contexto, da política de segurança e da documentação oficial de cada produto.
- Nenhum material institucional, dado de paciente, endereço interno ou código de projetos privados integra este projeto.

## Autoria e uso

Conteúdo de Alyson César Sena. Nenhuma licença de código aberto foi definida; a visibilidade pública deste repositório não implica permissão automática para reutilizar o conteúdo.
