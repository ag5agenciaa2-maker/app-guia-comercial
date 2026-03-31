---
name: Links360-Recepcao-Planejamento
description: Módulo de recepção de briefing, varredura de assets, análise de perfil expandido e planejamento da construção do Links 360. Cobre os Passos 0, 1, 1B, 2, 3 e 4A.
type: project
---

# MÓDULO 01 — RECEPÇÃO E PLANEJAMENTO

> Carregar este módulo ao iniciar um novo projeto Links 360.
> Cobre: Passo 0 (conformidade), Passo 1 (briefing), Passo 1B (assets), Passo 2 (análise), Passo 3 (mapa) e Passo 4A (design system).

---

## ⚠️ PASSO 0 — CONFORMIDADE ÉTICA E REGULATÓRIA POR NICHO

> **Executar SEMPRE, antes de qualquer construção.** Identificar o nicho e aplicar as restrições correspondentes em todo o projeto.

### Nichos com Regulação Específica

#### ⚖️ ADVOCACIA / DIREITO (OAB — Código de Ética e Disciplina)

**PROIBIDO usar:**
- Termos de resultado garantido: "garantimos", "sua vitória", "vamos vencer", "sucesso garantido"
- Comparação com outros advogados ou escritórios
- Elogios excessivos: "melhor advogado", "o #1 do Brasil"
- Desconto ou tabela de preços exibida publicamente
- CTA agressivo: "Ligue agora!", "Agende já!" (evitar ton urgente)
- Imagens de tribunais, algemas, processos como elemento de marketing
- Depoimentos de clientes com nomes e casos reais sem autorização expressa

**PERMITIDO usar:**
- Áreas de atuação (ex: "Atua em Direito Trabalhista e Previdenciário")
- Informações objetivas: formação, OAB, pós-graduação
- CTA discreto: "Agende uma consulta", "Fale conosco", "Entenda seu direito"
- Status Badge: "Consultas Disponíveis" (sem urgência artificial)

**Ajustes obrigatórios na construção:**
- ❌ **NÃO usar badge vermelho** (`.whatsapp-notify`) no botão flutuante do WhatsApp
- ❌ NÃO usar CTA "Agendar Agora" — trocar por "Falar com Assessoria" ou "Entrar em Contato"
- ❌ NÃO usar efeito `pulse-custom-slow` exagerado no botão WhatsApp
- ✅ Usar tom sério e profissional em todos os textos

---

#### 🦷 ODONTOLOGIA / DENTISTA (CFO — Res. 196/2019)

**PROIBIDO usar:**
- Promessas de sorriso perfeito ou resultado específico: "dentes perfeitos garantidos"
- Antes/Depois com identificação do paciente sem autorização
- Preglões de preço: "faceta a partir de R$X"
- "O melhor dentista", "rápido e barato"
- Depoimentos com nome completo sem consentimento formal
- Comparações com outros profissionais

**PERMITIDO usar:**
- Especialidades: "Especialista em Implantodontia", "Ortodontia"
- CTA: "Agendar Avaliação Gratuita", "Marque sua Consulta"
- Galeria de resultados com imagens aprovadas pelo CFO (sem identificação do paciente)
- Informações de formação e título de especialista

**Ajustes obrigatórios na construção:**
- ❌ **NÃO usar badge vermelho** (`.whatsapp-notify`) no botão flutuante do WhatsApp
- ❌ NÃO exibir antes/depois com identificação do paciente
- ✅ Imagens de resultados devem usar legenda genérica (ex: "Resultado clínico")

---

#### 🧬 MEDICINA / SAÚDE (CFM — Res. 2.336/2023)

**PROIBIDO usar:**
- Garantia de cura ou resultados: "tratamento definitivo", "cura garantida"
- Preglões comerciais: preços, descontos públicos
- "o melhor médico", rankings, comparações
- Depoimentos que vinculem resultado ao médico

**PERMITIDO usar:**
- Especialidade registrada no CRM
- Informações educativas sobre procedimentos
- CTA: "Agendar Consulta", "Solicitar Informações"

**Ajustes obrigatórios na construção:**
- ❌ **NÃO usar badge vermelho** (`.whatsapp-notify`) no botão flutuante do WhatsApp
- ❌ NÃO usar linguagem de promessa de resultado
- ✅ Nomenclatura de procedimentos conforme denominado pelo CFM

---

### Nichos Livres (sem restrições especiais)

Automotivo, Gastronomia, Fitness, Imobiliária, Beleza/Estética (exceto Biomedicina/Enfermagem que seguem CFM/COFEN), Pets, Educação, Serviços Gerais.

> Para nichos livres: CTAs agressivos, pulsantes e badge vermelho do WhatsApp estão liberados.

---

### Tabela de Decisão: Badge Vermelho do WhatsApp (`.whatsapp-notify`)

| Nicho | Badge Vermelho | Motivo |
|-------|---------------|--------|
| Advocacia / OAB | ❌ **REMOVER** | Aparência comercial agressiva viola ética da OAB |
| Odontologia / CFO | ❌ **REMOVER** | Vedado por resolução do CFO |
| Medicina / CFM | ❌ **REMOVER** | Aparência mercantil vedada pelo CFM |
| Fisioterapia / COFFITO | ❌ **REMOVER** | Mesmo princípio dos conselhos de saúde |
| Biomedicina / CFBM | ❌ **REMOVER** | Idem |
| Todos os outros nichos | ✅ Manter | Livre uso |

**Como remover o badge no HTML (nichos restritos):**
```html
<!-- WhatsApp Float SEM badge (nichos regulados) -->
<a href="https://wa.me/55[TEL]" target="_blank" class="whatsapp-float reveal">
    <i class="fa-brands fa-whatsapp"></i>
    <!-- NÃO incluir o <span class="whatsapp-notify"> -->
</a>
```

**Como remover o badge no CSS (adicionar ao style.css de nichos restritos):**
```css
/* Badge de notificação removido por conformidade ética */
/* .whatsapp-notify { display: none; } */
```

---

## 📥 PASSO 1 — RECEBIMENTO DE BRIEFING

### Como o agente receberá as informações

O agente deve aceitar qualquer um dos seguintes formatos de entrada:

| Formato | Como processar | Asset Scan? |
|---------|----------------|-------------|
| **Texto no chat** | Extrair diretamente | ❌ Não se aplica |
| **Arquivo TXT/PDF** | Ler e extrair os dados | ❌ Não se aplica |
| **HTML de um site existente (colado no chat)** | Parsear e extrair dados + listar imagens referenciadas | ⚠️ Listar assets referenciados no HTML |
| **Caminho de pasta com código HTML/CSS/JS** | Ler arquivos, extrair dados E **copiar assets automaticamente** | ✅ EXECUTAR PASSO 1B |
| **URL de site público** | Solicitar o caminho da pasta local onde está o site | ⚠️ Redirecionar para pasta |

> ⚡ **Se receber um caminho de pasta: execute o PASSO 1B (Varredura de Assets) ANTES de qualquer outra coisa.**

### Tabela de extração de dados (preencha com o que receber)

```
DADOS DO NEGÓCIO:
- Nome da empresa/profissional:
- Segmento/nicho:
- Cidade e estado:
- Endereço completo:
- Telefone/WhatsApp (com DDI):
- Site oficial (URL):
- Instagram (@):
- Outras redes sociais:
- Horário de funcionamento:
- Fundação/anos de mercado:
- Descrição/slogan:
- Diferenciais (mín. 4):
- Serviços oferecidos:
- Google Meu Negócio (Place ID para avaliações):
- Link Google Maps (embed):
- Link Google Maps (direções GPS):
- Avaliações do Google (nome + texto):
- Imagens disponíveis (sim/não, lista):
- Vídeos disponíveis (sim/não):
- Tour 360° (link iframe, se houver):
- Paleta de cores da marca (hex):
- Estilo visual (dark/light/mixed):
- Música de fundo (MP3, se houver):
```

> **🧠 Análise de Perfil:** Ao receber o briefing, vá além dos campos padrão. Leia as entrelinhas. Se o cliente mencionou algo que pode virar uma seção diferenciadora (cargo, prêmio, publicação, etc.), anote para propor no Passo 2.

### Ao receber o briefing, o agente deve:

1. **Se for pasta:** Executar o PASSO 1B (varredura de assets) imediatamente
2. Preencher a tabela acima com os dados extraídos dos arquivos
3. Identificar quais itens estão **ausentes**
4. Apresentar um **RESUMO DO QUE TEM vs O QUE FALTA** (incluindo lista de assets encontrados e copiados)
5. **Perguntar os itens ausentes críticos** antes de prosseguir (WhatsApp, nome, cores)
6. Identificar seções extras que podem ser aplicadas ao negócio
7. Aguardar confirmação para iniciar a construção

---

## 🗂️ PASSO 1B — VARREDURA E CÓPIA AUTOMÁTICA DE ASSETS

> **Executar SOMENTE quando receber um caminho de pasta com o site de origem.**
> O objetivo é poupar o criador de copiar manualmente cada arquivo.

### Etapa 1 — Mapear a estrutura da pasta de origem

```
Pasta recebida: [CAMINHO_DA_PASTA]
```

O agente deve listar todos os subdiretórios e identificar:
- Onde estão as imagens (ex: `/assets/`, `/images/`, `/img/`, `/fotos/`, raiz)
- Onde estão os vídeos (ex: `/assets/`, `/videos/`, `/media/`)
- Onde está o logo (ex: logo.png, logo.webp, logo.svg, logomark.*)
- Onde está o favicon (ex: favicon.ico, favicon.png, *.ico)
- Onde está a música de fundo (ex: music.mp3, background.mp3)
- O arquivo HTML principal (index.html)

### Etapa 2 — Tipos de arquivo a copiar

| Tipo | Extensões detectadas | Destino no projeto |
|------|---------------------|--------------------|
| **Imagens** | `.webp`, `.jpg`, `.jpeg`, `.png`, `.gif`, `.avif`, `.svg` | `assets/` |
| **Vídeos** | `.mp4`, `.webm`, `.mov` | `assets/` |
| **Áudio** | `.mp3`, `.ogg`, `.wav` | `assets/` |
| **Logo** | Qualquer imagem com "logo" no nome | `assets/` (renomear para `logo.[ext]`) |
| **Favicon** | `.ico`, ou imagem com "favicon" no nome | `assets/favicon.ico` |
| **Outros ícones** | Imagens com "icon", "apple-touch" no nome | `assets/` |

### Etapa 3 — Regras de cópia e renomeação

1. **Copie TODOS os arquivos de mídia** encontrados na pasta de origem para `[projeto]/assets/`
2. **NÃO altere** arquivos que já têm nomes SEO adequados (kebab-case descritivo com mais de 15 chars)
3. **RENOMEIE** arquivos com nomes ruins (ex: `IMG_2045.jpg`, `foto1.png`, `DSC_0012.webp`) seguindo o padrão:
   ```
   [nome-empresa]-[descrição-do-conteúdo]-[sequência].[ext]
   Exemplo: vasques-auto-center-oficina-mecanica-bangu-01.webp
   ```
4. **Logo:** Copiar e nomear como `logo.[ext]` (manter extensão original)
5. **Favicon:** Copiar e nomear como `favicon.ico` (converter se necessário via HTML `<link>`)
6. **Música:** Copiar e nomear como `music.mp3`

### Etapa 4 — Extrair dados do HTML de origem

Ao ler o `index.html` da pasta, extrair automaticamente:

- **Nome do negócio:** `<title>`, `<h1>`, `og:title`, Schema `name`
- **Descrição:** `<meta name="description">`, Schema `description`
- **Telefone/WhatsApp:** links `href="tel:"`, `href="wa.me/"`, Schema `telephone`
- **Endereço:** Schema `address`, footer, seção de contato
- **Horários:** Schema `openingHoursSpecification`, table/list de horários
- **Redes sociais:** links com instagram.com, facebook.com, tiktok.com, etc.
- **Site oficial:** `<link rel="canonical">`, Schema `url`
- **Google Maps embed:** `<iframe src="google.com/maps/embed">`
- **Google Maps directions:** links href com `google.com/maps/dir`
- **Place ID do Google:** links `search.google.com/local/writereview?placeid=`
- **Paleta de cores:** variáveis CSS `--brand-main`, `--brand-hover`, etc. no `:root`
- **Fontes:** `@import` ou `<link>` do Google Fonts
- **Serviços:** seções com cards, listas de serviços, h2/h3 de serviços
- **Avaliações:** seções com depoimentos/reviews
- **Diferenciais:** seções com ícones + textos de diferenciais
- **Tour 360°:** iframes com tour virtual

### Etapa 5 — Relatório de assets encontrados

Após a varredura, apresentar o seguinte relatório ANTES de prosseguir:

```
📁 VARREDURA CONCLUÍDA — [NOME DA EMPRESA]
==========================================

✅ ASSETS COPIADOS PARA assets/:
  🖼️ Imagens: [N] arquivo(s)
     - nome-arquivo-01.webp → [descrição do uso]
     - nome-arquivo-02.webp → [descrição do uso]
     ...
  🎬 Vídeos: [N] arquivo(s)
     - video-01.mp4 → [título/label]
     ...
  🎵 Áudio: [Sim/Não]
     - music.mp3
  🔖 Logo: [nome-do-arquivo]
  🏷️ Favicon: [nome-do-arquivo]

📊 DADOS EXTRAÍDOS DO HTML:
  Nome: [NOME]
  Telefone: [TEL]
  WhatsApp: [TEL]
  Instagram: [@handle]
  Site: [URL]
  Paleta de cores: [HEX principais]
  Fontes: [nomes]

⚠️ ITENS NÃO ENCONTRADOS (precisam ser fornecidos):
  - [lista de dados ausentes]
  - [lista de imagens mencionadas no HTML mas não encontradas na pasta]

❓ IMAGENS SEM CONTEXTO (precisam de label para usar corretamente):
  - [arquivo] → Para qual seção seria usado?
```

### Etapa 6 — Identificar o logo para o Hero

- Procurar imagem usada no `<header>` ou `<nav>` com class contendo "logo"
- Ou imagem referenciada com alt contendo o nome da empresa
- Copiar para `assets/logo.[ext]`
- Usar essa imagem no Hero do Links 360
- Se for PNG transparente: manter transparência (não converter para JPG)
- Se for SVG: copiar como SVG e referenciar no HTML

### Etapa 7 — Identificar imagens por seção (automático)

Ao ler o HTML, tentar associar cada imagem ao seu contexto de uso:

| Tag/Classe no HTML origem | Uso provável no Links 360 |
|--------------------------|---------------------------|
| Imagem em `<header>`, class `logo` | Logo do Hero |
| Imagens em seção com "servic" | Cards de Serviços |
| Imagens em seção com "galeria", "fotos", "gallery" | Galeria de Fotos |
| Imagens com "antes", "depois", "before", "after" | Seção Antes/Depois |
| Imagens em seção com "sobre", "história", "about" | Card da seção Sobre |
| Vídeos em `<video>` com label visível | Galeria de Vídeos |
| Imagem do `og:image` | Capa para SEO (OG image) |

---

## 🔍 PASSO 2 — ANÁLISE E RECOMENDAÇÕES DE SEÇÕES

Após receber os dados, o agente deve apresentar uma lista de **seções recomendadas** baseada nas informações do cliente.

> ⚠️ **REGRA DE OURO:** A estrutura de seções do **Vasquez Auto Center** é o padrão OBRIGATÓRIO (skeleton). O DNA de outros projetos (como Tatiane Gomes) deve ser usado apenas para ESTILO (cores, fontes, refinamento), nunca para remover seções estruturais.

### Seções do Padrão Base OBRIGATÓRIO (Vasquez Auto Center)

| # | Seção | Quando usar |
|---|-------|-------------|
| 1 | **Ticker de boas-vindas** | Sempre |
| 2 | **Hero com logo/foto + badge online** | Sempre |
| 3 | **CTA WhatsApp principal** (pulsante) | Sempre |
| 4 | **Grid de contato rápido** (Ligar + Salvar Contato vCard) | Sempre |
| 5 | **Botões de links secundários** (site, Google, Instagram...) | Conforme os links disponíveis |
| 6 | **Galeria de vídeos** (carrossel horizontal) | Se houver vídeos |
| 7 | **Diferenciais** (grid 2x2 com ícones) | Sempre |
| 8 | **Antes e Depois** (slider interativo) | Se houver imagens de antes/depois |
| 9 | **Avaliações Google** (scroll automático infinito) | Se houver avaliações |
| 10 | **Botão Avaliar no Google** | Se houver Place ID |
| 11 | **Serviços com Cards e Modais** (grid 2x2 + detalhe em popup) | Se houver serviços para detalhar |
| 12 | **Botão CTA extra** (outros serviços via WhatsApp) | Se houver muitos serviços |
| 13 | **Seção Sobre / História** (com stats) | Sempre que houver história |
| 14 | **Galeria de fotos** (carrossel com zoom) | Se houver fotos |
| 15 | **Localização** (mapa embed + horários + botão GPS) | Se tiver endereço físico |
| 16 | **Footer** (social icons + copyright + AG5) | Sempre |
| 17 | **WhatsApp Flutuante** | Sempre |
| 18 | **Modais de Serviço** (um por serviço) | Se tiver seção de serviços |
| 19 | **Modal Tour 360°** | Se tiver tour virtual |
| 20 | **Modal Preview de Imagem** (lightbox) | Se tiver galeria |

### Seções Extras Opcionais (detectadas por nicho)

O agente deve **identificar e propor** seções extras com base nas informações recebidas:

- 📚 **E-book/Lead Magnet** — Se a empresa tiver material para download
- 🗓️ **Agendamento Online** — Se houver plataforma de agendamento (Cal.com, Google Agenda, etc.)
- 📹 **Reels/TikTok em destaque** — Se for profissional com conteúdo viral
- 🎓 **Mentoria/Cursos** — Se for especialista que também ensina
- 🛍️ **Cardápio/Catálogo** — Se for restaurante, loja, etc.
- 📍 **Múltiplas Localidades** — Se atender em mais de um endereço
- 🏆 **Prêmios/Certificações** — Se houver credenciais para exibir
- 💬 **Threads/TikTok/YouTube** — Redes adicionais além de Instagram

> **Como propor:** Apresente ao usuário dizendo: "Encontrei X informação que indica possibilidade de seção Y. Deseja incluir? Sim/Não."

---

## 🔍 ANÁLISE DE PERFIL EXPANDIDO — SEÇÕES ÚNICAS POR CLIENTE

O agente deve ir além do briefing padrão e analisar o perfil completo do cliente em busca de diferenciais que justifiquem seções únicas e exclusivas. O objetivo é dar corpo e relevância máxima ao Links 360 de cada cliente.

**Elementos que indicam seções extras:**

| Elemento identificado | Seção sugerida |
|----------------------|----------------|
| Cargo em conselho/ordem profissional (ex: presidente OAB, diretor de CRM) | "Cargos e Representatividade" |
| Membro de comissão(ões) | "Comissões e Atuação" |
| Livros publicados / artigos / publicações | "Publicações" |
| Prêmios, reconhecimentos, certificações de destaque | "Prêmios e Reconhecimentos" |
| Aparições em mídia (TV, rádio, podcasts, jornais) | "Na Mídia" |
| Eventos, palestras, workshops que ministra | "Agenda / Eventos" |
| Conteúdo educativo (reels virais, canal YouTube, TikTok relevante) | "Conteúdo em Destaque" |
| E-book, material gratuito para download | "Lead Magnet / E-book" |
| Agendamento online disponível | "Agendamento Online" |
| Múltiplas unidades / franquias | "Nossas Unidades" |
| Cardápio / catálogo de produtos | "Cardápio / Catálogo" |
| Parcerias com marcas conhecidas | "Parceiros e Marcas" |

**Como o agente deve propor:**
- Para cada elemento encontrado: pausar e perguntar antes de incluir no mapa
- Formato da pergunta: `"💡 Encontrei que [cliente] [elemento]. Isso justifica uma seção '[nome]'. Deseja incluir? Isso vai diferenciar bastante o projeto."`
- O agente pode e deve sugerir seções que não estão listadas acima se encontrar algo relevante e único
- **Regra:** nunca inventar dados para preencher uma seção sugerida — se confirmada, solicitar as informações específicas antes de construir

---

## 🏗️ PASSO 3 — MAPA DE CONSTRUÇÃO

Com base nas seções confirmadas pelo usuário, criar um **MAPA DE CONSTRUÇÃO** assim:

```
PLANO DE CONSTRUÇÃO — [NOME DA EMPRESA]
=====================================
FASE 1: Head + Ticker + Hero
FASE 2: CTAs (WhatsApp + Contatos rápidos + Links Secundários)
FASE 3: Galeria de Vídeos + Diferenciais
FASE 4: Antes/Depois + Avaliações
FASE 5: Serviços + Botão CTA Extra
FASE 6: Sobre/História + Galeria de Fotos
FASE 7: Localização + Footer + Scripts
FASE 8: Modais (um bloco por modal)
FASE 9: CSS completo (style.css)
```

Apresentar o mapa e aguardar confirmação para iniciar.

> Após confirmação, carregar o módulo `02-construcao-A.md` para iniciar a construção.

---

## 🎨 PASSO 4A — DESIGN SYSTEM DO PROJETO

Antes de iniciar o HTML, definir o design system:

### Decisão de Estética por Nicho

| Nicho | Estética Recomendada | Paleta Típica |
|-------|---------------------|---------------|
| Automotivo | Dark mode, industrial, fogo/energia | Laranja, preto, branco |
| Estética/Beleza | Light mode, suave, elegante | Rose gold, bege, cream |
| Gastronomia | Warm dark ou editorial | Âmbar, marrom, creme |
| Jurídico/Advocacia | Editorial sóbrio, authority | Dourado, preto, branco/creme |
| Saúde/Médico | Clean light, confiança | Azul, verde, branco |
| Fitness | Dark energético | Neon, preto, cinza |
| Imobiliária | Premium dark | Dourado, granito, branco |

### Definição do Design System (preencher por projeto):

```css
/* DEFINIÇÃO ANTES DE ESCREVER QUALQUER CÓDIGO */
:root {
    --brand-main: [COR PRIMÁRIA];       /* Cor de destaque */
    --brand-hover: [COR SECUNDÁRIA];    /* Hover/gradiente */
    --brand-accent: [COR DE FUNDO CARD];
    --brand-dark: [COR DO TEXTO PRINCIPAL];
    --brand-gray: [COR DO TEXTO SECUNDÁRIO];
    --brand-light: [COR DO FUNDO GERAL];
}

/* TIPOGRAFIA */
/* Font-Serif (títulos): [FONTE ESCOLHIDA] */
/* Font-Sans  (corpo):   [FONTE ESCOLHIDA] */
```

**Combinações de fontes por nicho:**
- Automotivo: Oswald (títulos) + Inter (corpo)
- Estética/Beleza: Playfair Display (títulos) + Inter (corpo)
- Gastronomia: Cormorant Garamond (títulos) + Outfit (corpo)
- Jurídico: Cormorant Garamond (títulos) + Inter (corpo)
- Saúde: Playfair Display (títulos) + Inter (corpo)
- Fitness: Oswald (títulos) + Inter (corpo)

> Design System definido? Carregar `02-construcao-A.md` e iniciar a Fase 1.

---

*Módulo 01 — AG5 Agência | Links 360 Premium*
