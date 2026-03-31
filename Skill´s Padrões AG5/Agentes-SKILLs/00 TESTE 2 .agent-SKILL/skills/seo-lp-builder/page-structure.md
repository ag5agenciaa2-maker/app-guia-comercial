# Page Structure — Arquitetura das Páginas de Serviço

> Layout padrão seção por seção. Seguir esta ordem. Cada seção tem propósito SEO e de conversão definido.

---

## PÁGINA INDIVIDUAL DE SERVIÇO `/servicos/[slug]`

### Ordem das Seções (Top → Bottom)

```
01. <head>          Meta tags, Schema JSON-LD, Fonts
02. <nav>           Navbar (reutilizar da LP principal)
03. BREADCRUMB      Navegação estrutural
04. HERO            H1 + keyword + CTA primário
05. SOBRE O SERVIÇO Explicação clara (o que é, para quem)
06. DOR + SOLUÇÃO   Problema do cliente → como você resolve
07. PROCESSO        Como funciona (passo a passo visual)
08. DIFERENCIAIS    Por que escolher você (3-4 cards)
09. CREDENCIAIS     E-E-A-T: qualificações, registro, experiência
10. DEPOIMENTO      1 depoimento relacionado ao serviço
11. FAQ             Acordeão com 5-8 perguntas + Schema FAQPage
12. OUTROS SERVIÇOS Links para serviços relacionados
13. CTA FINAL       Bloco de conversão com WhatsApp
14. <footer>        Footer (reutilizar da LP principal)
```

---

## DETALHAMENTO SEÇÃO POR SEÇÃO

---

### 01. `<head>` — SEO Técnico

```html
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <!-- SEO Primary -->
  <title>[Keyword] | [Nome Empresa]</title>
  <meta name="description" content="[150-160 chars com keyword e CTA]">
  <link rel="canonical" href="[URL completa da página]">
  <meta name="robots" content="index, follow">

  <!-- Open Graph -->
  <meta property="og:title" content="[=title]">
  <meta property="og:description" content="[=description]">
  <meta property="og:type" content="website">
  <meta property="og:url" content="[URL]">
  <meta property="og:image" content="[imagem 1200x630]">

  <!-- Performance: Preconnect Fonts -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
  <link href="[Google Fonts URL com &display=swap]" rel="stylesheet">

  <!-- Schema JSON-LD (ver schema-templates.md) -->
  <script type="application/ld+json">
    { ...schema do serviço... }
  </script>

  <!-- CSS -->
  <link rel="stylesheet" href="/assets/css/style.css">
</head>
```

---

### 02. `<nav>` — Navegação

Reutilizar exatamente o navbar da LP principal.
- Manter `position: fixed` ou `sticky`
- Highlight no item "Serviços" do menu (estado ativo)
- Link "Fale Conosco" deve abrir WhatsApp

---

### 03. BREADCRUMB — Navegação Estrutural

```html
<!-- Imediatamente abaixo do navbar, acima do hero -->
<nav aria-label="breadcrumb" class="breadcrumb">
  <ol itemscope itemtype="https://schema.org/BreadcrumbList">
    <li itemprop="itemListElement" itemscope itemtype="https://schema.org/ListItem">
      <a itemprop="item" href="/"><span itemprop="name">Início</span></a>
      <meta itemprop="position" content="1">
    </li>
    <li itemprop="itemListElement" itemscope itemtype="https://schema.org/ListItem">
      <a itemprop="item" href="/servicos"><span itemprop="name">Serviços</span></a>
      <meta itemprop="position" content="2">
    </li>
    <li itemprop="itemListElement" itemscope itemtype="https://schema.org/ListItem">
      <span itemprop="name">[Nome do Serviço]</span>
      <meta itemprop="position" content="3">
    </li>
  </ol>
</nav>
```

**CSS base:**
```css
.breadcrumb {
  padding: 12px 0;
  font-size: 0.85rem;
  color: var(--text-muted);
}
.breadcrumb a {
  color: var(--accent);
  text-decoration: none;
}
.breadcrumb ol {
  list-style: none;
  display: flex;
  gap: 8px;
  align-items: center;
}
.breadcrumb li:not(:last-child)::after {
  content: "/";
  margin-left: 8px;
  opacity: 0.4;
}
```

---

### 04. HERO — Primeira Dobra

**Propósito:** Capturar atenção + declarar claramente o serviço + CTA imediato

```html
<section class="hero-servico" id="hero">
  <div class="hero-content">
    <!-- TAG de categoria (opcional, elegante) -->
    <span class="hero-tag">Direito de Família</span>

    <!-- H1: OBRIGATÓRIO conter keyword principal -->
    <h1 class="hero-title">
      Advogado para <em>Divórcio Consensual</em><br>em São Paulo
    </h1>

    <!-- Subtítulo: benefício principal, não descrição genérica -->
    <p class="hero-subtitle">
      Resolva sua separação com rapidez, discrição e sem desgaste emocional.
      Processo completo em até 30 dias.
    </p>

    <!-- CTAs -->
    <div class="hero-ctas">
      <a href="https://wa.me/[numero]" class="btn-primary" target="_blank">
        Fale com a Dra. Manoela agora
      </a>
      <a href="#processo" class="btn-outline">
        Como funciona →
      </a>
    </div>

    <!-- Prova social rápida (credibilidade imediata) -->
    <div class="hero-stats">
      <span>+500 casos resolvidos</span>
      <span>OAB/SP 123.456</span>
      <span>12 anos de experiência</span>
    </div>
  </div>

  <!-- Imagem com loading eager para LCP -->
  <div class="hero-image">
    <img
      src="/assets/[servico]-hero.jpg"
      alt="[keyword principal]"
      loading="eager"
      fetchpriority="high"
      width="600"
      height="700"
    >
  </div>
</section>
```

**CSS base:**
```css
.hero-servico {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  align-items: center;
  min-height: 85vh;
  padding: 6rem 2rem;
  max-width: 1200px;
  margin: 0 auto;
}
.hero-title {
  font-size: clamp(2.5rem, 5vw, 4rem);
  line-height: 1.1;
  font-weight: 600;
}
.hero-title em {
  font-style: normal;
  color: var(--accent);
}
@media (max-width: 768px) {
  .hero-servico {
    grid-template-columns: 1fr;
    min-height: auto;
    padding: 4rem 1.5rem;
  }
  .hero-image { order: -1; }
}
```

**Animação de entrada (obrigatória):**
```css
@keyframes fadeUp {
  from { opacity: 0; transform: translateY(30px); }
  to   { opacity: 1; transform: translateY(0); }
}
.hero-tag    { animation: fadeUp 0.5s ease forwards; }
.hero-title  { animation: fadeUp 0.6s ease 0.1s forwards; opacity: 0; }
.hero-subtitle { animation: fadeUp 0.6s ease 0.2s forwards; opacity: 0; }
.hero-ctas   { animation: fadeUp 0.6s ease 0.3s forwards; opacity: 0; }
.hero-stats  { animation: fadeUp 0.6s ease 0.4s forwards; opacity: 0; }
```

---

### 05. SOBRE O SERVIÇO — Explicação

**Propósito:** SEO (conteúdo rico com keyword) + educar o cliente

```html
<section class="sobre-servico" id="sobre">
  <div class="container">
    <h2>O que é o Divórcio Consensual?</h2>
    <div class="content-grid">
      <div class="texto">
        <p>[Parágrafo 1: definição clara e direta, com keyword natural]</p>
        <p>[Parágrafo 2: para quem é indicado, situações comuns]</p>
        <p>[Parágrafo 3: vantagens em relação à alternativa]</p>
      </div>
      <div class="destaque-card">
        <!-- Card lateral com dado impactante -->
        <strong>[Número/Dado]</strong>
        <p>[Contexto do dado]</p>
      </div>
    </div>
  </div>
</section>
```

---

### 06. DOR + SOLUÇÃO — Conexão Emocional

**Propósito:** Validar o problema do cliente + posicionar como solução

```html
<section class="dor-solucao" id="solucao">
  <div class="container">
    <div class="dor-bloco">
      <h2>Você provavelmente está passando por isso:</h2>
      <ul class="lista-dor">
        <li>Medo de que o processo seja longo e caro</li>
        <li>Insegurança sobre a guarda dos filhos</li>
        <li>Preocupação com a divisão de bens</li>
        <li>Não sabe por onde começar</li>
      </ul>
    </div>
    <div class="solucao-bloco">
      <h2>Como resolvemos isso para você:</h2>
      <ul class="lista-solucao">
        <li>Processo simplificado em até 30 dias</li>
        <li>Acompanhamento em todas as etapas</li>
        <li>Atendimento online disponível</li>
        <li>Consulta inicial gratuita para tirar todas as dúvidas</li>
      </ul>
    </div>
  </div>
</section>
```

---

### 07. PROCESSO — Como Funciona (Passo a Passo)

**Propósito:** Reduzir fricção/medo + SEO (rich content)

```html
<section class="processo" id="processo">
  <div class="container">
    <h2>Como Funciona Nosso Processo</h2>
    <div class="steps">

      <div class="step">
        <span class="step-number">01</span>
        <h3>Consulta Inicial Gratuita</h3>
        <p>Explicamos tudo sobre o seu caso, sem compromisso.</p>
      </div>

      <div class="step">
        <span class="step-number">02</span>
        <h3>Análise e Documentação</h3>
        <p>Reunimos todos os documentos necessários para iniciar.</p>
      </div>

      <div class="step">
        <span class="step-number">03</span>
        <h3>Protocolo e Andamento</h3>
        <p>Cuidamos de tudo junto ao cartório ou fórum.</p>
      </div>

      <div class="step">
        <span class="step-number">04</span>
        <h3>Conclusão e Entrega</h3>
        <p>Processo finalizado. Você recebe toda a documentação.</p>
      </div>

    </div>
  </div>
</section>
```

---

### 08. DIFERENCIAIS — Por Que Escolher

**Propósito:** Diferenciação + conversão

```html
<section class="diferenciais" id="diferenciais">
  <div class="container">
    <h2>Por Que Escolher a [Nome Escritório]</h2>
    <div class="cards-grid">
      <!-- 3-4 cards máximo -->
      <div class="card-diferencial">
        <div class="card-icon">[SVG icon]</div>
        <h3>[Diferencial]</h3>
        <p>[Explicação em 1-2 frases]</p>
      </div>
    </div>
  </div>
</section>
```

---

### 09. CREDENCIAIS — E-E-A-T

**Propósito:** Autoridade para Google e confiança para o cliente

```html
<section class="credenciais" id="credenciais">
  <div class="container">
    <div class="perfil">
      <img src="/assets/foto-profissional.jpg" alt="[Nome] — [Título]" width="300" height="350" loading="lazy">
      <div class="perfil-info">
        <h2>Dra. Manoela Gil</h2>
        <p class="registro">OAB/SP 123.456</p>
        <p>[Bio focada em experiência e resultados, 3-4 linhas]</p>
        <ul class="formacao">
          <li>Direito — USP</li>
          <li>Especialização em Direito de Família — FGV</li>
        </ul>
        <!-- Data visível: sinal E-E-A-T -->
        <time datetime="2026-03">Atualizado em março de 2026</time>
      </div>
    </div>
  </div>
</section>
```

---

### 10. DEPOIMENTO — Prova Social

**Propósito:** Credibilidade + redução de objeções

```html
<section class="depoimento-servico" id="depoimento">
  <div class="container">
    <blockquote class="depoimento-destaque">
      <p>"[Depoimento relacionado especificamente a este serviço]"</p>
      <footer>
        <strong>[Nome do Cliente]</strong>
        <span>[Serviço utilizado], [Ano]</span>
      </footer>
    </blockquote>
  </div>
</section>
```

---

### 11. FAQ — Perguntas Frequentes (Schema FAQPage)

**Propósito:** SEO (featured snippets) + responder objeções + Schema FAQ

```html
<section class="faq" id="faq">
  <div class="container">
    <h2>Perguntas Frequentes sobre Divórcio Consensual</h2>

    <div class="faq-lista" itemscope itemtype="https://schema.org/FAQPage">

      <div class="faq-item" itemscope itemprop="mainEntity" itemtype="https://schema.org/Question">
        <button class="faq-pergunta" aria-expanded="false">
          <span itemprop="name">Quanto tempo demora um divórcio consensual?</span>
          <span class="faq-icon">+</span>
        </button>
        <div class="faq-resposta" itemscope itemprop="acceptedAnswer" itemtype="https://schema.org/Answer">
          <p itemprop="text">
            Em média, um divórcio consensual demora entre 15 e 30 dias quando feito em cartório.
            Quando há menores de idade, o processo passa pelo judiciário e pode levar de 60 a 90 dias.
          </p>
        </div>
      </div>

      <!-- Repetir para cada pergunta -->

    </div>
  </div>
</section>
```

**CSS do Acordeão:**
```css
.faq-item {
  border-bottom: 1px solid var(--border);
  overflow: hidden;
}
.faq-pergunta {
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1.5rem 0;
  background: none;
  border: none;
  cursor: pointer;
  font-size: 1rem;
  font-weight: 500;
  text-align: left;
  color: var(--text);
}
.faq-resposta {
  max-height: 0;
  overflow: hidden;
  transition: max-height 0.35s ease, padding 0.35s ease;
}
.faq-item.open .faq-resposta {
  max-height: 300px;
  padding-bottom: 1.5rem;
}
.faq-item.open .faq-icon {
  transform: rotate(45deg);
  transition: transform 0.3s ease;
}
```

**JavaScript do Acordeão:**
```javascript
document.querySelectorAll('.faq-pergunta').forEach(btn => {
  btn.addEventListener('click', () => {
    const item = btn.parentElement;
    const isOpen = item.classList.contains('open');
    // Fechar todos
    document.querySelectorAll('.faq-item').forEach(i => i.classList.remove('open'));
    // Abrir clicado (se estava fechado)
    if (!isOpen) item.classList.add('open');
    btn.setAttribute('aria-expanded', !isOpen);
  });
});
```

---

### 12. OUTROS SERVIÇOS — Links Relacionados

**Propósito:** Link building interno + retenção

```html
<section class="outros-servicos" id="mais-servicos">
  <div class="container">
    <h2>Outros Serviços</h2>
    <div class="servicos-relacionados">
      <a href="/servicos/[slug-relacionado-1]" class="card-servico-link">
        <h3>[Serviço Relacionado 1]</h3>
        <p>[Uma linha de descrição]</p>
        <span>Saiba mais →</span>
      </a>
      <a href="/servicos/[slug-relacionado-2]" class="card-servico-link">
        <h3>[Serviço Relacionado 2]</h3>
        <p>[Uma linha de descrição]</p>
        <span>Saiba mais →</span>
      </a>
    </div>
  </div>
</section>
```

---

### 13. CTA FINAL — Conversão

**Propósito:** Última chance de converter antes do footer

```html
<section class="cta-final" id="contato">
  <div class="container">
    <h2>Pronto para resolver <em>[problema do serviço]</em>?</h2>
    <p>Fale agora com a Dra. Manoela Gil. Primeira consulta gratuita.</p>
    <a href="https://wa.me/[numero]?text=[mensagem pre-preenchida]"
       class="btn-primary btn-large"
       target="_blank"
       rel="noopener">
      Falar pelo WhatsApp agora
    </a>
    <p class="cta-credencial">OAB/SP 123.456 • Atendimento online disponível</p>
  </div>
</section>
```

**Mensagem WhatsApp pré-preenchida (URL encoded):**
```
Olá, vim pelo site e tenho interesse em [Nome do Serviço]. Poderia me dar mais informações?
```

---

## PÁGINA HUB `/servicos`

Estrutura simplificada — lista de todos os serviços:

```
01. <head>    Title: "Serviços | [Nome Empresa]" + Schema ItemList
02. <nav>     Navbar
03. HERO      H1 "Nossos Serviços" + subtítulo sobre especialização
04. GRID      Cards de cada serviço com link para página individual
05. CTA       WhatsApp genérico
06. <footer>  Footer
```

O grid de serviços usa Schema `ItemList` para aparecer no Google como lista estruturada.
