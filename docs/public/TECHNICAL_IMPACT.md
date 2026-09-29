# REST Gentill — Technical Impact

## Scope map

O projeto combina múltiplas disciplinas que normalmente aparecem separadas:

| Área | Escopo |
| --- | --- |
| Product architecture | superfícies, papéis, domínio e fluxos |
| Backend | regras, contratos, autenticação e integrações |
| Frontend | operação administrativa e visualização |
| Mobile | PWA e Android nativo |
| Endpoint engineering | agente Windows nativo |
| Data | PostgreSQL e PostGIS |
| Telemetry | Traccar e heartbeat |
| Security | OIDC, RBAC, machine credentials e secrets |
| Infrastructure | Linux, containers, proxy e observabilidade |
| Governance | migrations, baselines, gates e rollback |

## Architectural pressure points

### Identity persistence

O endpoint precisa continuar reconhecível mesmo quando:

- IP muda;
- MAC muda;
- hostname muda;
- agente é reinstalado;
- posição muda.

Por isso esses valores não definem identidade primária.

### Telemetry separation

Uma posição observada é um fato temporal.

Um ambiente cadastrado é uma referência operacional.

Misturar os dois leva a ambiguidades de domínio.

### Human vs machine identity

Usuários humanos e agentes não compartilham o mesmo modelo de autenticação.

Isso reduz o risco de uma credencial de dispositivo conceder acesso administrativo.

### Offline mobile behavior

Android precisa continuar operando quando a rede falha.

A arquitetura considera fila, sincronização e recuperação de conectividade.

### Recoverability

Backup é tratado como parte de uma estratégia maior.

Restore e rollback são capacidades explícitas, não pressupostos.

## What this demonstrates technically

O case demonstra capacidade de:

- decompor um problema operacional em domínios;
- definir autoridades claras;
- integrar tecnologias especializadas sem criar um monólito acoplado;
- projetar identidades persistentes;
- tratar segurança e operação como requisitos de arquitetura;
- coordenar evolução entre múltiplos clientes e plataformas.

## Portfolio signal

O REST Gentill é apresentado publicamente como documentação de arquitetura e produto.

O código-fonte permanece privado, mas o case torna visíveis as decisões, os trade-offs e o nível de complexidade enfrentado no projeto.
