# Arquitetura do REST Gentill

## Objetivo

O REST Gentill centraliza inventário, identidade de dispositivos, custódia, autorizações e contexto físico de ativos, mantendo telemetria de localização como domínio separado.

## Autoridades de dados

### REST Core

É a fonte de verdade para:

- ativos;
- dispositivos;
- usuários e setores;
- custódias;
- autorizações;
- prédios, pisos e salas;
- credenciais e enrollment;
- auditoria;
- políticas operacionais;
- integrações externas.

### Traccar

É a fonte de verdade para:

- posições GPS;
- histórico de localização;
- geocercas;
- eventos de telemetria.

A posição dinâmica não substitui o ambiente físico cadastrado do ativo.

## Topologia

```text
                   ┌──────────────────┐
                   │    Dashboard     │
                   └────────┬─────────┘
                            │
                   ┌────────▼─────────┐
Windows Agent ────►│                  │
Android Agent ────►│    REST Core     │◄──── TI PWA
                   │                  │
                   └───┬──────────┬───┘
                       │          │
             ┌─────────▼───┐  ┌──▼───────────┐
             │ PostgreSQL/ │  │   Traccar    │
             │   PostGIS   │  │  Telemetria  │
             └─────────────┘  └──────────────┘
```

## Identidade

O modelo diferencia:

- **Asset** — patrimônio físico;
- **Device** — endpoint associado ao ativo;
- **agent_installation_id** — identidade persistente da instalação do agente;
- **credencial do agente** — segredo individual revogável;
- MAC, IP e hostname — metadata, nunca identidade primária.

## Ambientes físicos

A hierarquia física segue:

```text
Building
  └─ Floor
      └─ Room
```

O vínculo estático pertence ao ativo. O dispositivo herda esse contexto por meio do ativo associado.

## Agentes

### Windows

Agente nativo em .NET 8 Worker Service. Coleta inventário técnico e heartbeat, utiliza credencial individual e protege segredo local com DPAPI.

### Android

Agente nativo em Kotlin. Opera com WorkManager, armazenamento seguro da plataforma e integração de localização com Traccar.

## PWA TI

A PWA é uma interface operacional da equipe de TI. Ela não substitui agentes nativos e não executa rastreamento permanente de endpoints.

## REST Mapper

Ferramenta separada para levantamento indoor. Sua função é produzir evidências de geometria e fingerprints posicionais sem se tornar agente permanente.

## Segurança e auditoria

O Core suporta:

- OIDC para identidade humana;
- RBAC;
- credenciais separadas para agentes e integrações;
- secrets por arquivo;
- auditoria de ações administrativas;
- políticas operacionais;
- validações de ciclo de vida.

## Evolução

Mudanças estruturais são registradas por ADRs e migrations. Contratos estáveis e candidatas de evolução são mantidos separados para reduzir regressões e preservar rastreabilidade.
