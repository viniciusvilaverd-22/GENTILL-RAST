# REST Gentill — Portfolio Snapshot

## What this project shows

O REST Gentill é um case de portfólio focado em produto, arquitetura de sistemas e engenharia operacional.

Ele demonstra capacidade de estruturar um produto técnico complexo desde o modelo de domínio até a operação multi-plataforma.

## 1. Product thinking

O produto não foi tratado como uma coleção de telas.

A definição parte de perguntas operacionais:

- o que é o patrimônio?
- qual endpoint representa esse patrimônio?
- quem é responsável?
- onde deveria estar?
- onde foi visto?
- qual instalação está autorizada a reportar?
- quem alterou cada estado?

Essas perguntas guiaram a arquitetura.

## 2. Domain modeling

Uma decisão central do sistema é:

```text
Asset ≠ Device ≠ Agent Installation ≠ Last Position
```

Cada conceito possui ciclo de vida e autoridade próprios.

## 3. Multi-platform architecture

O ecossistema envolve:

- Dashboard web;
- PWA de campo;
- Windows Agent;
- Android Agent;
- Linux control plane;
- REST Mapper para contexto indoor.

## 4. Security engineering

O projeto incorpora:

- OIDC;
- RBAC;
- identidade de máquinas;
- enrollment;
- credenciais revogáveis;
- DPAPI no Windows;
- armazenamento seguro no Android;
- secrets por arquivo;
- auditoria.

## 5. Data & telemetry

O REST Core é autoridade de patrimônio, identidade e responsabilidade.

Traccar permanece autoridade de localização dinâmica.

PostgreSQL/PostGIS fornece persistência e suporte geoespacial.

## 6. Operational maturity

O desenho considera:

- backup;
- restore;
- rollback;
- observabilidade;
- homologação;
- compatibilidade de contratos;
- separação entre baseline e candidata.

## 7. My role

**Vinícius Vilaverde — Product & System Architecture**

Áreas de atuação:

- visão e direção do produto;
- arquitetura;
- modelagem de domínio;
- UX operacional;
- integrações;
- segurança;
- estratégia de agentes;
- infraestrutura;
- governança técnica.

## Why this matters

O principal valor do case não é a quantidade de tecnologias.

É a capacidade de manter **identidade, patrimônio, responsabilidade e telemetria coerentes ao mesmo tempo** em um sistema multi-plataforma.
