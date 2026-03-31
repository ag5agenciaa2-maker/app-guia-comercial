# Fase 4 — Páginas por Bairro

> Para cada serviço principal, criar 6 páginas de bairro.
> Total: 3 serviços × 6 bairros = 18 páginas.
> Executar todos os 6 bairros de um serviço juntos, depois passar para o próximo serviço.

---

## LÓGICA DE EXECUÇÃO

```
Para cada serviço (3 serviços):
  Para cada bairro (6 bairros):
    1. Copiar estrutura da página do serviço (fase 3)
    2. Substituir: title, meta description, H1, H2 principal, Schema
    3. Adaptar sutilmente subtítulo e CTA (mencionar o bairro)
    4. Manter todo o restante igual
    5. Salvar em: servicos/[slug-servico]/[slug-bairro]/index.html
```

---

## PASSO 1 — DEFINIR OS 6 BAIRROS

### Se o usuário informou os bairros:
Usar exatamente os informados.

### Se o usuário NÃO informou:
Identificar o bairro da empresa pelo endereço extraído do index na Fase 1.
Depois, identificar os 6 bairros vizinhos mais relevantes com base em:

1. Bairros diretamente adjacentes ao bairro da empresa
2. Bairros com maior densidade populacional próximos
3. Bairros com alto tráfego de busca para o segmento na cidade

**Apresentar a lista sugerida ao usuário ANTES de criar as páginas.**

```
BAIRROS SUGERIDOS PARA [CIDADE]:
Bairro da empresa: [bairro]

Bairros vizinhos sugeridos para as 6 páginas:
  1. [Bairro 1]
  2. [Bairro 2]
  3. [Bairro 3]
  4. [Bairro 4]
  5. [Bairro 5]
  6. [Bairro 6]

Confirme ou substitua antes de prosseguir.
```

---

## PASSO 2 — GERAR SLUGS DOS BAIRROS

```
Regras (mesmas dos serviços):
- Minúsculas, hifens, sem acentos, sem caracteres especiais

Exemplos:
"Pinheiros"       → pinheiros
"Vila Madalena"   → vila-madalena
"Itaim Bibi"      → itaim-bibi
"Moema"           → moema
"Vila Olímpia"    → vila-olimpia
"Brooklin"        → brooklin
```

---

## PASSO 3 — O QUE MUDA EM CADA PÁGINA DE BAIRRO

### Elementos que MUDAM (substituição do bairro da empresa pelo bairro alvo):

**`<title>`**
```
ANTES: [Serviço] em [Bairro Empresa], [Cidade] | [Nome Empresa]
DEPOIS: [Serviço] em [Bairro Alvo], [Cidade] | [Nome Empresa]
```

**`<meta name="description">`**
```
ANTES: ... [NOME EMPRESA] oferece [SERVIÇO] em [BAIRRO EMPRESA]...
DEPOIS: ... [NOME EMPRESA] oferece [SERVIÇO] em [BAIRRO ALVO]...
```

**`<link rel="canonical">`**
```
ANTES: https://[DOMINIO]/servicos/[SLUG-SERVICO]
DEPOIS: https://[DOMINIO]/servicos/[SLUG-SERVICO]/[SLUG-BAIRRO]
```

**`<h1>`**
```
ANTES: [Serviço] em [Bairro Empresa], [Cidade]
DEPOIS: [Serviço] em [Bairro Alvo], [Cidade]
```

**Subtítulo do hero** (adaptação leve e natural):
```
ANTES: Atendimento especializado em [Bairro Empresa] e região.
DEPOIS: Atendimento especializado para clientes de [Bairro Alvo] e região.
```

**Schema `Service` — campo `areaServed`:**
```json
ANTES: { "@type": "City", "name": "[CIDADE]" }
DEPOIS: { "@type": "Place", "name": "[BAIRRO ALVO], [CIDADE]" }
```

**Schema `BreadcrumbList`:**
```json
ANTES: 3 itens (Início / Serviços / [Serviço])
DEPOIS: 4 itens (Início / Serviços / [Serviço] / [Bairro Alvo])
```

**Breadcrumb HTML:**
```html
ANTES:
<li><a href="/">Início</a></li>
<li><a href="/servicos">Serviços</a></li>
<li>[Nome Serviço]</li>

DEPOIS:
<li><a href="/">Início</a></li>
<li><a href="/servicos">Serviços</a></li>
<li><a href="/servicos/[slug-servico]">[Nome Serviço]</a></li>
<li>[Bairro Alvo]</li>
```

**CTA Final — texto:**
```
ANTES: Precisa de [Serviço] em [Cidade]?
DEPOIS: Precisa de [Serviço] em [Bairro Alvo]?
```

---

## PASSO 4 — O QUE NÃO MUDA

- Navbar (idêntico)
- Footer (idêntico)
- Seção "Sobre o Serviço" (idêntica)
- Seção "Como Funciona" (idêntica)
- Seção "Diferenciais" (idêntica)
- FAQ — perguntas e respostas (idênticas)
- Seção de Bairros (idêntica — os links continuam apontando para os outros bairros)
- CSS e JavaScript
- Schemas LocalBusiness e FAQPage

---

## PASSO 5 — ESTRUTURA DE ARQUIVOS

```
servicos/
└── [slug-servico]/
    ├── index.html                 ← Fase 3 (bairro da empresa)
    ├── [slug-bairro-1]/
    │   └── index.html             ← Fase 4
    ├── [slug-bairro-2]/
    │   └── index.html
    ├── [slug-bairro-3]/
    │   └── index.html
    ├── [slug-bairro-4]/
    │   └── index.html
    ├── [slug-bairro-5]/
    │   └── index.html
    └── [slug-bairro-6]/
        └── index.html
```

---

## PASSO 6 — ATUALIZAR SITEMAP.XML

Ao final da Fase 4 de cada serviço, gerar os trechos para o sitemap:

```xml
<!-- Página do serviço (fase 3) -->
<url>
  <loc>https://[DOMINIO]/servicos/[SLUG-SERVICO]</loc>
  <lastmod>[DATA-HOJE]</lastmod>
  <changefreq>monthly</changefreq>
  <priority>0.8</priority>
</url>

<!-- Páginas de bairro (fase 4) -->
<url>
  <loc>https://[DOMINIO]/servicos/[SLUG-SERVICO]/[SLUG-BAIRRO-1]</loc>
  <lastmod>[DATA-HOJE]</lastmod>
  <changefreq>monthly</changefreq>
  <priority>0.6</priority>
</url>
<!-- Repetir para os 6 bairros -->
```

---

## CONFIRMAÇÃO AO FINAL DA FASE 4

### Por serviço:
```
✅ FASE 4 — [SERVIÇO] CONCLUÍDO

Páginas de bairro criadas:
  servicos/[slug]/[bairro-1]/index.html ✅  → H1: [texto]
  servicos/[slug]/[bairro-2]/index.html ✅  → H1: [texto]
  servicos/[slug]/[bairro-3]/index.html ✅  → H1: [texto]
  servicos/[slug]/[bairro-4]/index.html ✅  → H1: [texto]
  servicos/[slug]/[bairro-5]/index.html ✅  → H1: [texto]
  servicos/[slug]/[bairro-6]/index.html ✅  → H1: [texto]

[Se há mais serviços para fazer:]
Próximo serviço: [nome]
Aguardando aprovação para continuar.
```

### Final completo (após os 3 serviços):
```
🎉 TODAS AS 4 FASES CONCLUÍDAS

RESUMO GERAL:
├── index.html          → ajustado (fase 1)
├── servicos/index.html → criado (fase 2) — [n] serviços
├── Serviço 1: /servicos/[slug-1] + 6 bairros = 7 páginas
├── Serviço 2: /servicos/[slug-2] + 6 bairros = 7 páginas
└── Serviço 3: /servicos/[slug-3] + 6 bairros = 7 páginas

TOTAL DE PÁGINAS CRIADAS: 22
  1  hub de serviços
  3  páginas de serviço
  18 páginas de bairro

SITEMAP: [trechos gerados para adicionar ao sitemap.xml]

PRÓXIMOS PASSOS RECOMENDADOS:
  1. Adicionar trechos ao sitemap.xml
  2. Submeter sitemap no Google Search Console
  3. Validar schemas em: search.google.com/test/rich-results
  4. Testar responsivo em mobile
  5. Verificar links do WhatsApp
```
