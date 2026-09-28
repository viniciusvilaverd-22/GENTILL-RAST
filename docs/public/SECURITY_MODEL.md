# Modelo de Segurança

## Separação de identidades

O REST Gentill separa três classes de credencial:

1. identidade humana;
2. credencial individual de agente;
3. token de integração de serviço.

Uma credencial de agente não concede privilégios administrativos humanos.

## Acesso humano

O Core suporta OIDC e RBAC.

Papéis canônicos:

- `admin`;
- `gestor`;
- `operador`;
- `auditor`;
- `leitura`.

Produção deve operar com autenticação humana habilitada.

## Enrollment e agentes

O enrollment utiliza token temporário de uso controlado para emitir uma credencial individual do Device.

Princípios:

- credenciais são revogáveis;
- tokens temporários não devem ser persistidos em texto simples;
- identidade de instalação é persistente e separada de hostname/MAC/IP;
- agentes não operam de forma furtiva.

## Proteção local

### Windows

Segredo local protegido com DPAPI LocalMachine e ACL restritiva.

### Android

Segredos devem permanecer no armazenamento seguro da plataforma.

## Secrets no servidor

A infraestrutura é preparada para receber segredos por arquivo montado, evitando sua presença direta na configuração de processo quando o componente suporta esse modelo.

Arquivos reais de segredo:

- não entram no Git;
- devem possuir permissões restritas;
- não devem ser copiados para documentação, logs ou evidências públicas.

## Auditoria

Ações administrativas relevantes geram eventos de auditoria com identidade do ator e contexto da operação.

## Telemetria

Telemetria de localização é separada do domínio patrimonial. Essa divisão reduz ambiguidades entre:

- localização conhecida;
- local de referência do ativo;
- identidade do dispositivo;
- responsabilidade/custódia.

## Publicação

A árvore pública não deve conter:

- tokens;
- senhas;
- chaves privadas;
- dumps de banco;
- ambientes locais;
- evidências de homologação com dados operacionais;
- perfis de navegador;
- binários de agentes.
