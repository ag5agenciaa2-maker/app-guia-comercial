# Fase 3 — Página Individual de Serviço

> Executar UM serviço por vez. Aguardar aprovação antes de passar para o próximo.
> Design baseado no index — sem inventar layout novo.

---

## PASSO 1 — CONTEXTO ANTES DE GERAR

Para cada serviço, definir antes de escrever uma linha de HTML:

```
CONTEXTO DO SERVIÇO:
├── Nome exato do serviço (como está no index)
├── Slug: [gerado na fase 1]
├── Keyword principal: [serviço] + [cidade ou bairro da empresa]
├── Keyword secundária: [serviço] + [variação natural]
├── Bairro da empresa: [extraído do endereço no index]
├── Informações disponíveis no index sobre este serviço:
│   └── [listar tudo que o index diz sobre ele]
├── Informações extras fornecidas pelo cliente: [se houver]
└── FAQ: [4 perguntas mais buscadas para este serviço + segmento]
```

**Regra de conteúdo:**
- Usar APENAS o que estiver no index ou for enviado pelo cliente
- Se não houver informação suficiente, ser objetivo e genérico de forma honesta
- NUNCA inventar dados, casos, números ou credenciais que não foram fornecidos
- FAQ: usar perguntas reais do segmento — não inventar perguntas improváveis

---

## PASSO 2 — DEFINIR AS 4 PERGUNTAS FREQUENTES

Escolher as 4 perguntas mais pesquisadas no Google para este serviço + segmento.

Exemplos por serviço (usar como referência, adaptar ao contexto real):

| Serviço | Perguntas típicas |
|---------|------------------|
| Divórcio consensual | Quanto tempo demora? Preciso ir ao fórum? Tem filhos, posso fazer? Qual o custo? |
| Implante dentário | Quanto tempo dura o implante? É doloroso? Quanto custa? Tem restrições de saúde? |
| Revisão veicular | O que é verificado? Com que frequência fazer? Quanto tempo leva? Vale a garantia? |
| Imposto de renda PF | Quem é obrigado a declarar? Qual o prazo? Como declarar bens? O que é malha fina? |
| Botox | Quanto dura o efeito? Com que idade posso fazer? É seguro? Tem contraindicações? |

---

## PASSO 3 — ESTRUTURA DA PÁGINA

```
servicos/[slug-servico]/
└── index.html
```

### Ordem das seções:

```
01. <head>          Meta SEO + 4 Schemas + Fonts + CSS
02. <nav>           COPIADO DO INDEX
03. BREADCRUMB      Início / Serviços / [Nome do Serviço]
04. HERO            H1 com serviço+localização + subtítulo + CTA WhatsApp
05. SOBRE           O que é o serviço (objetivo, sem inventar)
06. PROCESSO        Como funciona (3-4 passos — genérico se não tiver info)
07. DIFERENCIAIS    Por que a empresa (baseado no que o index comunica)
08. FAQ             4 perguntas em acordeão com Schema FAQPage
09. BAIRROS         Seção "Atendemos sua região" com 6 bairros (links fase 4)
10. CTA FINAL       Bloco WhatsApp com credencial
11. <footer>        COPIADO DO INDEX
<script>            Acordeão FAQ
```

---

## PASSO 4 — HEAD

```html
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">

  <title>[SERVIÇO] em [CIDADE/BAIRRO] | [NOME EMPRESA]</title>
  <meta name="description" content="[EMPRESA] oferece [SERVIÇO] em [CIDADE]. [BENEFÍCIO PRINCIPAL]. Entre em contato e fale com um especialista.">
  <link rel="canonical" href="https://[DOMINIO]/servicos/[SLUG]">
  <meta name="robots" content="index, follow">

  <meta property="og:title" content="[SERVIÇO] em [CIDADE] | [NOME EMPRESA]">
  <meta property="og:description" content="[= meta description]">
  <meta property="og:type" content="website">
  <meta property="og:url" content="https://[DOMINIO]/servicos/[SLUG]">

  <!-- 4 Schemas: ver seo-schema-service.md -->
  <script type="application/ld+json">{ LocalBusiness }</script>
  <script type="application/ld+json">{ Service }</script>
  <script type="application/ld+json">{ FAQPage }</script>
  <script type="application/ld+json">{ BreadcrumbList }</script>

  <!-- Fontes e CSS do index -->
</head>
```

---

## PASSO 5 — BREADCRUMB

```html
<nav class="breadcrumb" aria-label="breadcrumb">
  <ol>
    <li><a href="/">Início</a></li>
    <li><a href="/servicos">Serviços</a></li>
    <li>[NOME DO SERVIÇO]</li>
  </ol>
</nav>
```

---

## PASSO 6 — HERO

```html
<section class="hero-servico">
  <div class="container">
    <div class="hero-content">

      <!-- Tag de categoria (opcional) -->
      <span class="hero-tag">[SEGMENTO — ex: Direito de Família]</span>

      <!-- H1: serviço + localização — OBRIGATÓRIO -->
      <h1>[SERVIÇO] em [BAIRRO DA EMPRESA], [CIDADE]</h1>

      <!-- Subtítulo: benefício direto, sem exageros -->
      <p class="hero-sub">
        [Frase de benefício baseada no que o index comunica sobre a empresa.
        Se não houver info suficiente: "Atendimento especializado com foco no seu caso."]
      </p>

      <!-- CTAs -->
      <div class="hero-ctas">
        <a href="https://wa.me/55[NUMERO]?text=Ol%C3%A1%2C+vim+pelo+site+e+tenho+interesse+em+[SERVICO+URL+ENCODED]."
           class="[CLASSE-BTN-PRIMARIO]"
           target="_blank" rel="noopener">
          Falar pelo WhatsApp
        </a>
        <a href="#sobre" class="[CLASSE-BTN-OUTLINE]">
          Saiba mais ↓
        </a>
      </div>

    </div>
  </div>
</section>
```

**CSS do hero (ajustar às variáveis do index):**
```css
.hero-servico {
  padding: 8rem 2rem 4rem;
  min-height: 60vh;
  display: flex;
  align-items: center;
}
.hero-servico h1 {
  font-size: clamp(2.2rem, 4.5vw, 3.8rem);
  line-height: 1.15;
  margin-bottom: 1rem;
}
.hero-sub {
  font-size: 1.1rem;
  opacity: 0.75;
  max-width: 560px;
  margin-bottom: 2rem;
  line-height: 1.6;
}

/* Animação de entrada — obrigatória */
@keyframes fadeUp {
  from { opacity: 0; transform: translateY(24px); }
  to   { opacity: 1; transform: translateY(0); }
}
.hero-tag     { animation: fadeUp 0.5s ease forwards; }
.hero-servico h1 { animation: fadeUp 0.55s ease 0.1s both; }
.hero-sub     { animation: fadeUp 0.55s ease 0.2s both; }
.hero-ctas    { animation: fadeUp 0.55s ease 0.3s both; }
```

---

## PASSO 7 — SOBRE O SERVIÇO

```html
<section class="sobre-servico" id="sobre">
  <div class="container">
    <h2>O que é [SERVIÇO]?</h2>
    <div class="sobre-content">
      <p>
        [Parágrafo 1: explicação direta do que é o serviço.
        Usar informações do index ou conhecimento objetivo do segmento.
        Máximo 3-4 linhas. Incluir keyword naturalmente.]
      </p>
      <p>
        [Parágrafo 2: para quem é indicado / quando procurar.
        Se não houver informação do cliente, ser genérico e verdadeiro.]
      </p>
    </div>
  </div>
</section>
```

---

## PASSO 8 — COMO FUNCIONA (PROCESSO)

```html
<section class="processo" id="processo">
  <div class="container">
    <h2>Como Funciona</h2>
    <div class="steps">

      <div class="step">
        <span class="step-num">01</span>
        <h3>Primeiro Contato</h3>
        <p>Entre em contato pelo WhatsApp para uma conversa inicial sem compromisso.</p>
      </div>

      <div class="step">
        <span class="step-num">02</span>
        <h3>Análise do Caso</h3>
        <p>[Etapa específica do serviço — ex: "Avaliação completa da situação" para advocacia, "Exame e planejamento" para odontologia]</p>
      </div>

      <div class="step">
        <span class="step-num">03</span>
        <h3>[Etapa de execução]</h3>
        <p>[Descrição breve e verdadeira]</p>
      </div>

      <div class="step">
        <span class="step-num">04</span>
        <h3>Conclusão</h3>
        <p>[Como termina o processo para o cliente]</p>
      </div>

    </div>
  </div>
</section>
```

> Se o index descreve o processo de trabalho da empresa, usar aquele texto como base.

---

## PASSO 9 — DIFERENCIAIS

Extrair os diferenciais do que já está comunicado no index (missão, valores, depoimentos, seção "sobre").

```html
<section class="diferenciais" id="diferenciais">
  <div class="container">
    <h2>Por que a [NOME EMPRESA]?</h2>
    <div class="cards-grid">

      <div class="card-diferencial">
        <h3>[DIFERENCIAL 1 — extraído do index]</h3>
        <p>[Explicação curta]</p>
      </div>

      <div class="card-diferencial">
        <h3>[DIFERENCIAL 2]</h3>
        <p>[Explicação curta]</p>
      </div>

      <div class="card-diferencial">
        <h3>[DIFERENCIAL 3]</h3>
        <p>[Explicação curta]</p>
      </div>

    </div>
  </div>
</section>
```

---

## PASSO 10 — FAQ (4 PERGUNTAS)

```html
<section class="faq" id="faq">
  <div class="container">
    <h2>Perguntas Frequentes sobre [SERVIÇO]</h2>

    <div class="faq-lista">

      <div class="faq-item">
        <button class="faq-pergunta" aria-expanded="false">
          [PERGUNTA 1]
          <span class="faq-icon" aria-hidden="true">+</span>
        </button>
        <div class="faq-resposta">
          <p>[RESPOSTA OBJETIVA — mínimo 2 frases, sem inventar dados]</p>
        </div>
      </div>

      <!-- Repetir para perguntas 2, 3 e 4 -->

    </div>
  </div>
</section>

<script>
document.querySelectorAll('.faq-pergunta').forEach(btn => {
  btn.addEventListener('click', () => {
    const item = btn.parentElement;
    const isOpen = item.classList.contains('open');
    document.querySelectorAll('.faq-item').forEach(i => i.classList.remove('open'));
    if (!isOpen) {
      item.classList.add('open');
      btn.setAttribute('aria-expanded', 'true');
    } else {
      btn.setAttribute('aria-expanded', 'false');
    }
  });
});
</script>
```

---

## PASSO 11 — SEÇÃO DE BAIRROS

Esta seção serve dois propósitos: UX (mostrar abrangência) + SEO (criar links para as páginas de bairro da Fase 4).

```html
<section class="bairros" id="bairros">
  <div class="container">
    <h2>[SERVIÇO] — Atendemos sua Região</h2>
    <p class="bairros-sub">
      Atendemos clientes de [BAIRRO DA EMPRESA] e das regiões vizinhas.
    </p>

    <div class="bairros-grid">

      <a href="/servicos/[SLUG-SERVICO]/[SLUG-BAIRRO-1]" class="bairro-card">
        <span class="bairro-nome">[BAIRRO 1]</span>
        <span class="bairro-link">[SERVIÇO] em [BAIRRO 1] →</span>
      </a>

      <a href="/servicos/[SLUG-SERVICO]/[SLUG-BAIRRO-2]" class="bairro-card">
        <span class="bairro-nome">[BAIRRO 2]</span>
        <span class="bairro-link">[SERVIÇO] em [BAIRRO 2] →</span>
      </a>

      <!-- Repetir para os 6 bairros -->

    </div>
  </div>
</section>
```

CSS:
```css
.bairros-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1rem;
  margin-top: 2rem;
}
.bairro-card {
  display: flex;
  flex-direction: column;
  padding: 1.25rem 1.5rem;
  border: 1px solid var(--border, rgba(0,0,0,0.1));
  border-radius: var(--radius, 8px);
  text-decoration: none;
  color: inherit;
  transition: background 0.2s ease;
}
.bairro-card:hover { background: var(--bg-muted, rgba(0,0,0,0.03)); }
.bairro-nome { font-weight: 600; font-size: 1rem; }
.bairro-link { font-size: 0.8rem; color: var(--accent); margin-top: 0.25rem; }
@media (max-width: 768px) {
  .bairros-grid { grid-template-columns: repeat(2, 1fr); }
}
```

---

## PASSO 12 — CTA FINAL

```html
<section class="cta-servico-final">
  <div class="container">
    <h2>Precisa de [SERVIÇO] em [CIDADE]?</h2>
    <p>Fale agora com a equipe da [NOME EMPRESA]. Atendimento rápido pelo WhatsApp.</p>
    <a href="https://wa.me/55[NUMERO]?text=Ol%C3%A1%2C+preciso+de+[SERVICO+URL+ENCODED]+em+[CIDADE+URL+ENCODED]."
       class="[CLASSE-BTN-PRIMARIO]"
       target="_blank" rel="noopener">
      Falar pelo WhatsApp
    </a>
  </div>
</section>
```

---

## CONFIRMAÇÃO AO FINAL DE CADA SERVIÇO

```
✅ FASE 3 — SERVIÇO [N] CONCLUÍDO

Arquivo: servicos/[slug]/index.html

H1: [texto exato do H1]
Keyword principal: [keyword]
Schemas: LocalBusiness ✅ | Service ✅ | FAQPage ✅ | BreadcrumbList ✅
CTAs WhatsApp: 2 (hero + cta final) ✅
Seção de bairros: 6 links criados ✅
FAQ: 4 perguntas ✅

Conteúdo inventado: [listar se houver algo que não veio do index]

[Se há mais serviços:]
Próximo serviço: [nome]
Aguardando aprovação para continuar.

[Se foi o último:]
Todos os 3 serviços concluídos.
Aguardando aprovação para iniciar FASE 4.
```
