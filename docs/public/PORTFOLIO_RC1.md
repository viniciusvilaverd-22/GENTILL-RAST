# P7 — Portfolio Release Candidate 1

Registro de preparação documental do REST Gentill para publicação via GitHub Pages.

## Estado

| Gate | Resultado |
| --- | --- |
| Repositório `main` público | Verificado pelo conector |
| Imagem premium e social preview | Arquivos completos de 75.625 bytes cada; guard de mídia |
| Galeria de quatro imagens | Publicada e preservada no projeto local |
| Versões PT e EN | Fontes HTML presentes |
| Navegação HTML e recursos locais | **PASS — CI**, incluindo páginas PT/EN e galerias PT/EN |
| Documentos técnicos | Links encaminhados ao Markdown renderizado no GitHub, evitando conteúdo bruto no Pages |
| Código-fonte do produto | Não publicado |
| GitHub Pages — build e deploy | **PASS — GitHub Actions run 36729196069** |
| Acesso HTTP externo independente | **NÃO VERIFICADO: ferramentas externas sem acesso ao hostname** |
| Revisão visual por navegador real | **PENDENTE ATÉ O SITE RESPONDER** |
| Description, topics, preview configurado e pin no perfil | **PENDENTE DE CONFERÊNCIA NA INTERFACE** |

## Ativação registrada

GitHub Pages foi ativado pelo titular do repositório. Os jobs `build` e `deploy` do workflow `pages build and deployment` concluíram com `success` na SHA `0ae29578a1ae83316b96b662c1a4b67c9027ca54` (run `36729196069`). A verificação HTTP anônima fora do GitHub e a inspeção visual em navegador real continuam pendentes por limitação do ambiente de consulta.

## Testes de aceitação após a ativação

- Abrir `https://viniciusvilaverd-22.github.io/GENTILL-RAST/` e confirmar resposta pública e capa integral.
- Abrir `https://viniciusvilaverd-22.github.io/GENTILL-RAST/en.html`, alternar PT/EN em ambas as direções.
- Abrir `https://viniciusvilaverd-22.github.io/GENTILL-RAST/gallery.html` e `gallery.en.html`; conferir as quatro capturas, legendas e alternância de idioma.
- Abrir links de Case Study, Threat Model e Engineering Decisions: devem mostrar o Markdown formatado no GitHub.
- Conferir layout e overflow em larguras de 360, 768 e 1440 px; teclado e texto alternativo.
- Conferir HTTPS, favicon, Social Preview e ausência de imagem truncada.
- Verificar CI da SHA publicada, sem presumir que CI substitui auditoria visual ou revisão de segurança.

## Limites

O RC1 refere-se exclusivamente à superfície pública de portfólio, não à homologação de produção do REST Gentill. Nenhum dado de HML, segredo, banco, agente ou runtime do produto é liberado por este gate.

## Correções após ativação

- Galeria inglesa independente (`docs/gallery.en.html`).
- Navegação PT/EN direcionada às galerias no idioma correto.
- Ajustes de teclado, redução de movimento e quebra de linhas no mobile.
- Sitemap com os quatro endereços HTML.
- Guard de links estendido a quatro páginas, sem liberar código privado.
