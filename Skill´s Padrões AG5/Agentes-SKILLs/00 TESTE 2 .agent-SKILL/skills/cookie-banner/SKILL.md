---
name: cookie-banner
description: >
  Implementa um sistema completo de consentimento de cookies (LGPD) com banner de aceite e modal de personalização.
  Gera automaticamente o CSS e JS nas cores do layout do site A&A Advocacia (teal + dourado metálico).
  Inclui 5 categorias de cookies: Necessários, Funcionais, Analíticos, Desempenho e Publicidade.
skills:
  - frontend-design
---

# 🍪 SKILL: Cookie Banner — Sistema de Consentimento LGPD

## Objetivo
Implementar um sistema de consentimento de cookies completo, visualmente integrado ao layout do site,
em conformidade com a LGPD (Lei nº 13.709/2018) e boas práticas de UX.

---

## 📁 Arquivos desta Skill

```
.agent/skills/cookie-banner/
├── SKILL.md              ← Este arquivo (instruções)
├── cookie-banner.css     ← Estilos do banner e modal
└── cookie-banner.js      ← Lógica de consentimento
```

---

## 🎨 Paleta de Cores do Site (A&A Advocacia)

| Token                | Valor       | Uso                          |
|----------------------|-------------|------------------------------|
| `--color-primary-dark` | `#0d2d38` | Fundo do banner e modal      |
| `--color-primary`    | `#1a4a5a`   | Hover, bordas                |
| `--color-gold`       | `#c9a962`   | Botão primário, destaques    |
| `--color-gold-dark`  | `#a68a4a`   | Hover do botão dourado       |
| `--color-white`      | `#ffffff`   | Textos sobre fundo escuro    |
| `--color-bg`         | `#fafbfc`   | Fundo do modal               |

---

## 🚀 Como Implementar

### PASSO 1 — Copiar os arquivos CSS e JS para a raiz do projeto

```
cookie-banner.css  →  /raiz-do-projeto/cookie-banner.css
cookie-banner.js   →  /raiz-do-projeto/cookie-banner.js
```

### PASSO 2 — Adicionar no `<head>` de TODAS as páginas HTML

```html
<!-- Cookie Banner CSS -->
<link rel="stylesheet" href="cookie-banner.css">
```

### PASSO 3 — Adicionar antes do `</body>` de TODAS as páginas HTML

```html
<!-- Cookie Banner JS -->
<script src="cookie-banner.js" defer></script>
```

### PASSO 4 — Adicionar o HTML do banner antes do `</body>`

Cole o bloco abaixo imediatamente antes do `</body>` (após o script):

```html
<!-- ========== COOKIE BANNER ========== -->
<div id="cookie-banner" class="cookie-banner" role="dialog" aria-modal="true"
  aria-label="Aviso de cookies" aria-live="polite">
  <div class="cookie-banner__inner">
    <div class="cookie-banner__icon" aria-hidden="true">🍪</div>
    <div class="cookie-banner__content">
      <h2 class="cookie-banner__title">Valorizamos sua privacidade</h2>
      <p class="cookie-banner__text">
        Utilizamos cookies para aprimorar sua experiência de navegação, exibir conteúdo
        personalizado e analisar nosso tráfego. Ao clicar em <strong>"Aceitar todos"</strong>,
        você concorda com nosso uso de cookies conforme nossa
        <a href="politica-de-privacidade.html" class="cookie-banner__link">Política de Privacidade</a>.
      </p>
    </div>
    <div class="cookie-banner__actions">
      <button id="cookie-customize" class="cookie-btn cookie-btn--ghost">Personalizar</button>
      <button id="cookie-reject" class="cookie-btn cookie-btn--outline">Rejeitar</button>
      <button id="cookie-accept-all" class="cookie-btn cookie-btn--primary">Aceitar todos</button>
    </div>
  </div>
</div>

<!-- ========== COOKIE MODAL (Personalização) ========== -->
<div id="cookie-modal" class="cookie-modal" role="dialog" aria-modal="true"
  aria-label="Personalizar preferências de cookies" aria-hidden="true">
  <div class="cookie-modal__overlay" id="cookie-modal-overlay"></div>
  <div class="cookie-modal__box">
    <div class="cookie-modal__header">
      <h2 class="cookie-modal__title">Personalizar preferências de consentimento</h2>
      <button class="cookie-modal__close" id="cookie-modal-close" aria-label="Fechar modal">
        <svg width="20" height="20" viewBox="0 0 24 24" fill="none" aria-hidden="true">
          <path d="M18 6L6 18M6 6l12 12" stroke="currentColor" stroke-width="2"
            stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
      </button>
    </div>

    <div class="cookie-modal__body">
      <p class="cookie-modal__intro">
        Utilizamos cookies para ajudar você a navegar com eficiência e executar certas funções.
        Você encontrará informações detalhadas sobre todos os cookies sob cada categoria abaixo.
        Os cookies classificados como <strong>"Necessário"</strong> são armazenados em seu navegador,
        pois são essenciais para o funcionamento básico do site.
      </p>

      <!-- Categoria: Necessários -->
      <div class="cookie-category">
        <div class="cookie-category__header">
          <div class="cookie-category__info">
            <h3 class="cookie-category__name">Necessário</h3>
            <p class="cookie-category__desc">
              Cookies necessários são cruciais para as funções básicas do site e ele não funcionará
              como pretendido sem eles. Esses cookies não armazenam nenhum dado pessoalmente identificável.
            </p>
          </div>
          <span class="cookie-category__badge">Sempre ativo</span>
        </div>
      </div>

      <!-- Categoria: Funcionais -->
      <div class="cookie-category">
        <div class="cookie-category__header">
          <div class="cookie-category__info">
            <h3 class="cookie-category__name">Funcional</h3>
            <p class="cookie-category__desc">
              Cookies funcionais ajudam a executar certas funcionalidades, como compartilhar o conteúdo
              do site em plataformas de mídia social, coletar feedbacks e outros recursos de terceiros.
            </p>
          </div>
          <label class="cookie-toggle" aria-label="Ativar cookies funcionais">
            <input type="checkbox" id="cookie-functional" name="functional">
            <span class="cookie-toggle__slider"></span>
          </label>
        </div>
      </div>

      <!-- Categoria: Analíticos -->
      <div class="cookie-category">
        <div class="cookie-category__header">
          <div class="cookie-category__info">
            <h3 class="cookie-category__name">Analítico</h3>
            <p class="cookie-category__desc">
              Cookies analíticos são usados para entender como os visitantes interagem com o site.
              Esses cookies fornecem informações sobre métricas como número de visitantes, taxa de
              rejeição, fonte de tráfego, etc.
            </p>
          </div>
          <label class="cookie-toggle" aria-label="Ativar cookies analíticos">
            <input type="checkbox" id="cookie-analytics" name="analytics">
            <span class="cookie-toggle__slider"></span>
          </label>
        </div>
      </div>

      <!-- Categoria: Desempenho -->
      <div class="cookie-category">
        <div class="cookie-category__header">
          <div class="cookie-category__info">
            <h3 class="cookie-category__name">Desempenho</h3>
            <p class="cookie-category__desc">
              Cookies de desempenho são usados para entender e analisar os principais índices de
              desempenho do site, ajudando a oferecer uma melhor experiência ao visitante.
            </p>
          </div>
          <label class="cookie-toggle" aria-label="Ativar cookies de desempenho">
            <input type="checkbox" id="cookie-performance" name="performance">
            <span class="cookie-toggle__slider"></span>
          </label>
        </div>
      </div>

      <!-- Categoria: Publicidade -->
      <div class="cookie-category">
        <div class="cookie-category__header">
          <div class="cookie-category__info">
            <h3 class="cookie-category__name">Publicidade</h3>
            <p class="cookie-category__desc">
              Cookies de anúncios são usados para entregar aos visitantes anúncios personalizados
              com base nas páginas que visitaram antes e analisar a eficácia da campanha publicitária.
            </p>
          </div>
          <label class="cookie-toggle" aria-label="Ativar cookies de publicidade">
            <input type="checkbox" id="cookie-advertising" name="advertising">
            <span class="cookie-toggle__slider"></span>
          </label>
        </div>
      </div>
    </div>

    <div class="cookie-modal__footer">
      <button id="cookie-modal-reject" class="cookie-btn cookie-btn--outline">Rejeitar</button>
      <button id="cookie-modal-save" class="cookie-btn cookie-btn--ghost">Salvar Minhas Preferências</button>
      <button id="cookie-modal-accept-all" class="cookie-btn cookie-btn--primary">Aceitar todos</button>
    </div>
  </div>
</div>
<!-- ========== FIM COOKIE BANNER ========== -->
```

---

## ✅ Checklist de Implementação

- [ ] `cookie-banner.css` linkado no `<head>` de todas as páginas
- [ ] `cookie-banner.js` adicionado antes do `</body>` de todas as páginas
- [ ] HTML do banner e modal colado antes do `</body>`
- [ ] Links para `politica-de-privacidade.html` funcionando
- [ ] Testado em mobile (banner empilha corretamente)
- [ ] Testado em desktop (banner aparece na parte inferior)
- [ ] Preferências salvas no localStorage após escolha
- [ ] Banner não reaparece após aceite/rejeição

---

## 🔧 Personalização

### Alterar cores (se o site mudar de paleta):
Edite as variáveis no início de `cookie-banner.css`:

```css
:root {
  --ck-bg: #0d2d38;          /* Fundo do banner */
  --ck-gold: #c9a962;        /* Cor de destaque */
  --ck-gold-dark: #a68a4a;   /* Hover dourado */
  --ck-text: #ffffff;        /* Texto principal */
  --ck-text-muted: rgba(255,255,255,0.7); /* Texto secundário */
}
```

### Alterar duração de expiração do consentimento:
Em `cookie-banner.js`, localize e altere:

```js
const COOKIE_EXPIRY_DAYS = 365; // Altere para o número de dias desejado
```

---

## 📋 Notas Legais (LGPD)

- Os cookies **Necessários** são sempre ativos (não podem ser desativados)
- O consentimento é armazenado no `localStorage` com a chave `aa_cookie_consent`
- O banner reaparece automaticamente após o período de expiração
- Recomenda-se revisar periodicamente as categorias de cookies conforme os serviços utilizados no site
