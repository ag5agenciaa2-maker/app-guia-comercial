# Fase 2 — Hub de Serviços `/servicos`

> Cria a página que lista todos os serviços da empresa. Design extraído do index — sem inventar nada novo.

---

## PASSO 1 — EXTRAIR REFERÊNCIAS DO INDEX

Antes de criar qualquer código, extrair do `index.html`:

```
EXTRAIR PARA REUTILIZAR:
├── HTML completo do <nav> (copiar idêntico)
├── HTML completo do <footer> (copiar idêntico)
├── Variáveis CSS ou valores de cores usados
├── Fontes (links do Google Fonts)
├── Classes de botão primário e secundário/outline
├── Padrão de seção (ex: class="section", padding padrão, max-width)
├── Padrão de card (se existir na seção de serviços do index)
└── Qualquer animação de entrada usada no index (scroll reveal, fade)
```

---

## PASSO 2 — ESTRUTURA DA PÁGINA HUB

```
servicos/
└── index.html
```

### Ordem das seções:

```
01. <head>       Meta SEO + Schema ItemList + Fonts + CSS
02. <nav>        COPIADO DO INDEX — idêntico
03. HERO         H1 simples + subtítulo sobre os serviços
04. GRID         Todos os serviços (cards)
05. CTA          Bloco WhatsApp genérico
06. <footer>     COPIADO DO INDEX — idêntico
```

---

## PASSO 3 — HEAD DA PÁGINA HUB

```html
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <!-- SEO -->
  <title>Serviços de [SEGMENTO] em [CIDADE] | [NOME EMPRESA]</title>
  <meta name="description" content="Conheça todos os serviços de [SEGMENTO] da [NOME EMPRESA] em [CIDADE]. [SERVIÇO 1], [SERVIÇO 2], [SERVIÇO 3] e mais. Fale conosco pelo WhatsApp.">
  <link rel="canonical" href="https://[DOMINIO]/servicos">
  <meta name="robots" content="index, follow">

  <!-- Open Graph -->
  <meta property="og:title" content="Serviços | [NOME EMPRESA]">
  <meta property="og:description" content="[= meta description]">
  <meta property="og:type" content="website">
  <meta property="og:url" content="https://[DOMINIO]/servicos">

  <!-- Schema: ItemList de serviços -->
  <script type="application/ld+json">
  {
    "@context": "https://schema.org",
    "@type": "ItemList",
    "name": "Serviços — [NOME EMPRESA]",
    "description": "Serviços de [SEGMENTO] em [CIDADE]",
    "url": "https://[DOMINIO]/servicos",
    "itemListElement": [
      {
        "@type": "ListItem",
        "position": 1,
        "name": "[SERVIÇO 1]",
        "url": "https://[DOMINIO]/servicos/[SLUG-1]"
      },
      {
        "@type": "ListItem",
        "position": 2,
        "name": "[SERVIÇO 2]",
        "url": "https://[DOMINIO]/servicos/[SLUG-2]"
      }
      /* repetir para todos os serviços */
    ]
  }
  </script>

  <!-- Mesmos links de fontes do index -->
  <!-- Mesmo CSS do index (link externo ou <style> copiado) -->
</head>
```

---

## PASSO 4 — HERO DA PÁGINA HUB

Hero simples — não competir visualmente com o index.

```html
<section class="hero-hub">
  <div class="container">
    <!-- Breadcrumb -->
    <nav class="breadcrumb" aria-label="breadcrumb">
      <a href="/">Início</a> / <span>Serviços</span>
    </nav>

    <h1>Nossos Serviços</h1>
    <p class="hero-hub-sub">
      Conheça todas as soluções que a [NOME EMPRESA] oferece em [CIDADE].
    </p>
  </div>
</section>
```

CSS:
```css
.hero-hub {
  padding: 8rem 2rem 3rem; /* espaço para navbar fixa */
  text-align: center;
}
.hero-hub h1 {
  font-size: clamp(2rem, 4vw, 3.5rem);
  margin-bottom: 1rem;
}
.hero-hub-sub {
  font-size: 1.1rem;
  opacity: 0.7;
  max-width: 500px;
  margin: 0 auto;
}
```

---

## PASSO 5 — GRID DE SERVIÇOS

### Lógica dos cards:

```
Para cada serviço encontrado no index:

SE o serviço tem página própria (está nos 3 principais):
  → Card com link para /servicos/[slug]
  → Badge "Ver detalhes →"

SE o serviço NÃO tem página própria:
  → Card com link para WhatsApp
  → Badge "Solicitar via WhatsApp →"
  → href="https://wa.me/55[NUMERO]?text=Olá, tenho interesse em [NOME SERVIÇO]."
```

```html
<section class="hub-grid">
  <div class="container">
    <div class="servicos-grid">

      <!-- Card com página própria -->
      <a href="/servicos/[slug-servico]" class="card-servico">
        <div class="card-servico-body">
          <h2 class="card-servico-titulo">[NOME DO SERVIÇO]</h2>
          <p class="card-servico-desc">[DESCRIÇÃO CURTA DO INDEX — se não tiver, deixar em branco]</p>
          <span class="card-servico-cta">Ver detalhes →</span>
        </div>
      </a>

      <!-- Card sem página (vai para WhatsApp) -->
      <a href="https://wa.me/55[NUMERO]?text=Ol%C3%A1%2C+tenho+interesse+em+[SERVICO+URL+ENCODED]."
         class="card-servico card-servico--whatsapp"
         target="_blank"
         rel="noopener">
        <div class="card-servico-body">
          <h2 class="card-servico-titulo">[NOME DO SERVIÇO]</h2>
          <p class="card-servico-desc">[DESCRIÇÃO CURTA — se não tiver, deixar em branco]</p>
          <span class="card-servico-cta">Solicitar via WhatsApp →</span>
        </div>
      </a>

    </div>
  </div>
</section>
```

CSS do grid:
```css
.servicos-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1.5rem;
  margin-top: 3rem;
}
.card-servico {
  display: block;
  padding: 2rem;
  border: 1px solid var(--border, rgba(0,0,0,0.1));
  border-radius: var(--radius, 8px);
  text-decoration: none;
  color: inherit;
  transition: transform 0.25s ease, box-shadow 0.25s ease;
}
.card-servico:hover {
  transform: translateY(-4px);
  box-shadow: 0 12px 32px rgba(0,0,0,0.1);
}
.card-servico-titulo {
  font-size: 1.25rem;
  font-weight: 600;
  margin-bottom: 0.5rem;
}
.card-servico-desc {
  font-size: 0.9rem;
  opacity: 0.65;
  margin-bottom: 1.5rem;
  line-height: 1.5;
}
.card-servico-cta {
  font-size: 0.85rem;
  font-weight: 600;
  color: var(--accent);
}
@media (max-width: 768px) {
  .servicos-grid { grid-template-columns: 1fr; }
}
```

> **Importante:** Se o index usa um padrão visual diferente de card (ex: lista, grid com ícone, etc.), **replicar esse padrão** ao invés do CSS acima.

---

## PASSO 6 — CTA FINAL

```html
<section class="hub-cta">
  <div class="container">
    <p>Não encontrou o que procura? Fale diretamente conosco.</p>
    <a href="https://wa.me/55[NUMERO]?text=Ol%C3%A1%2C+gostaria+de+mais+informa%C3%A7%C3%B5es+sobre+os+servi%C3%A7os."
       class="[CLASSE-BTN-PRIMARIO-DO-INDEX]"
       target="_blank"
       rel="noopener">
      Falar pelo WhatsApp
    </a>
  </div>
</section>
```

---

## CONFIRMAÇÃO AO FINAL DA FASE 2

```
✅ FASE 2 CONCLUÍDA

Arquivo criado: servicos/index.html

Cards gerados:
  COM página própria (link para /servicos/slug):
    → [serviço 1]
    → [serviço 2]
    → [serviço 3]

  SEM página (link para WhatsApp):
    → [serviço 4]
    → [serviço 5]
    → [serviço 6]

Design: navbar e footer copiados do index ✅
Schema ItemList: [n] itens ✅

Aguardando aprovação para iniciar FASE 3.
Serviço a ser criado primeiro: [nome do serviço 1]
```
