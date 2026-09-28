# Componentes do REST Gentill

## REST Core

API central e autoridade do domínio operacional.

Responsabilidades:

- inventário patrimonial;
- identidade de dispositivos;
- enrollment e heartbeat;
- custódias e autorizações;
- ambientes físicos;
- políticas operacionais;
- integrações externas;
- auditoria;
- ingestão e leitura de telemetria.

Tecnologias principais: Python, FastAPI, SQLAlchemy, Alembic e PostgreSQL/PostGIS.

## Dashboard

Interface administrativa e operacional.

Responsabilidades:

- visão consolidada;
- inventário;
- dispositivos;
- ambientes;
- custódia;
- autorizações;
- auditoria;
- mapa;
- filtros e pesquisa.

Tecnologias principais: React, TypeScript, Vite, Leaflet e PMTiles.

## TI PWA

Terminal móvel da equipe de TI.

Objetivos:

- consulta operacional;
- inventário em campo;
- leitura de QR quando disponível;
- mapa;
- detalhe de ativos e dispositivos;
- snapshot offline controlado.

A PWA não substitui agentes nativos.

## Windows Agent

Agente corporativo para computadores e notebooks Windows.

Responsabilidades:

- identidade da instalação;
- enrollment;
- proteção local de credenciais;
- inventário técnico;
- heartbeat;
- execução como serviço.

Tecnologia principal: .NET Worker Service.

## Android Agent

Agente corporativo para celulares e tablets Android.

Responsabilidades:

- identificação do endpoint;
- heartbeat;
- localização em background mediante permissões;
- operação offline-first;
- sincronização após recuperação de conectividade.

Tecnologias principais: Kotlin, WorkManager e Android Keystore.

## REST Mapper

Ferramenta separada para levantamento indoor.

Responsabilidades:

- geometria local;
- coleta de evidências Wi-Fi/BLE;
- apoio ao mapeamento de ambientes.

Não é agente permanente.

## Control plane

Runtime de servidor responsável por hospedar os componentes centrais e sua persistência.

Tecnologias principais: Linux, Docker Compose, PostgreSQL/PostGIS e Traccar.

## Observabilidade e homologação

Camada responsável por monitoramento, segurança de borda e diagnóstico operacional.

Tecnologias principais: Caddy, Prometheus e Grafana.

## Notificações

Serviços auxiliares podem consumir eventos do Core para entrega de notificações. Esses serviços não são fonte de verdade dos dados patrimoniais.
