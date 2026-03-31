---
name: Links360-Construcao-A
description: Módulo de construção das Fases 1 a 3 do Links 360. REGRA ABSOLUTA: Copiar o código do template Vasques Auto Center como base, substituindo APENAS dados do cliente. Nunca inventar layouts.
type: project
---

# MÓDULO 02-A — CONSTRUÇÃO: FASES 1, 2 E 3

> ⚠️ **REGRA DE OURO — TEMPLATE-FIRST (INEGOCIÁVEL)**
> Antes de escrever UMA LINHA de HTML, o agente DEVE:
> 1. Abrir e ler o arquivo: `C:\Users\mauri\Documents\00 Processo Landing Pages\04 - Links 360\vasques-auto-center\index.html`
> 2. Copiar TODA a estrutura como ponto de partida
> 3. Substituir **APENAS**: cores no `:root` do CSS (conforme o DNA escolhido), textos, `src` de imagens, `href` de links e dados do Schema
> 4. NÃO mudar classes, NÃO mudar tamanhos, NÃO mudar estrutura de elementos
> 5. **REGRA DE CONFIRMAÇÃO:** Nunca avance para o próximo bloco sem o OK explícito do usuário. Reporte o progresso detalhadamente para evitar perda de contexto.

---

## 🚫 O QUE É PROIBIDO

- **NUNCA** alterar classes de tamanho dos botões (`h-24`, `rounded-2xl`, `text-3xl`, etc.)
- **NUNCA** usar fundo claro (`bg-brand-light`, `bg-white`) nos botões de links e cards
- **NUNCA** inventar um componente visual que não existe no Vasques sem consultar o usuário
- **NUNCA** trocar o `bg-zinc-900` por outra cor de fundo em botões secundários
- **NUNCA** criar seções com bordas arredondadas grandes (`rounded-3xl`), glassmorphism ou gradientes verticais que não existem no Vasques
- **NUNCA** reorganizar a ordem das seções já existentes no Vasques

## ✅ O QUE É PERMITIDO (Adições Sutis)

- **OMITIR** seções do Vasques quando o cliente não tiver o recurso (sem víeos → sem seção de víeos; sem antes/depois → without essa seção)
- **ADICIONAR** um botão de link extra (LinkedIn, TikTok, YouTube) usando o **HTML idêntico** dos botões `h-24` existentes
- **ADICIONAR** uma seção nova contextual relevante ao nicho, **SE E SOMENTE SE:**
  1. O cliente tiver uma informação que não cabe em nenhuma seção existente do Vasques
  2. O agente informar ao usuário: *"Identifiquei que [RAZÃO]. Proponho adicionar [SEÇÃO] após [SEÇÃO EXISTENTE]. Aprova?"*
  3. A estrutura visual da nova seção copiar o componente mais similar do Vasques como base
  4. Nenhuma classe nova for inventada — apenas substituição de conteúdo
- **ADAPTAR** textos e números ao contexto do cliente (ex: "Alinhamento 3D" → "Usucapião")

---

## ✅ O QUE MUDAR — MAPEAMENTO CIRÚRGICO

### 1. `style.css` — DNA de Cores

Copiar o `style.css` do Vasques para o novo projeto. Alterar **SOMENTE** as variáveis no `:root` e no `body.dark-mode`:

```css
/* SUBSTITUIR APENAS ESTAS LINHAS: */
:root {
    --brand-main: [COR PRIMÁRIA DO CLIENTE];     /* era: #FF6600 */
    --brand-hover: [COR SECUNDÁRIA/DESTAQUE];    /* era: #E5A500 */
    /* MANTER O RESTO IDÊNTICO */
}

body.dark-mode {
    --brand-main: [MESMA COR PRIMÁRIA];
    --brand-hover: [MESMA COR SECUNDÁRIA];
    /* MANTER O RESTO IDÊNTICO */
}
```

> **Não alterar** `.hover-lift`, `.reveal`, `.pulse-custom-slow`, `.modal-*`, `.video-*` nem nenhuma outra classe.

---

### 2. `<head>` — Meta e Schema

Substituir literalmente, mantendo a mesma estrutura:

| Campo | Vasques (original) | Novo cliente |
|---|---|---|
| `<title>` | Vasques Auto Center | Nome do Cliente |
| `<meta name="description">` | Descrição da oficina | Descrição do negócio |
| `og:title` | Vasques Auto Center | Nome do Cliente |
| `og:image` | `assets/galeria-oficina-bangu-17.webp` | Melhor foto do cliente |
| Schema `"@type"` | `"AutoRepair"` | Tipo correto (ex: `"LegalService"`) |
| Schema `"telephone"` | `+5521964779051` | Telefone do cliente |
| Schema `"address"` | Endereço Bangu | Endereço do cliente |

---

### 3. Ticker (Welcome Ticker)

Manter a estrutura de `<div class="welcome-ticker">` **idêntica**. Substituir apenas o conteúdo dos `<span>`:

```html
<!-- VASQUES (original) -->
<span>Oficina Mecânica Especializada</span>
<span class="separator">|</span>
<span>Alinhamento 3D</span>

<!-- NOVO CLIENTE (substituição) -->
<span>[Nicho/Especialidade Principal]</span>
<span class="separator">|</span>
<span>[Especialidade 2]</span>
```

> Duplicar o conjunto para o loop infinito, exatamente como no Vasques.

---

### 4. Background Effect

- **Automotivo / Fitness / Energia:** Manter o `exhaust-fire-container` do Vasques  
- **Jurídico / Médico / Beleza:** Remover o `exhaust-fire-container` completamente (não substituir por outro)  
- **Nunca criar** um novo efeito de background não previsto no Vasques  

---

### 5. Botões Theme Toggle e Music Toggle

Manter **idênticos** ao Vasques. Se o cliente não tiver música: manter o botão de música oculto visualmente via CSS (`display: none`), não remover o HTML.

---

### 6. Hero Section

Manter a estrutura `<section style="background: var(--bg-hero, transparent);" class="relative flex flex-col items-center text-center pt-8 pb-10 px-4 reveal">` **idêntica**.

Substituições permitidas:

| Elemento | Substituição |
|---|---|
| `src` da imagem circular | Foto de perfil/logo do cliente |
| `alt` da imagem | Nome do cliente |
| `data-config="negocio.nome"` texto | Nome do cliente |
| `data-config="negocio.subtitulo"` texto | Subtítulo do nicho do cliente |
| `data-config="negocio.descricao"` texto | Descrição curta do cliente |
| `data-config="negocio.statusBadge"` texto | Tagline do status do cliente |

> **Não mudar** `w-40 h-40`, `rounded-full`, `bg-brand-main`, nem nenhuma outra classe do hero.

---

### 7. Botão WhatsApp Principal

Manter **identicamente** a estrutura `h-24 bg-gradient-to-r from-[...] to-[...] text-white shadow-xl pulse-custom-slow`.

Substituir:
- `href` com o link de WhatsApp do cliente (com mensagem pré-preenchida adequada ao nicho)
- `data-config="link.whatsapp.subtitulo"` texto: etiqueta de topo (ex: "Solicitar Orientação")
- `data-config="link.whatsapp.label"` texto: label principal (ex: "Falar com Dra. Nohana")

> **Regra OAB:** Trocar as cores do gradiente de laranja para a cor brand do cliente. Não adicionar badge pulsante vermelho.

---

### 8. Botões de Contato Rápido (Grid 2 Colunas)

Manter **identicamente** o `<div class="grid grid-cols-2 gap-3">`. Substituir apenas:
- `href="tel:..."` com o telefone do cliente
- Manter `downloadVCard()` para salvar contato

---

### 9. Botões H-24 de Links Secundários

Cada link usa **exatamente** este HTML (copiado do Vasques):

```html
<a href="[URL]" target="_blank"
   class="relative inline-flex items-center justify-center gap-4 rounded-2xl transition-all duration-300 transform active:scale-95 cursor-pointer group overflow-hidden h-24 bg-zinc-900 hover:bg-zinc-800 text-white shadow-xl border border-white/10 px-6 w-full">
    <div class="absolute -right-4 -bottom-4 opacity-10 transform rotate-12 group-hover:scale-110 transition-transform duration-500">
        <i class="fa-[tipo] fa-[ícone] text-8xl"></i>
    </div>
    <div class="shrink-0 z-10 transition-transform duration-300 group-hover:rotate-12">
        <i class="fa-[tipo] fa-[ícone] text-3xl"></i>
    </div>
    <div class="flex flex-col items-start z-10 text-left flex-1">
        <span class="text-[10px] uppercase tracking-widest font-bold mb-1 opacity-70 text-white/70">[SUBTÍTULO]</span>
        <span class="font-bold leading-tight text-xl uppercase font-serif">[LABEL PRINCIPAL]</span>
    </div>
    <div class="ml-auto pl-2 opacity-60 z-10 group-hover:opacity-100 group-hover:translate-x-1 transition-all">
        <i class="fa-solid fa-chevron-right text-brand-main"></i>
    </div>
</a>
```

**Ordem padrão dos botões (mantendo essa sequência):**
1. Site Oficial → `fa-globe`
2. Google Meu Negócio → `fa-brands fa-google`
3. Instagram → `fa-brands fa-instagram`
4. Facebook → `fa-brands fa-facebook` *(se tiver)*
5. LinkedIn → `fa-brands fa-linkedin` *(se tiver — adicionar ABAIXO do Instagram, mesmo padrão de HTML)*
6. Tour Virtual / outros → `fa-street-view` *(se tiver)*

> Se o cliente tiver um link que o Vasques não tem (ex: LinkedIn), criar mais um botão com **o mesmo HTML acima**, trocando apenas o ícone e os textos. Nunca criar um botão diferente.

---

### 10. Galeria de Vídeos

Manter a **estrutura completa** do `<section id="video-gallery" class="reveal video-gallery-section">` do Vasques.

Substituições:
- Trocar `<source src="assets/video-[nome-vasques].mp4">` pelos vídeos do cliente
- Trocar `<div class="video-label">` pelo label correspondente

Regra: **1 `<div class="video-slide">` por vídeo** que o cliente tiver. Não criar nem fictício.

Se **não houver vídeos**: omitir a section inteira sem substituir por nada.

---

### 11. Diferenciais (Grid 2x2)

Manter a estrutura `<div class="grid grid-cols-2 gap-4">` e os cards `<div class="flex flex-col items-center p-6 bg-[#18181b] rounded-[2rem] ...">` **idênticos**.

Substituir apenas:
- `<i class="fa-solid fa-[ícone]">` → ícone relevante ao nicho
- Texto do `<span>` → diferencial real do cliente

---

## 📣 PAUSA OBRIGATÓRIA — AGUARDAR CONFIRMAÇÃO

**NUNCA avance para a próxima fase sem o OK explícito. O objetivo é garantir que cada bloco esteja perfeito antes de seguir, evitando retrabalho e sobrecarga de contexto.**

**Fase 1:** "✅ Head + Ticker + Hero prontos. Posso avançar para a Fase 2 (botões de links)?"  
**Fase 2:** "✅ WhatsApp + grid contatos + botões de links prontos. Posso avançar para a Fase 3 (vídeos + diferenciais)?"  
**Fase 3:** "✅ Galeria de vídeos + diferenciais prontos. Deseja realizar algum ajuste nestas seções ou posso carregar o módulo `02-construcao-B.md` para as Fases 4, 5 e 6?"

---

*Módulo 02-A — AG5 Agência | Links 360 Premium | Versão Template-First*
