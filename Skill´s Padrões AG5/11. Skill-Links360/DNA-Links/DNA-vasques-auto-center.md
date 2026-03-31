# SITE DNA — Vasques Auto Center · Links 360

**Nicho:** Automotivo — Oficina Mecânica Especializada (Alinhamento 3D, Freios, Diagnóstico)  
**Posicionamento:** Autoridade Técnica com Agressividade Visual. Transmite potência, confiança e velocidade através de uma composição dark mode + fire effects + tipografia condensada. Sensação de pit stop premium.  
**Data de criação:** Março 2026

---

## IDENTIDADE VISUAL

### Paleta de Cores

| Variável CSS | Hex | Função Específica no Layout |
|---|---|---|
| `--brand-main` | `#FF6600` | Laranja de fogo — destaque em ícones, borders, CTAs, gradiente hero |
| `--brand-hover` | `#E5A500` | Âmbar — segundo ponto do gradiente, hover states |
| `--brand-dark` | `#ffffff` | Texto primário (dark mode: branco) |
| `--brand-gray` | `#a1a1aa` | Texto secundário, labels, metadados |
| `--brand-light` | `#000000` | Background geral da página |
| `--brand-accent` | `#27272a` | Fundo de inputs e containers internos |
| `--card-bg` | `#18181b` | Fundo dos cards de avaliação, diferenciais e serviços |
| `--border-color` | `rgba(255,255,255,0.05)` | Bordas ultra-sutis em dark mode |
| `whatsapp` | `#25D366` | Exclusivo para botão flutuante WhatsApp |
| Gradiente CTA | `from-[#FF6600] to-[#E5A500]` | Botão principal — linear-gradient horizontal |

### Tipografia

| Elemento | Família | Peso | Tamanho | Observações |
|---|---|---|---|---|
| `h1` (nome do negócio) | Oswald | 700 | `text-3xl` / `text-4xl` (30–36px) | `uppercase`, `tracking-tight`, `leading-[1.1]` |
| `h2` de seções | Oswald | 700 | `text-xl` (20px) | `uppercase`, `letter-spacing: -0.01em` |
| `h3` de cards | Inter | 700 | `text-[11px]` | `uppercase`, `tracking-tight` |
| Subtítulo hero | Inter | 700 | `text-[10px]` | `uppercase tracking-[0.3em]` — pill estilo badge |
| Corpo/descrição | Inter | 500 | `text-sm` (14px) | `opacity-80`, `leading-relaxed` |
| Micro-labels | Inter | 700 | `0.6rem` | `letter-spacing: 0.2em`, `uppercase`, `opacity: 0.5` |
| Labels de botão | Oswald | 700 | `text-xl` | `uppercase`, font-serif no Tailwind config |
| Sub-labels de botão | Inter | 700 | `text-[10px]` | `uppercase tracking-widest opacity-70` |
| Reviews body | Inter | 400 | `text-[13px]` | `italic`, `leading-relaxed` |

### Estilo Geral

Dark-industrial com influência brutalista-racional: o layout opera em preto puro (`#000`) com cards elevados em `#18181b`, bordering quase invisível (`rgba(255,255,255,0.05)`) e um único acento cromático (laranja `#FF6600`) usado cirurgicamente em ícones, highlights e no único gradiente horizontal do CTA principal. Toda a hierarquia vertical é construída via contraste de opacidade e tamanho tipográfico — zero uso de cor para separar seções — com exceção do exhaust-fire decorativo que sangra horizontalmente como background zerado.

---

## LAYOUT — SEÇÃO POR SEÇÃO

### SEÇÃO 1 — Welcome Ticker

**Estrutura:** `overflow: hidden; white-space: nowrap;` Full width. `.ticker-content` com `display: inline-block` duplicado para loop infinito.  
**Fundo:** Cor da brand principal (`--brand-main`) — única faixa laranja na página.  
**Elementos:** `<span>` com separadores `|`, incluindo um `.dynamic-greeting` com saudação por horário (Bom dia/tarde/noite via JS).  
**Animação:** `@keyframes marquee` — `translateX(0)` → `translateX(-50%)`, duração `30s linear infinite`.  
**Micro-interações:** Nenhuma — puramente decorativo/informativo.  
**Diferenciador Visual:** Ticker laranja no topo quebra a expectativa do dark mode, funciona como índice de serviços antes do scroll.

---

### SEÇÃO 2 — Background Exhaust Fire

**Estrutura:** `position: absolute; top: 50%; left: -50px; width: 120vw; height: 450px;` — z-index: -1, pointer-events: none.  
**Fundo:** Gradiente radial: `radial-gradient(ellipse at left, #fff 0%, #ffcc00 25%, #ff6600 50%, #ff2200 80%, transparent 100%)`. `mix-blend-mode: screen`.  
**Elementos:** 5 partículas `.fire-particle` com alturas variando de 80px a 200px, `filter: blur(15px–40px)`, posição `absolute left: 0`.  
**Animação:** `@keyframes backfire-stream` com delays escalonados (0s, 0.8s, 1.6s, 2.4s, 3.2s) de 4s cada, `ease-out infinite`. `opacity: 0` → pico → `opacity: 0`.  
**Micro-interações:** Nenhuma. Puramente decorativo.  
**Diferenciador Visual:** Background dinâmico único — cria movimento permanente sem JS, localizado no centro-esquerdo da viewport.

---

### SEÇÃO 3 — Hero (Authority Section)

**Estrutura:** `flex flex-col items-center text-center pt-8 pb-10 px-4`. Max-width via container pai `max-w-lg mx-auto`.  
**Fundo:** `bg-gradient-to-b from-brand-main/20 via-brand-main/10 to-transparent` — bloco `absolute` `-z-10 w-full h-80 rounded-b-[4rem]`.  
**Elementos:**
- Avatar: `w-40 h-40 rounded-full p-1 bg-brand-main shadow-xl shadow-brand-main/20` → inner `rounded-full overflow-hidden border-4 border-zinc-200/20 bg-[#121212]`
- Badge check: `absolute bottom-2 right-2 bg-[#18181b] rounded-full p-1.5 border border-white/10` → `fa-check-circle text-brand-main text-2xl`
- Nome h1: `text-3xl font-serif font-bold uppercase tracking-tight mb-3`
- Linha subtítulo: `bg-black/50 backdrop-blur-sm px-8 py-2.5 rounded-full border border-brand-main/30`
- Status badge: `.glass rounded-full py-2.5 px-6` com dot `animate-ping bg-green-500`

**Animação:** Classe `.reveal` — `opacity: 0; transform: translateY(20px)` → `.active: opacity: 1; transform: translateY(0)` via IntersectionObserver, `transition: all 0.8s cubic-bezier(0.23,1,0.32,1)`.  
**Micro-interações:** Badge de status sem interação. Avatar sem hover.  
**Diferenciador Visual:** Fundo em gradiente semi-transparente + avatar em `bg-brand-main` (laranja puro) com borda darkada — contraste forte no topo da composição.

---

### SEÇÃO 4 — CTAs e Links

**Estrutura:** `<main class="px-5 pt-4 space-y-4">` — espaçamento linear entre elementos, nenhum grid.

**Botão WhatsApp Principal:**
- Dimensão: `h-24` (96px) full-width, `rounded-2xl`
- Background: `bg-gradient-to-r from-[#FF6600] to-[#E5A500]`
- Sombra: `shadow-xl shadow-brand-main/30`
- Ícone fantasma: `absolute -right-4 -bottom-4 opacity-20 rotate-12 text-8xl` — cresce no hover
- Animação: `.pulse-custom-slow` — `@keyframes pulse-ring: scale(0.98) → box-shadow 10px → scale(0.98)`, 4s infinito

**Botões Secundários (Links h-24):**
- Background: `bg-zinc-900 hover:bg-zinc-800`
- Border: `border border-white/10`
- Ícone fantasma: `opacity-10`
- Ícone principal: `text-3xl shrink-0`
- Seta: `fa-chevron-right text-brand-main opacity-60 → group-hover:opacity-100 group-hover:translate-x-1`
- Micro-interação: `transition-all duration-300`, `active:scale-95`

**Grid Contatos Rápidos:**
- `grid grid-cols-2 gap-3`, `py-3 px-4 rounded-xl bg-zinc-900 border border-brand-main/20`

**Diferenciador Visual:** Botão principal em gradiente de fogo é a única cor quente num mar de zinc-900. Cria hierarquia imediata.

---

### SEÇÃO 5 — Galeria de Vídeos

**Estrutura:** `.video-carousel` com `overflow-x: hidden; display: flex; scroll-snap-type: x mandatory;`. Cada `.video-slide` `flex-shrink: 0; width: 100%`.  
**Fundo:** Transparente — absorve o dark do container pai.  
**Elementos:** `<video>` com `muted playsinline preload="none"` + `.video-label` absolute no bottom. Máscara `.video-slide-mask` de 1px lateral para efeito de peek.  
**Animação:** Scroll horizontal via JS com `scrollTo({behavior: 'smooth'})`. Autoplay ao entrar na viewport com IntersectionObserver.  
**Micro-interações:** `.video-dot active` muda `background-color` para `--brand-main`. `.btn-ativar-som` aparece via `display: block` após tap.  
**Diferenciador Visual:** Player nativo mobile-first com controle de som contextual — não usa YouTube/embed.

---

### SEÇÃO 6 — Diferenciais (2×2 Grid)

**Estrutura:** `grid grid-cols-2 gap-4` — cada card `flex flex-col items-center p-6 rounded-[2rem] border border-white/5`.  
**Fundo:** `bg-[#18181b]` — ligeiramente mais claro que o black puro.  
**Elementos:** Ícone em container `bg-[#27272a] p-4 rounded-full text-brand-main`, texto `text-[11px] font-bold uppercase`.  
**Animação:** `.hover-lift` — `transition: all 0.5s cubic-bezier(0.23,1,0.32,1)`.  
**Micro-interações:** `group-hover:bg-brand-main group-hover:text-white` no container do ícone — troca de cor sem transform.  
**Diferenciador Visual:** Cards square dark integrados ao fundo — ausência de profundidade visual intencional.

---

### SEÇÃO 7 — Antes/Depois (Slider)

**Estrutura:** `.image-comparison-container` com `--exposure: 50%` variável CSS. `position: relative`.  
**Fundo:** `var(--bg-caixas, var(--bg-card))` — seção com `border-radius: 2rem; border: 1px solid var(--border-color)`.  
**Elementos:** Imagem "depois" `.comparison-img-after` em largura 100%; "antes" `.comparison-img-before` com `clip-path: inset(0 calc(100% - var(--exposure)) 0 0)`. Handle `absolute` centralizado.  
**Animação:** `<input type="range">` move `--exposure` via JS `oninput`.  
**Micro-interações:** Handle com box-shadow suave, cursor `ew-resize`.  
**Diferenciador Visual:** Slider CSS puro — sem library externa. `mix-blend-mode` não usado, corte via clip-path.

---

### SEÇÃO 8 — Avaliações (Scroll Infinito)

**Estrutura:** `.animate-scroll` — `display: flex; width: max-content; animation: scrollReviews 60s linear infinite`. Cards duplicados para loop.  
**Fundo:** Cards `bg-[#18181b] p-6 rounded-[2rem] border border-white/5 min-w-[300px]`.  
**Elementos:** Estrelas `text-brand-main text-[10px]`, citação `italic text-[13px]`, avatar inicial `bg-[#27272a] rounded-full`.  
**Animação:** `@keyframes scrollReviews: translateX(0) → translateX(-50%)`, 60s linear.  
**Micro-interações:** `.animate-scroll:hover { animation-play-state: paused }`.  
**Diferenciador Visual:** Auto-scroll sem swipe — passivo e elegante. Indica volume de avaliações sem forçar interação.

---

### SEÇÃO 9 — Serviços (2×2 + variações)

**Estrutura:** `grid grid-cols-2 gap-4`. Cards `rounded-[2rem] overflow-hidden bg-[#18181b]`.  
**Fundo:** Imagem `h-36 object-cover` + overlay `bg-gradient-to-t from-black/90 via-black/40 to-transparent`.  
**Elementos:** `h3 absolute bottom-3 left-3 text-[11px] uppercase`. Botão "SAIBA MAIS" `text-brand-main text-[10px]`.  
**Animação:** `.reveal` padrão. Imagem `group-hover:scale-110 transition-transform duration-700`.  
**Micro-interações:** Botão `group-hover:translate-x-1 transition-transform`.  
**Diferenciador Visual:** Cards sem precio/descrição — apenas foto + label + CTA minimalista, induzindo ao modal.

---

## COMPONENTES REUTILIZÁVEIS

### Botão Link Secundário (h-24)

```css
/* Base */
.link-btn {
    height: 96px; /* h-24 */
    border-radius: 1rem; /* rounded-2xl */
    background: #18181b; /* bg-zinc-900 */
    border: 1px solid rgba(255,255,255,0.1);
    box-shadow: 0 20px 25px -5px rgba(0,0,0,0.1);
    transition: all 300ms ease;
    overflow: hidden;
    position: relative;
}
.link-btn:hover { background: #1f1f22; } /* zinc-800 */
.link-btn:active { transform: scale(0.95); }

/* Ícone fantasma background */
.link-btn .icon-ghost {
    position: absolute; right: -16px; bottom: -16px;
    font-size: 6rem; opacity: 0.1;
    transform: rotate(12deg);
    transition: transform 500ms ease;
}
.link-btn:hover .icon-ghost { transform: rotate(12deg) scale(1.1); }

/* Seta */
.link-btn .chevron { opacity: 0.6; transition: all 300ms; }
.link-btn:hover .chevron { opacity: 1; transform: translateX(4px); }
```

### Card de Diferencial

```css
.diff-card {
    background: #18181b;
    border-radius: 2rem;
    border: 1px solid rgba(255,255,255,0.05);
    padding: 1.5rem;
    transition: all 500ms cubic-bezier(0.23,1,0.32,1);
}
.diff-card:hover { transform: translateY(-8px); box-shadow: 0 20px 40px -15px rgba(255,102,0,0.4); }
.diff-card .icon-wrapper {
    background: #27272a; border-radius: 9999px; padding: 1rem;
    color: #FF6600; transition: colors 300ms;
}
.diff-card:hover .icon-wrapper { background: #FF6600; color: white; }
```

### Modal

```css
.modal-backdrop { background: rgba(18,18,18,0.8); backdrop-filter: blur(8px); }
.modal-content {
    background: var(--brand-light);
    border-radius: 2rem;
    max-width: 440px; max-height: 85vh;
    padding: 2.5rem;
    border: 1px solid rgba(255,255,255,0.05);
    animation: modalIn 500ms cubic-bezier(0.23,1,0.32,1);
}
@keyframes modalIn {
    from { opacity: 0; transform: translateY(30px) scale(0.98); }
    to   { opacity: 1; transform: translateY(0) scale(1); }
}
.close-modal:hover { transform: rotate(90deg); transition: 300ms; }
```

### Theme Toggle

```css
.theme-toggle {
    position: absolute; top: 1.5rem; right: 1.5rem;
    width: 44px; height: 44px; border-radius: 14px;
    background: var(--card-bg);
    border: 1px solid var(--border-color);
    box-shadow: 0 10px 25px -5px rgba(0,0,0,0.4);
    backdrop-filter: blur(8px);
    transition: all 400ms cubic-bezier(0.23,1,0.32,1);
}
.theme-toggle:hover { transform: scale(1.05) rotate(12deg); border-color: var(--brand-main); }
```
