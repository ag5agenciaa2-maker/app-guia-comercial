---
name: Links360-Entrega
description: Módulo de checklist de qualidade e entrega do Links 360 — verificação final, estrutura de pastas e geração do ASSETS_NECESSARIOS.md. Cobre os Passos 5 e 6.
type: project
---

# MÓDULO 03 — ENTREGA

> Carregar este módulo após a confirmação da Fase 9 (CSS completo).
> Cobre: Passo 5 (checklist de qualidade) e Passo 6 (estrutura de pastas e ASSETS_NECESSARIOS.md).

---

## 📄 PASSO 5 — CHECKLIST DE QUALIDADE

Antes de declarar o projeto concluído, verificar:

- [ ] Todos os links estão com telefone/URLs reais do cliente
- [ ] vCard tem todos os dados preenchidos
- [ ] WhatsApp links têm mensagem pré-preenchida contextualizada
- [ ] Todas as imagens referenciadas existem em `assets/` (ou foram documentadas para inserção)
- [ ] Schema.org JSON-LD adaptado ao tipo de negócio correto (`@type`)
- [ ] Meta tags SEO preenchidas (title, description, OG, Twitter)
- [ ] Copyright com ano e nome corretos
- [ ] Design coerente com o nicho (não genérico roxo-azul)
- [ ] Fontes compatíveis com o nicho
- [ ] Nenhum texto de exemplo permaneceu no código ("Lorem ipsum", "Empresa Modelo", etc.)
- [ ] Os horários de funcionamento estão corretos
- [ ] Todos os modais têm o botão de WhatsApp com a mensagem específica do serviço
- [ ] Grid de serviços tem exatamente 6 cards (último card é o logo se necessário)
- [ ] Todo card de serviço tem modal correspondente
- [ ] Imagens de serviços sem foto têm `data-photo-needed="true"` e estão documentadas no ASSETS_NECESSARIOS.md
- [ ] Seções extras sugeridas e confirmadas foram todas construídas
- [ ] **Dark/Light mode funciona perfeitamente em 100% dos elementos** — nenhum texto, card, modal ou seção "quebra" ao trocar o tema
- [ ] Variáveis CSS de tema (`--brand-dark`, `--brand-card`, `--brand-border`, etc.) usadas em todos os elementos temáticos — sem cores hardcoded onde não deve
- [ ] Modais mudam corretamente entre dark (`bg-zinc-900`) e light (`bg-white`) ao trocar o tema
- [ ] Animações são compatíveis com o nicho do cliente
- [ ] Nenhum elemento visualmente desalinhado (espaçamento, hierarquia, contraste)
- [ ] Nomenclatura (Serviços/Produtos) está correta para o nicho

---

## 📄 PASSO 6 — ESTRUTURA DE PASTAS DO PROJETO

### Pasta raiz de destino (SEMPRE usar este caminho)

```
C:\Users\mauri\Documents\00 Processo Landing Pages\04 - Links 360\[slug-nome-empresa]\
```

> **Regra:** O slug do nome da empresa deve ser em kebab-case minúsculo.
> Exemplos: `vasques-auto-center`, `hannah-advocacia`, `dra-tatiane-gomes`

O agente deve criar a seguinte estrutura completa dentro dessa pasta:

```
C:\Users\mauri\Documents\00 Processo Landing Pages\04 - Links 360\
└── [slug-nome-empresa]\
    ├── index.html              # Página principal (todo o HTML do projeto)
    ├── style.css               # Estilos customizados do projeto
    ├── script.js               # JS específico do projeto (vCard, etc.)
    ├── ASSETS_NECESSARIOS.md   # Lista de assets que ainda precisam ser inseridos
    └── assets\                 # Imagens, vídeos, logos, favicon
        ├── logo.[ext]          # Copiado automaticamente da origem
        ├── favicon.ico         # Copiado automaticamente da origem
        ├── music.mp3           # Copiado se disponível
        ├── [fotos-copiadas].webp
        └── [videos-copiados].mp4
```

**Nota:** O `script.js` do projeto geralmente contém apenas a função `downloadVCard()` e interações específicas. O `../shared/core.js` cuida de: theme toggle, música, modais, galeria, scroll, reveals — é compartilhado entre todos os projetos do sistema.

### Arquivo ASSETS_NECESSARIOS.md

Se após a varredura ainda houver imagens/vídeos faltantes para o projeto, o agente deve criar um arquivo `ASSETS_NECESSARIOS.md` na raiz do projeto com a lista organizada do que falta:

```markdown
# Assets Necessários — [NOME DA EMPRESA]

## 🖼️ Imagens para a seção HERO
- [ ] Foto da logo em alta resolução (fundo transparente ou sobre fundo escuro)
- [ ] Foto/avatar para o círculo do hero (rosto do profissional ou logo adequado)

## 🎬 Vídeos para a Galeria
- [ ] Vídeo 01 — [Label/tema do vídeo] (formato .mp4)
- [ ] Vídeo 02 — [Label/tema do vídeo]

## 🗂️ Imagens para Serviços
- [ ] [Nome do serviço 01] — imagem representativa
- [ ] [Nome do serviço 02] — imagem representativa

## 📸 Imagens para a Galeria de Fotos
- [ ] Mínimo 4 fotos do espaço/trabalho/produto

## 🔖 Identidade Visual
- [ ] Favicon em formato .ico ou .png (32x32px)
- [ ] OG Image (1200x630px) para compartilhamento em redes sociais
```

---

*Módulo 03 — AG5 Agência | Links 360 Premium*
