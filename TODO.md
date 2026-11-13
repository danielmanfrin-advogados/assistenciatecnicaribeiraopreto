# TODO — TUDOCON em Ribeirão Preto

## 1. Conteúdo e páginas estáticas
- [x] Entregar 13 páginas: `index.html`; três páginas em `servicos/<slug>/index.html`; seis páginas em `bairros/<slug>/index.html` para Centro, Jardim Botânico, Nova Aliança, Vila Tibério, Bonfim Paulista e Campos Elíseos; `sobre/index.html`; `perguntas-frequentes/index.html`; e `politica-de-privacidade/index.html`.
- [x] Usar HTML, CSS e JavaScript puros, sem React, Vite, framework ou dependência; cada página deve existir como HTML real com o conteúdo já presente no HTML, sem depender de JavaScript para renderizar o texto.
- [x] Na inicial, apresentar hero com selo de atendimento, H1 e subtítulo do nicho, botões de WhatsApp e telefone, seleção de bairro/região e serviço, introdução em duas colunas com passos, três cards de serviço, quatro diferenciais, links de bairros, FAQ em `details/summary`, CTA e rodapé.
- [x] Cada página de serviço deve ter breadcrumb, H1, foto, descrição, botões, no mínimo 250 palavras úteis e exclusivas, quando o serviço é indicado, dados para o atendimento, como pedir, 2–3 dúvidas próprias, links de bairros e de outros serviços, e CTA final.
- [x] Cada página de bairro deve ter breadcrumb, H1 com nome do serviço e do bairro, pelo menos 150 palavras originais, exemplos e situações variáveis sem inventar fatos geográficos, links para serviços e outros bairros, e CTA final.
- [x] A página Sobre, a página completa de perguntas frequentes com as perguntas do nicho e a página de privacidade devem existir; todas as páginas devem ter botões de contato no topo, no conteúdo e na faixa final.

## 2. SEO, GEO e conteúdo correto
- [x] Cada HTML terá `lang="pt-BR"`, viewport, theme-color, favicon, index/follow, um único H1, título de até 60 caracteres, description de 120–155 caracteres, canonical absoluto, Open Graph, Twitter Card e hierarquia lógica de headings.
- [x] Manter `/sitemap.xml` com as 13 URLs, lastmod da data de entrega, prioridades 1.0/0.8/0.6 conforme inicial/serviços/demais; `/robots.txt` liberando rastreamento e apontando sitemap; e `/llms.txt` com resumo, serviços, bairros, institucionais e todas as perguntas e respostas.
- [x] Incluir links internos descritivos, breadcrumb com `BreadcrumbList` nas internas, `WebSite` na inicial, `Service` nas páginas de serviço e bairro, e `FAQPage` na inicial e FAQ. A FAQ no JSON-LD deve corresponder literalmente às respostas do HTML.
- [x] Entregar respostas diretas e factuais, conteúdo original por rota e termos consistentes. Não inventar endereço, CNPJ, história, avaliações, leis, normas, disponibilidade ou dados de bairro; evitar promessas de preço, desconto, prazo, atendimento 24 h, garantia, certificação ou avaliações.
- [x] Exibir em todas as páginas o aviso obrigatório: “Este site é um portal de contato e não presta o serviço diretamente. O atendimento é feito por prestadores parceiros da região. Valores, prazos e formas de pagamento são informados pelo prestador no atendimento.” Redigir na terceira pessoa, em português brasileiro simples, sem travessões.

## 3. Contato, seleção rápida e registro
- [x] Criar `config.js` com site, nicho, números provisórios, mensagem padrão, cidade e endpoint Apps Script; comentários devem explicar como trocar os números sem alterar as páginas.
- [x] Copiar o Anexo A para `tracker.js` sem alterar sua lógica. O script configura os links WhatsApp/telefone, a seleção rápida, o identificador de sessão e o registro com fetch `no-cors`, `keepalive` e alternativa `new Image()`.
- [x] Os cliques devem enviar `site`, `nicho`, `acao`, `local`, `pagina`, `titulo`, `origem`, UTMs, gclid apenas como “sim” quando presente, dispositivo, tela, idioma, detalhe/mensagem e sessão aleatória ao endpoint fornecido.
- [x] Cada WhatsApp deve ter `data-acao="whatsapp"`, `data-local` de localização e `data-msg`; cada telefone deve ter `data-acao="ligar"` e `data-local`. Hrefs iniciais devem usar o número provisório `5516900000000` e ser substituídos por `config.js`.
- [x] A busca rápida deve oferecer os seis bairros, “Ribeirão Preto (qualquer bairro)” e “Região de Ribeirão Preto”, os três serviços, e construir a mensagem correspondente às escolhas.
- [x] Não solicitar nem registrar nome, e-mail, CPF ou outro dado pessoal, e não usar cookies de publicidade.

## 4. Design, acessibilidade e imagens
- [x] Implementar a referência visual aprovada: barra branca flutuante; hero fotográfico arredondado e escurecido; busca rápida sobreposta; seções alternando creme e tons suaves; cards com cantos amplos; botões em pílula; rodapé escuro e barra fixa de contato em telas menores que 760 px.
- [x] Usar Fira Sans com fallback, paleta do plano e botões de WhatsApp verde `#157a3e`/hover `#0f5f30`, telefone `#1f2937`; assegurar contraste AA, foco visível, alvos táteis de pelo menos 44 px e suporte a `prefers-reduced-motion`.
- [x] Gerar `img/hero.jpg` (16:9) e `img/sobre.jpg` mais uma foto 4:3 por serviço. Fotos realistas, cotidianas e sem texto, logotipos, marcas, placas legíveis ou rostos em destaque; comprimir imagens para cerca de 150 KB ou menos, incluir `alt` neutro, `width`, `height` e lazy loading fora da primeira dobra.
- [x] Criar `favicon.svg`; não afirmar que as imagens ilustrativas retratam empresa, equipe, veículo ou prestador.

## 5. Privacidade e planilha
- [x] Criar `politica-de-privacidade/index.html` explicando quais eventos de clique e metadados são registrados, finalidade, ausência de dados pessoais e de cookies de publicidade, tratamento separado pelo prestador/WhatsApp, direitos LGPD e data de atualização.
- [x] Criar `apps-script/Code.gs` com o código do Anexo B sem alterações e documentar setup, atualização de implantação existente e relatório por site conforme o pedido.

## 6. Vercel, documentação e entrega
- [x] Criar `package.json` sem `dependencies` nem `devDependencies`, com o nome do site e `build: node build.js`; criar `build.js` com recursos nativos do Node para copiar a raiz a `dist/`; criar `vercel.json` com buildCommand `npm run build`, outputDirectory `dist`, `cleanUrls: true` e `trailingSlash: true`.
- [x] Manter HTML, CSS, JS, imagens e documentos na raiz, criar `/manus-routes.json` com todas as rotas e usar caminhos absolutos de site iniciados com `/` para os assets e links.
- [x] Criar `LEIA-ME.txt` explicando como trocar telefones, atualizar Apps Script (Extensões > Apps Script, colar `Code.gs`, `setup()` uma vez, editar implantação existente para Nova versão e acesso “Qualquer pessoa”), importar no GitHub/Vercel sem build de framework, cadastrar no Search Console/enviar sitemap, substituir fotos pelos mesmos nomes e criar Perfil da Empresa no Google somente quando houver prestador com endereço real.
- [x] Entregar o projeto pronto para repositório GitHub e importação Vercel (Framework Preset Other); não publicar o site nesta tarefa.
