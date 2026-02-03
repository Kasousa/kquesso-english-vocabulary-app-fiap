# Guia de Deploy

## Vercel

1. Instale a CLI:
```bash
npm install -g vercel
```

2. Faça login:
```bash
vercel login
```

3. Execute na raiz do projeto:
```bash
vercel
```

4. Para produção:
```bash
vercel --prod
```

## Netlify

1. Instale a CLI:
```bash
npm install -g netlify-cli
```

2. Build:
```bash
npm run build
```

3. Deploy:
```bash
netlify deploy --prod --dir=dist
```

## Render

1. Crie uma conta em render.com
2. Conecte seu repositório GitHub
3. Configure:
   - Build Command: `npm run build`
   - Publish Directory: `dist`
4. Deploy automático a cada push!

## Variáveis de Ambiente

Se você configurar sua própria API, crie um arquivo `.env`:

```env
VITE_API_URL=https://sua-api.onrender.com/ask
```

E use no código:
```javascript
const API_URL = import.meta.env.VITE_API_URL
```
