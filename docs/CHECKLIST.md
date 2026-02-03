# ✅ Checklist do Projeto - FIAP Front-end Engineering

## 📋 Requisitos Mínimos (7 pontos)

### 1. GitHub
- [ ] Criar repositório público no GitHub
- [ ] Adicionar todos os arquivos do projeto
- [ ] Fazer commit inicial
- [ ] (Se em grupo) Adicionar nomes dos integrantes no README
  ```markdown
  ## Integrantes
  - **Nome do Aluno 1** - RM: XXXXX
  - **Nome do Aluno 2** - RM: XXXXX
  ```

### 2. Deploy em Cloud
- [ ] Escolher plataforma (Vercel, Netlify, Render)
- [ ] Fazer build do projeto: `npm run build`
- [ ] Realizar deploy
- [ ] Testar a URL pública
- [ ] Confirmar que o site está acessível

---

## 🎯 Requisitos para 10 pontos

### 3. README Estruturado (+1 ponto)
- [ ] Título e descrição do projeto
- [ ] Badges (Vue.js, Vite, Tailwind)
- [ ] Finalidade do projeto explicada
- [ ] Stack tecnológica listada e explicada
- [ ] Pré-requisitos claros
- [ ] Instruções de instalação
- [ ] Como executar o projeto
- [ ] Como fazer o build
- [ ] Instruções de deploy detalhadas
- [ ] Estrutura do projeto documentada
- [ ] Seção de integrantes
- [ ] Links úteis

**Recursos:**
- Use o README.md já criado como base
- Consulte: https://www.alura.com.br/artigos/escrever-bom-readme

### 4. Deploy da Própria API (+1 ponto)

#### Opção A: Fork do BFF Original
- [ ] Fork do repositório: https://github.com/jaisonschmidt/fiap-bff
- [ ] Obter chave da OpenAI
- [ ] Configurar variável de ambiente no Render
- [ ] Fazer deploy no Render (ou outra plataforma)
- [ ] Testar a URL da sua API
- [ ] Adicionar repositório da API ao README
- [ ] Adicionar URL pública da API ao README
- [ ] Atualizar URL da API no código do front-end

#### Estrutura no README:
```markdown
## 🔌 Minha API

- **Repositório**: [Link para seu fork/repositório]
- **URL Pública**: https://sua-api.onrender.com/ask
- **Status**: ✅ Online

### Como foi feito
1. Fork do repositório original
2. Configuração da chave OpenAI
3. Deploy no Render
4. Integração com o front-end
```

### 5. Web Vitals / Lighthouse (+1 ponto)

#### Executar Lighthouse
- [ ] Deploy do site em produção
- [ ] Abrir Chrome DevTools (F12)
- [ ] Ir para aba Lighthouse
- [ ] Executar análise completa
- [ ] Capturar screenshot dos resultados

#### Adicionar ao README
- [ ] Screenshot do Lighthouse em `docs/lighthouse-results.png`
- [ ] Tabela com scores obtidos
- [ ] Explicação das métricas principais:

```markdown
### 📊 Métricas do Lighthouse

#### Scores Obtidos
| Categoria | Score |
|-----------|-------|
| Performance | XX |
| Accessibility | XX |
| Best Practices | XX |
| SEO | XX |

#### Core Web Vitals
- **LCP (Largest Contentful Paint)**: X.Xs
  - *Significado*: Tempo até o maior elemento aparecer...
  
- **FID (First Input Delay)**: XXms
  - *Significado*: Tempo de resposta à primeira interação...
  
- **CLS (Cumulative Layout Shift)**: X.XX
  - *Significado*: Estabilidade visual da página...
```

#### Métricas para Explicar
- [ ] **LCP** - Largest Contentful Paint
- [ ] **FID** - First Input Delay  
- [ ] **CLS** - Cumulative Layout Shift
- [ ] **FCP** - First Contentful Paint
- [ ] **TTI** - Time to Interactive
- [ ] **Speed Index**

**Referência**: Use `docs/LIGHTHOUSE_GUIDE.md` para ajuda

---

## 🚀 Passo a Passo Completo

### Fase 1: Preparação
```bash
# 1. Verificar se está tudo funcionando
cd /Users/kaiquesantossousa/Projects/FrontEndFiap
npm install
npm run dev

# 2. Testar no navegador
# Abra: http://localhost:5173
```

### Fase 2: Git e GitHub
```bash
# 1. Inicializar Git (se ainda não foi)
git init

# 2. Adicionar todos os arquivos
git add .

# 3. Fazer commit inicial
git commit -m "feat: initial commit - English Vocabulary App"

# 4. Criar repositório no GitHub
# Vá para: https://github.com/new

# 5. Conectar e enviar
git remote add origin https://github.com/seu-usuario/english-vocabulary-app.git
git branch -M main
git push -u origin main
```

### Fase 3: Deploy
```bash
# Opção A: Vercel
npm install -g vercel
vercel login
vercel
# Copie a URL fornecida

# Opção B: Netlify
npm install -g netlify-cli
npm run build
netlify deploy --prod --dir=dist
# Copie a URL fornecida
```

### Fase 4: Lighthouse
```bash
# 1. Acesse a URL do deploy no Chrome
# 2. Abra DevTools (F12)
# 3. Vá para aba Lighthouse
# 4. Clique em "Analyze page load"
# 5. Aguarde a análise
# 6. Tire um screenshot
# 7. Salve em: docs/lighthouse-results.png
```

### Fase 5: README Final
```bash
# 1. Edite o README.md
# 2. Adicione:
#    - Seu nome e RM
#    - Link do GitHub
#    - Link do deploy
#    - Screenshot do Lighthouse
#    - (Se fez) Link da sua API

# 3. Commit e push
git add .
git commit -m "docs: complete README with deployment info"
git push
```

---

## 📤 Entrega Final

### O que enviar no sistema da FIAP:

1. **Link do Repositório GitHub**
   ```
   https://github.com/seu-usuario/english-vocabulary-app
   ```

2. **Link do Deploy**
   ```
   https://seu-app.vercel.app
   ```

3. **(Opcional) Link da sua API**
   ```
   Repositório: https://github.com/seu-usuario/fiap-bff-fork
   URL: https://sua-api.onrender.com/ask
   ```

4. **Observações**
   - Confirme que o README está completo
   - Verifique que todos os links funcionam
   - Teste o site em diferentes dispositivos

---

## 🎨 Dicas de Personalização

Para destacar seu projeto:

1. **Customize o design**
   - Altere cores em `tailwind.config.js`
   - Adicione seu toque pessoal

2. **Adicione features extras**
   - [ ] Filtro de palavras
   - [ ] Busca
   - [ ] Modo escuro
   - [ ] Favoritos com localStorage
   - [ ] Histórico de palavras
   - [ ] Compartilhar palavra

3. **Melhore o README**
   - Adicione GIFs demonstrativos
   - Crie um logo personalizado
   - Adicione badges do shields.io

---

## ⚠️ Problemas Comuns

### Erro no deploy
```bash
# Certifique-se que o build funciona localmente
npm run build

# Verifique se a pasta dist foi criada
ls -la dist/
```

### API não responde
```bash
# Teste a API original primeiro
curl https://fiap-bff-9aojr.onrender.com/ask

# Verifique a URL no código
# Arquivo: src/App.vue, linha 48
```

### Lighthouse com score baixo
- Use modo anônimo (sem extensões)
- Limpe o cache do navegador
- Execute múltiplas vezes e use a média
- Foque nos Core Web Vitals

---

## ✅ Checklist Final de Entrega

Antes de submeter, confirme:

- [ ] ✅ Código está no GitHub (público)
- [ ] ✅ Site está deployado e acessível
- [ ] ✅ README completo e bem formatado
- [ ] ✅ Nome(s) e RM(s) no README
- [ ] ✅ Links funcionando (GitHub, Deploy)
- [ ] ✅ Screenshot do Lighthouse adicionado
- [ ] ✅ Explicação das métricas Web Vitals
- [ ] ✅ (Bônus) API própria deployada
- [ ] ✅ Teste final em diferentes navegadores
- [ ] ✅ Código limpo e comentado

---

## 🎯 Critérios de Avaliação

| Critério | Pontos | O que avaliar |
|----------|--------|---------------|
| GitHub + Deploy | 7 | Código público e site online |
| README | +1 | Completo e bem estruturado |
| API Própria | +1 | Deploy funcionando |
| Web Vitals | +1 | Screenshot e explicação |
| **TOTAL** | **10** | |

---

## 📞 Suporte

Se tiver dúvidas:

1. Consulte o README.md principal
2. Leia os docs/ (LIGHTHOUSE_GUIDE.md, DEPLOY.md)
3. Teste localmente antes de fazer deploy
4. Peça ajuda aos colegas ou professor

---

**Boa sorte! Você consegue! 🚀**

Data limite: **12/02/2026**
