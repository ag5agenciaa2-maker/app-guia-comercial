# QA Checklist — Páginas de Serviço SEO

> Checklist objetivo. Resposta apenas: ✅ SIM | ❌ NÃO | ⚠️ PARCIAL
> **Regra:** Nenhum item pode estar ❌ na entrega. ⚠️ deve ter justificativa.

---

## BLOCO A — SEO TÉCNICO

### Meta Tags
- [ ] `<title>` tem entre 50 e 60 caracteres?
- [ ] `<title>` começa com a keyword principal?
- [ ] `<meta name="description">` tem entre 150 e 160 caracteres?
- [ ] Description inclui keyword e CTA?
- [ ] `<link rel="canonical">` aponta para a URL correta da página?
- [ ] URL da página está em kebab-case sem acentos?
- [ ] URL inclui a keyword ou parte dela?

### Headings
- [ ] Existe exatamente **1 (um)** `<h1>` na página?
- [ ] O `<h1>` contém a keyword principal (exata ou variação)?
- [ ] A hierarquia H1 → H2 → H3 está correta (sem pular níveis)?
- [ ] Pelo menos 1 `<h2>` contém keyword secundária?

### Conteúdo
- [ ] A keyword aparece nos primeiros 100 words do conteúdo visível?
- [ ] A página tem no mínimo 600 palavras de texto?
- [ ] O texto soa natural (keyword não está sendo forçada)?
- [ ] Existem variações semânticas da keyword no texto?

### Links Internos
- [ ] Existe breadcrumb funcional e visível abaixo do navbar?
- [ ] Existe link para `/servicos` (hub)?
- [ ] Existem links para pelo menos 2 serviços relacionados no final?

---

## BLOCO B — SCHEMA JSON-LD

- [ ] Schema `LocalBusiness` (ou tipo correto do segmento) está no `<head>`?
- [ ] Schema `Service` com dados deste serviço específico está no `<head>`?
- [ ] Schema `FAQPage` com todas as perguntas está no `<head>`?
- [ ] Schema `BreadcrumbList` está no `<head>`?
- [ ] As perguntas no JSON-LD são **idênticas** ao texto visível no HTML?
- [ ] Todos os campos `[COLCHETES]` foram substituídos pelos dados reais?
- [ ] Schema foi validado no Google Rich Results Test? *(opcional mas recomendado)*

---

## BLOCO C — CONTEÚDO E ESTRUTURA

### Seções Obrigatórias
- [ ] Breadcrumb presente?
- [ ] Hero com H1, subtítulo e CTA está presente?
- [ ] Seção "O que é / Sobre o Serviço" presente?
- [ ] Seção "Dor + Solução" presente?
- [ ] Seção "Como Funciona" (passo a passo) presente?
- [ ] Seção de Diferenciais presente?
- [ ] Seção de Credenciais/E-E-A-T presente?
- [ ] Seção de Depoimento presente?
- [ ] Seção de FAQ com acordeão presente?
- [ ] Seção de Outros Serviços (links relacionados) presente?
- [ ] CTA Final antes do footer presente?

### FAQ
- [ ] Mínimo de 5 perguntas e respostas?
- [ ] Acordeão funciona corretamente (abre e fecha)?
- [ ] Perguntas são relevantes ao serviço e ao público?

---

## BLOCO D — DESIGN E ANTI-GENÉRICO

- [ ] H1 tem font-size >= 3rem (tipografia marcante)?
- [ ] Existe pelo menos 1 elemento com `color: var(--accent)` destacando keyword/frase?
- [ ] O hero usa animação de entrada (não é estático)?
- [ ] A animação não é simplesmente `opacity: 0 → 1` sem movimento?
- [ ] As cores do design system da LP principal foram mantidas?
- [ ] Fontes são as mesmas da LP principal?
- [ ] O layout da página não é genérico (não parece um template WordPress)?

---

## BLOCO E — IMAGENS

- [ ] Imagem do hero tem `loading="eager"` e `fetchpriority="high"`?
- [ ] Todas as outras imagens têm `loading="lazy"`?
- [ ] Todas as imagens têm atributo `alt` descritivo (não vazio)?
- [ ] Alt da imagem principal contém a keyword?
- [ ] Todas as imagens têm `width` e `height` definidos?
- [ ] Não existe texto placeholder (Lorem Ipsum)?

---

## BLOCO F — PERFORMANCE

- [ ] Fontes Google Fonts têm `<link rel="preconnect">` antes de carregar?
- [ ] Fontes têm `&display=swap` na URL?
- [ ] Não há JavaScript bloqueante no `<head>` (scripts sem `defer` ou `async`)?
- [ ] CSS está em arquivo externo ou no `<head>` (não inline no body)?

---

## BLOCO G — CONVERSÃO

- [ ] Existe CTA para WhatsApp no Hero (topo)?
- [ ] Existe CTA para WhatsApp no meio da página?
- [ ] Existe CTA para WhatsApp no Final (antes do footer)?
- [ ] O número de WhatsApp está correto com DDD?
- [ ] O link do WhatsApp abre no formato `https://wa.me/55[DDD][NUMERO]`?
- [ ] O WhatsApp tem mensagem pré-preenchida relevante ao serviço?
- [ ] O link do WhatsApp tem `target="_blank"` e `rel="noopener"`?

---

## BLOCO H — RESPONSIVO

- [ ] A página é legível em tela de 375px (iPhone SE)?
- [ ] O Hero empilha verticalmente no mobile?
- [ ] O grid de serviços vira 1 coluna no mobile?
- [ ] O FAQ está usável em telas pequenas?
- [ ] O navbar mobile (hamburguer) funciona?
- [ ] Nenhum texto está cortado ou sobreposto no mobile?

---

## BLOCO I — ENTREGA FINAL

- [ ] Pasta do projeto está em `03 - LP Concluídas`?
- [ ] Arquivo `blueprint.md` atualizado com as novas páginas?
- [ ] `sitemap.xml` inclui as novas URLs?
- [ ] `robots.txt` está configurado corretamente?
- [ ] Screenshot da versão desktop salvo?
- [ ] Screenshot da versão mobile salvo?

---

## RESUMO DE APROVAÇÃO

| Bloco | Total | ✅ OK | ❌ Falhou |
|-------|-------|-------|----------|
| A — SEO Técnico | 14 | | |
| B — Schema JSON-LD | 7 | | |
| C — Conteúdo | 16 | | |
| D — Design Anti-Genérico | 8 | | |
| E — Imagens | 6 | | |
| F — Performance | 5 | | |
| G — Conversão | 7 | | |
| H — Responsivo | 6 | | |
| I — Entrega | 6 | | |
| **TOTAL** | **75** | | |

**Aprovação mínima:** 70/75 (93%). Qualquer item ❌ nos blocos A, B, G é bloqueante.

---

> **Para o gerente:** Se travar em algum item, descreva o problema no campo abaixo e consulte antes de entregar.
>
> **Observações/Bloqueios:**
> ```
>
> ```
