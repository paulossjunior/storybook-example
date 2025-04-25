# 📦 Publicando uma Biblioteca com Storybook Manualmente no npm

Este guia mostra como criar, buildar e publicar manualmente uma biblioteca de componentes que usa o [Storybook](https://storybook.js.org/) para documentação visual e o [npm](https://www.npmjs.com/) como registro público de pacotes.

---

## ✅ Pré-requisitos

- Conta no [npm](https://www.npmjs.com/signup)
- Node.js e npm instalados (`node -v` e `npm -v`)
- Projeto com:
  - `package.json`
  - Pasta `src/` com os componentes
  - Storybook configurado (`.storybook/`)
  - Um script `build` funcional para gerar a lib (ex: `dist/`)

---

## 📁 Estrutura esperada

```
meu-design-system/
├── .storybook/
├── dist/
├── src/
├── package.json
├── vite.config.ts
└── README.md
```

---

## 🛠️ Passo a Passo

### 1. 📦 Configure o `package.json`

```json
{
  "name": "meu-design-system",
  "version": "1.0.0",
  "main": "dist/index.js",
  "types": "dist/index.d.ts",
  "files": ["dist"],
  "scripts": {
    "build": "vite build",
    "storybook": "storybook dev -p 6006",
    "storybook:build": "storybook build -o storybook-static"
  },
  "keywords": ["componentes", "storybook", "design-system"],
  "author": "Seu Nome",
  "license": "MIT"
}
```

> ⚠️ Escolha um nome de pacote **único**, que ainda não esteja publicado no [npmjs.com](https://www.npmjs.com/).

---

### 2. 🛠️ Build da biblioteca

Gere os arquivos da lib:

```bash
npm run build
```

> Isso deve gerar a pasta `dist/` com os arquivos de saída.

---

### 3. 🧪 Teste local do Storybook

Você pode rodar o Storybook localmente:

```bash
npm run storybook
```

Ou gerar os arquivos para deploy:

```bash
npm run storybook:build
```

> Isso gera a pasta `storybook-static/`, que pode ser usada para publicar no GitHub Pages, Netlify, etc.

---

### 4. 🔐 Faça login no npm

```bash
npm login
```

Siga as instruções e informe seu usuário, senha e e-mail.

---

### 5. 🚀 Publique no npm

```bash
npm publish --access public
```

> Use `--access public` **na primeira publicação**, especialmente se for um pacote com escopo (ex: `@seunome/pacote`).

O Exemplo publicado: [https://www.npmjs.com/package/@paulossjunior/storybook-example](https://www.npmjs.com/package/@paulossjunior/storybook-example)

---



## ✅ Atualizações futuras

1. Mude a versão com:

```bash
npm version patch   # ou minor / major
```

2. Rode novamente:

```bash
npm run build
npm publish
```

---

## 🌐 Publicar o Storybook (opcional)

Para publicar o Storybook visualmente (em GitHub Pages, Netlify, etc.):

```bash
npm run storybook:build
```

Depois hospede o conteúdo da pasta `storybook-static`.

---



## 📎 Links úteis

- [Documentação oficial do Storybook](https://storybook.js.org/docs/react/get-started/introduction)
- [npm CLI publish](https://docs.npmjs.com/cli/v9/commands/npm-publish)
- [Como versionar pacotes](https://docs.npmjs.com/cli/v9/commands/npm-version)
