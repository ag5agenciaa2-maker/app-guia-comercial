# SEO Rules — Páginas de Serviço Premium

> Regras técnicas não-negociáveis. Aplicar em TODAS as páginas geradas por esta Skill.

---

## 1. ESTRUTURA DE URL

```
✅ CORRETO
/servicos/divorcio-consensual-sao-paulo
/servicos/inventario-extrajudicial-campinas

❌ ERRADO
/servicos/servico1
/servicos/divórcio (acentos proibidos na URL)
/s/div (URLs curtas demais sem keyword)
```

**Regras:**
- Sempre em kebab-case (hifens, sem underscore)
- Sem acentos ou caracteres especiais
- Incluir cidade quando possível
- Máximo 5 segmentos de URL

---

## 2. META TAGS OBRIGATÓRIAS

Cada página de serviço DEVE ter:

```html
<!-- Title: 50-60 caracteres, keyword no início -->
<title>Advogado Divórcio Consensual em SP | [Nome Escritório]</title>

<!-- Description: 150-160 caracteres, incluir CTA -->
<meta name="description" content="Especialista em divórcio consensual em São Paulo. Processo rápido, online e sem desgaste. Fale agora com a Dra. Manoela Gil — OAB/SP 123.456.">

<!-- Canonical: URL exata da página -->
<link rel="canonical" href="https://www.site.com.br/servicos/divorcio-consensual-sao-paulo">

<!-- Open Graph (para compartilhamento) -->
<meta property="og:title" content="[mesmo do title]">
<meta property="og:description" content="[mesmo do description]">
<meta property="og:type" content="website">
<meta property="og:url" content="[URL canônica]">
<meta property="og:image" content="[URL de imagem 1200x630]">

<!-- Robots -->
<meta name="robots" content="index, follow">

<!-- Mobile -->
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

**Fórmula do Title:**
`[Keyword Principal] | [Nome do Escritório/Profissional]`

**Fórmula da Description:**
`[Benefício principal] em [cidade]. [Diferencial único]. [CTA com autoridade].`

---

## 3. HIERARQUIA DE HEADINGS

```html
<!-- UMA única H1 por página — contém a keyword principal -->
<h1>Advogado para Divórcio Consensual em São Paulo</h1>

<!-- H2 para seções principais -->
<h2>O que é o Divórcio Consensual?</h2>
<h2>Quando Você Precisa de um Advogado?</h2>
<h2>Como Funciona Nosso Processo</h2>
<h2>Perguntas Frequentes sobre Divórcio</h2>

<!-- H3 para subseções -->
<h3>Etapa 1: Consulta Inicial</h3>
<h3>Etapa 2: Documentação</h3>
```

**Regras:**
- H1: exatamente 1 por página, contém keyword
- Nunca pular nível (H1 → H3 sem H2 é proibido)
- Keywords secundárias nos H2
- H1 deve aparecer nos primeiros 200px visíveis da tela

---

## 4. KEYWORD DENSITY E PLACEMENT

**Posições obrigatórias da keyword principal:**
- [ ] `<title>`
- [ ] `<h1>` (exata ou variação natural)
- [ ] Primeiros 100 words do conteúdo
- [ ] Pelo menos 1 `<h2>`
- [ ] Meta description
- [ ] Alt de pelo menos 1 imagem
- [ ] URL da página

**Densidade ideal:** 1-2% do texto total (não forçar, soar natural)

**Variações semânticas (LSI) a incluir:**
- Sinônimos do serviço
- Perguntas relacionadas ("como funciona", "quanto custa", "quando preciso")
- Localização (bairro, região, além de cidade)

---

## 5. CONTEÚDO MÍNIMO POR PÁGINA

Cada página de serviço deve ter:

| Elemento | Mínimo | Recomendado |
|----------|--------|-------------|
| Palavras totais | 600 | 1000-1500 |
| Perguntas FAQ | 5 | 8-10 |
| Parágrafos de texto | 4 | 6-8 |
| Imagens com alt | 1 | 2-3 |
| Links internos | 2 | 3-5 |
| CTA para WhatsApp | 2 | 3 (topo, meio, fim) |

---

## 6. LINKS INTERNOS OBRIGATÓRIOS

Em cada página de serviço, incluir:

```html
<!-- Link para hub de serviços -->
<a href="/servicos">Ver todos os serviços</a>

<!-- Breadcrumb (aparece no topo, abaixo do nav) -->
<nav aria-label="breadcrumb">
  <a href="/">Início</a> /
  <a href="/servicos">Serviços</a> /
  <span>Divórcio Consensual</span>
</nav>

<!-- Links para 2-3 serviços relacionados no final -->
<a href="/servicos/divorcio-litigioso">Divórcio Litigioso</a>
<a href="/servicos/guarda-de-filhos">Guarda de Filhos</a>
```

---

## 7. IMAGENS

```html
<!-- Alt descritivo com keyword -->
<img
  src="/assets/divorcio-consensual-advogada-sp.jpg"
  alt="Advogada especialista em divórcio consensual em São Paulo"
  width="800"
  height="500"
  loading="lazy"
>

<!-- Hero image: loading="eager" (não lazy) -->
<img
  src="/assets/hero-servico.jpg"
  alt="[keyword principal]"
  loading="eager"
  fetchpriority="high"
>
```

**Regras:**
- Alt sempre descritivo, nunca vazio ou "imagem1.jpg"
- Hero image: `loading="eager"` e `fetchpriority="high"` (impacto no LCP)
- Outras imagens: `loading="lazy"`
- Sempre definir `width` e `height` (evita CLS)
- Formato WebP quando possível

---

## 8. PERFORMANCE (Core Web Vitals)

Metas obrigatórias:

| Métrica | Meta | Como Garantir |
|---------|------|---------------|
| LCP | < 2.5s | Hero image com `fetchpriority="high"`, sem JS bloqueante |
| CLS | < 0.1 | Definir width/height em imagens, fontes com `font-display: swap` |
| INP | < 200ms | Evitar JS pesado no clique de CTA |

**Fontes Google Fonts:**
```html
<!-- Preconnect obrigatório -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
<!-- font-display: swap via parâmetro &display=swap -->
<link href="https://fonts.googleapis.com/css2?family=Cormorant+Garamond:wght@400;600&display=swap" rel="stylesheet">
```

---

## 9. SINAIS E-E-A-T (Google Trust)

Para segmentos YMYL (saúde, direito, finanças), estes elementos são críticos:

```html
<!-- Credenciais do profissional visíveis na página -->
<p class="credencial">Dra. Manoela Gil — OAB/SP 123.456</p>
<p class="experiencia">12 anos de experiência em Direito de Família</p>

<!-- Data de atualização do conteúdo -->
<time datetime="2026-03">Atualizado em março de 2026</time>

<!-- Endereço físico visível -->
<address>Rua das Flores, 123 — Pinheiros, São Paulo/SP</address>
```

---

## 10. SITEMAP E ROBOTS

Após criar todas as páginas, adicionar ao `sitemap.xml`:

```xml
<url>
  <loc>https://www.site.com.br/servicos/divorcio-consensual-sao-paulo</loc>
  <lastmod>2026-03-24</lastmod>
  <changefreq>monthly</changefreq>
  <priority>0.8</priority>
</url>
```

`robots.txt` deve permitir indexação:
```
User-agent: *
Allow: /
Sitemap: https://www.site.com.br/sitemap.xml
```
