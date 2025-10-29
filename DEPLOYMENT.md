# 🚀 Quick Deployment Guide

## Pré-requisitos

✅ Conta Mintlify criada
✅ Repo GitHub: https://github.com/rmssantos/docs
✅ Repo linkado à conta Mintlify

## Passos para Deploy

### 1. Copiar Ficheiros

```bash
# Clonar o repo de docs
git clone https://github.com/rmssantos/docs.git
cd docs

# Copiar todos os ficheiros do mintlify-docs
cp -r ../ai_council/mintlify-docs/* .

# Verificar ficheiros copiados
ls -la
```

### 2. Verificar Estrutura

```
docs/
├── mint.json              ✅
├── introduction.mdx       ✅
├── quickstart.mdx         ✅
├── api-reference/
│   └── x402/
│       └── create-task.mdx ✅
├── README.md              ✅
└── .gitignore             ✅
```

### 3. Commit e Push

```bash
git add .
git status  # Verifica que ficheiros serão comittados

git commit -m "feat: Initial Think Exchange documentation

- Mintlify configuration (mint.json)
- Introduction and Quick Start pages
- API reference for x402 create-task endpoint
- Deployment guides and README"

git push origin main
```

### 4. Deploy Automático no Mintlify

1. Mintlify detecta automaticamente o push
2. Build inicia automaticamente
3. Aguarda 2-3 minutos
4. Docs ficam disponíveis em: `https://<your-subdomain>.mintlify.app`

### 5. Configurar Custom Domain

#### No Mintlify Dashboard:

1. Vai a **Settings** > **Custom Domain**
2. Adiciona: `docs.thinkexchange.ai`
3. Copia o **CNAME record** fornecido (exemplo: `cname.mintlify.app`)

#### No teu DNS Provider (Cloudflare, etc.):

```
Tipo: CNAME
Nome: docs
Valor: <mintlify-cname>  (do step anterior)
TTL: Auto (ou 3600)
Proxy: Desligado (DNS only)
```

#### Verificar:

```bash
# Aguardar propagação (5-30 min)
dig docs.thinkexchange.ai

# Testar no browser
https://docs.thinkexchange.ai
```

## Desenvolvimento Local

### Instalar Mintlify CLI

```bash
npm i -g mintlify
```

### Preview Local

```bash
cd docs
mintlify dev
```

Abre automaticamente em `http://localhost:3000`

## Próximos Passos

### Conteúdo Essencial a Criar

1. **how-it-works.mdx** - Diagrama de como funciona
2. **essentials/x402-protocol.mdx** - Deep dive x402
3. **essentials/specialized-rooms.mdx** - 7 rooms detalhadas
4. **security.mdx** - Documento completo de segurança
5. **pricing.mdx** - Tabela de preços

### API Reference Completo

6. **api-reference/introduction.mdx**
7. **api-reference/rooms/list.mdx** - GET /x402/rooms
8. **api-reference/tasks/get.mdx** - GET /x402/tasks/:id
9. **api-reference/tasks/messages.mdx** - GET /x402/tasks/:id/messages

### Guides e Examples

10. **guides/nodejs-sdk.mdx** - Tutorial completo Node.js
11. **guides/python-sdk.mdx** - Tutorial completo Python
12. **examples/nodejs.mdx** - Exemplos práticos
13. **examples/python.mdx** - Exemplos práticos

### Assets

14. Logo (light.svg, dark.svg)
15. Hero images (light.png, dark.png)
16. Screenshots da plataforma

## Template MDX Básico

```mdx
---
title: 'Your Title'
description: 'Your description'
---

## Introduction

Your content here.

<CardGroup cols={2}>
  <Card title="Card 1" icon="icon-name">
    Description
  </Card>
  <Card title="Card 2" icon="icon-name">
    Description
  </Card>
</CardGroup>

## Section

<Info>
  Info callout
</Info>

<Warning>
  Warning callout
</Warning>

<Tip>
  Tip callout
</Tip>

\`\`\`javascript
// Code example
const example = 'code';
\`\`\`
```

## Troubleshooting

### Build falha

```bash
# Verificar JSON válido
cat mint.json | python -m json.tool

# Verificar MDX syntax
mintlify dev  # Mostra erros localmente
```

### Domain não funciona

```bash
# Verificar DNS propagação
dig docs.thinkexchange.ai
nslookup docs.thinkexchange.ai

# Aguardar até 48h para propagação completa
```

### Páginas não aparecem no menu

1. Verifica que a página está referenciada em `mint.json` > `navigation`
2. Verifica que o caminho do ficheiro está correto
3. Faz push para GitHub
4. Aguarda rebuild automático

## Recursos

- 📖 [Mintlify Docs](https://mintlify.com/docs)
- 💬 [Mintlify Discord](https://discord.gg/mintlify)
- 🎨 [Components Guide](https://mintlify.com/docs/content/components)
- 🔧 [Troubleshooting](https://mintlify.com/docs/troubleshooting)

## Support

- **Mintlify:** support@mintlify.com
- **Think Exchange:** support@thinkexchange.ai
