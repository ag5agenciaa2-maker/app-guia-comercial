# Padrão AG5 de Qualidade UI/UX

Favor aplicar as seguintes melhorias técnicas nos arquivos index.html, style.css e script.js:"


## 1. Padrão de Conversão via WhatsApp Dinâmico

A captação de leads via WhatsApp precisa ter rastreabilidade intuitiva:

- **Otimização de Mensagem por Contexto (Fundamental):**
  - Todo link de botão do WhatsApp espalhado pelo site DEVE incluir o parâmetro `?text=` com uma introdução específica baseada em onde o botão está localizado.
  - O formato genérico (header/footer/solto) é: `"Olá, vim através do site e gostaria de uma informação."`
  - O formato específico (Card de serviço ou preço) é: `"Olá, vim através do site e gostaria de saber sobre [Nome do Serviço/Produto da seção]"` (Ex: *Olá, vim através do site e gostaria de saber sobre Consultoria Trabalhista.*)

- **Botão Flutuante (Obrigatório):**
  - Um ícone fixo e nítido no canto inferior direito.
  - Utilize sempre o **SVG Oficial do WhatsApp** para melhor legibilidade e identidade da marca da Meta.
  - O design deve ser minimalista, elegante e limpo.
  - **Regra para Nichos com Alto Rigor de Marketing:** É **estritamente proibido** utilizar a bolinha vermelha flutuante (notification badge) ou animações de pulsação/urgência. Deve-se manter **apenas o balão flutuante do WhatsApp** simples, para evitar penalizações ou percepção de falsas notificações.
  - O link `<a href="wa.me/...>` deve ter `role="button"` e `aria-label="Falar pelo WhatsApp"` para o crivo de acessibilidade.

<br>

### 🛠️ Códigos e Estrutura Padrão

**HTML (Logo Oficial e Link Padrão - Inserir antes do `</body>`):**
```html
<!-- Botão Flutuante WhatsApp (AG5 Standard) -->
<a href="https://wa.me/DDI_DDB_AQUI?text=Ol%C3%A1%2C%20vim%20atrav%C3%A9s%20do%20site%20e%20gostaria%20de%20uma%20informa%C3%A7%C3%A3o." class="btn-flutuante-whatsapp" target="_blank" role="button" aria-label="Falar pelo WhatsApp">
    <svg viewBox="0 0 16 16" width="30" height="30" fill="currentColor">
        <path d="M13.601 2.326A7.85 7.85 0 0 0 7.994 0C3.627 0 .068 3.558.064 7.926c0 1.399.366 2.76 1.057 3.965L0 16l4.204-1.102a7.9 7.9 0 0 0 3.79.965h.004c4.368 0 7.926-3.558 7.93-7.93A7.9 7.9 0 0 0 13.6 2.326zM7.994 14.521a6.6 6.6 0 0 1-3.356-.92l-.24-.144-2.494.654.666-2.433-.156-.251a6.56 6.56 0 0 1-1.007-3.505c0-3.626 2.957-6.584 6.591-6.584a6.56 6.56 0 0 1 4.66 1.931 6.56 6.56 0 0 1 1.928 4.66c-.004 3.639-2.961 6.592-6.592 6.592m3.615-4.934c-.197-.099-1.17-.578-1.353-.646-.182-.065-.315-.099-.445.099-.133.197-.513.646-.627.775-.114.133-.232.148-.43.05-.197-.1-.836-.308-1.592-.985-.59-.525-.985-1.175-1.103-1.372-.114-.198-.011-.304.088-.403.087-.088.197-.232.296-.346.1-.114.133-.198.198-.33.065-.134.034-.248-.015-.347-.05-.099-.445-1.076-.612-1.47-.16-.389-.323-.335-.445-.34-.114-.007-.247-.007-.38-.007a.73.73 0 0 0-.529.247c-.182.198-.691.677-.691 1.654s.71 1.916.81 2.049c.098.133 1.394 2.132 3.383 2.992.47.205.84.326 1.129.418.475.152.904.129 1.246.08.38-.058 1.171-.48 1.338-.943.164-.464.164-.86.114-.943-.049-.084-.182-.133-.38-.232"/>
    </svg>
</a>
```

**CSS Padrão (Sem animações extravagantes e centralizado):**
```css
/* ========================================
   WHATSAPP FLUTUANTE 
   ======================================== */
.btn-flutuante-whatsapp {
    position: fixed;
    bottom: 24px;
    right: 24px;
    width: 60px;
    height: 60px;
    background-color: #25D366;
    color: #FFF;
    border-radius: 50%;
    display: flex;
    justify-content: center;
    align-items: center;
    box-shadow: 0px 4px 10px rgba(0, 0, 0, 0.3);
    z-index: 1000;
    transition: transform 0.3s ease;
}

.btn-flutuante-whatsapp:hover {
    transform: scale(1.05);
    color: #FFF;
}
```


