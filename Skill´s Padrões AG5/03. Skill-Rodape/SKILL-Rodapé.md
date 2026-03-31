# SKILL — Rodapé (Footer) AG5

> **Molde de criação de rodapé para landing pages AG5.**
> Baseado na estrutura do site Batista e Calzolari Advogados como referência de qualidade e organização. Use este guia para criar o rodapé de qualquer site, adaptando conteúdo e cores sem alterar a estrutura.

---

## 1. ESTRUTURA GERAL

O rodapé é dividido em **duas seções**:

1. **`footer-main`** — Seção principal com colunas de conteúdo
2. **`footer-bottom`** — Seção de créditos e links legais

---

## 2. COR DO RODAPÉ

> **Regra obrigatória:** A cor de fundo do rodapé deve ser a **cor principal do site escurecida**, para que não se destaque demais nem se misture visualmente com o restante da página.

**Como aplicar:**
- Pegue a cor primária do site (ex: `#1A3A5C`)
- Escureça entre **20% a 40%** usando `color-mix()` ou ajustando manualmente o valor HSL/hex
- Exemplo: cor primária `#1A3A5C` → rodapé `#0D1E2F`

**Hierarquia de cores dentro do rodapé:**
| Elemento | Opacidade / Cor |
|---|---|
| Fundo geral | Cor primária escurecida (ver acima) |
| Borda superior | Cor de destaque do site com 20% opacidade |
| Títulos das colunas (h4) | Cor de destaque/acento do site |
| Links e textos | `rgba(255,255,255, 0.7)` |
| Hover nos links | Cor de destaque/acento do site |
| Texto de copyright | `rgba(255,255,255, 0.5)` |
| Links legais | `rgba(255,255,255, 0.4)` |

---

## 3. SEÇÃO PRINCIPAL — COLUNAS (`footer-main`)

### 3.1 Espaçamentos

| Dispositivo | Padding Top | Padding Bottom | Padding Lateral |
|---|---|---|---|
| Desktop (≥1024px) | `35px` | `30px` | `1.5rem` |
| Tablet (768–991px) | `35px` | `30px` | `1.5rem` |
| Mobile (<767px) | `40px` | `30px` | `25px` |

### 3.2 Grid de Colunas

| Dispositivo | Layout | Gap entre colunas |
|---|---|---|
| Desktop (≥1024px) | 4 colunas iguais (`repeat(4, 1fr)`) | `2.5rem` |
| Tablet (768–991px) | 2 colunas (`1fr 1fr`) | `2.5rem` |
| Mobile (<767px) | 1 coluna (`1fr`) | `2rem` |

> **Nota:** O container das colunas tem max-width de `1280px` e é centralizado com `margin: 0 auto`.

### 3.3 Ordem das Colunas (Desktop → Mobile)

```
┌───────────────────┬───────────────────┬───────────────────┬──────────────────┐
│  COLUNA 1         │  COLUNA 2         │  COLUNA 3         │  COLUNA 4        │
│  Marca/Identidade │  Links Rápidos    │  Seção de Lista   │  Contato         │
│  .footer-brand    │  .footer-links    │  .footer-links    │  .footer-contact │
└───────────────────┴───────────────────┴───────────────────┴──────────────────┘
```

> No **tablet**, colunas 1+2 ficam na primeira linha e 3+4 na segunda.
> No **mobile**, todas as colunas empilham uma sobre a outra nessa ordem.

---

## 4. COLUNA 1 — MARCA (`.footer-brand`)

**Conteúdo:**
1. Logo da empresa
2. Descrição curta (máx. 5 linhas)
3. Ícones de redes sociais (se houver)

**Logo:**
- Fica alinhada à **esquerda** da coluna
- Em alguns layouts pode ser centralizada horizontalmente dentro da coluna
- Largura máxima: `220px` no desktop, `180px` no mobile
- Altura automática (`height: auto`) para manter proporção
- `object-fit: contain`

**Descrição:**
- Máximo de **5 linhas** de texto
- Font-size: `0.875rem`
- Cor: `rgba(255,255,255, 0.7)`
- Line-height: `1.6`
- Margin-bottom: `1.5rem`

**Redes sociais (se houver):**
- Ícones SVG de `20x20px`
- Alinhados à esquerda
- Hover: cor de destaque + `translateY(-2px)` (leve elevação)

---

## 5. COLUNAS 2 e 3 — LINKS (`.footer-links`)

**Estrutura:**
- Título da coluna em `<h4>`
- Lista de links em `<ul>` / `<li>` / `<a>`

**Estilo dos títulos `<h4>`:**
- Font-size: `0.875rem`
- Font-weight: `600`
- Text-transform: `uppercase`
- Letter-spacing: `0.1em`
- Cor: cor de destaque/acento do site
- Margin-bottom: `1.5rem`

**Estilo dos links:**
- Cor normal: `rgba(255,255,255, 0.7)`
- Cor hover: cor de destaque do site
- Transição: `300ms ease`
- Font-size: `0.875rem`
- Margin-bottom por item: `0.75rem`

---

## 6. COLUNA 4 — CONTATO (`.footer-contact`)

> **Atenção: a ordem dos itens nesta coluna é OBRIGATÓRIA e não deve ser alterada.**

**Título:** "Contato" (segue o mesmo estilo dos `<h4>` das outras colunas)

**Itens em ordem exata:**
1. **Nome da empresa** — com ícone de edifício/prédio (16x16px)
   - Link clicável (ex: Google Meu Negócio ou busca no Google)
   - Abre em `_blank` com `rel="noopener noreferrer"`

2. **Endereço** — com ícone de pin/localização (16x16px)
   - Link clicável apontando para o Google Maps
   - Abre em `_blank` com `rel="noopener noreferrer"`

3. **Telefone principal / WhatsApp** (se houver) — com ícone do WhatsApp (16x16px)
   - Link `href="https://wa.me/55XXXXXXXXXXX?text=..."`
   - Abre em `_blank`

4. **Telefone secundário** (se houver) — com ícone de telefone (16x16px)
   - Link `href="tel:+55XXXXXXXXXX"`

> Se o cliente tiver apenas 1 telefone, usa só o item 3 ou 4 — nunca adicionar campos vazios.

**Estilo dos itens de contato:**
- Display: `inline-flex`
- Align-items: `center`
- Gap entre ícone e texto: `0.5rem`
- Cor: `rgba(255,255,255, 0.7)`
- Hover: cor de destaque do site
- Transição: `300ms ease`
- Font-size: `0.875rem`
- Margin-bottom por item: `0.75rem`

---

## 7. SEÇÃO DE CRÉDITOS (`.footer-bottom`)

**Separador:** linha `1px solid rgba(255,255,255, 0.1)` separando o `footer-main` do `footer-bottom`

**Espaçamentos:**
- Padding-top: `20px`
- Padding-bottom: `20px`

**Layout:**
- Desktop: `flex`, `justify-content: space-between`, `align-items: center`
- Mobile: `flex-direction: column`, `align-items: flex-start`, `gap: 1rem`

### 7.1 Lado Esquerdo (`.footer-credits-left`)

Exibe dois elementos empilhados com gap de `4px`:

**1. Copyright:**
- Formato: `© [ano] [Nome Completo da Empresa]`
- Font-size: `0.75rem`
- Cor: `rgba(255,255,255, 0.5)`

**2. Links legais (`.footer-legal-links`):**
- Exibidos em linha (`display: flex`, `flex-wrap: wrap`)
- Font-size: `11px`
- Cor: `rgba(255,255,255, 0.4)`
- Separador entre links: ` | ` com `margin: 0 10px` e `opacity: 0.3`
- Hover nos links: cor de destaque do site
- Itens na ordem:
  1. Cookies (se houver script de consentimento)
  2. Termos e Condições
  3. Política de Privacidade

### 7.2 Lado Direito (`.footer-credits-right`)

- Texto: `Desenvolvido por AG5 Agência`
- "AG5 Agência" é um link para `https://www.ag5agencia.com.br`
- Font-size: `0.75rem`
- Cor do texto: `rgba(255,255,255, 0.5)`
- Cor do link "AG5 Agência": cor de destaque do site
- Font-weight do link: `600`
- Hover no link: versão mais clara da cor de destaque
- `white-space: nowrap` para não quebrar linha

---

## 8. COMPORTAMENTO MOBILE (< 767px)

Todas as margens e paddings customizados de desktop são zerados. As regras são:

- `.footer-container` → `grid-template-columns: 1fr`, `padding lateral: 0`, `gap: 2rem`
- Todas as colunas → `margin-left: 0`, `padding-left: 0`, `text-align: left`
- `.footer-logo` → `justify-content: flex-start`, margens zeradas
- `.footer-logo img` → `max-width: 180px`, todas as margens zeradas
- `.footer-social` → `justify-content: flex-start`
- `.footer-bottom .footer-container` → `flex-direction: column`, `align-items: flex-start`, `gap: 1rem`
- `.footer-legal-links` → `justify-content: flex-start`
- `.footer-credits-right` → `text-align: left`, `margin-left: 0`

> **Importante:** Usar `!important` nos overrides mobile para garantir que sobrescrevam os ajustes customizados de desktop.

---

## 9. CHECKLIST DE CRIAÇÃO

Antes de finalizar o rodapé, verificar:

- [ ] Cor de fundo é a cor primária do site **escurecida**
- [ ] Borda superior usa a cor de destaque com baixa opacidade
- [ ] Títulos das colunas usam a cor de destaque/acento
- [ ] Coluna 1: logo alinhada à esquerda, descrição com no máximo 5 linhas
- [ ] Coluna 4 (Contato): ordem exata — Nome → Endereço → Telefone(s)
- [ ] Todos os links de contato são clicáveis e apontam para destino correto
- [ ] Seção de créditos: Copyright à esquerda, "Desenvolvido por AG5 Agência" à direita
- [ ] Link "AG5 Agência" aponta para `https://www.ag5agencia.com.br`
- [ ] Layout responsivo testado: desktop (4 colunas), tablet (2 colunas), mobile (1 coluna)
- [ ] No mobile, todas as margens customizadas de desktop estão zeradas com `!important`
