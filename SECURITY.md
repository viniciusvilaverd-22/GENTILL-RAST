# Security Policy

## Escopo

A segurança do REST Gentill abrange o Core, Dashboard, PWA TI, agentes Windows/Android, integrações de telemetria e infraestrutura de execução.

## Relato responsável

Não publique vulnerabilidades, credenciais, tokens, chaves, dados pessoais ou detalhes de exploração em issues públicas.

Ao utilizar GitHub para hospedar este repositório, prefira um **Private Vulnerability Report / Security Advisory** quando disponível no repositório.

O relato deve incluir, quando possível:

- componente afetado;
- versão ou commit observado;
- pré-condições;
- passos mínimos de reprodução;
- impacto técnico;
- evidências sem dados sensíveis.

## Princípios

- nenhum segredo real deve ser versionado;
- arquivos `.env` reais permanecem fora do Git;
- credenciais de agentes são individuais e revogáveis;
- acesso humano em produção requer autenticação apropriada;
- alterações de contrato e migrations devem ser explícitas e auditáveis;
- telemetria, custódia e identidade possuem autoridades separadas;
- logs e evidências públicas não devem conter tokens ou credenciais.

## Suporte de segurança

Este repositório contém somente documentação pública. Relatos sobre o produto devem identificar claramente o componente e a versão observada sem incluir segredos ou dados operacionais.

## Divulgação

A divulgação pública de uma vulnerabilidade deve ocorrer somente após a correção estar disponível e depois de removidos dados que facilitem abuso direto.
