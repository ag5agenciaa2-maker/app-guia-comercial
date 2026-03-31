---
name: Links360-Construcao-C
description: Módulo de construção das Fases 7, 8 e 9 do Links 360 — Localização, Footer, Scripts, Modais e CSS completo. Cobre os Passos 4H, 4I e 4J.
type: project
---

# MÓDULO 02-C — CONSTRUÇÃO: FASES 7, 8 E 9

> Carregar este módulo após a confirmação da Fase 6 (módulo `02-construcao-B.md`).
> Cobre: Fase 7 (Localização + Footer + Scripts), Fase 8 (Modais), Fase 9 (CSS completo).

---

## ⚡ FASE FINAL DE CONSTRUÇÃO — ATENÇÃO REDOBRADA

Antes de iniciar cada fase deste módulo, revisar mentalmente:
- [ ] O nicho foi verificado (badge WhatsApp, linguagem, CTAs)?
- [ ] Os assets de todas as seções anteriores estão referenciados corretamente?
- [ ] Há alguma sugestão de melhoria que ainda não foi feita ao cliente?

**PAUSE E SUGIRA:** Se ao construir os modais ou o CSS perceber oportunidade de melhoria visual (animação, efeito, micro-interação), proponha antes de fechar a fase.

> 🚨 **REGRA DE OURO:** A cada 2 seções, PARE e mostre o resultado. Não entregue tudo de uma vez para não perder a qualidade e o controle do usuário.

---

## 📄 FASE 7: LOCALIZAÇÃO + FOOTER + FECHAMENTO

**Localização** (apenas se tiver endereço físico):
- Iframe do Google Maps embed
- Endereço formatado
- Tabela de horários
- Botão "Como Chegar (GPS)" com link do Maps directions

**Footer:**
- Logo/imagem pequena
- Ícones sociais (todos os links do cliente)
- Copyright (© ANO NOME DA EMPRESA)
- Link AG5 Agência (sempre manter)

**Fechamento do HTML:**
- `</main></div></div>`
- **WhatsApp Flutuante:** verificar o nicho antes de incluir o badge:
  - ❌ Nichos regulados (Advocacia, Odontologia, Medicina): **sem `.whatsapp-notify`** (sem bolinha vermelha)
  - ✅ Demais nichos: incluir `<span class="whatsapp-notify">1</span>` normalmente
- Config do `window.Link360Config` com os dados do vCard:
  ```javascript
  window.Link360Config = {
    projectName: "[SLUG DO PROJETO]",
    themeKey: "[slug-tema]",
    defaultDark: [true/false conforme o estilo],
    greetingText: "Seja Bem-Vindo",
    accentColor: "[HEX DA COR BRAND-MAIN]",
    officialUrl: "[URL DO SITE]",
    vcard: {
      fn: "[NOME COMPLETO DA EMPRESA]",
      n: "[NOME];;;",
      org: "[NOME DA EMPRESA | SEGMENTO]",
      title: "[SEGMENTO/PROFISSÃO]",
      tel: "+55[DDD][NÚMERO]",
      telWork: "[DDD][NÚMERO]",
      url: "[URL DO SITE]",
      adr: "[ENDEREÇO COMPLETO];[CIDADE];[ESTADO];[CEP];Brasil",
      filename: "[Nome_Empresa]"
    }
  };
  ```
- `<script src="../shared/core.js">` (script compartilhado do sistema)
- `<script src="script.js">` (script local do projeto)

**Ao terminar:** "✅ Fase 7 concluída! Posso prosseguir para a Fase 8 (Modais)? Algum ajuste necessário nesta estrutura de localização/footer?"

---

## 📄 FASE 8: MODAIS

**Construir um modal por serviço**, seguindo este padrão:

```html
<!-- Modal [NOME DO SERVIÇO] -->
<div id="modal-[slug-servico]" class="modal-backdrop">
  <div class="modal-content !bg-zinc-900 border border-white/10">
    <span class="close-modal" onclick="closeModal('modal-[slug-servico]')">
      <i class="fa-solid fa-xmark text-xl"></i>
    </span>
    <img src="assets/[imagem-servico].webp" loading="lazy"
         class="w-full h-40 object-cover rounded-2xl mb-6 shadow-md border border-white/10">
    <h2 class="text-2xl font-serif font-bold text-white mb-4 uppercase">[NOME DO SERVIÇO]</h2>
    <p class="text-brand-gray text-sm mb-6 leading-relaxed">[DESCRIÇÃO DO SERVIÇO]</p>
    <div class="space-y-3 mb-8 text-left">
      <!-- 3 bullet points reais do serviço -->
    </div>
    <a href="https://wa.me/55[TEL]?text=Olá, vim do link da bio e tenho interesse em [NOME DO SERVIÇO]. Pode me dar mais informações?"
       target="_blank" class="w-full py-4 rounded-xl bg-brand-main text-white font-bold flex items-center justify-center gap-2 ...">
      AGENDAR AGORA <i class="fa-brands fa-whatsapp text-lg"></i>
    </a>
  </div>
</div>
```

**Modal Tour 360°** (se houver):
```html
<div id="modal-360" class="modal-backdrop">
  <div class="modal-content !p-2 !max-w-3xl !h-[80vh] !bg-zinc-900 border border-white/10">
    <!-- Iframe do tour virtual -->
  </div>
</div>
```

**Modal de Imagem** (sempre incluir se tiver galeria):
```html
<div id="modal-image" class="modal-backdrop">
  <div class="modal-content !bg-transparent !border-none !shadow-none !p-0 !max-w-4xl flex justify-center items-center">
    <span class="close-modal text-white" onclick="closeModal('modal-image')">
      <i class="fa-solid fa-xmark text-2xl"></i>
    </span>
    <img id="popup-img" src="" alt="Preview" class="max-w-full max-h-[85vh] object-contain rounded-2xl animate-modalZoom">
  </div>
</div>
```

**Ao terminar:** "✅ Fase 8 concluída! Posso prosseguir para a Fase 9 (CSS)? Deseja que eu adicione algum detalhe extra nos popups?"

---

## 📄 FASE 9: CSS (style.css)

Construir o arquivo `style.css` **completo** com:

1. **Variáveis CSS `:root`** com as cores do cliente
2. **Proteção de conteúdo** (user-select, tap-highlight)
3. **WhatsApp Float** (.whatsapp-float, .whatsapp-notify)
4. **Dark Mode / Light Mode — FUNCIONAMENTO PERFEITO OBRIGATÓRIO**

   O toggle de tema deve funcionar em **100% dos elementos** da página. Nenhum elemento pode "quebrar" ao trocar de tema.

   ### Estrutura obrigatória do sistema de temas

   **`:root` (Dark — padrão):**
   ```css
   :root {
     --brand-main: [COR PRIMÁRIA];
     --brand-hover: [COR HOVER];
     --brand-accent: [COR FUNDO CARD];
     --brand-dark: [COR TEXTO PRINCIPAL];      /* ex: #ffffff no dark */
     --brand-gray: [COR TEXTO SECUNDÁRIO];     /* ex: #a1a1aa no dark */
     --brand-light: [COR FUNDO GERAL];         /* ex: #09090b no dark */
     --brand-card: [COR FUNDO CARD];           /* ex: #18181b no dark */
     --brand-border: [COR BORDA];              /* ex: rgba(255,255,255,0.1) no dark */
   }
   ```

   **`[data-theme="light"]` (Light mode — overrides):**
   ```css
   [data-theme="light"] {
     --brand-dark: #1a1a1a;           /* texto escuro */
     --brand-gray: #52525b;           /* texto secundário */
     --brand-light: #f4f4f5;          /* fundo geral claro */
     --brand-card: #ffffff;           /* cards brancos */
     --brand-border: rgba(0,0,0,0.08); /* bordas sutis */
     /* brand-main e brand-hover MANTÊM a cor da marca */
   }
   ```

   ### Regras de cobertura total do tema

   | Elemento | Dark | Light |
   |----------|------|-------|
   | Fundo do body / root | `var(--brand-light)` | `var(--brand-light)` |
   | Texto principal | `var(--brand-dark)` | `var(--brand-dark)` |
   | Texto secundário | `var(--brand-gray)` | `var(--brand-gray)` |
   | Cards e seções | `var(--brand-card)` | `var(--brand-card)` |
   | Bordas | `var(--brand-border)` | `var(--brand-border)` |
   | Botões da marca | `var(--brand-main)` | `var(--brand-main)` — mantém |
   | Ticker | fundo escuro adaptado | fundo claro adaptado |
   | Modais | `!bg-zinc-900` no dark | `!bg-white` no light |
   | Hero background | gradiente escuro | gradiente claro |
   | Glass effect | blur + branco/10 | blur + preto/5 |
   | Scrollbar | dark | light |
   | Avaliações cards | dark card | white card com sombra |

   ### Overrides adicionais para Light Mode (após `[data-theme="light"]`):
   ```css
   [data-theme="light"] .glass {
     background: rgba(255, 255, 255, 0.7);
     border-color: rgba(0, 0, 0, 0.08);
   }
   [data-theme="light"] .modal-content {
     background: #ffffff !important;
     color: #1a1a1a;
   }
   [data-theme="light"] .modal-content p,
   [data-theme="light"] .modal-content span {
     color: #52525b;
   }
   [data-theme="light"] h1,
   [data-theme="light"] h2,
   [data-theme="light"] h3 {
     color: #1a1a1a;
   }
   ```

   > **Regra de ouro:** NUNCA usar cores hardcoded (ex: `text-white`, `bg-zinc-900`) em elementos que devem mudar com o tema. Usar sempre `var(--brand-dark)`, `var(--brand-card)`, etc. Exceções permitidas apenas em elementos que devem ser sempre escuros (ex: botão WhatsApp, modal de vídeo).

5. **Glassmorphism** (.glass)
7. **Modal** (.modal-backdrop, .modal-content, .close-modal)
8. **Animações:**
   - `.hover-lift` (cards elevam no hover)
   - `.reveal` (fade-up no scroll)
   - `.pulse-custom-slow` (pulsação do botão WhatsApp)
   - `@keyframes scrollReviews` + `.animate-scroll` (avaliações infinitas)
   - `@keyframes modalIn` (entrada dos modais)
9. **Theme Toggle** (.theme-toggle)
10. **Ticker de boas-vindas** (.welcome-ticker, .ticker-content, @keyframes tickerScroll)
11. **Galeria de Vídeos** (se aplicável: .video-carousel, .video-slide, .video-player, etc.)
12. **Galeria de Fotos** (.active-dot para o carousel)
13. **Comparador Antes/Depois** (se aplicável: .image-comparison-container, .comparison-slider)
14. **Efeito visual de fundo** (adaptado ao nicho: o Vasquez tem chamas, outros podem ter partículas, gradientes, etc.)
15. **Scrollbar customizada**
16. **Tipografia** (.font-serif, .micro-label, h1/h2/h3)

> **Regra:** O CSS deve conter APENAS o que o projeto usa. Não copiar estilos de seções que foram omitidas.

**Ao terminar:** "✅ CSS concluído! O projeto está tecnicamente pronto. Podemos avançar para o checklist final no módulo `03-entrega.md`?"

> Após confirmação do CSS, carregar o módulo `03-entrega.md` para o checklist final e entrega.

---

*Módulo 02-C — AG5 Agência | Links 360 Premium*
