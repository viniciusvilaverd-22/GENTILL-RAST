# REST Gentill

Plataforma corporativa para **inventário, custódia, identidade de endpoints e localização de ativos**.

O REST Gentill organiza o ciclo operacional de equipamentos corporativos em uma arquitetura auditável, com agentes nativos, API central, dashboard web, terminal móvel para a equipe de TI e integração dedicada de telemetria.

> Alguns identificadores técnicos históricos ainda usam o prefixo `RAST` para preservar compatibilidade de banco, packages, serviços e automações existentes.

## Visão geral

O sistema foi desenhado para separar claramente patrimônio, responsabilidade e telemetria:

- **REST Core** — fonte de verdade para ativos, dispositivos, custódias, autorizações, ambientes, credenciais e auditoria;
- **Traccar** — fonte de telemetria de localização e histórico GPS;
- **Dashboard** — interface administrativa e operacional;
- **PWA TI** — terminal móvel de campo para consulta e operação assistida;
- **Windows Agent** — agente nativo para computadores e notebooks Windows;
- **Android Agent** — agente nativo para celulares e tablets Android;
- **REST Mapper** — ferramenta separada para levantamento físico e mapeamento indoor.

## Capacidades

- inventário patrimonial e técnico;
- cadastro e identidade de dispositivos;
- enrollment e credenciais individuais de agentes;
- heartbeat com informações operacionais do endpoint;
- custódia por usuário e setor;
- autorizações de saída e retorno;
- ambientes físicos: prédio, piso e sala;
- mapa operacional e última posição conhecida;
- geocercas e políticas operacionais;
- auditoria de ações administrativas;
- importações e identidades externas;
- notificações e outbox;
- suporte a OIDC/RBAC para acesso humano;
- backup, restore, logging e observabilidade no plano de infraestrutura.

## Arquitetura

```text
Windows Agent ─┐
Android Agent ─┼──── REST Core ───── PostgreSQL/PostGIS
TI PWA ────────┤         │
Dashboard ─────┘         ├────────── Traccar
                         ├────────── Auditoria
                         └────────── Notificações
```

A localização dinâmica não é armazenada como atributo patrimonial. O Core mantém o vínculo estático do ativo com seu ambiente físico; telemetria e posição continuam sendo tratadas como informações dinâmicas.

## Componentes principais

| Componente | Responsabilidade | Tecnologia principal |
| --- | --- | --- |
| REST Core | API, domínio, autenticação, auditoria e regras de negócio | Python, FastAPI, SQLAlchemy, Alembic |
| Dashboard | Painel administrativo e operacional | React, TypeScript, Vite |
| TI PWA | Terminal móvel da equipe de TI | React, TypeScript, PWA |
| Windows Agent | Agente corporativo Windows | .NET Worker Service |
| Android Agent | Agente corporativo Android | Kotlin, WorkManager, Android Keystore |
| REST Mapper | Levantamento e mapeamento indoor | Android |
| Control plane | Runtime do servidor | Linux, Docker Compose |
| Observabilidade | Monitoramento e diagnóstico | Prometheus, Grafana |

## Princípios de segurança

- credenciais de agente são individuais e revogáveis;
- identidade de dispositivo não depende de MAC, IP ou hostname;
- Windows protege segredo local com DPAPI;
- Android utiliza armazenamento seguro da plataforma;
- o Core aceita segredos por arquivo para runtime protegido;
- acesso humano pode operar com OIDC e papéis canônicos;
- ações administrativas relevantes são auditáveis;
- produção não deve operar com autenticação humana desabilitada;
- agentes não utilizam técnicas furtivas;
- arquivos locais, chaves, dumps, tokens e artefatos de homologação não fazem parte da distribuição pública.

Consulte [SECURITY.md](SECURITY.md) e [docs/public/SECURITY_MODEL.md](docs/public/SECURITY_MODEL.md).

## Estrutura de documentação

- [Arquitetura pública](docs/public/ARCHITECTURE.md)
- [Componentes](docs/public/COMPONENTS.md)
- [Modelo de segurança](docs/public/SECURITY_MODEL.md)
- [Visão de implantação](docs/public/DEPLOYMENT_OVERVIEW.md)
- [Política do repositório público](docs/public/REPOSITORY_POLICY.md)

Esta publicação contém apenas a documentação destinada à apresentação pública. ADRs internos, evidências de validação, backups e material operacional permanecem fora deste repositório.

## Desenvolvimento

Pré-requisitos dependem do componente:

- Docker / Docker Compose para o control plane;
- Node.js para Dashboard e PWA;
- Python 3.13 para o Core;
- .NET 8 SDK para o agente Windows;
- JDK 17 + Android SDK para Android Agent e Mapper.

Cada componente possui sua própria configuração de build. Variáveis de ambiente reais e segredos nunca devem ser versionados.

## Estado do projeto

O REST Gentill está em desenvolvimento ativo. Contratos e mudanças estruturais são registrados por ADRs e migrations, com separação entre baseline estável, candidatas de evolução e ambientes de homologação.

Esta documentação não deve ser interpretada como uma distribuição binária nem como autorização para operar o sistema em produção.

## Distribuição pública

Este repositório público contém **somente documentação**.

O código-fonte, instaladores, APKs, agentes, dumps, chaves, credenciais, evidências internas e arquivos operacionais permanecem privados.

Os termos de uso da documentação estão definidos em [LICENSE](LICENSE).

## Contribuições

Contribuições externas não são aceitas automaticamente. Consulte [CONTRIBUTING.md](CONTRIBUTING.md).

## Licença

Copyright © 2026 REST Gentill. Todos os direitos reservados.

Consulte [LICENSE](LICENSE).
