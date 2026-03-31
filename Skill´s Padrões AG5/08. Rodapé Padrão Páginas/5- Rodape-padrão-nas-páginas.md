# SKILL — Sincronizar Nav e Rodapé Padrão em Todas as Páginas

## Quando acionar esta skill
Acione sempre que uma landing page tiver páginas secundárias (políticas, termos, etc.) que precisam receber o mesmo header/nav e footer da página principal (`index.html`).

---

## PASSO 1 — Identificar o padrão existente

Leia o `index.html` e extraia **exatamente**:

### Nav / Header
- Todo o bloco `<header>` ou `<nav>`, incluindo:
  - Logo (tag, src, alt, classes)
  - Links de navegação e seus `href`
  - Botão hamburger/mobile (HTML + classes)
  - Classes e atributos de animação (`data-*`, classes JS, `id`)
  - Links para CSS e fontes usados exclusivamente pelo header

### Rodapé / Footer
- Todo o bloco `<footer>`, incluindo:
  - Colunas, textos, links, ícones
  - Classes e atributos de animação
  - Ícones SVG ou de fontes (Font Awesome, etc.)

### Scripts linkados
- Identifique todos os `<script src="...">` no final do `<body>` do `index.html`
- Identifique especialmente o `script.js` principal e qualquer biblioteca (GSAP, ScrollReveal, AOS, etc.)

---

## PASSO 2 — Listar todas as páginas secundárias

Varra o projeto em busca de todos os arquivos `.html` exceto o `index.html`.

Exemplo de busca:
```
*.html  →  politica-privacidade.html, termos-uso.html, obrigado.html, etc.
```

---

## PASSO 3 — Replicar em cada página secundária

Para **cada** arquivo `.html` encontrado, faça:

### 3a. Substituir ou inserir o `<header>`/`<nav>`
- Remova o header/nav existente (se houver)
- Cole o bloco idêntico ao do `index.html`
- Ajuste `href` dos links se a página estiver em subpasta (ex.: `../index.html`)

### 3b. Substituir ou inserir o `<footer>`
- Remova o footer existente (se houver)
- Cole o bloco idêntico ao do `index.html`
- Ajuste caminhos de imagens/ícones se necessário

### 3c. Garantir os scripts no final do `<body>`
- Verifique se todos os `<script src="...">` do `index.html` estão presentes antes do `</body>`
- Inclua o `script.js` principal se estiver ausente
- Mantenha a **ordem** dos scripts (bibliotecas antes do script.js)

---

## PASSO 4 — Verificar animações (Web e Mobile)

Confirme que as seguintes funcionalidades do nav e footer funcionam em **todas** as páginas:

### Animações e interações — Desktop (Web)
- Efeito de scroll no header (ex.: `navbar--scrolled`, mudança de cor/transparência)
- Hover nos links de navegação (underline, cor, transição CSS)
- Qualquer animação de entrada do header/footer (fade, slide, GSAP, AOS, ScrollReveal)
- Smooth scroll ao clicar em âncoras (`#section`)

### Animações e interações — Mobile
- Menu hamburger: abertura e fechamento com animação (classe `active`, transform, opacity)
- Overlay ou backdrop do menu mobile (se existir)
- Fechamento do menu ao clicar em um link
- Fechamento do menu ao clicar fora (se implementado)
- Transições CSS do menu (height, transform, opacity, visibility)

### Checklist de verificação
- [ ] Header aparece corretamente no desktop e mobile
- [ ] Footer aparece corretamente no desktop e mobile
- [ ] Menu hamburger abre e fecha com animação
- [ ] Links do nav funcionam (hrefs corretos para a profundidade da página)
- [ ] `script.js` está linkado no final do `<body>`
- [ ] Bibliotecas de animação estão linkadas antes do `script.js`
- [ ] Não há erros de console (404 em CSS, JS ou imagens)

---

## PASSO 5 — Sincronização e Performance

- **Consistência**: qualquer alteração futura no header ou footer do `index.html` deve ser replicada manualmente (ou via esta skill) para todas as páginas secundárias.
- **Caminhos relativos**: verifique se CSS, JS e imagens usam caminhos corretos para a profundidade do arquivo (ex.: `../css/style.css` para páginas em subpasta).
- **Evitar duplicação de scripts**: não adicione o mesmo `<script>` duas vezes na mesma página.
- **Meta tags**: mantenha `<meta charset>`, `<meta viewport>` e o link do CSS principal em todas as páginas.

---

## Exemplo de estrutura esperada ao final do `<body>`

```html
  <!-- Bibliotecas (se usadas) -->
  <script src="https://cdnjs.cloudflare.com/ajax/libs/gsap/3.x.x/gsap.min.js"></script>
  <!-- ou -->
  <script src="https://unpkg.com/scrollreveal"></script>

  <!-- Script principal -->
  <script src="script.js"></script>
</body>
```

---

## Notas finais
- Esta skill **não reescreve** o conteúdo principal da página — apenas sincroniza nav e footer.
- Se o projeto usar includes server-side (PHP, SSI) ou componentes (React, Vue), adapte conforme a tecnologia.
- Em projetos HTML puro, a sincronização é manual — use esta skill como guia de execução.
