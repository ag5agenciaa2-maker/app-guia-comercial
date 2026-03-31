# SITE DNA — Tatiane Gomes · Links 360

**Nicho:** Saúde Estética Avançada — Harmonização Facial, Bioestimuladores, Tratamentos Corporais  
**Posicionamento:** Autoridade Clínica com Elegância Sofisticada. Transmite delicadeza médica, alto padrão estético e confiança científica através de uma composição light mode editorial + tipografia serifada + paleta rosé-dourada. Sensação de clínica premium parisiense.  
**Data de criação:** Março 2026

---

## IDENTIDADE VISUAL

### Paleta de Cores

| Variável CSS | Hex (referência) | Função Específica no Layout |
|---|---|---|
| `--brand-main` | Rosé/Mauve (ex: `#C9A09A`) | Cor primária — ícones, bordas de avatar, CTA gradient, estrelas do hero |
| `--brand-hover` | Dourado suave (ex: `#D4AF37`) | Segundo ponto do gradient CTA, accents dourados |
| `--brand-dark` | `#18181b` | Texto primário em light mode |
| `--brand-gray` | `#52525b` | Texto secundário, labels, metadados |
| `--brand-light` | `#FAF8F6` ou off-white similar | Background geral da página (off-white quente) |
| `--brand-accent` | `#f0ebe6` | Fundo interno de botões de contato rápido e ícones de diferenciais |
| `--card-bg` | `#ffffff` | Fundo dos cards de reviews e diferenciais |
| `--border-color` | `rgba(0,0,0,0.08)` | Bordas sutis em light mode |
| `zinc-100` / `border-zinc-100` | `#f4f4f5` | Bordas dos cards de avaliação |
| `text-yellow-500` | `#EAB308` | Estrelas de avaliação (não brand-main como no Vasques) |
| `whatsapp` | `#25D366` | Botão flutuante WhatsApp |

### Tipografia

| Elemento | Família | Peso | Tamanho | Observações |
|---|---|---|---|---|
| `h1` (nome) | Playfair Display | 700 | `text-3xl` / `text-4xl` (30–36px) | `tracking-tight`, sem uppercase (contraste com Vasques) |
| `h2` editoriais | Playfair Display | 700 | `text-4xl` (36px) | `tracking-tighter`, `italic` em alguns contextos |
| Subtítulo hero | Inter | 700 | `text-[10px]` | `uppercase tracking-[0.3em]`, pill com `bg-white/50 backdrop-blur-sm` |
| Corpo/descrição | Inter | 500 | `text-sm` (14px) | `leading-relaxed`, `opacity-80` |
| Labels de botão | Inter | 700 | `text-xl` (20px) | **sem uppercase** — diferença chave do Vasques |
| Sub-labels | Inter | 700 | `text-[10px]` | `uppercase tracking-widest opacity-70` |
| Micro-label galeria | Inter | 700 | `text-[10px]` | `tracking-[0.5em] uppercase` |
| Reviews body | Inter | 400 | `text-[13px]` | `italic leading-relaxed` |
| Badges de resultado | Inter | 700 | `text-[10px]` | `uppercase tracking-wider text-white` |

### Estilo Geral

Editorial-clínico com referências minimalistas nórdicas: layout em off-white quente com ausência total de dark mode como estado padrão — cards brancos emergem do background quase-branco via sombra suave e borda zinc-100. A única tensão visual vem do gradiente da cor da marca no CTA principal e dos acentos dourados na galeria de resultados. Tipografia serif (Playfair Display) introduz sofisticação e feminilidade sem clichê — usada em títulos editoriais, não nos botões. Ausência de efeitos de fogo, exhaust ou dark backgrounds agressivos é intencional e programática.

---

## LAYOUT — SEÇÃO POR SEÇÃO

### SEÇÃO 1 — Welcome Ticker

**Estrutura:** Identico ao Vasques — `overflow: hidden; white-space: nowrap; .ticker-content: display: inline-block` duplicado.  
**Fundo:** Cor `--brand-main` (rosé) — único block de cor satura no topo.  
**Elementos:** Especialidades estéticas no lugar de serviços mecânicos. `.dynamic-greeting` presente.  
**Animação:** `@keyframes marquee` — `translateX(0) → translateX(-50%)`, velocidade `30s linear infinite`.  
**Micro-interações:** Nenhuma.  
**Diferenciador Visual:** A cor rosé suave no topo cria expectativa de leveza antes do scroll — oposto ao laranja agressivo do Vasques.

---

### SEÇÃO 2 — Theme Toggle

**Estrutura:** `position: absolute; top: 1.5rem; right: 1.5rem; width: 44px; height: 44px; border-radius: 14px`.  
**Fundo:** `var(--card-bg)` = branco em light mode.  
**Elementos:** Ícone `fa-moon` como padrão (light mode ativo = lua visível).  
**Micro-interações:** Mesmo padrão do Vasques: `scale(1.05) rotate(12deg)` no hover.  
**Diferenciador Visual:** Ausência do music-toggle — Tatiane não usa música ambiente.

> ⚠️ **SEM exhaust-fire-container** — removido completamente para perfil clínico/minimalista.

---

### SEÇÃO 3 — Hero

**Estrutura:** `flex flex-col items-center text-center pt-8 pb-10 px-4`.  
**Fundo:** `bg-gradient-to-b from-brand-main/10 via-brand-main/5 to-transparent` — intensidade menor que Vasques (10% vs 20%).  
**Elementos:**
- Avatar: `w-36 h-36 rounded-full p-1 bg-gradient-to-tr from-brand-main to-brand-accent shadow-2xl` → inner `border-4 border-white` (branco, não zinc)
- Badge check: `bg-white rounded-full p-1.5 shadow-md` (branco com sombra suave)
- h1: `font-serif font-bold tracking-tight` — **sem uppercase** (chave distintiva)
- Pill subtítulo: `bg-white/50 dark:bg-transparent backdrop-blur-sm border border-brand-main/10`
- Status badge: `.glass rounded-full py-2.5 px-6` com dot verde ping

**Animação:** `.reveal` padrão idêntico ao Vasques.  
**Micro-interações:** Nenhuma adicional.  
**Diferenciador Visual:** Avatar em gradiente da marca (não cor sólida), borda branca pura, background-badge semitransparente — mais leve visualmente.

---

### SEÇÃO 4 — CTAs e Links

**Estrutura:** Idêntica ao Vasques — `space-y-4` vertical.

**Botão WhatsApp:**
- `h-24 bg-gradient-to-r from-brand-main to-brand-hover`
- Texto do label em **Inter** sem uppercase (vs Oswald uppercase do Vasques)
- `pulse-custom-slow` idêntico

**Grid Contatos Rápidos (diferença-chave):**
- Light mode: `bg-white dark:bg-zinc-900` — fundo branco no padrão
- Border: `border-brand-main/20`
- Texto: `text-brand-dark dark:text-gray-300`

**Botões h-24 Secundários:** Idênticos ao Vasques (`bg-zinc-900`) — dark nos botões mesmo em light mode geral.

**Botões adicionais únicos:**
- Threads: `bg-black hover:bg-zinc-900` (distinto do zinc-900 padrão)
- TikTok: `bg-zinc-950 hover:bg-black` (mais escuro ainda)

**Diferenciador Visual:** Mesmo padrão h-24 mas com presença de redes adicionais (Threads, TikTok) como extensão natural.

---

### SEÇÃO 5 — Diferenciais (2×2 Grid)

**Estrutura:** `grid grid-cols-2 gap-4` — mesma proporção do Vasques.  
**Fundo (DIFERENÇA CRÍTICA):** `bg-white border border-brand-accent` — **fundo branco**, não `#18181b`.  
**Elementos:** Texto `text-zinc-600` (não `text-brand-dark`).  
**Micro-interações:** Ícone: `bg-brand-light p-4 rounded-full group-hover:bg-brand-main group-hover:text-white` — mesma lógica de troca de cor.  
**Diferenciador Visual:** Cards brancos emergindo de background off-white — separação por sombra suave, não por contraste de cor.

---

### SEÇÃO 6 — Avaliações (Scroll Infinito)

**Estrutura:** Idêntica ao Vasques — `animate-scroll 60s linear infinite`.  
**Fundo (DIFERENÇA CRÍTICA):** Cards `bg-white p-6 rounded-[2rem] border border-zinc-100` — **brancos**, não dark.  
**Elementos:** Estrelas `text-yellow-500` (não `text-brand-main`). Texto `text-brand-dark` (preto).  
**Diferenciador Visual:** Reviews em cartão branco limpo vs. dark card — reforça a leveza clínica.

---

### SEÇÃO 7 — Galeria de Resultados (EXCLUSIVA — não existe no Vasques)

**Estrutura:** `flex flex-col gap-10` — layout editorial assimétrico. Item central em destaque + grid 2 colunas com offset vertical.  
**Fundo:** `bg-brand-light -mx-5 px-5 border-y border-brand-accent/30` — sangra nas margens.  
**Elementos:**
- Destaque central: `rounded-[3rem] shadow-2xl h-[450px] overflow-hidden cursor-zoom-in`
- Overlay: `bg-gradient-to-t from-black/80 via-black/20 to-transparent`
- Caption: `text-white font-serif italic text-2xl`
- Linha accent dourada: `h-px w-8 bg-brand-main`
- Grid suporte: coluna direita com `pt-12` offset
- Itens: `rounded-[2.5rem] aspect-[4/5]` ou `aspect-square`

**Animação:** `group-hover:scale-110 transition-all duration-1000`. Blur halo `group-hover:opacity-100 transition-opacity duration-700`.  
**Micro-interações:** `cursor-zoom-in` → abre `openImageModal()` com imagem fullscreen.  
**Diferenciador Visual:** Grid editorial com offset intencional, aspect ratios mistos (4/5 e square), sem labels genéricos — sugere portfólio de moda/editorial médico.

---

### SEÇÃO 8 — Serviços (2×2 Grid)

**Estrutura:** Idêntica ao Vasques — `grid grid-cols-2 gap-4`, cards com imagem `h-36`.  
**Fundo:** `bg-[#18181b]` — mantém dark nos cards de serviço mesmo no light mode.  
**Micro-interações:** Identicas ao Vasques.  
**Diferenciador Visual:** Conteúdo clínico (tratamentos) vs. mecânico — estrutura idêntica, contexto diferente.

---

## COMPONENTES REUTILIZÁVEIS

### Grid de Contatos Rápidos (Light Mode)

```css
.contact-quick {
    background: white; /* bg-white */
    border-radius: 0.75rem; /* rounded-xl */
    border: 1px solid rgba(var(--brand-main-rgb), 0.2);
    padding: 0.75rem 1rem; /* py-3 px-4 */
    transition: transform 150ms ease;
}
.contact-quick:active { transform: scale(0.95); }
```

### Card de Review (Light)

```css
.review-card {
    min-width: 300px;
    background: white;
    padding: 1.5rem; /* p-6 */
    border-radius: 2rem; /* rounded-[2rem] */
    border: 1px solid #f4f4f5; /* border-zinc-100 */
    box-shadow: 0 1px 3px rgba(0,0,0,0.04);
}
.review-stars { color: #EAB308; font-size: 10px; } /* text-yellow-500 */
.review-avatar {
    width: 40px; height: 40px;
    border-radius: 9999px;
    background: var(--brand-accent);
    color: var(--brand-main);
    font-weight: 700;
}
```

### Modal de Imagem Fullscreen

```css
.image-modal-backdrop {
    position: fixed; inset: 0; z-index: 200;
    background: rgba(0,0,0,0.92);
    backdrop-filter: blur(8px);
    display: flex; align-items: center; justify-content: center;
    padding: 1.5rem;
}
.image-modal-img {
    max-width: 100%; max-height: 85vh;
    object-fit: contain;
    border-radius: 1.5rem;
    animation: modalIn 400ms cubic-bezier(0.23,1,0.32,1);
}
```

### Card de Diferencial (Light)

```css
.diff-card-light {
    background: white;
    border-radius: 2rem;
    border: 1px solid var(--brand-accent); /* f0ebe6 */
    padding: 1.5rem;
}
.diff-card-light .icon-wrap {
    background: var(--brand-light);
    border-radius: 9999px;
    padding: 1rem;
    color: var(--brand-main);
    transition: background 300ms, color 300ms;
}
.diff-card-light:hover .icon-wrap {
    background: var(--brand-main);
    color: white;
}
.diff-card-light span { font-size: 11px; font-weight: 700; color: #52525b; }
```

