# SKILL — Seção Dor & Solução com Imagens Contextuais

## Comportamento principal

### LEITURA OBRIGATÓRIA ANTES DE QUALQUER AÇÃO
Antes de criar qualquer coisa, leia e extraia do projeto:

1. **CSS principal** — identifique no `:root` todas as variáveis: cores (primária, secundária, fundo, texto, card, bordas), fontes (`font-family`), border-radius, shadows e espaçamentos padrão
2. **Padrão visual das seções existentes** — observe como as outras seções do site estão estruturadas: padding, max-width do container, estilo dos títulos (tamanho, peso, cor, letter-spacing), estilo dos cards (background, borda, sombra, border-radius), estilo dos botões e ícones
3. **Tom e estética geral** — o site é minimalista? dark? claro? editorial? corporativo? luxo? Esta seção deve seguir exatamente o mesmo tom
4. **Animações existentes** — que tipo de animação o site já usa (fade, slide, scale, nenhuma)? Replique o mesmo padrão

**REGRA PREMIUM:** Tudo que for criado ou adicionado nesta seção deve parecer que sempre fez parte do site. Nunca usar valores hardcoded (cores, fontes, border-radius) quando já existem variáveis CSS. Nunca criar um estilo visual diferente do restante do site.

---

Analise também o HTML do projeto e identifique se já existe uma seção de "Dor e Solução" (ou equivalente: problemas/benefícios, antes/depois, desafios/resultados).

---

## CASO A — Seção JÁ EXISTE no site

Localize a seção existente (busque por termos como: "dor", "problema", "desafio", "solução", "benefício", "antes", "depois", ou por estrutura de dois cards/colunas com copy negativa/positiva).

Ação: NÃO recrie a seção. Apenas adicione as imagens nos cards corretos:

### Card da Dor (esquerda ou primeiro card)
- Identifique o card que fala de problema/limitação/dificuldade
- Adicione uma imagem conceitual/metafórica que represente essa dor específica do segmento do site
  - Sem rostos humanos
  - Foco em objetos, ambientes ou situações que remetam ao problema
  - Exemplo para advocacia: papéis acumulados, relógio com prazo, porta fechada
  - Exemplo para saúde: pessoa parada, ambiente desordenado, objeto quebrado
- Posicione a imagem no topo do card, acima do texto, com border-radius consistente com o design atual
- Adicione `loading="lazy"` e atributos `width` e `height`

### Card da Solução (direita ou segundo card)
- Identifique o card que fala de resultado/benefício/transformação
- Adicione uma imagem otimista e vibrante que represente o resultado final
  - Sem rostos humanos
  - Foco em ambientes organizados, objetos funcionando, cenários de sucesso
  - Exemplo para advocacia: documentos organizados, chave na fechadura, caminho livre
  - Exemplo para saúde: ambiente limpo, objeto consertado, espaço amplo e luminoso
- Posicione a imagem no topo do card, acima do texto, com border-radius consistente
- Adicione `loading="lazy"` e atributos `width` e `height`

### CSS para as imagens inseridas
Adicione estilos que mantenham consistência com o design atual:
```css
.card-dor-solucao img {
  width: 100%;
  height: 220px;
  object-fit: cover;
  border-radius: [usar o mesmo border-radius dos cards existentes];
  margin-bottom: 1.2rem;
}
```

---

## CASO B — Seção NÃO EXISTE no site

Crie uma seção editorial de alto impacto após a hero (ou após a seção de serviços, se a hero já tiver muita informação).

**ANTES DE ESCREVER O CSS:** Liste mentalmente as variáveis do `:root` que serão usadas. Nunca use `#fff`, `#333`, `16px` ou qualquer valor fixo que já exista como variável no projeto. Se o site usa `--border-radius: 12px`, use `var(--border-radius)`. Se usa `--shadow-card: 0 4px 20px ...`, use `var(--shadow-card)`. O CSS abaixo é apenas um modelo estrutural — **substitua todos os valores pelos do projeto real**.

### Estrutura HTML
```html
<section class="secao-dor-solucao" id="dor-solucao">
  <div class="dor-solucao-container">
    <div class="dor-solucao-header">
      <h2>[Título central: ex. "Você reconhece essa situação?"]</h2>
      <p>[Subtítulo empático e direto ao segmento do cliente]</p>
    </div>
    <div class="dor-solucao-cards">

      <!-- Card Dor -->
      <div class="card-dor">
        <img src="[imagem-dor]" alt="[descrição da situação problema]" width="600" height="400" loading="lazy">
        <h3>[Título da Dor: ex. "A situação atual"]</h3>
        <p>[Copy empática focada na limitação e no incômodo do dia a dia]</p>
        <ul>
          <li>[Ponto negativo 1]</li>
          <li>[Ponto negativo 2]</li>
          <li>[Ponto negativo 3]</li>
        </ul>
      </div>

      <!-- Divisor visual -->
      <div class="dor-solucao-divisor">
        <span class="divisor-icone">→</span>
      </div>

      <!-- Card Solução -->
      <div class="card-solucao">
        <img src="[imagem-solucao]" alt="[descrição do resultado alcançado]" width="600" height="400" loading="lazy">
        <h3>[Título da Solução: ex. "Como fica depois"]</h3>
        <p>[Copy inspiradora focada na transformação e resultado concreto]</p>
        <ul>
          <li>✓ [Benefício 1]</li>
          <li>✓ [Benefício 2]</li>
          <li>✓ [Benefício 3]</li>
        </ul>
      </div>

    </div>
  </div>
</section>
```

### CSS base — USAR VARIÁVEIS DO PROJETO, não valores fixos
Substitua cada propriedade pelos valores reais encontrados no `:root` do projeto:

```css
.secao-dor-solucao {
  padding: [mesmo padding vertical das outras seções do site];
  background: var(--[variável de cor de fundo do projeto]);
}
.dor-solucao-container {
  max-width: [mesmo max-width das outras seções];
  margin: 0 auto;
  padding: 0 [mesmo padding horizontal do container padrão];
}
.dor-solucao-header {
  text-align: center;
  margin-bottom: [espaçamento consistente com o projeto];
}
.dor-solucao-header h2 {
  font-family: var(--[fonte-titulo do projeto]);
  font-size: [mesmo tamanho dos h2 das outras seções];
  font-weight: [mesmo peso dos títulos do projeto];
  color: var(--[cor-titulo do projeto]);
  letter-spacing: [mesmo letter-spacing dos títulos];
}
.dor-solucao-cards {
  display: grid;
  grid-template-columns: 1fr auto 1fr;
  gap: [mesmo gap entre cards do projeto];
  align-items: start;
}
.card-dor,
.card-solucao {
  background: var(--[cor-card do projeto]);
  border-radius: var(--[border-radius do projeto]);
  padding: [mesmo padding interno dos cards existentes];
  box-shadow: var(--[shadow do projeto]);
  border: [mesma borda dos cards existentes, se houver];
  opacity: 0;
  transform: translateY(20px);
  transition: opacity 0.6s ease, transform 0.6s ease;
}
.card-dor.visivel,
.card-solucao.visivel {
  opacity: 1;
  transform: translateY(0);
}
.card-dor img,
.card-solucao img {
  width: 100%;
  height: 220px;
  object-fit: cover;
  border-radius: calc(var(--[border-radius do projeto]) - 4px);
  margin-bottom: 1.2rem;
}
.card-dor h3,
.card-solucao h3 {
  font-family: var(--[fonte-titulo do projeto]);
  font-size: [mesmo tamanho dos h3 do projeto];
  color: var(--[cor-titulo do projeto]);
}
.card-dor ul li,
.card-solucao ul li {
  font-family: var(--[fonte-corpo do projeto]);
  color: var(--[cor-texto do projeto]);
  font-size: [mesmo tamanho do texto de lista do projeto];
  line-height: [mesmo line-height do projeto];
}
.dor-solucao-divisor {
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 2rem;
  color: var(--[cor-primaria do projeto]);
  padding-top: 120px;
}
@media (max-width: 768px) {
  .dor-solucao-cards {
    grid-template-columns: 1fr;
  }
  .dor-solucao-divisor {
    padding-top: 0;
    transform: rotate(90deg);
  }
}
```

### JS — animação de entrada com IntersectionObserver
Adicionar no `script.js` (ou ao final do HTML se não houver script.js):
```javascript
const cardsDorSolucao = document.querySelectorAll('.card-dor, .card-solucao');
if (cardsDorSolucao.length) {
  const observer = new IntersectionObserver((entries) => {
    entries.forEach(entry => {
      if (entry.isIntersecting) entry.target.classList.add('visivel');
    });
  }, { threshold: 0.15 });
  cardsDorSolucao.forEach(card => observer.observe(card));
}
```

---

## Regras de imagem para ambos os casos

- As imagens devem ser **conceituais/metafóricas**, sem rostos humanos
- Devem ser **específicas ao segmento** do cliente (não imagens genéricas)
- Se o projeto usa imagens locais: criar/indicar nomes de arquivo sugestivos (ex.: `img/dor-situacao.webp`, `img-solucao-resultado.webp`)
- Se o projeto usa imagens externas (Unsplash, Pexels): buscar pelo segmento + conceito (ex.: "messy desk law", "organized clean office")
- Sempre incluir `alt` descritivo, `width`, `height` e `loading="lazy"`
