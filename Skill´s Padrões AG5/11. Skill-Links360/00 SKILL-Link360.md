---
name: Skill-Links360
description: Orquestrador principal da Skill para construção progressiva de páginas Links 360 (estilo Linktree premium) baseada nos padrões AG5. Carrega os módulos corretos em cada momento do processo.
type: project
---

# SKILL — CONSTRUTOR DE LINKS 360 (AG5)

> **Padrão de Referência:** Vasquez Auto Center (`04 - Links 360/vasques-auto-center/`)
Caminho: C:\Users\mauri\Documents\00 Processo Landing Pages\04 - Links 360\vasques-auto-center
> **DNA Reference (Style ONLY):** Tatiane Gomes (`04 - Links 360/tatiane-gomes/`)
Caminho: C:\Users\mauri\Documents\00 Processo Landing Pages\04 - Links 360\tatiane-gomes
> **Versão:** 2.1 — Março 2026 (Estrutura Unificada Vasques)

---

## 🚨🚨🚨 LEITURA OBRIGATÓRIA ANTES DE QUALQUER CÓDIGO 🚨🚨🚨

> **NÃO CRIE LAYOUT HTML DO ZERO. NUNCA.**
>
> **PASSO 0 DE CONSTRUÇÃO (INEGOCIÁVEL):**
> 1. Use `view_file` para ler **NA ÍNTEGRA** o arquivo:  
>    `C:\Users\mauri\Documents\00 Processo Landing Pages\04 - Links 360\vasques-auto-center\index.html`
> 2. Copie a estrutura HTML completa como ponto de partida
> 3. Use `view_file` para ler o `style.css` do Vasques e copiar para o novo projeto
> 4. Substitua **SOMENTE**: `--brand-main`, `--brand-hover` e assets do cliente
>
> **PROIBIDO:** Inventar classes, alterar `h-24` dos botões, mudar estilo de cards, criar background effects diferentes, trocar `bg-zinc-900` por cores claras nos links.
>
> **PERMITIDO (addições sutis):** Se o cliente tiver um canal ou informação que não existe no Vasques (ex: LinkedIn, página de agendamento, QR code), o agente PODE adicionar uma nova seção ou botão, **desde que:**
> - Use o **HTML idêntico** do componente mais próximo do Vasques (ex: novo botão de link = copiar um dos botões `h-24` existentes)
> - Não mude nenhuma classe, tamanho ou estrutura do componente base
> - Informe o usuário sobre a adição antes de construir
> - Se a seção não existir no Vasques (ex: galeria de fotos diferente), use a seção mais similar como referência exata
>
> **Não existir no Vasques = não existe para o agente. Se precisar criar algo novo, apresentar ao usuário primeiro e aguardar confirmação.**

---


1. **NÃO construa tudo de uma vez.** O processo é faseado em blocos de 2 seções.
2. **NÃO invente informações.** Tudo que não foi fornecido deve ser marcado como `[INSERIR]` ou perguntado.
3. **NÃO seja resumidor.** Cada seção deve ter o código COMPLETO, não esboços ou comentários como "adicione aqui os outros cards".
4. **NÃO pule etapas.** Siga o processo na ordem exata definida nesta skill.
5. **NÃO misture dados** de clientes diferentes. Cada projeto é isolado.
6. **PERGUNTE se tiver dúvida** sobre informações específicas do cliente em vez de inventar.
7. Após cada bloco de 2 seções, **PARE e aguarde confirmação** antes de prosseguir.
8. **Se receber caminho de pasta: SEMPRE fazer a varredura de assets PRIMEIRO** (Passo 1B) antes de qualquer construção.
9. **COPIE os assets automaticamente** para a pasta `assets/` do novo projeto. Nunca deixe essa tarefa para o criador.
10. **RENOMEIE os arquivos** copiados para padrão SEO durante a cópia (kebab-case descritivo).
11. **VERIFIQUE O NICHO antes de escrever qualquer texto de marketing.** Nichos regulados (Advocacia, Odontologia, Medicina) têm restrições severas de linguagem e elementos visuais — consulte o módulo `01-recepcao-planejamento.md` (Passo 0).
12. **PASTA DE DESTINO FIXA:** Todo projeto Links 360 deve ser criado SEMPRE em `C:\Users\mauri\Documents\00 Processo Landing Pages\04 - Links 360\[slug-nome-empresa]\`. Nunca criar em outro local.
13. **🚨 REGRA FUNDAMENTAL DE CONSTRUÇÃO — NUNCA INVENTE ESTRUTURA:** O agente NÃO deve criar design, layout ou estrutura HTML do zero. O processo correto é:
    - **PASSO A:** Ler o arquivo `C:\Users\mauri\Documents\00 Processo Landing Pages\04 - Links 360\vasques-auto-center\index.html` na íntegra
    - **PASSO B:** Usar esse código como template literal — copiar a estrutura completa
    - **PASSO C:** Substituir APENAS: cores da marca, textos, imagens, links e dados do cliente
    - **PASSO D:** Para novos botões/links não presentes no Vasquez → adicionar abaixo, com HTML idêntico ao dos botões existentes, trocando só ícone e texto
    - **PASSO E:** Para novas seções (ex: LinkedIn, vídeos de outro tipo) → criar seção com estrutura idêntica à seção equivalente do Vasquez, nunca inventar novo layout
    - **JAMAIS** criar um visual diferente, reorganizar seções, mudar tamanhos de elementos ou inventar componentes que não existem no Vasquez

---

## 📂 MÓDULOS DA SKILL (carregar conforme o momento)

→ Ao iniciar: carregar `01-recepcao-planejamento.md`
→ Ao construir (fases 1-3): carregar `02-construcao-A.md`
→ Ao construir (fases 4-6): carregar `02-construcao-B.md`
→ Ao construir (fases 7-9): carregar `02-construcao-C.md`
→ Ao finalizar: carregar `03-entrega.md`

---

## 🔄 FLUXO RESUMIDO DO PROCESSO

```
PASSO 1: Receber briefing (qualquer formato)
    ↓
PASSO 1B [SE FOR PASTA]: Varredura de assets → Copiar tudo para assets/ → Relatório
    ↓
PASSO 2: Extrair dados do HTML/briefing → Apresentar resumo → Perguntar ausentes
    ↓
PASSO DNA: Ler TODOS os arquivos da pasta:
    C:\Users\mauri\Documents\00 Processo Landing Pages\02 - LP (Processando)\Skill´s Padrões AG5\11. Skill-Links360\DNA-Links\
    ↓
    → Identificar qual DNA aplicar (Cores, Fontes e Refinamento Visual):
       - Nicho energético/dark (Automotivo, Construção, Fitness) → DNA: Vasques (DNA-vasques-auto-center.md)
       - Nicho calm/minimalista (Jurídico, Saúde, Estética, Advocacia) → DNA: Tatiane (DNA-tatiane-gomes.md)
    ↓
    → **ESTRUTURA OBRIGATÓRIA:** Independentemente do DNA escolhido, a ESTRUTURA (seções) deve ser SEMPRE a do Vasques.
    → Apresentar ao usuário: "Identifico que [NICHO]. Usarei a ESTRUTURA completa do Vasques com o DNA visual de [REFERÊNCIA]. Confirma?"
    ↓
PASSO TEMPLATE: Ler o index.html + style.css do projeto referência escolhido
    ↓
ANÁLISE EXPANDIDA: Comparar DNA referência vs. informações do cliente
    → Identificar o que OMITIR (sem vídeos, sem exhaust, etc.)
    → Identificar o que ADICIONAR (LinkedIn, Threads, novo canal)
    → Apresentar mapa de seções previstas + diferenças → Aguardar confirmação
    ↓
FASE 1: Head + Ticker + Hero (usando logo copiado) → [PAUSE] Aguarda OK
    ↓
FASE 2: CTAs + Links → [PAUSE] Aguarda OK
    ↓
FASE 3: Vídeos (se tiver) + Diferenciais → [PAUSE] Aguarda OK
    ↓
FASE 4: Antes/Depois (se tiver) + Avaliações → [PAUSE] Aguarda OK
    ↓
FASE 5: Serviços (usando fotos copiadas) + CTA Extra → [PAUSE] Aguarda OK
    ↓
FASE 6: Sobre + Galeria Fotos (se tiver) → [PAUSE] Aguarda OK
    ↓
FASE 7: Localização + Footer + Scripts → [PAUSE] Aguarda OK
    ↓
FASE 8: Modais (usando fotos copiadas) → [PAUSE] Aguarda OK
    ↓
FASE 9: CSS completo → [PAUSE] Aguarda OK
    ↓
PASSO 5: Checklist de qualidade
    ↓
ENTREGA: Projeto concluído + ASSETS_NECESSARIOS.md (somente o que ainda falta)
```

---

## ⚡ REFERÊNCIAS TÉCNICAS RÁPIDAS

### Schema.org por Tipo de Negócio

| Nicho | @type |
|-------|-------|
| Oficina mecânica | `AutoRepair` |
| Clínica estética | `ProfessionalService` |
| Médico/Dentista | `MedicalBusiness` ou `Dentist` |
| Restaurante | `Restaurant` |
| Academia | `HealthClub` |
| Advogado | `LegalService` |
| Imobiliária | `RealEstateAgent` |
| Salão de beleza | `BeautySalon` |
| Hotel/Pousada | `Hotel` |
| Loja | `Store` |
| Genérico | `LocalBusiness` |

### Ícones FontAwesome por Tipo de Link

| Link | Ícone |
|------|-------|
| WhatsApp | `fa-brands fa-whatsapp` |
| Instagram | `fa-brands fa-instagram` |
| Facebook | `fa-brands fa-facebook` |
| TikTok | `fa-brands fa-tiktok` |
| YouTube | `fa-brands fa-youtube` |
| Threads | `fa-brands fa-threads` |
| Twitter/X | `fa-brands fa-x-twitter` |
| Site | `fa-solid fa-globe` |
| Google | `fa-brands fa-google` |
| Telefone | `fa-solid fa-phone` |
| Email | `fa-solid fa-envelope` |
| Localização | `fa-solid fa-location-dot` |
| Tour Virtual | `fa-solid fa-street-view` |
| Contato/vCard | `fa-solid fa-address-book` |
| Cardápio | `fa-solid fa-utensils` |
| Agendamento | `fa-solid fa-calendar-check` |
| E-book | `fa-solid fa-book-open` |
| Curso/Mentoria | `fa-solid fa-graduation-cap` |
| Loja/Catálogo | `fa-solid fa-bag-shopping` |

---

## 🧠 COMO O AGENTE DEVE INICIAR

Quando for acionado com esta skill, o agente deve começar COM ESTA MENSAGEM EXATA:

---

**"Olá! Vou construir o Links 360 para você com qualidade máxima, seguindo o padrão premium da AG5.**

**Para começar, preciso das informações do negócio. Você pode me enviar em qualquer formato:**
- ✉️ **Texto direto** com os dados da empresa
- 📄 **Arquivo TXT ou PDF** com o briefing
- 💻 **HTML do site** existente (cole o código aqui)
- 📁 **Caminho da pasta** com os arquivos do site atual (ex: `C:\\Users\\mauri\\Documents\\...\\nome-empresa`)

> 💡 **Se enviar o caminho da pasta, farei a varredura automática de todos os assets (fotos, vídeos, logo, favicon) e os copiarei automaticamente para o projeto — sem trabalho manual para você!**

**Aguardo as informações para iniciar o processo! 🚀"**

---

*Skill desenvolvida pela AG5 Agência — Processo padronizado para garantia de qualidade e consistência na produção de Links 360 premium.*

---

## 🏁 REGRA DE OURO FINAL — QUALIDADE vs VELOCIDADE

**O agente NUNCA deve entregar o projeto "sem parar" para não sobrecarregar o contexto e entregar algo "meia-boca".**

1. Ao final de cada bloco de 2 seções (conforme o Passo a Passo), o agente DEVE reportar o que foi feito detalhadamente.
2. O agente DEVE perguntar se o usuário deseja realizar algum ajuste fino naquelas seções antes de prosseguir.
3. Somente após o "OK" ou "Pode seguir" do usuário, o agente carrega o próximo módulo e continua.
4. Se o contexto começar a ficar pesado, o agente deve sugerir um resumo do que já foi consolidado e focar apenas no código novo.
