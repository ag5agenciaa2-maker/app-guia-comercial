# SEO Schema Service — JSON-LD para Páginas de Serviço

> 4 schemas obrigatórios por página. Todos no `<head>`, cada um em seu próprio `<script>`.
> Preencher com dados reais extraídos do index — sem campos vazios ou colchetes na entrega.

---

## SCHEMA 1 — LocalBusiness

Representa a empresa. **Igual em todas as páginas do site.**

```json
{
  "@context": "https://schema.org",
  "@type": "[TIPO_POR_SEGMENTO]",
  "name": "[NOME DA EMPRESA]",
  "url": "https://[DOMINIO]",
  "telephone": "[+55 11 91234-5678]",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "[RUA, NÚMERO, SALA]",
    "addressLocality": "[CIDADE]",
    "addressRegion": "[UF]",
    "addressCountry": "BR"
  },
  "openingHoursSpecification": [{
    "@type": "OpeningHoursSpecification",
    "dayOfWeek": ["Monday","Tuesday","Wednesday","Thursday","Friday"],
    "opens": "09:00",
    "closes": "18:00"
  }]
}
```

**Tipos por segmento:**

| Segmento | @type |
|----------|-------|
| Advocacia | `LegalService` |
| Odontologia | `Dentist` |
| Psicologia / Medicina | `MedicalBusiness` |
| Estética | `HealthAndBeautyBusiness` |
| Automotivo (oficina) | `AutoRepair` |
| Contabilidade | `ProfessionalService` |
| Nutrição / Saúde geral | `MedicalBusiness` |
| Outros | `LocalBusiness` |

---

## SCHEMA 2 — Service

Representa o serviço específico desta página. **Muda em cada página.**

### Página de serviço (fase 3 — bairro da empresa):

```json
{
  "@context": "https://schema.org",
  "@type": "Service",
  "name": "[NOME DO SERVIÇO]",
  "description": "[DESCRIÇÃO DO SERVIÇO — 2 frases objetivas]",
  "url": "https://[DOMINIO]/servicos/[SLUG-SERVICO]",
  "provider": {
    "@type": "[TIPO_POR_SEGMENTO]",
    "name": "[NOME DA EMPRESA]",
    "url": "https://[DOMINIO]"
  },
  "areaServed": {
    "@type": "City",
    "name": "[CIDADE]"
  },
  "serviceType": "[CATEGORIA — ex: Direito de Família, Implantodontia, Mecânica Automotiva]"
}
```

### Página de bairro (fase 4 — areaServed muda):

```json
{
  "@context": "https://schema.org",
  "@type": "Service",
  "name": "[NOME DO SERVIÇO] em [BAIRRO ALVO]",
  "description": "[DESCRIÇÃO] Atendemos clientes de [BAIRRO ALVO] e região.",
  "url": "https://[DOMINIO]/servicos/[SLUG-SERVICO]/[SLUG-BAIRRO]",
  "provider": {
    "@type": "[TIPO_POR_SEGMENTO]",
    "name": "[NOME DA EMPRESA]",
    "url": "https://[DOMINIO]"
  },
  "areaServed": {
    "@type": "Place",
    "name": "[BAIRRO ALVO], [CIDADE]"
  },
  "serviceType": "[CATEGORIA]"
}
```

---

## SCHEMA 3 — FAQPage

Representa as 4 perguntas frequentes. **Idêntico em página de serviço e páginas de bairro.**

> As perguntas no JSON-LD devem ser **textualmente idênticas** ao HTML visível.

```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "[PERGUNTA 1 — exatamente igual ao HTML]",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "[RESPOSTA 1 — exatamente igual ao HTML, mínimo 2 frases]"
      }
    },
    {
      "@type": "Question",
      "name": "[PERGUNTA 2]",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "[RESPOSTA 2]"
      }
    },
    {
      "@type": "Question",
      "name": "[PERGUNTA 3]",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "[RESPOSTA 3]"
      }
    },
    {
      "@type": "Question",
      "name": "[PERGUNTA 4]",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "[RESPOSTA 4]"
      }
    }
  ]
}
```

---

## SCHEMA 4 — BreadcrumbList

### Página de serviço (fase 3) — 3 níveis:

```json
{
  "@context": "https://schema.org",
  "@type": "BreadcrumbList",
  "itemListElement": [
    {
      "@type": "ListItem",
      "position": 1,
      "name": "Início",
      "item": "https://[DOMINIO]"
    },
    {
      "@type": "ListItem",
      "position": 2,
      "name": "Serviços",
      "item": "https://[DOMINIO]/servicos"
    },
    {
      "@type": "ListItem",
      "position": 3,
      "name": "[NOME DO SERVIÇO]",
      "item": "https://[DOMINIO]/servicos/[SLUG-SERVICO]"
    }
  ]
}
```

### Página de bairro (fase 4) — 4 níveis:

```json
{
  "@context": "https://schema.org",
  "@type": "BreadcrumbList",
  "itemListElement": [
    {
      "@type": "ListItem",
      "position": 1,
      "name": "Início",
      "item": "https://[DOMINIO]"
    },
    {
      "@type": "ListItem",
      "position": 2,
      "name": "Serviços",
      "item": "https://[DOMINIO]/servicos"
    },
    {
      "@type": "ListItem",
      "position": 3,
      "name": "[NOME DO SERVIÇO]",
      "item": "https://[DOMINIO]/servicos/[SLUG-SERVICO]"
    },
    {
      "@type": "ListItem",
      "position": 4,
      "name": "[BAIRRO ALVO]",
      "item": "https://[DOMINIO]/servicos/[SLUG-SERVICO]/[SLUG-BAIRRO]"
    }
  ]
}
```

---

## REGRAS DE PREENCHIMENTO

1. **Sem colchetes na entrega** — todo `[CAMPO]` deve ser substituído por dados reais
2. **Domínio com https://** — sempre incluir protocolo
3. **Telefone em formato internacional** — `+55 11 91234-5678`
4. **Perguntas idênticas ao HTML** — copiar exatamente, sem reescrever
5. **Respostas completas** — mínimo 2 frases, sem truncar
6. **URLs sem barra final** — `https://site.com/servicos` não `https://site.com/servicos/`

---

## VALIDAÇÃO

Após gerar, testar em:
- Google Rich Results Test: `search.google.com/test/rich-results`
  - FAQ deve aparecer como "Perguntas frequentes" ✅
  - Breadcrumb deve aparecer como trilha de navegação ✅
