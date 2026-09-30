# P7 — Portfolio Release Candidate 1

Registro de preparação documental do REST Gentill para publicação via GitHub Pages.

## Estado

| Gate | Resultado |
| --- | --- |
| Repositório `main` público | Verificado pelo conector |
| Imagem premium e social preview | Arquivos completos de 75.625 bytes cada; guard de mídia |
| Galeria de quatro imagens | Publicada e preservada no projeto local |
| Versões PT e EN | Fontes HTML presentes |
| Navegação HTML e recursos locais | Verificação automática na CI |
| Documentos técnicos | Links encaminhados ao Markdown renderizado no GitHub, evitando conteúdo bruto no Pages |
| Código-fonte do produto | Não publicado |
| GitHub Pages ativado e acessível | **PENDENTE DE CONFIRMAÇÃO EXTERNA** |
| Revisão visual por navegador real | **PENDENTE ATÉ O SITE RESPONDER** |
| Description, topics, preview configurado e pin no perfil | **PENDENTE DE CONFERÊNCIA NA INTERFACE** |

## Ativação necessária

No repositório: **Settings → Pages → Build and deployment → Deploy from a branch → main → /docs → Save**.

Este ajuste pertence à configuração do repositório e não foi autorizado pelo conector disponível nesta sessão.

## Testes de aceitação após a ativação

- Abrir `https://viniciusvilaverd-22.github.io/GENTILL-RAST/` e confirmar resposta pública e capa integral.
- Abrir `https://viniciusvilaverd-22.github.io/GENTILL-RAST/en.html`, alternar PT/EN em ambas as direções.
- Abrir `https://viniciusvilaverd-22.github.io/GENTILL-RAST/gallery.html` e conferir as quatro capturas e legendas.
- Abrir links de Case Study, Threat Model e Engineering Decisions: devem mostrar o Markdown formatado no GitHub.
- Conferir layout e overflow em larguras de 360, 768 e 1440 px; teclado e texto alternativo.
- Conferir HTTPS, favicon, Social Preview e ausência de imagem truncada.
- Verificar CI da SHA publicada, sem presumir que CI substitui auditoria visual ou revisão de segurança.

## Limites

O RC1 refere-se exclusivamente à superfície pública de portfólio, não à homologação de produção do REST Gentill. Nenhum dado de HML, segredo, banco, agente ou runtime do produto é liberado por este gate.
