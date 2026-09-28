# Visão de Implantação

## Control plane

O ambiente de servidor é baseado em Linux e containers.

Componentes típicos:

- REST Core;
- PostgreSQL/PostGIS;
- Traccar;
- Dashboard;
- reverse proxy;
- observabilidade;
- serviços auxiliares.

## Camadas

### Runtime base

Definido em `infra/linux/`.

Inclui os serviços centrais, rede interna e volumes persistentes.

### Homologação e segurança

Definida em `infra/hml/`.

Adiciona, quando habilitada:

- reverse proxy;
- TLS;
- proteção de acesso;
- Prometheus;
- Grafana;
- exporters;
- logging e validações de segurança.

## Secrets

Segredos reais não devem ser codificados em Compose nem versionados.

A estratégia preferida é:

- arquivos protegidos;
- mount somente leitura;
- variáveis `*_FILE` / `__FILE` quando suportadas;
- configuração gerada em runtime para componentes que não suportam leitura direta por arquivo.

## Persistência

PostgreSQL/PostGIS e Traccar utilizam volumes separados.

Backups devem registrar:

- dump;
- SHA-256;
- contagens de tabelas;
- revisão de schema;
- evidência de restore testado.

## Produção

Antes de produção, devem estar validados:

- autenticação humana;
- TLS;
- firewall;
- segredos;
- backup/restore;
- logging;
- observabilidade;
- retenção;
- rollback.

Este documento descreve arquitetura. Ele não substitui um runbook operacional específico do ambiente.
