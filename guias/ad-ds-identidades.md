# AD DS: identidades centralizadas em uma rede corporativa

O Active Directory Domain Services (AD DS) é o serviço de diretório do Windows Server que organiza e disponibiliza informações sobre objetos de um domínio, como contas de usuários, computadores e grupos. Ele permite que a equipe de TI administre identidades de maneira consistente em várias estações e serviços.

## Como as peças se relacionam

| Componente | Papel principal | O que não faz sozinho |
| --- | --- | --- |
| Controlador de domínio (DC) | Armazena uma cópia dos dados do domínio e oferece serviços de autenticação. | Não concede automaticamente acesso a toda pasta ou aplicação. |
| Unidade organizacional (OU) | Agrupa objetos para administração, delegação e escopo de GPOs. | Não é uma lista de permissões para recursos. |
| Grupo de segurança | Reúne contas para atribuição de direitos e permissões. | Não substitui a avaliação de permissões no recurso. |
| GPO | Reúne configurações aplicáveis a usuários e computadores conforme vínculos e escopo. | Não é, por si só, a permissão de leitura de uma pasta compartilhada. |

Quando uma pessoa entra em uma estação associada ao domínio, a autenticação envolve os serviços do DC. Em um cenário comum, o Kerberos usa o controlador de domínio como centro de distribuição de chaves. Depois da autenticação, cada recurso avalia a autorização adequada, incluindo as permissões associadas aos grupos da identidade. Essa distinção evita a ideia equivocada de que “estar no domínio” basta para acessar qualquer dado.

## Exemplo inteiramente fictício

A empresa **Exemplo** usa o domínio `corp.exemplo.test` e tem equipes de TI, Financeiro e Comercial.

1. A equipe organiza contas e computadores em OUs conforme as necessidades de administração e de aplicação de políticas. Uma estrutura inicial pode conter `TI`, `Financeiro`, `Comercial` e `Computadores`.
2. Cria o grupo de segurança `GRP_Financeiro_Leitura` para quem precisa consultar uma pasta compartilhada do Financeiro. A permissão de leitura é configurada no recurso para esse grupo; a OU não concede o acesso.
3. Vincula uma GPO à OU das estações para configurações como bloqueio de tela. O resultado depende do escopo, herança e filtros aplicáveis à GPO.
4. Quando alguém muda de função, revisa a associação aos grupos e os direitos concedidos, seguindo o princípio do menor privilégio.

Essa é uma estrutura didática, não um modelo universal de desenho de domínio. Em um ambiente real, OUs e grupos devem seguir requisitos de administração, segurança e crescimento.

## Perguntas úteis antes de implementar

- Quais tarefas de administração precisam ser delegadas e a quem?
- Quais configurações devem alcançar usuários, computadores ou ambos?
- Quais recursos exigem acesso e qual grupo deve receber cada permissão?
- Como será feita a revisão periódica das associações a grupos?

## Referências

- [Microsoft Learn — Visão geral do AD DS](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/active-directory-domain-services)
- [Microsoft Learn — Modelo lógico do AD DS](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/plan/understanding-the-active-directory-logical-model)
- [Microsoft Learn — Grupos de segurança](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/understand-security-groups)
- [Microsoft Learn — Group Policy](https://learn.microsoft.com/en-us/windows-server/identity/ad-ds/manage/group-policy/group-policy-overview)
- [Microsoft Learn — Autenticação Kerberos](https://learn.microsoft.com/windows-server/security/kerberos/kerberos-authentication-overview)
