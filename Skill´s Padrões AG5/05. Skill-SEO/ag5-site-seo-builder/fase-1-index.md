# Fase 1 — Ajuste do Index

> Lê o `index.html` existente, identifica os serviços e ajusta a seção para focar nos 3 principais.

---

## PASSO 1 — LER O INDEX

Antes de qualquer mudança, ler o `index.html` completo e extrair:

```
EXTRAIR DO INDEX:
├── Nome da empresa
├── Segmento / área de atuação
├── Cidade e endereço (para fase de bairros)
├── WhatsApp (número exato)
├── Lista de serviços encontrados na página
│   └── Nome, descrição curta (se houver), destaque visual
├── Cores CSS (variáveis ou valores usados)
├── Fontes utilizadas
├── Classes do navbar
├── Classes do footer
└── Classes de botões e cards de serviço
```

Montar um relatório interno antes de modificar qualquer coisa:

```
RELATÓRIO PRÉ-FASE-1:
- Empresa: [nome]
- Segmento: [segmento]
- Cidade: [cidade]
- Endereço: [endereço]
- WhatsApp: [número]
- Serviços encontrados: [lista]
- Total de serviços: [n]
- Decisão: [reduzir para 3 / manter todos]
```

Apresentar este relatório ao usuário e aguardar confirmação antes de modificar.

---

## PASSO 2 — DEFINIR OS 3 SERVIÇOS PRINCIPAIS

### Se o usuário informou quais são os 3 principais:
Usar exatamente os informados. Sem questionar.

### Se o usuário NÃO informou:
Aplicar a lógica de mercado por segmento:

| Segmento | Serviços mais buscados (ordem) |
|----------|-------------------------------|
| Advocacia — Família | Divórcio, Guarda de filhos, Inventário |
| Advocacia — Trabalhista | Rescisão indevida, Assédio moral, Horas extras |
| Advocacia — Criminal | Flagrante, Habeas corpus, Revisão criminal |
| Advocacia — Cível | Dívidas, Indenização, Contratos |
| Advocacia — Previdenciária | Aposentadoria por invalidez, BPC/LOAS, Revisão do INSS |
| Advocacia — Imobiliária | Usucapião, Despejo, Compra e venda |
| Odontologia | Implante dentário, Clareamento, Ortodontia (aparelho) |
| Estética | Botox, Preenchimento labial, Limpeza de pele |
| Automotivo (oficina) | Revisão completa, Freios, Suspensão |
| Contabilidade | Abertura de empresa, Imposto de renda, BPO financeiro |
| Psicologia | Terapia individual, Ansiedade, Depressão |
| Nutrição | Emagrecimento, Reeducação alimentar, Nutrição esportiva |

Se o segmento não estiver na tabela, escolher os 3 serviços que aparecem com **maior destaque visual** no index (maior card, primeiro da lista, título em destaque).

---

## PASSO 3 — LÓGICA DE MODIFICAÇÃO

### Cenário A: Index tem > 3 serviços

1. Manter apenas os 3 serviços principais na seção
2. Adicionar link em cada um apontando para `/servicos/[slug]`
3. Adicionar botão ao final da seção:

```html
<div class="servicos-ver-todos">
  <a href="/servicos" class="btn-outline">
    Ver todos os nossos serviços →
  </a>
</div>
```

O botão deve usar a classe de botão secundário/outline já existente no index.

### Cenário B: Index tem exatamente 3 serviços

1. Manter todos
2. Adicionar link em cada um apontando para `/servicos/[slug]`
3. NÃO adicionar botão "ver todos" (desnecessário)

### Cenário C: Index tem < 3 serviços

1. Manter todos
2. Adicionar links para `/servicos/[slug]`
3. Informar ao usuário: "O index tem apenas [n] serviço(s). Considere adicionar mais serviços ao briefing para maximizar o SEO."

---

## PASSO 4 — REGRAS DE MODIFICAÇÃO DO INDEX

**O que pode ser modificado:**
- Texto dos cards/itens de serviço (apenas para remover os não-principais)
- Adicionar `<a href>` nos cards de serviço
- Adicionar botão "ver todos" ao final da seção de serviços

**O que NÃO pode ser modificado:**
- Layout, cores, fontes, espaçamentos
- Navbar, footer, hero, qualquer outra seção
- Nomes dos serviços (manter exatamente como estão)
- Textos de outras seções que não sejam a de serviços

---

## PASSO 5 — GERAR SLUGS DOS SERVIÇOS

Para cada serviço principal, gerar o slug:

```
Regras:
- Minúsculas
- Hifens no lugar de espaços
- Sem acentos (á→a, ê→e, ç→c, etc.)
- Sem caracteres especiais
- Incluir cidade quando possível para SEO local

Exemplos:
"Divórcio Consensual" + São Paulo → divorcio-consensual-sao-paulo
"Implante Dentário" + Campinas   → implante-dentario-campinas
"Revisão Completa" + Belo Horizonte → revisao-completa-belo-horizonte
```

---

## CONFIRMAÇÃO AO FINAL DA FASE 1

Ao terminar, reportar:

```
✅ FASE 1 CONCLUÍDA

Empresa: [nome]
Segmento: [segmento]
Endereço: [endereço completo]
WhatsApp: [número]

Serviços originais encontrados: [lista completa]
Serviços principais selecionados:
  1. [nome] → /servicos/[slug]
  2. [nome] → /servicos/[slug]
  3. [nome] → /servicos/[slug]

Bairros identificados para Fase 4:
  Bairro da empresa: [bairro]
  Bairros vizinhos sugeridos: [lista de 6]
  ⚠️ Confirme ou substitua os bairros antes da Fase 4.

Modificações feitas no index.html:
  - Seção de serviços reduzida de [n] para 3 itens
  - Links adicionados nos 3 serviços principais
  - Botão "Ver todos os serviços" adicionado

Aguardando aprovação para iniciar FASE 2.
```
