---
name: ag5-site-seo-builder
description: Sistema de expansão SEO em 4 fases para landing pages AG5. Lê o index.html existente, ajusta a seção de serviços, cria hub /servicos, cria página individual por serviço com FAQ + Schema + bairro, e replica para 6 bairros vizinhos. Execução em fases separadas para máxima qualidade e sem invenções.
allowed-tools: Read, Write, Edit, Glob, Grep, Bash
---

# AG5 Site SEO Builder — Expansão em 4 Fases

> Transforma uma landing page simples em uma máquina de SEO local com até 21 páginas otimizadas (1 hub + 3 serviços + 18 bairros), sem inventar conteúdo e sem sair do design do index.

## Filosofia

> "Cada página é uma porta de entrada. Cada bairro é um cliente que ainda não te encontrou."

A LP principal converte quem já te conhece.
Este sistema **encontra quem ainda não conhece** — via busca por serviço + bairro.

---

## REGRA DE OURO — EXECUÇÃO EM FASES

**NUNCA execute mais de uma fase por vez.**

Cada fase termina com uma confirmação antes da próxima começar.
Isso garante qualidade, evita erros em cascata e permite revisão entre etapas.

```
FASE 1 → aguardar aprovação → FASE 2 → aguardar aprovação → FASE 3 → ...
```

---

## Mapa de Arquivos

| Arquivo | Quando Ler |
|---------|------------|
| `fase-1-index.md` | Ao executar Fase 1 |
| `fase-2-hub-servicos.md` | Ao executar Fase 2 |
| `fase-3-pagina-servico.md` | Ao executar Fase 3 |
| `fase-4-paginas-bairro.md` | Ao executar Fase 4 |
| `seo-schema-service.md` | Durante Fases 3 e 4 |
| `sitemap-robots.md` | Ao final da Fase 4 — indexação obrigatória |

---

## Visão Geral das 4 Fases

### FASE 1 — Ajuste do Index
**Input:** `index.html` + briefing
**Output:** `index.html` modificado

- Lê todos os serviços do index
- Define os 3 principais (briefing ou lógica de mercado)
- Se houver > 3 serviços: reduz para os 3 principais + botão "Ver todos os serviços → /servicos"
- Os 3 serviços principais ganham link para `/servicos/[slug]`
- Se houver ≤ 3 serviços: mantém todos, apenas adiciona links

---

### FASE 2 — Hub de Serviços `/servicos`
**Input:** `index.html` (referência de design) + briefing
**Output:** `servicos/index.html`

- Cria página listando TODOS os serviços originais
- Navbar, footer, cores, tipografia: idênticos ao index
- Serviços com página própria (os 3 principais) → link para `/servicos/[slug]`
- Serviços sem página → link direto para WhatsApp com mensagem pré-preenchida

---

### FASE 3 — Páginas Individuais de Serviço (3 páginas)
**Input:** `index.html` (referência) + briefing + dados do serviço
**Output:** `servicos/[slug-servico]/index.html`

Executar **um serviço por vez** — aguardar confirmação entre cada um.

Cada página contém:
- H1: `[Serviço] em [Bairro da Empresa]` ou `[Serviço] — [Cidade]`
- H2s com variações do serviço + contexto local
- Descrição objetiva (só o que vier do cliente — sem inventar)
- 4 perguntas frequentes reais do serviço
- Schema JSON-LD: Service + FAQPage + BreadcrumbList + LocalBusiness
- Seção "Atendemos sua região" com os 6 bairros (links para fase 4)

---

### FASE 4 — Páginas por Bairro (6 páginas por serviço = 18 total)
**Input:** Página do serviço (fase 3) + lista de bairros
**Output:** `servicos/[slug-servico]/[slug-bairro]/index.html`

Executar **um serviço de cada vez, todos os bairros juntos**.

Cada página:
- Clone da página do serviço
- H1, H2, title, description, Schema: trocados para incluir o bairro específico
- Demais conteúdos: iguais ou com adaptação mínima e natural

---

## Estrutura de Saída Final

```
[projeto]/
├── index.html                              ← FASE 1: modificado
├── servicos/
│   ├── index.html                          ← FASE 2: hub de serviços
│   ├── [slug-servico-1]/
│   │   ├── index.html                      ← FASE 3: página do serviço
│   │   ├── [slug-bairro-1]/index.html      ← FASE 4
│   │   ├── [slug-bairro-2]/index.html      ← FASE 4
│   │   ├── [slug-bairro-3]/index.html      ← FASE 4
│   │   ├── [slug-bairro-4]/index.html      ← FASE 4
│   │   ├── [slug-bairro-5]/index.html      ← FASE 4
│   │   └── [slug-bairro-6]/index.html      ← FASE 4
│   ├── [slug-servico-2]/
│   │   ├── index.html
│   │   └── [6 bairros]/
│   └── [slug-servico-3]/
│       ├── index.html
│       └── [6 bairros]/
└── sitemap.xml                             ← atualizado ao final
```

**Total de páginas criadas:** 1 hub + 3 serviços + 18 bairros = **22 páginas**

---

## Agentes Relacionados

| Agente | Quando Usar |
|--------|-------------|
| `seo-specialist` | Revisão de keywords e E-E-A-T após geração |
| `frontend-specialist` | Ajustes de animações e componentes |
| `performance-optimizer` | Validar Core Web Vitals < 2.5s |
