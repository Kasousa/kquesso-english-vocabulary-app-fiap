# 📚 Guia de Git e GitHub para o Projeto

## 🚀 Primeiro Uso - Configuração Inicial

### 1. Configurar seu Git (se ainda não fez)
```bash
# Configure seu nome
git config --global user.name "Seu Nome"

# Configure seu email (use o mesmo do GitHub)
git config --global user.email "seu.email@exemplo.com"

# Verifique as configurações
git config --list
```

### 2. Criar Repositório no GitHub

1. Acesse: https://github.com/new
2. Preencha:
   - **Repository name**: `english-vocabulary-app` (ou outro nome)
   - **Description**: `Aplicação web para aprender vocabulário em inglês - FIAP`
   - **Public**: ✅ (obrigatório para o trabalho)
   - **Initialize this repository**: ❌ Não marque nada
3. Clique em "Create repository"

## 📤 Enviar Projeto para o GitHub

### Método 1: Projeto Novo (Recomendado)

```bash
# 1. Entre na pasta do projeto
cd /Users/kaiquesantossousa/Projects/FrontEndFiap

# 2. Inicialize o Git
git init

# 3. Adicione todos os arquivos
git add .

# 4. Faça o primeiro commit
git commit -m "feat: initial commit - English Vocabulary App FIAP"

# 5. Renomeie a branch para main
git branch -M main

# 6. Adicione o repositório remoto (substitua SEU_USUARIO)
git remote add origin https://github.com/SEU_USUARIO/english-vocabulary-app.git

# 7. Envie para o GitHub
git push -u origin main
```

### Método 2: Se já existe um repositório

```bash
# 1. Clone o repositório vazio
git clone https://github.com/SEU_USUARIO/english-vocabulary-app.git

# 2. Entre na pasta
cd english-vocabulary-app

# 3. Copie os arquivos do projeto para esta pasta

# 4. Adicione e commite
git add .
git commit -m "feat: initial commit"

# 5. Envie
git push origin main
```

## 🔄 Comandos do Dia a Dia

### Ver status das mudanças
```bash
git status
```

### Adicionar arquivos
```bash
# Adicionar arquivo específico
git add README.md

# Adicionar todos os arquivos modificados
git add .

# Adicionar todos os arquivos .vue
git add *.vue
```

### Fazer commit
```bash
# Commit com mensagem
git commit -m "docs: update README with deployment info"

# Commit de múltiplos arquivos
git add .
git commit -m "feat: add new feature"
```

### Enviar para o GitHub
```bash
# Enviar para a branch main
git push origin main

# Ou simplesmente (se já configurou upstream)
git push
```

### Ver histórico de commits
```bash
# Ver últimos commits
git log

# Ver últimos 5 commits de forma compacta
git log --oneline -5

# Ver mudanças de cada commit
git log -p
```

### Desfazer mudanças
```bash
# Desfazer mudanças de um arquivo (antes do add)
git checkout -- README.md

# Remover arquivo do stage (depois do add)
git reset HEAD README.md

# Desfazer último commit (mantém as mudanças)
git reset --soft HEAD~1

# Desfazer último commit (descarta as mudanças) ⚠️
git reset --hard HEAD~1
```

## 🌿 Trabalhando em Grupo

### Clonar o repositório
```bash
# Cada integrante clona
git clone https://github.com/USUARIO/english-vocabulary-app.git
cd english-vocabulary-app
```

### Atualizar seu repositório local
```bash
# Puxar mudanças do GitHub
git pull origin main
```

### Workflow recomendado
```bash
# 1. Sempre puxe as mudanças primeiro
git pull origin main

# 2. Faça suas mudanças
# ... edite os arquivos ...

# 3. Veja o que mudou
git status

# 4. Adicione as mudanças
git add .

# 5. Faça commit
git commit -m "feat: add dark mode toggle"

# 6. Envie para o GitHub
git push origin main
```

### Resolver conflitos
```bash
# 1. Puxe as mudanças
git pull origin main

# 2. Se houver conflito, o Git vai avisar
# Abra os arquivos com conflito e procure por:
# <<<<<<< HEAD
# suas mudanças
# =======
# mudanças do outro integrante
# >>>>>>> branch

# 3. Escolha qual versão manter (ou combine)

# 4. Adicione os arquivos resolvidos
git add arquivo-com-conflito.js

# 5. Finalize o merge
git commit -m "merge: resolve conflicts"

# 6. Envie
git push origin main
```

## 📋 Boas Práticas de Commit

### Padrão de Mensagens (Conventional Commits)

```bash
# Adicionar nova funcionalidade
git commit -m "feat: add word favorite feature"

# Corrigir bug
git commit -m "fix: resolve API timeout issue"

# Atualizar documentação
git commit -m "docs: improve README instructions"

# Refatorar código
git commit -m "refactor: optimize WordCard component"

# Estilização
git commit -m "style: improve card animations"

# Testes
git commit -m "test: add unit tests for API calls"

# Build/Deploy
git commit -m "build: update vite config"

# Outros
git commit -m "chore: update dependencies"
```

### Mensagens Descritivas
```bash
# ❌ Ruim
git commit -m "fix"
git commit -m "update"
git commit -m "asdfsdf"

# ✅ Bom
git commit -m "fix: resolve API error handling"
git commit -m "docs: add Lighthouse guide"
git commit -m "feat: implement dark mode"
```

## 🏷️ Tags e Releases

### Criar uma tag (versão)
```bash
# Tag leve
git tag v1.0.0

# Tag anotada (recomendado)
git tag -a v1.0.0 -m "Release 1.0.0 - Initial version"

# Enviar tag para o GitHub
git push origin v1.0.0

# Enviar todas as tags
git push origin --tags
```

### Criar Release no GitHub
1. Vá para o repositório no GitHub
2. Clique em "Releases"
3. Clique em "Create a new release"
4. Escolha a tag ou crie uma nova
5. Adicione título e descrição
6. Clique em "Publish release"

## 🔧 Comandos Úteis

### Ver repositório remoto
```bash
git remote -v
```

### Mudar URL do repositório remoto
```bash
git remote set-url origin https://github.com/NOVO_USUARIO/novo-repo.git
```

### Ver diferenças
```bash
# Ver mudanças não commitadas
git diff

# Ver mudanças de um arquivo específico
git diff README.md

# Ver mudanças já adicionadas (staged)
git diff --staged
```

### Criar .gitignore
```bash
# Já existe no projeto, mas se precisar adicionar mais:
echo "node_modules/" >> .gitignore
echo ".env" >> .gitignore
echo "dist/" >> .gitignore
git add .gitignore
git commit -m "chore: update .gitignore"
```

## 📝 Adicionar Integrantes no README

### Para Trabalhos em Grupo

Edite o README.md e adicione:

```markdown
## 👥 Integrantes

- **João Silva** - RM: 12345
  - GitHub: [@joaosilva](https://github.com/joaosilva)
  
- **Maria Santos** - RM: 67890
  - GitHub: [@mariasantos](https://github.com/mariasantos)
  
- **Pedro Costa** - RM: 54321
  - GitHub: [@pedrocosta](https://github.com/pedrocosta)
  
- **Ana Oliveira** - RM: 98765
  - GitHub: [@anaoliveira](https://github.com/anaoliveira)
```

Depois:
```bash
git add README.md
git commit -m "docs: add team members info"
git push origin main
```

## 🚨 Problemas Comuns

### Erro: "fatal: not a git repository"
```bash
# Solução: Inicialize o Git
git init
```

### Erro: "fatal: remote origin already exists"
```bash
# Solução: Remova e adicione novamente
git remote remove origin
git remote add origin https://github.com/USUARIO/repo.git
```

### Erro: "Permission denied"
```bash
# Solução 1: Use HTTPS em vez de SSH
git remote set-url origin https://github.com/USUARIO/repo.git

# Solução 2: Configure SSH
# Veja: https://docs.github.com/en/authentication/connecting-to-github-with-ssh
```

### Erro: "Updates were rejected"
```bash
# Solução: Puxe as mudanças primeiro
git pull origin main
# Resolva conflitos se houver
git push origin main
```

### Não quer commitar node_modules
```bash
# Certifique-se que está no .gitignore
echo "node_modules/" >> .gitignore

# Se já foi commitado, remova do Git (mas mantém no disco)
git rm -r --cached node_modules/
git commit -m "chore: remove node_modules from git"
git push origin main
```

## 📚 Recursos Adicionais

- **GitHub Docs**: https://docs.github.com
- **Git Cheat Sheet**: https://education.github.com/git-cheat-sheet-education.pdf
- **Interactive Git Tutorial**: https://learngitbranching.js.org/
- **Conventional Commits**: https://www.conventionalcommits.org/

## ✅ Checklist Git para Entrega

Antes de submeter o trabalho:

- [ ] Repositório é público
- [ ] README está atualizado
- [ ] Todos os arquivos importantes estão commitados
- [ ] `.gitignore` está configurado (não subir `node_modules/`, `dist/`, `.env`)
- [ ] Commits têm mensagens descritivas
- [ ] (Se grupo) Nome de todos os integrantes no README
- [ ] Link do repositório está funcionando
- [ ] Testar: clonar em outra pasta e rodar `npm install && npm run dev`

---

**Dica Final**: Faça commits frequentes com mensagens claras. É melhor muitos commits pequenos do que um commit gigante! 🚀
