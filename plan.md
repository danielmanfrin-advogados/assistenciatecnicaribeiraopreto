# Plano de implementação — TUDOCON em Ribeirão Preto

## Escopo e decisões

Criar um site estático com 13 páginas reais em HTML, sem framework, sem dependências e sem conteúdo essencial gerado pelo JavaScript no navegador. Será um portal de contato para serviços de assistência técnica, com o nome TUDOCON, e não afirmará que o portal executa o serviço. O número provisório permanecerá em `config.js` para substituição posterior. O site não será publicado nesta tarefa.

- **Slug e origem canônica prevista:** `assistenciatecnicaribeiraopreto`; `https://assistenciatecnicaribeiraopreto.vercel.app` (fácil de trocar no README, sitemap e metadados se o domínio mudar).
- **Nome do portal:** TUDOCON em Ribeirão Preto.
- **Termo principal:** assistência técnica de ar-condicionado e eletrodomésticos.
- **Serviços/páginas:** `instalacao-manutencao-ar-condicionado`, `conserto-lavadoras-lava-e-seca` e `conserto-lava-loucas`.
- **Bairros/páginas:** Centro, Jardim Botânico, Nova Aliança, Vila Tibério, Bonfim Paulista e Campos Elíseos.
- **Paleta:** destaque `#5b21b6` (contraste calculado de 8,98:1 com branco); escura `#421883`; suaves `#f2edf9` e `#ded3f0`.
- **Build:** manter o `package.json` sem dependências, criar `build.js` com os recursos nativos de Node e saída `dist/`, e usar a configuração Vercel indicada no pedido para site estático.

## Design

- **Movimento:** interface orgânica de serviço local, inspirada diretamente na referência de imobiliária aprovada no pedido.
- **Princípios:** acolhedor sem exagero; conversão clara por WhatsApp/telefone; informação prática antes do contato; consistência e leitura fácil no celular.
- **Filosofia de cor:** violeta profundo para identificação e contraste, lilás pálido para pausas visuais, creme para leitura confortável; verde WhatsApp e grafite para telefone.
- **Layout:** barra branca flutuante, hero fotográfico arredondado, faixa de pedido rápido sobreposta, seções alternadas e CTAs arredondados.
- **Elementos de assinatura:** selos arredondados de atendimento local, cartões fotográficos com cantos amplos e faixa final violeta.
- **Interação/animação:** controles com área tátil mínima de 44 px, foco visível, navegação por âncoras, transições discretas e respeito a `prefers-reduced-motion`.
- **Tipografia:** Fira Sans (400–800) com fallback de sistema.
- **Essência/voz:** TUDOCON organiza pedidos locais de assistência técnica; direta, cuidadosa e prática. Exemplos: “Descreva o aparelho e o que aconteceu.” “Peça o orçamento pelo WhatsApp.”
- **Marca:** wordmark tipográfico TUDOCON com símbolo geométrico simples inspirado em ventilação/fluxo de ar; cor própria violeta `#5b21b6`.

## Arquitetura de arquivos

- `index.html`: home com hero, seletores de pedido, serviços, diferenciais, bairros e FAQ.
- `servicos/<slug>/index.html`: três páginas com pelo menos 250 palavras úteis cada.
- `bairros/<slug>/index.html`: seis páginas com pelo menos 150 palavras originais cada, sem inventar detalhes geográficos.
- `sobre/index.html`, `perguntas-frequentes/index.html`, `politica-de-privacidade/index.html`.
- `style.css`: estilos mobile-first compartilhados; `config.js`: marca, números, mensagem padrão e endpoint; `tracker.js`: lógica do anexo A.
- `img/`: `hero.jpg`, `sobre.jpg` e uma foto JPG individual para cada serviço.
- `apps-script/Code.gs`: cópia do anexo B; `favicon.svg`, `sitemap.xml`, `robots.txt`, `llms.txt`, `vercel.json`, `package.json`, `build.js` e `LEIA-ME.txt`.
- `/manus-routes.json`: manifesto das 13 rotas para o Preview.

Cada HTML conterá o próprio texto, um único H1, metadata específica, canonical e cartões sociais, breadcrumb quando interno, JSON-LD aplicável e links internos funcionais. Os botões manterão os atributos de rastreamento pedidos. A FAQ visível e o JSON-LD usarão as mesmas respostas. Textos e avisos seguirão as proibições do pedido; conteúdo de manutenção elétrica, refrigeração e segurança será cauteloso e recomendará confirmar as condições com o prestador.

## Fluxo de build e entrega

Servir as páginas diretamente no Preview para preservar as URLs em pastas. `npm run build` executará o script nativo que copia o site para `dist/`, e o `vercel.json` usará essa saída estática. Após a revisão do plano, preparar TODO, registrar diagnósticos, gerar as cinco imagens previstas, criar os arquivos e verificar conteúdo, SEO/JSON-LD, links, contagem das páginas, build e responsividade. Entregar o diretório do projeto, sem publicar o site.
