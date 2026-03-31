---
name: skill-github-deploy
description: >
  Guia mestre para o processo de deploy no GitHub, abrangendo desde a instalação inicial
  até o fluxo de atualizações rotineiras. Essencial para garantir a integridade do código
  e versionamento correto em todos os projetos da AG5.
skills:
  - version-control
  - devops-basics
  - clean-git-history
---

# 🚀 SKILL: Deploy GitHub (Master Guide)

## 📋 OBJETIVO

Padronizar e simplificar o uso do GitHub nos projetos. Esta skill orienta o agente (ou usuário) sobre como preparar o ambiente, sincronizar repositórios e realizar atualizações de forma segura e eficiente.

---

## 🛠️ PASSO 1 — INSTALAÇÃO E CONFIGURAÇÃO INICIAL

Se o ambiente ainda não possui Git configurado, siga esta ordem:

### 1.1 Instalação (Windows)
```powershell
# Verificar se já existe
git --version

# Se não existir, instalar via winget
winget install --id Git.Git -e --source winget
```

### 1.2 Configuração de Identidade
Essencial para que os commits apareçam com o autor correto no GitHub.
```powershell
git config --global user.name "Seu Nome"
git config --global user.email "seu-email@exemplo.com"
```

---

## 🏗️ PASSO 2 — SETUP DO REPOSITÓRIO

Como conectar um projeto local a um repositório novo ou existente no GitHub.

### 2.1 Novo Repositório Local
```powershell
# Na raiz da pasta do projeto
git init
git add .
git commit -m "init: setup inicial do projeto"
git branch -M main
git remote add origin https://github.com/usuario/nome-do-repositorio.git
git push -u origin main
```

### 2.2 Clonando Repositório Existente
```powershell
git clone https://github.com/usuario/nome-do-repositorio.git
```

---

## 🔄 PASSO 3 — FLUXO DE DEPLOY ROTINEIRO (PADRÃO AG5)

Toda vez que uma alteração/melhoria for finalizada e validada localmente, o deploy DEVE seguir estes 3 comandos:

### 3.1 Adicionar e Comitar
Sempre use mensagens claras seguindo o padrão [Conventional Commits](https://www.conventionalcommits.org/).

```powershell
# 1. Adiciona todas as mudanças
git add .

# 2. Registra a alteração com prefixo descritivo
# Prefixos: feat (nova funcionalidade), fix (correção), refactor (melhoria de código), docs (documentação)
git commit -m "feat: adiciona nova seção de contato no rodapé"
```

### 3.2 Enviar para o GitHub
```powershell
# 3. Envia para a branch principal
git push origin main
```

---

## 🛡️ PASSO 4 — BOAS PRÁTICAS E SEGURANÇA

### 4.1 Arquivo `.gitignore`
Sempre verifique se arquivos sensíveis ou pastas pesadas não estão sendo rastreados.
**Obrigatório ignorar:**
- `node_modules/`
- `.env` (credenciais e chaves API)
- `.vscode/` ou `.idea/` (configurações pessoais de IDE)
- `tmp/` ou logs de erro

### 4.2 Verificação Pré-Push
Antes de fazer o `push`, o agente DEVE:
1. Confirmar que não há chaves de API expostas no código.
2. Verificar se o projeto roda sem erros críticos de console.

---

## 📋 CHECKLIST DE DEPLOY RÁPIDO

> [!TIP]
> Use este checklist quando solicitado para "fazer deploy":
> - [ ] `git status` (verificar o que mudou)
> - [ ] `git add .`
> - [ ] `git commit -m "descrição curta e clara"`
> - [ ] `git push origin main`
