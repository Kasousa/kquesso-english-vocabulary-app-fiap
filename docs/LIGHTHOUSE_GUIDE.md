# 📊 Guia Completo do Lighthouse

## O que é o Lighthouse?

O Lighthouse é uma ferramenta automatizada de código aberto do Google para melhorar a qualidade de páginas web. Ele executa auditorias de:
- **Performance** (desempenho)
- **Accessibility** (acessibilidade)
- **Best Practices** (melhores práticas)
- **SEO** (otimização para motores de busca)
- **PWA** (Progressive Web App)

## Como Executar o Lighthouse

### Método 1: Chrome DevTools (Mais Fácil)

1. **Abra seu site no Google Chrome**
   - Acesse a URL do seu deploy (Vercel, Netlify, etc.)

2. **Abra o DevTools**
   - Windows/Linux: `F12` ou `Ctrl + Shift + I`
   - Mac: `Cmd + Option + I`

3. **Vá para a aba Lighthouse**
   - Clique na aba "Lighthouse" (pode estar no menu ">>")

4. **Configure a análise**
   - ✅ Performance
   - ✅ Accessibility
   - ✅ Best Practices
   - ✅ SEO
   - Escolha: Desktop ou Mobile (recomendo ambos!)

5. **Execute a análise**
   - Clique em "Analyze page load"
   - Aguarde alguns segundos

6. **Veja os resultados**
   - O Lighthouse mostrará scores de 0-100 para cada categoria
   - Role a página para ver detalhes e recomendações

7. **Salve o relatório**
   - Clique no ícone de "Download" (⬇️) no topo
   - Salve como HTML ou JSON

### Método 2: PageSpeed Insights (Online)

1. Acesse: https://pagespeed.web.dev/
2. Cole a URL do seu site
3. Clique em "Analisar"
4. Veja os resultados para Mobile e Desktop
5. Tire um print ou salve o PDF

### Método 3: CLI (Linha de Comando)

```bash
# Instalar globalmente
npm install -g lighthouse

# Executar análise
lighthouse https://seu-site.vercel.app

# Salvar relatório HTML
lighthouse https://seu-site.vercel.app --output html --output-path ./lighthouse-report.html

# Abrir automaticamente
lighthouse https://seu-site.vercel.app --view

# Modo mobile
lighthouse https://seu-site.vercel.app --preset=mobile

# Modo desktop
lighthouse https://seu-site.vercel.app --preset=desktop
```

## Entendendo as Métricas

### 🎯 Core Web Vitals (Mais Importantes)

#### 1. **LCP - Largest Contentful Paint**
- **O que é**: Tempo até o maior elemento de conteúdo aparecer
- **Meta**: ≤ 2.5 segundos (bom) | 2.5-4s (precisa melhorar) | > 4s (ruim)
- **Por que importa**: Indica quando o usuário vê o conteúdo principal
- **Como melhorar**:
  - Otimizar imagens (comprimir, usar WebP)
  - Usar CDN
  - Fazer lazy loading de imagens
  - Minimizar CSS/JS

#### 2. **FID - First Input Delay**
- **O que é**: Tempo até a página responder à primeira interação
- **Meta**: ≤ 100ms (bom) | 100-300ms (precisa melhorar) | > 300ms (ruim)
- **Por que importa**: Mede a responsividade da página
- **Como melhorar**:
  - Reduzir JavaScript pesado
  - Code splitting
  - Web Workers para tarefas pesadas

#### 3. **CLS - Cumulative Layout Shift**
- **O que é**: Quanto os elementos "pulam" durante o carregamento
- **Meta**: ≤ 0.1 (bom) | 0.1-0.25 (precisa melhorar) | > 0.25 (ruim)
- **Por que importa**: Evita cliques acidentais e frustrações
- **Como melhorar**:
  - Definir tamanhos de imagens (width/height)
  - Reservar espaço para anúncios/embeds
  - Evitar injetar conteúdo acima do conteúdo existente

### 📊 Outras Métricas Importantes

#### 4. **FCP - First Contentful Paint**
- **O que é**: Tempo até aparecer o primeiro conteúdo (qualquer texto/imagem)
- **Meta**: ≤ 1.8s (bom)
- **Significado**: Primeiro feedback visual ao usuário

#### 5. **TTI - Time to Interactive**
- **O que é**: Tempo até a página estar totalmente interativa
- **Meta**: ≤ 3.8s (bom)
- **Significado**: Quando o usuário pode usar a página completamente

#### 6. **Speed Index**
- **O que é**: Rapidez com que o conteúdo é exibido
- **Meta**: ≤ 3.4s (bom)
- **Significado**: Velocidade percebida pelo usuário

#### 7. **TBT - Total Blocking Time**
- **O que é**: Tempo total que a thread principal está bloqueada
- **Meta**: ≤ 200ms (bom)
- **Significado**: Afeta a responsividade

## Como Capturar e Documentar

### Passo 1: Faça o Deploy
```bash
# Vercel
vercel --prod

# Netlify
npm run build
netlify deploy --prod --dir=dist
```

### Passo 2: Execute o Lighthouse
- Abra o Chrome DevTools
- Vá para Lighthouse
- Execute a análise

### Passo 3: Capture a Tela
- **Windows**: `Win + Shift + S` ou Ferramenta de Captura
- **Mac**: `Cmd + Shift + 4` ou `Cmd + Shift + 5`
- Capture a tela inteira dos resultados

### Passo 4: Salve a Imagem
```
/docs/lighthouse-results.png
```

### Passo 5: Adicione ao README
```markdown
### 📸 Resultados do Lighthouse

![Lighthouse Results](./docs/lighthouse-results.png)

**Data da análise**: 12/02/2026
**URL analisada**: https://seu-app.vercel.app
**Modo**: Desktop

| Categoria | Score |
|-----------|-------|
| Performance | 98 |
| Accessibility | 100 |
| Best Practices | 100 |
| SEO | 100 |

#### Core Web Vitals
- **LCP**: 1.2s ✅
- **FID**: 8ms ✅
- **CLS**: 0.01 ✅
```

## Dicas para Obter 100 em Performance

### ✅ Otimização de Imagens
```html
<!-- Use WebP -->
<img src="image.webp" alt="description" width="800" height="600">

<!-- Lazy loading -->
<img src="image.jpg" loading="lazy" alt="description">
```

### ✅ Minificação
```bash
# Vite já faz isso automaticamente no build
npm run build
```

### ✅ Code Splitting
```javascript
// Componentes assíncronos
const WordCard = defineAsyncComponent(() =>
  import('./components/WordCard.vue')
)
```

### ✅ Fontes Otimizadas
```html
<!-- Preconnect para fontes -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
```

### ✅ Cache
```javascript
// Service Worker para cache (PWA)
// Vite PWA Plugin
```

## Interpretando os Resultados

### 🟢 Verde (90-100): Excelente
- Seu site está otimizado!
- Continue monitorando

### 🟡 Amarelo (50-89): Bom, mas pode melhorar
- Identifique as principais recomendações
- Implemente as correções sugeridas

### 🔴 Vermelho (0-49): Precisa de atenção
- Priorize as correções
- Foque nos Core Web Vitals primeiro

## Checklist Pré-Análise

Antes de rodar o Lighthouse, certifique-se:

- [ ] Site está em produção (não localhost)
- [ ] Build de produção foi feito (`npm run build`)
- [ ] Navegador está em modo anônimo (sem extensões)
- [ ] Não há outras abas consumindo recursos
- [ ] Conexão de internet está estável
- [ ] Cache do navegador foi limpo

## Recursos Adicionais

- 📚 [Documentação Oficial](https://developer.chrome.com/docs/lighthouse/)
- 📊 [Web.dev - Core Web Vitals](https://web.dev/vitals/)
- 🎓 [Google Web Fundamentals](https://developers.google.com/web/fundamentals)
- 🔧 [PageSpeed Insights](https://pagespeed.web.dev/)

## Exemplo de Análise Completa

```markdown
# Análise Lighthouse - English Vocabulary App

## Informações
- **Data**: 12/02/2026
- **URL**: https://english-vocab-fiap.vercel.app
- **Dispositivo**: Desktop
- **Navegador**: Chrome 120

## Scores Gerais
| Categoria | Score | Status |
|-----------|-------|--------|
| Performance | 98 | 🟢 Excelente |
| Accessibility | 100 | 🟢 Perfeito |
| Best Practices | 100 | 🟢 Perfeito |
| SEO | 100 | 🟢 Perfeito |

## Core Web Vitals
- **LCP**: 1.2s (Meta: ≤2.5s) ✅
- **FID**: 8ms (Meta: ≤100ms) ✅
- **CLS**: 0.01 (Meta: ≤0.1) ✅

## Métricas Adicionais
- **FCP**: 0.9s ✅
- **TTI**: 2.1s ✅
- **Speed Index**: 1.3s ✅
- **TBT**: 45ms ✅

## Oportunidades Identificadas
Nenhuma oportunidade crítica encontrada.

## Diagnósticos
✅ Todas as verificações passaram.

## Conclusão
O site apresenta excelente performance e está otimizado para uma experiência de usuário superior.
```

---

**Boa sorte com sua análise! 🚀**
