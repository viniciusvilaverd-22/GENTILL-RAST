# Política do Repositório Público

## Objetivo

A publicação pública do REST Gentill serve para:

- apresentação técnica;
- revisão arquitetural;
- avaliação de segurança;
- documentação do produto;
- transparência de engenharia.

## Código público e download

GitHub não oferece uma opção para tornar o código de um repositório público visível e, ao mesmo tempo, impedir clone ou download ZIP.

Por isso existem duas formas de publicação possíveis:

### 1. Source-visible

O código-fonte é público, mas permanece sob licença proprietária.

Nesse modo:

- não são publicados binários oficiais;
- não são anexados APKs, EXEs, ZIPs de agentes ou instaladores;
- não são publicados dumps ou dados de homologação;
- o uso e redistribuição seguem o arquivo `LICENSE`.

### 2. Documentation-only

O código-fonte permanece privado e somente a documentação pública é publicada em um repositório/site separado.

Esse é o único modelo compatível com o requisito de não disponibilizar o código para download público.

## Conteúdo excluído da árvore pública

A publicação documental exclui:

- histórico interno de desenvolvimento;
- trilhas de auditoria e controle local;
- dados e evidências de homologação;
- caches, builds e artefatos gerados;
- perfis de navegador e resultados de testes;
- arquivos reais de ambiente;
- chaves e certificados privados;
- dumps, backups e bancos locais;
- binários, instaladores e pacotes de agentes;
- material operacional destinado a ambientes internos.

## Histórico Git

A publicação pública deve usar **histórico Git novo**, sem reutilizar o histórico local de desenvolvimento.

Isso evita que arquivos removidos do HEAD continuem acessíveis em commits antigos.

## Conteúdo proprietário

A visibilidade pública não converte o projeto em open source. Consulte `LICENSE`.
