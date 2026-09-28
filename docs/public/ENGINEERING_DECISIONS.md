# Engineering Decisions

Esta página resume decisões arquiteturais que definem o REST Gentill.

## Asset ≠ Device

Um patrimônio físico e um endpoint computacional representam conceitos distintos.

Essa separação permite:

- substituir hardware;
- manter histórico patrimonial;
- preservar identidade operacional;
- evitar que dados técnicos contaminem o cadastro patrimonial.

## Device ≠ Agent Installation

O agente instalado também possui identidade própria.

Motivos:

- reinstalações acontecem;
- credenciais precisam ser revogadas;
- uma instalação precisa ser distinguida de metadata do equipamento.

## MAC/IP/hostname não são identidade

Esses valores mudam ao longo do ciclo de vida do endpoint.

São metadata úteis, mas não chaves de identidade.

## REST Core ≠ Traccar

O Core é autoridade patrimonial e operacional.

Traccar é autoridade especializada de localização.

A divisão evita duplicação de lógica de tracking e preserva responsabilidades claras.

## Static location ≠ Dynamic position

`Room` representa um local físico de referência.

Uma coordenada de telemetria representa uma observação temporal.

Os dois conceitos não devem competir pela mesma coluna ou autoridade.

## PWA ≠ Agent

A PWA foi desenhada para pessoas.

Os agentes foram desenhados para telemetria persistente de endpoints.

Misturar essas funções aumentaria consumo, permissões e complexidade operacional.

## Native agents

Windows e Android possuem agentes nativos porque execução em background, segurança local e lifecycle são específicos de plataforma.

## OIDC + machine credentials

Identidade humana e identidade de máquina utilizam fluxos separados.

Uma credencial de agente não concede acesso administrativo.

## Secrets por arquivo

Ambientes protegidos devem evitar secrets diretamente na configuração de processo quando existe suporte a arquivos montados.

## Auditability over convenience

Operações administrativas importantes precisam ser rastreáveis mesmo quando isso exige mais estrutura de domínio.

## Restore is part of backup

Um dump existente não prova recuperabilidade.

O desenho operacional considera restore testado como parte da estratégia de backup.

## Compatibility-first evolution

Mudanças estruturais devem ser versionadas e documentadas para que agentes, Core e interfaces possam evoluir sem breaking changes silenciosos.
