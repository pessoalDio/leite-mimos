# Leite mimos — site

Site institucional simples (sem carrinho, sem checkout) para apresentar os
produtos personalizados da Leite mimos e direcionar cada pedido para o
WhatsApp da loja.

É um site 100% estático: `index.html`, `css/style.css`, `js/script.js`.
Não precisa de servidor, banco de dados nem build — funciona direto no
GitHub Pages, Vercel, Netlify etc.

## 1. Antes de publicar — o que trocar

### Número de WhatsApp (obrigatório)
Abra `js/script.js` e troque a primeira constante pelo número real da loja,
só com dígitos, com código do país e DDD:

```js
const WHATSAPP_NUMBER = "5592900000000"; // <- troque aqui
```

### Fotos dos produtos
O site está usando ilustrações de linha como "foto provisória" de cada
produto, para já sair bonito e funcional. Quando o cliente enviar fotos
reais, o ideal é:

1. Colocar as fotos em `images/` (ex.: `images/garrafa-termica.jpg`).
2. Em `js/script.js`, no array `PRODUCTS`, trocar a exibição do ícone por
   uma tag `<img>` apontando para o arquivo — ou pedir para eu fazer essa
   troca quando tiver as fotos em mãos.

Fotos verticais (proporção 4:5), com fundo neutro e boa luz natural,
combinam melhor com os cards já estilizados.

### Catálogo de produtos
Também em `js/script.js`, edite o array `PRODUCTS` para adicionar, remover
ou alterar produtos (nome, categoria, descrição, preço, se é "queridinho"):

```js
{ id: "garrafa-termica", name: "Garrafa Térmica Personalizada",
  category: "garrafas", desc: "500ml, nome ou frase gravada",
  price: 59.90, favorite: true },
```

A mensagem do WhatsApp é gerada automaticamente a partir do `name` e do
`price` — não precisa escrever a mensagem à mão para cada produto.

### Redes sociais e e-mail
No rodapé de `index.html` (seção `<footer>`), troque o link do Instagram e
o e-mail de contato pelos reais do cliente.

## 2. Publicar no GitHub

```bash
cd leite-mimos
git init
git add .
git commit -m "Site Leite mimos"
git branch -M main
git remote add origin https://github.com/SEU-USUARIO/leite-mimos.git
git push -u origin main
```

## 3. Publicar na Vercel

1. Acesse [vercel.com](https://vercel.com) e faça login (pode usar a conta
   do GitHub).
2. Clique em **Add New → Project**.
3. Selecione o repositório `leite-mimos` que você acabou de subir.
4. Em **Framework Preset**, deixe como **Other** (é um site estático, sem
   build). Não é necessário configurar build command nem output directory.
5. Clique em **Deploy**.
6. Depois do deploy, em **Settings → Domains**, adicione o domínio próprio
   do cliente (ex. `leitemimos.com.br`) e siga as instruções de DNS que a
   Vercel mostrar (geralmente um registro `CNAME` ou `A`).

Qualquer novo `git push` na branch `main` atualiza o site automaticamente.

## 4. Estrutura de arquivos

```
leite-mimos/
├── index.html          → estrutura e conteúdo do site
├── css/style.css        → todo o estilo visual
├── js/script.js         → catálogo de produtos, filtros e links de WhatsApp
├── images/               → pasta reservada para as fotos reais dos produtos
└── README.md            → este guia
```
