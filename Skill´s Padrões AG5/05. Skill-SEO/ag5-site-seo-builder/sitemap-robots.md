# Sitemap & Robots.txt — Indexação das Páginas

> Estas duas tarefas são obrigatórias ao final da Fase 4.
> Sem sitemap atualizado, o Google pode demorar semanas para encontrar as novas páginas.
> Com sitemap, o Google descobre em horas.

---

## SITEMAP.XML

### Lógica de geração

O agente deve verificar se já existe um `sitemap.xml` na raiz do projeto:

**SE EXISTIR:** Adicionar os novos URLs ao arquivo existente (não substituir).
**SE NÃO EXISTIR:** Criar do zero com todos os URLs do projeto.

---

### Estrutura completa do sitemap.xml

```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="https://www.sitemaps.org/schemas/sitemap/0.9">

  <!-- Página principal -->
  <url>
    <loc>https://[DOMINIO]/</loc>
    <lastmod>[DATA-HOJE]</lastmod>
    <changefreq>monthly</changefreq>
    <priority>1.0</priority>
  </url>

  <!-- Hub de serviços (Fase 2) -->
  <url>
    <loc>https://[DOMINIO]/servicos</loc>
    <lastmod>[DATA-HOJE]</lastmod>
    <changefreq>monthly</changefreq>
    <priority>0.9</priority>
  </url>

  <!-- Página do Serviço 1 (Fase 3) -->
  <url>
    <loc>https://[DOMINIO]/servicos/[SLUG-SERVICO-1]</loc>
    <lastmod>[DATA-HOJE]</lastmod>
    <changefreq>monthly</changefreq>
    <priority>0.8</priority>
  </url>

  <!-- Páginas de bairro do Serviço 1 (Fase 4) — 6 entradas -->
  <url>
    <loc>https://[DOMINIO]/servicos/[SLUG-SERVICO-1]/[SLUG-BAIRRO-1]</loc>
    <lastmod>[DATA-HOJE]</lastmod>
    <changefreq>monthly</changefreq>
    <priority>0.6</priority>
  </url>
  <url>
    <loc>https://[DOMINIO]/servicos/[SLUG-SERVICO-1]/[SLUG-BAIRRO-2]</loc>
    <lastmod>[DATA-HOJE]</lastmod>
    <changefreq>monthly</changefreq>
    <priority>0.6</priority>
  </url>
  <url>
    <loc>https://[DOMINIO]/servicos/[SLUG-SERVICO-1]/[SLUG-BAIRRO-3]</loc>
    <lastmod>[DATA-HOJE]</lastmod>
    <changefreq>monthly</changefreq>
    <priority>0.6</priority>
  </url>
  <url>
    <loc>https://[DOMINIO]/servicos/[SLUG-SERVICO-1]/[SLUG-BAIRRO-4]</loc>
    <lastmod>[DATA-HOJE]</lastmod>
    <changefreq>monthly</changefreq>
    <priority>0.6</priority>
  </url>
  <url>
    <loc>https://[DOMINIO]/servicos/[SLUG-SERVICO-1]/[SLUG-BAIRRO-5]</loc>
    <lastmod>[DATA-HOJE]</lastmod>
    <changefreq>monthly</changefreq>
    <priority>0.6</priority>
  </url>
  <url>
    <loc>https://[DOMINIO]/servicos/[SLUG-SERVICO-1]/[SLUG-BAIRRO-6]</loc>
    <lastmod>[DATA-HOJE]</lastmod>
    <changefreq>monthly</changefreq>
    <priority>0.6</priority>
  </url>

  <!-- Repetir bloco para Serviço 2 e Serviço 3 -->

</urlset>
```

**Prioridades:**
| Página | priority |
|--------|----------|
| Home (index) | 1.0 |
| Hub /servicos | 0.9 |
| Página de serviço | 0.8 |
| Página de bairro | 0.6 |

**Data:** usar a data real de geração no formato `YYYY-MM-DD` (ex: `2026-03-24`)

---

## ROBOTS.TXT

### SE já existir robots.txt no projeto:

Verificar se tem a linha `Sitemap:`. Se não tiver, adicionar:

```
Sitemap: https://[DOMINIO]/sitemap.xml
```

### SE não existir robots.txt:

Criar com o padrão AG5 (inclui bots de IA para GEO — aparecer no ChatGPT, Perplexity, etc.):

```
User-agent: *
Allow: /

# AI Bots (GEO Optimization — aparecer em buscas de IA)
User-agent: GPTBot
Allow: /
User-agent: ChatGPT-User
Allow: /
User-agent: Claude-Web
Allow: /
User-agent: PerplexityBot
Allow: /
User-agent: Google-Extended
Allow: /

# Sitemap
Sitemap: https://[DOMINIO]/sitemap.xml

# Áreas restritas
Disallow: /cgi-bin/
Disallow: /tmp/

# Crawl-delay para bots agressivos
User-agent: AhrefsBot
Crawl-delay: 10
User-agent: SemrushBot
Crawl-delay: 10
User-agent: DotBot
Crawl-delay: 10
```

> **Por que incluir bots de IA?** Além do Google, cada vez mais pessoas pesquisam no ChatGPT, Perplexity e Claude. Permitir explicitamente esses bots aumenta a chance do site ser citado como referência nessas plataformas (GEO — Generative Engine Optimization).

---

## APÓS GERAR — PRÓXIMOS PASSOS PARA O GERENTE

Informar sempre ao final da Fase 4:

```
📋 AÇÕES MANUAIS NECESSÁRIAS (gerente faz):

1. GOOGLE SEARCH CONSOLE
   → Acessar: search.google.com/search-console
   → Ir em: Sitemaps
   → Adicionar: https://[DOMINIO]/sitemap.xml
   → Clicar em "Enviar"
   ✅ Google vai indexar as novas páginas em horas/dias

2. VALIDAR SCHEMAS (opcional mas recomendado)
   → Acessar: search.google.com/test/rich-results
   → Colar a URL de uma página de serviço
   → Verificar: FAQ aparece como "Perguntas frequentes" ✅
   → Verificar: Breadcrumb aparece como trilha ✅

3. TESTAR WHATSAPP
   → Clicar em cada botão de WhatsApp em desktop e mobile
   → Confirmar que a mensagem pré-preenchida está correta

4. TESTAR MOBILE
   → Abrir no celular ou usar DevTools (F12 → ícone de celular)
   → Verificar que nada está cortado ou sobreposto
```

---

## CONTAGEM TOTAL DE URLS NO SITEMAP

Para um projeto padrão AG5 (3 serviços × 6 bairros):

| Tipo | Qtd | priority |
|------|-----|----------|
| Home | 1 | 1.0 |
| Hub /servicos | 1 | 0.9 |
| Páginas de serviço | 3 | 0.8 |
| Páginas de bairro | 18 | 0.6 |
| **TOTAL** | **23** | — |
