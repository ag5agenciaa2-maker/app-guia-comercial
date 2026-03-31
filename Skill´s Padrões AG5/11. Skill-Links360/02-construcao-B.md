---
name: Links360-Construcao-B
description: Módulo de construção das Fases 4, 5 e 6 do Links 360. REGRA ABSOLUTA: Usar o código do Vasques como base. Apenas substituir dados. Nunca inventar componentes.
type: project
---

# MÓDULO 02-B — CONSTRUÇÃO: FASES 4, 5 E 6

> ⚠️ **REGRA DE OURO — TEMPLATE-FIRST (INEGOCIÁVEL)**
> Todo componente desta fase existe no Vasques. Copie-o. Substitua SOMENTE: textos, imagens, links, cores.
> **REGRA DE CONFIRMAÇÃO:** Nunca avance para a próxima fase ou módulo sem o OK explícito do usuário. Pare e pergunte após cada bloco.

---

## 📄 FASE 4: ANTES/DEPOIS + AVALIAÇÕES GOOGLE

### 4A — Seção Antes/Depois

Copiar a `<section class="py-8 reveal" style="background-color: var(--bg-caixas, ...)">` do Vasques.

| O que substituir | Vasques | Novo cliente |
|---|---|---|
| Título h2 | "Excelência no Antes e Depois" | Título relevante ao nicho |
| Texto descritivo (`<p>`) | "Veja a diferença que o cuidado técnico..." | Texto relevante |
| `src` da imagem "Depois" | `assets/galeria-oficina-bangu-4.webp` | Imagem de resultado do cliente |
| `src` da imagem "Antes" | `assets/galeria-oficina-bangu-15.webp` | Imagem de situação inicial |
| Benefício 01 → título | "Resultados Visíveis" | Benefício real do cliente |
| Benefício 01 → texto | "Soluções definitivas..." | Texto real |
| Benefício 02 → título | "Transparência Total" | Benefício real 2 |
| Benefício 02 → texto | "Você acompanha a evolução..." | Texto real |

> **Se não houver imagens Antes/Depois:** Omitir a seção completamente (sem criar nada no lugar). Informar o usuário no relatório final que faltam imagens.

---

### 4B — Cards de Avaliações Google

Copiar a `<section class="py-8 overflow-hidden reveal">` de avaliações do Vasques, **incluindo** a estrutura `<div class="animate-scroll flex gap-6 py-2 pb-8 px-1">`.

Cada card segue exatamente este HTML:

```html
<div class="min-w-[300px] bg-[#18181b] p-6 rounded-[2rem] border border-white/5 shadow-sm flex flex-col justify-between relative">
    <div>
        <div class="absolute top-6 right-6 opacity-30">
            <i class="fa-brands fa-google text-xs"></i>
        </div>
        <div class="flex items-center gap-1 mb-3 text-brand-main text-[10px]">
            <i class="fa-solid fa-star"></i>
            <i class="fa-solid fa-star"></i>
            <i class="fa-solid fa-star"></i>
            <i class="fa-solid fa-star"></i>
            <i class="fa-solid fa-star"></i>
        </div>
        <p class="text-white text-[13px] leading-relaxed mb-4 italic">
            "[TEXTO DA AVALIAÇÃO REAL DO CLIENTE]"
        </p>
    </div>
    <div class="flex items-center gap-3 border-t border-white/10 pt-4">
        <div class="w-10 h-10 rounded-full bg-[#27272a] flex items-center justify-center font-bold text-brand-main">
            [INICIAIS]
        </div>
        <div>
            <h4 class="font-bold text-sm text-brand-dark">[NOME DO AVALIADOR]</h4>
            <p class="text-[10px] text-brand-gray">[Local Guide / Cliente Verificado]</p>
        </div>
    </div>
</div>
```

**Duplicar todos os cards** ao final para criar o efeito de scroll infinito (exatamente como no Vasques).

---

### 4C — Link "Avaliar no Google"

Copiar o `<div class="flex justify-center -mt-4 mb-8">` com o link de avaliação do Vasques:

```html
<div class="flex justify-center -mt-4 mb-8">
    <a href="https://search.google.com/local/writereview?placeid=[PLACE_ID_DO_CLIENTE]"
       target="_blank"
       class="inline-flex items-center gap-2 text-white text-[10px] uppercase tracking-widest font-bold opacity-90 hover:opacity-100 transition-opacity border-b border-white/20 pb-1">
        <i class="fa-regular fa-star text-brand-main"></i> Avaliar [Nome do Negócio] no Google
    </a>
</div>
```

---

## 📄 FASE 5: SERVIÇOS / PRODUTOS

### Nomenclatura por Nicho

- **Advocacia / Consultoria / Saúde:** usar "Serviços" ou "Áreas de Atuação"
- **Comércio / Restaurante:** usar "Produtos" ou "Cardápio"

### Grid de Serviços (2x2 — OBRIGATÓRIO)

Copiar a `<section class="py-12 reveal">` de serviços do Vasques, com a `<div class="grid grid-cols-2 gap-4">`.

Cada card de serviço segue exatamente este HTML:

```html
<div class="group relative flex flex-col bg-[#18181b] rounded-[2rem] overflow-hidden shadow-sm border border-white/5 transition-all duration-300">
    <div class="relative w-full h-36 overflow-hidden border-b border-white/5">
        <img src="assets/[IMAGEM-DO-SERVIÇO].webp"
             alt="[Nome do Serviço]"
             loading="lazy"
             class="w-full h-full object-cover group-hover:scale-110 transition-transform duration-700">
        <div class="absolute inset-0 bg-gradient-to-t from-black/90 via-black/40 to-transparent"></div>
        <h3 class="absolute bottom-3 left-3 text-white font-bold text-[11px] uppercase tracking-tight">
            [NOME DO SERVIÇO]
        </h3>
    </div>
    <div class="p-4 flex flex-col flex-1">
        <button onclick="openModal('modal-[slug-servico]')"
                class="mt-auto flex items-center text-brand-main text-[10px] font-bold gap-2 group-hover:translate-x-1 transition-transform">
            SAIBA MAIS <i class="fa-solid fa-arrow-right text-[8px]"></i>
        </button>
    </div>
</div>
```

**Regra de quantidade:**
- Se tiver 5 serviços → 5 cards normais + 1 card especial com logo (ver abaixo)
- Se tiver 6+ → usar os 6 principais
- Se tiver menos de 4 → completar com subáreas/variações ou PERGUNTAR ao usuário

**Card especial com logo (slot 6):**

```html
<div class="group relative flex flex-col bg-[#18181b] rounded-[2rem] overflow-hidden shadow-sm border border-white/5 transition-all duration-300 cursor-pointer hover-lift"
     onclick="openModal('modal-sobre')">
    <div class="flex items-center justify-center h-full p-6 aspect-square">
        <img src="assets/[LOGO-DO-CLIENTE].webp"
             alt="[Nome do Cliente]"
             class="max-w-[75%] max-h-[75%] object-contain opacity-70 group-hover:opacity-100 transition-opacity">
    </div>
    <div class="p-4 pt-0 text-center">
        <h3 class="text-white font-bold text-[11px] uppercase tracking-tight">[Nome do Cliente]</h3>
        <span class="text-brand-main text-[9px] font-bold uppercase tracking-widest mt-1 block">Conheça nossa história →</span>
    </div>
</div>
```

### Modais de Serviços

Copiar a estrutura `<div class="modal-backdrop" id="modal-[slug]">` do Vasques para cada serviço. Substituir:
- `id` do modal → `modal-[slug-serviço]`
- `src` da imagem do modal → foto do serviço
- Título, descrição, lista de benefícios → dados reais do cliente
- Link WhatsApp do botão CTA → link com mensagem específica do serviço:  
  `"Olá, vim do link da bio e tenho interesse em [NOME DO SERVIÇO]. Pode me dar mais informações?"`

---

## 📄 FASE 6: SOBRE / GALERIA DE FOTOS

### Seção Sobre

Copiar a seção `<section class="py-12 reveal">` com histórico da empresa do Vasques. Substituir apenas:
- Título e subtítulo
- Estatísticas reais (anos de mercado, casos, clientes atendidos)
- Texto de história/missão do cliente

> Se o cliente não forneceu stats: PERGUNTAR antes de inventar números.

### Galeria de Fotos

Copiar o `<section id="galeria">` com carousel horizontal do Vasques. Substituir apenas os `src` das imagens.

- Um item por foto disponível
- **Não criar slots vazios** com `src` ficticios
- Se não houver fotos da galeria: omitir a seção

---

## 📣 PAUSA OBRIGATÓRIA — AGUARDAR CONFIRMAÇÃO

**NUNCA avance para a próxima fase sem o OK explícito. O objetivo é manter a qualidade e o controle do usuário sobre cada seção.**

**Fase 4:** "✅ Antes/Depois + Avaliações prontos. Posso avançar para a Fase 5 (serviços)?"  
**Fase 5:** "✅ Grid de serviços + modais prontos. Posso avançar para a Fase 6 (sobre + galeria)?"  
**Fase 6:** "✅ Sobre + galeria prontos. Deseja ajustar algo ou posso carregar o módulo `02-construcao-C.md` para Fases 7, 8 e 9?"

---

*Módulo 02-B — AG5 Agência | Links 360 Premium | Versão Template-First*
