---
name: seo-lp-builder
description: Gerador de páginas de serviço com SEO técnico completo para landing pages premium. Cria página hub /servicos + páginas individuais por serviço com Schema JSON-LD, meta tags, FAQ estruturado e copy focado em keyword. Integra com o design system existente do projeto.
allowed-tools: Read, Write, Edit, Glob, Grep, Bash
---

# SEO LP Builder — Gerador de Páginas de Serviço

> Cria páginas de serviço elegantes e altamente ranqueáveis. Cada página é uma "porta de entrada" independente no Google.

## Filosofia

> "Uma página por serviço. Cada página = uma keyword. Cada keyword = um cliente em potencial."

A landing page principal converte. As páginas de serviço **encontram o cliente antes** da decisão de compra.

---

## Mapa de Arquivos — Leia Apenas o Necessário

| Arquivo | Descrição | Quando Ler |
|---------|-----------|------------|
| `briefing-template.md` | Formulário de entrada do projeto | Início — coletar dados do cliente |
| `seo-rules.md` | Regras técnicas de SEO obrigatórias | Antes de gerar qualquer página |
| `page-structure.md` | Arquitetura seção por seção de cada página | Ao construir o HTML |
| `schema-templates.md` | Schemas JSON-LD prontos por segmento | Ao adicionar dados estruturados |
| `qa-checklist.md` | Checklist sim/não de validação final | Antes de entregar ao cliente |

---

## Fluxo de Execução

```
1. BRIEFING      → Preencher / receber briefing-template.md
2. SEO PLAN      → Definir keyword principal de cada serviço
3. GENERATE HUB  → Criar /servicos (página índice)
4. GENERATE EACH → Criar /servicos/[slug] para cada serviço
5. SCHEMA        → Injetar JSON-LD correto em cada página
6. QA            → Passar pelo qa-checklist.md
7. ENTREGA       → Confirmar estrutura e passar para 03 - LP Concluídas
```

---

## Estrutura de Saída

```
[projeto]/
├── index.html                          ← LP principal (já existe)
├── servicos/
│   ├── index.html                      ← Hub de serviços
│   ├── [slug-servico-1]/
│   │   └── index.html                  ← Página individual
│   ├── [slug-servico-2]/
│   │   └── index.html
│   └── ...
├── sobre/
│   └── index.html                      ← Página Sobre (E-E-A-T)
└── contato/
    └── index.html                      ← Página Contato
```

---

## Regras Anti-Genérico (Obrigatórias)

Estas regras se aplicam MESMO em páginas de serviço:

1. **Tipografia marcante** — H1 com font-size >= 3rem, nunca serif padrão genérico
2. **Hero diferenciado** — Não usar foto de stock de advogado/médico com terno
3. **Cor de destaque aplicada** — Keyword ou frase de impacto com `color: var(--accent)`
4. **Animação de entrada** — Pelo menos fade-up no H1, não fade simples
5. **Seção de FAQ visual** — Não lista pura, usar acordeão com transição

---

## Segmentos Suportados

| Segmento | Schema Principal | Keywords Típicas |
|----------|-----------------|-----------------|
| Advocacia | `LegalService` | "advogado [área] [cidade]" |
| Odontologia | `Dentist` | "dentista [especialidade] [cidade]" |
| Estética | `HealthAndBeautyBusiness` | "[serviço] estética [cidade]" |
| Automotivo | `AutoRepair` | "[serviço] carro [cidade]" |
| Contabilidade | `ProfessionalService` | "contador [serviço] [cidade]" |
| Outros | `LocalBusiness` | "[serviço] [cidade]" |

---

## Agentes Relacionados

| Agente | Quando Usar |
|--------|-------------|
| `seo-specialist` | Auditoria após geração, análise de keywords |
| `frontend-specialist` | Ajustes de componentes e animações |
| `performance-optimizer` | Core Web Vitals < 2.5s LCP |
