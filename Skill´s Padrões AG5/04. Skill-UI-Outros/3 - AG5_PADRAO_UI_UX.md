Preciso que você realize uma série de melhorias estruturais e de UX neste projeto, focando em um design premium/editorial. Siga estas diretrizes técnicas, usando as variáveis de cores e fontes já existentes no :root:



1. Menu Mobile (Drawer Premium)
Estrutura: Implemente um menu lateral (Drawer) que deslize da direita para a esquerda ao ser acionado no mobile.
Conteúdo: O menu deve conter o logotipo do projeto no topo, um botão de fechar ('X') e a lista de links de navegação.
Estética: Use uma tipografia com base o desing e layout do código atual. Os links devem ter um efeito visual ao passar o mouse (hover) e uma opacidade suave por padrão.
Comportamento: O menu deve travar o scroll da página ao abrir e fechar automaticamente ao clicar em um link.


2. Performance & SEO (Anti-CLS e LCP)

--- REGRA DE URL PADRÃO ---
O domínio canônico do site SEMPRE segue este padrão:
  http://www.[slug-empresa].ag5agencia.site

O slug é derivado do campo "alternateName" da empresa:
  - Tudo em minúsculas
  - Sem acentos (ã→a, é→e, ç→c, etc.)
  - Sem espaços (substituir por nada, não por hífen)
  - Exemplo: alternateName "Clínica Saúde" → slug "clinicasaude"
  - URL final: http://www.clinicasaude.ag5agencia.site

Use esta URL em: og:url, canonical e em qualquer link de compartilhamento (WhatsApp, etc.).

--- IMAGENS ---
Imagens: Conferir se tiver ou Adicionar atributos width e height em todas as tags <img> para evitar saltos de layout (CLS).

Preload Crítico: Identificar a imagem da Hero e as fontes principais e injetar <link rel="preload"> no head para turbinar o LCP (Largest Contentful Paint).

--- OG TAGS (COMPARTILHAMENTO) ---
Configurar ou revisar os seguintes metadados no <head>:

  <meta property="og:title" content="[Especialidade Principal] em [Bairro/Cidade] | [Nome da Empresa]">
  <meta property="og:description" content="[Copy persuasiva de 1–2 frases com benefício principal e CTA]">
  <meta property="og:url" content="http://www.[slug-empresa].ag5agencia.site">
  <meta property="og:image" content="http://www.[slug-empresa].ag5agencia.site/[caminho-da-imagem]">
  <meta property="og:image:width" content="1200">
  <meta property="og:image:height" content="630">
  <meta property="og:type" content="website">
  <link rel="canonical" href="http://www.[slug-empresa].ag5agencia.site">

Regra da og:image (prioridade de escolha):
  1. Imagem da seção Hero (primeira imagem de impacto da página)
  2. Se a Hero não tiver imagem de pessoa, usar a foto da seção "Sobre"
  3. A imagem escolhida DEVE continuar presente no corpo da página — nunca remover

A imagem deve ter no mínimo 1200x630px para funcionar no WhatsApp, Facebook e LinkedIn.
Se a imagem original for menor, usar a maior disponível e indicar para o cliente criar uma versão 1200x630px.

--- TITLE E SEO DE RANKING ---
Altere o <title> e og:title seguindo sempre este formato:
  [Especialidade/Categoria Principal] em [Bairro ou Cidade] | [Nome da Empresa]

Exemplos:
  "Advocacia Trabalhista em Moema | Dr. Carlos Silva"
  "Clínica de Fisioterapia no Centro | Saúde & Movimento"

--- FAVICON ---
Conferir se tiver ou garantir um favicon SVG de alta definição (ou fallback temático caso não haja logo isolada).
