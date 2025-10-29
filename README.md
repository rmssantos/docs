# Think Exchange Documentation - Mintlify Setup

Este repositório contém a documentação do Think Exchange pronta para deploy no Mintlify.

## 📁 Estrutura Atual

```
mintlify-docs/
├── mint.json                    ✅ CRIADO - Configuração principal
├── introduction.mdx             ✅ CRIADO - Página inicial
├── quickstart.mdx               ✅ CRIADO - Quick start guide
├── how-it-works.mdx             ⏳ A CRIAR
├── essentials/
│   ├── x402-protocol.mdx        ⏳ A CRIAR
│   ├── specialized-rooms.mdx    ⏳ A CRIAR
│   └── payment-methods.mdx      ⏳ A CRIAR
├── guides/
│   ├── web-interface.mdx        ⏳ A CRIAR
│   ├── nodejs-sdk.mdx           ⏳ A CRIAR
│   ├── python-sdk.mdx           ⏳ A CRIAR
│   └── ai-agents.mdx            ⏳ A CRIAR
├── api-reference/
│   ├── introduction.mdx         ⏳ A CRIAR
│   ├── authentication.mdx       ⏳ A CRIAR
│   ├── rooms/
│   │   └── list.mdx             ⏳ A CRIAR
│   ├── tasks/
│   │   ├── get.mdx              ⏳ A CRIAR
│   │   └── messages.mdx         ⏳ A CRIAR
│   └── x402/
│       └── create-task.mdx      ✅ CRIADO
├── examples/
│   ├── nodejs.mdx               ⏳ A CRIAR
│   ├── python.mdx               ⏳ A CRIAR
│   └── curl.mdx                 ⏳ A CRIAR
├── security.mdx                 ⏳ A CRIAR
├── pricing.mdx                  ⏳ A CRIAR
├── faq.mdx                      ⏳ A CRIAR
├── images/                      ⏳ A CRIAR
│   ├── hero-light.png
│   ├── hero-dark.png
│   └── ...
└── logo/                        ⏳ A CRIAR
    ├── light.svg
    └── dark.svg
```

## 🚀 Deploy para Mintlify

### Passo 1: Copiar Ficheiros para o Repo GitHub

```bash
# Navegar para o repo de docs
cd /caminho/para/docs

# Copiar ficheiros do mintlify-docs para o repo
cp -r /caminho/para/ai_council/mintlify-docs/* .

# Verificar estrutura
ls -la
```

### Passo 2: Fazer Commit e Push

```bash
# Add todos os ficheiros
git add .

# Commit
git commit -m "feat: Initial Mintlify documentation setup

- Added mint.json configuration
- Created introduction and quickstart pages
- Added API reference for x402 create-task endpoint
- Setup navigation structure"

# Push para GitHub
git push origin main
```

### Passo 3: Conectar ao Mintlify

1. Vai a [Mintlify Dashboard](https://dashboard.mintlify.com/)
2. Clica em "New Project"
3. Conecta o repo: `https://github.com/rmssantos/docs`
4. Mintlify irá automaticamente detectar o `mint.json`
5. Deploy será feito automaticamente

### Passo 4: Configurar Custom Domain

1. No Mintlify Dashboard, vai a "Settings" > "Custom Domain"
2. Adiciona: `docs.thinkexchange.ai`
3. Mintlify fornece um CNAME record
4. No teu DNS provider (Cloudflare, etc.):
   - Tipo: CNAME
   - Nome: `docs`
   - Valor: `<mintlify-cname>` (fornecido pelo Mintlify)
   - TTL: Auto
5. Aguarda propagação DNS (5-30 minutos)
6. Verifica em: `https://docs.thinkexchange.ai`

## 📝 Ficheiros a Criar

### Essenciais (Alta Prioridade)

1. **how-it-works.mdx** - Como funciona o sistema
2. **essentials/x402-protocol.mdx** - Explicação detalhada do x402
3. **essentials/specialized-rooms.mdx** - As 7 rooms especializadas
4. **essentials/payment-methods.mdx** - Comparação x402 vs créditos
5. **security.mdx** - Documento de segurança
6. **pricing.mdx** - Tabela de preços detalhada
7. **faq.mdx** - Perguntas frequentes

### API Reference (Alta Prioridade)

1. **api-reference/introduction.mdx** - Overview da API
2. **api-reference/authentication.mdx** - JWT vs x402
3. **api-reference/rooms/list.mdx** - GET /x402/rooms
4. **api-reference/tasks/get.mdx** - GET /x402/tasks/:id
5. **api-reference/tasks/messages.mdx** - GET /x402/tasks/:id/messages

### Guides (Média Prioridade)

1. **guides/web-interface.mdx** - Usar a plataforma web
2. **guides/nodejs-sdk.mdx** - Guia completo Node.js
3. **guides/python-sdk.mdx** - Guia completo Python
4. **guides/ai-agents.mdx** - Como AI agents usam o serviço

### Examples (Média Prioridade)

1. **examples/nodejs.mdx** - Exemplos completos Node.js
2. **examples/python.mdx** - Exemplos completos Python
3. **examples/curl.mdx** - Exemplos cURL com HTTP 402

### Assets (Baixa Prioridade)

1. Logo light/dark (SVG)
2. Hero image light/dark (PNG)
3. Screenshots da plataforma
4. Diagramas de fluxo

## 🎨 Customização

### Cores (mint.json)

```json
"colors": {
  "primary": "#3B82F6",      // Think Exchange blue
  "light": "#60A5FA",
  "dark": "#2563EB",
  "anchors": {
    "from": "#3B82F6",
    "to": "#8B5CF6"          // Gradient purple
  }
}
```

### Navigation

A navigation está configurada em `mint.json`. Para adicionar novas páginas:

1. Cria o ficheiro MDX na pasta apropriada
2. Adiciona a referência em `mint.json` > `navigation`
3. Push para GitHub
4. Mintlify atualiza automaticamente

## 📚 Recursos Mintlify

- [Mintlify Documentation](https://mintlify.com/docs)
- [MDX Components](https://mintlify.com/docs/content/components)
- [API Reference Guide](https://mintlify.com/docs/api-playground/openapi)
- [Custom Domain Setup](https://mintlify.com/docs/settings/custom-domain)

## 🔧 Desenvolvimento Local

```bash
# Install Mintlify CLI
npm i -g mintlify

# Preview docs locally
cd docs
mintlify dev

# Abrir em http://localhost:3000
```

## ✅ Checklist de Deploy

### Antes do Deploy

- [x] Criar mint.json com configuração
- [x] Criar páginas principais (introduction, quickstart)
- [x] Criar pelo menos 1 API reference completo
- [ ] Adicionar logos (light/dark)
- [ ] Adicionar imagens hero
- [ ] Configurar analytics (Google Analytics)
- [ ] Testar todos os links internos
- [ ] Verificar código syntax highlighting

### Depois do Deploy

- [ ] Configurar custom domain (docs.thinkexchange.ai)
- [ ] Verificar SSL funciona
- [ ] Testar navegação completa
- [ ] Verificar search funciona
- [ ] Adicionar link na plataforma principal
- [ ] Anunciar nas redes sociais

## 🆘 Troubleshooting

### Mintlify não detecta mint.json

- Certifica-te que `mint.json` está na root do repo
- Verifica JSON é válido (usa [JSONLint](https://jsonlint.com/))
- Faz push para branch `main`

### Custom domain não funciona

- Aguarda propagação DNS (até 48h)
- Verifica CNAME record no DNS provider
- Usa `dig docs.thinkexchange.ai` para debug

### Imagens não aparecem

- Imagens devem estar em `/images` ou `/logo`
- Usa caminhos relativos: `/images/hero.png`
- Commit e push das imagens para GitHub

## 📞 Suporte

- Mintlify Support: support@mintlify.com
- Mintlify Discord: https://discord.gg/mintlify
- Think Exchange: https://thinkexchange.ai/support
