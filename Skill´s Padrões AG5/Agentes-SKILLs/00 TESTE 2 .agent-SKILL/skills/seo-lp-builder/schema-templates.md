# Schema Templates — JSON-LD para Páginas de Serviço

> Schemas prontos. Copiar, preencher os campos `[COLCHETES]` e injetar no `<head>` de cada página.
> Todo schema vai dentro de `<script type="application/ld+json">`.

---

## COMO USAR

Cada página de serviço precisa de **3 schemas empilhados** no `<head>`:

1. **LocalBusiness** (ou schema específico do segmento) — quem é a empresa
2. **Service** — o serviço específico desta página
3. **FAQPage** — as perguntas e respostas da seção FAQ
4. **BreadcrumbList** — a navegação estrutural

```html
<head>
  <!-- Schema 1: LocalBusiness -->
  <script type="application/ld+json">{ ...LocalBusiness... }</script>

  <!-- Schema 2: Service -->
  <script type="application/ld+json">{ ...Service... }</script>

  <!-- Schema 3: FAQ -->
  <script type="application/ld+json">{ ...FAQPage... }</script>

  <!-- Schema 4: Breadcrumb -->
  <script type="application/ld+json">{ ...BreadcrumbList... }</script>
</head>
```

---

## SCHEMA 1 — LocalBusiness (base para todos os segmentos)

```json
{
  "@context": "https://schema.org",
  "@type": "[TIPO_SEGMENTO]",
  "name": "[NOME DA EMPRESA]",
  "description": "[DESCRIÇÃO DA EMPRESA EM 1-2 FRASES]",
  "url": "https://[DOMINIO]",
  "logo": "https://[DOMINIO]/assets/logo.png",
  "image": "https://[DOMINIO]/assets/og-image.jpg",
  "telephone": "[+55 11 91234-5678]",
  "email": "[email@empresa.com.br]",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "[RUA, NÚMERO, COMPLEMENTO]",
    "addressLocality": "[CIDADE]",
    "addressRegion": "[UF]",
    "postalCode": "[CEP]",
    "addressCountry": "BR"
  },
  "geo": {
    "@type": "GeoCoordinates",
    "latitude": "[LATITUDE]",
    "longitude": "[LONGITUDE]"
  },
  "openingHoursSpecification": [
    {
      "@type": "OpeningHoursSpecification",
      "dayOfWeek": ["Monday","Tuesday","Wednesday","Thursday","Friday"],
      "opens": "09:00",
      "closes": "18:00"
    }
  ],
  "sameAs": [
    "https://www.instagram.com/[INSTAGRAM]",
    "https://www.linkedin.com/in/[LINKEDIN]"
  ]
}
```

### Tipos por Segmento (`@type`)

| Segmento | @type |
|----------|-------|
| Advocacia | `LegalService` |
| Odontologia | `Dentist` |
| Medicina | `Physician` |
| Psicologia | `MedicalBusiness` |
| Estética | `HealthAndBeautyBusiness` |
| Automotivo (oficina) | `AutoRepair` |
| Automotivo (concessionária) | `AutoDealer` |
| Contabilidade | `ProfessionalService` |
| Decoração / Arquitetura | `ProfessionalService` |
| Geral | `LocalBusiness` |

---

## SCHEMA 2 — Service (um por página de serviço)

```json
{
  "@context": "https://schema.org",
  "@type": "Service",
  "name": "[NOME DO SERVIÇO — ex: Divórcio Consensual]",
  "description": "[DESCRIÇÃO DO SERVIÇO EM 2-3 FRASES]",
  "url": "https://[DOMINIO]/servicos/[SLUG-SERVICO]",
  "provider": {
    "@type": "[TIPO_SEGMENTO]",
    "name": "[NOME DA EMPRESA]",
    "url": "https://[DOMINIO]"
  },
  "areaServed": {
    "@type": "City",
    "name": "[CIDADE]"
  },
  "serviceType": "[CATEGORIA DO SERVIÇO — ex: Direito de Família]",
  "offers": {
    "@type": "Offer",
    "description": "[OFERTA OU CONDIÇÃO — ex: Consulta inicial gratuita]",
    "priceCurrency": "BRL",
    "availability": "https://schema.org/InStock"
  }
}
```

---

## SCHEMA 3 — FAQPage (uma por página de serviço)

```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "[PERGUNTA 1]",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "[RESPOSTA COMPLETA 1 — mínimo 2 frases]"
      }
    },
    {
      "@type": "Question",
      "name": "[PERGUNTA 2]",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "[RESPOSTA COMPLETA 2]"
      }
    },
    {
      "@type": "Question",
      "name": "[PERGUNTA 3]",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "[RESPOSTA COMPLETA 3]"
      }
    },
    {
      "@type": "Question",
      "name": "[PERGUNTA 4]",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "[RESPOSTA COMPLETA 4]"
      }
    },
    {
      "@type": "Question",
      "name": "[PERGUNTA 5]",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "[RESPOSTA COMPLETA 5]"
      }
    }
  ]
}
```

> **Importante:** As perguntas no JSON-LD devem ser EXATAMENTE iguais ao texto visível no HTML.

---

## SCHEMA 4 — BreadcrumbList (uma por página de serviço)

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

---

## SCHEMA 5 — ItemList (para página HUB /servicos)

Usar na página `/servicos/index.html` para listar todos os serviços:

```json
{
  "@context": "https://schema.org",
  "@type": "ItemList",
  "name": "Serviços — [NOME DA EMPRESA]",
  "description": "Todos os serviços oferecidos por [NOME DA EMPRESA] em [CIDADE]",
  "url": "https://[DOMINIO]/servicos",
  "itemListElement": [
    {
      "@type": "ListItem",
      "position": 1,
      "name": "[NOME SERVIÇO 1]",
      "url": "https://[DOMINIO]/servicos/[SLUG-1]"
    },
    {
      "@type": "ListItem",
      "position": 2,
      "name": "[NOME SERVIÇO 2]",
      "url": "https://[DOMINIO]/servicos/[SLUG-2]"
    }
  ]
}
```

---

## SCHEMA 6 — Person (para página /sobre)

```json
{
  "@context": "https://schema.org",
  "@type": "Person",
  "name": "[NOME DO PROFISSIONAL]",
  "jobTitle": "[TÍTULO — ex: Advogada Especialista em Direito de Família]",
  "description": "[BIO CURTA 2-3 FRASES]",
  "url": "https://[DOMINIO]/sobre",
  "image": "https://[DOMINIO]/assets/foto-profissional.jpg",
  "worksFor": {
    "@type": "[TIPO_SEGMENTO]",
    "name": "[NOME DA EMPRESA]",
    "url": "https://[DOMINIO]"
  },
  "alumniOf": [
    {
      "@type": "EducationalOrganization",
      "name": "[INSTITUIÇÃO DE ENSINO]"
    }
  ],
  "sameAs": [
    "https://www.linkedin.com/in/[LINKEDIN]",
    "https://www.instagram.com/[INSTAGRAM]"
  ]
}
```

---

## VALIDAÇÃO

Após gerar os schemas, validar em:
- Google Rich Results Test: `search.google.com/test/rich-results`
- Schema.org Validator: `validator.schema.org`

**O que deve aparecer como resultado rico no Google:**
- FAQ expandida nos resultados de busca
- Endereço e horário no Knowledge Panel
- Breadcrumb no snippet
