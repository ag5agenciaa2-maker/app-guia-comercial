---
name: cookie-banner-universal
description: >
  Skill universal AG5 para implementação de sistema de consentimento de cookies (LGPD/GDPR).
  Gera CSS com cores sutis e alta legibilidade, JS vanilla com suporte a link no rodapé
  e HTML semântico. Padrão atualizado para evitar botões flutuantes intrusivos.
skills:
  - frontend-design
  - seo-fundamentals
---

# 🍪 SKILL: Cookie Banner Universal — Padrão AG5

> **Skill profissional e refinada.** Focada em discrição, legibilidade e conformidade total
> com a LGPD, integrada à identidade visual de cada projeto.

---

## 📁 Estrutura da Skill

```
Skill-Cookie-Site/
├── SKILL.md              ← Este arquivo (instruções completas)
├── cookie-banner.css     ← CSS com cores sutis e fontes legíveis
├── cookie-banner.js      ← JS com suporte a link no rodapé (showFloatingBtn: false)
├── cookie-banner.html    ← Snippet HTML otimizado
└── README.md             ← Documentação rápida
```

---

## 🚀 Implementação AG5 em 5 Passos

### PASSO 1 — Copiar arquivos
```
cookie-banner.css  →  /raiz-do-projeto/
cookie-banner.js   →  /raiz-do-projeto/
```

### PASSO 2 — Configurar o Head
Adicione no `<head>`:
```html
<link rel="stylesheet" href="cookie-banner.css">
```

### PASSO 3 — No Rodapé (Link de Preferências)
No rodapé legal (geralmente abaixo do copyright), adicione o seletor visual AG5:
```html
<a href="#" id="ck-prefs-link" style="text-decoration:none; color:inherit; display:inline-flex; align-items:center; gap:6px;">
  <span style="display:inline-flex; align-items:center; width:28px; height:14px; background:rgba(255,255,255,0.1); border-radius:10px; padding:2px; border:1px solid rgba(255,255,255,0.2); position:relative; font-size:8px; font-weight:bold;">
    <span style="color:#86EFAC; margin-left:2px;">✓</span>
    <span style="color:#FCA5A5; margin-left:auto; margin-right:2px;">✕</span>
    <span style="position:absolute; left:15px; width:10px; height:10px; background:var(--ck-accent); border-radius:50%; box-shadow:0 0 5px rgba(0,0,0,0.3);"></span>
  </span>
  Cookie
</a>
```

### PASSO 4 — No final do Body
Cole o conteúdo de `cookie-banner.html` antes do `</body>` e carregue o script:
```html
<script src="cookie-banner.js" defer></script>
```

### PASSO 5 — Sincronizar Cores
O padrão AG5 usa variáveis CSS. No seu `style.css` (ou no :root do `cookie-banner.css`), certifique-se de que `--ck-accent` seja a cor de destaque do site.

---

## ⚙️ Diferenciais do Padrão AG5 (v2.1.0)

1. **Legibilidade Aumentada**: Fontes maiores e contraste de cores otimizado para usuários com dificuldade visual.
2. **Menos Intrusão**: O `showFloatingBtn` vem desativado (`false`) por padrão, sendo substituído pelo link discreto no rodapé.
3. **Cores Sutis**: Fundo do banner em cinza neutro (`#1a1a1a`) e modal com textos escuros nítidos.
4. **Seletor Visual**: Link no rodapé com ícone de toggle (Check/X) para indicar claramente a funcionalidade.

---

## 🔌 API e Integrações

### Abrir manual (ex: via outro botão)
```js
CookieBanner.open();
```

### Evento para Analytics/Pixel
```js
window.addEventListener('cookieConsentUpdated', function(e) {
  const { preferences } = e.detail;
  if (preferences.analytics) { /* gTag granted */ }
});
```

---

## 📋 Checklist de Entrega

- [ ] Banner aparece após o delay configurado.
- [ ] Link "Cookie" no rodapé abre o modal corretamente.
- [ ] Textos no modal são perfeitamente legíveis (fundo branco, letras escuras).
- [ ] Cores do banner (Dark Mode) respeitam o accent dourado do site.
- [ ] Consentimento persiste após refresh e troca de página.
