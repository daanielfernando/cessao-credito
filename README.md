# Simulador de parcelamento — Solturi

Simulador comercial para uso do time de vendas. Três modalidades: Cessão de crédito Santander,
Promoção e Cartão de crédito. Arquivo único, sem dependências externas.

## Publicar no GitHub Pages

1. Crie um repositório novo em github.com/new. Nome sugerido: `simulador`. Pode ser público ou privado — o Pages funciona nos dois em contas Free desde 2021.
2. Envie o arquivo `index.html` para a raiz do repositório (botão **Add file → Upload files**).
3. Abra **Settings → Pages**.
4. Em **Source**, escolha **Deploy from a branch**; em **Branch**, selecione `main` e a pasta `/ (root)`. Salve.
5. Aguarde de 1 a 3 minutos. O link aparece no topo da própria tela de Pages, no formato:
   `https://SEU-USUARIO.github.io/simulador/`

Esse é o link para compartilhar com a equipe.

## Código de acesso

A página abre pedindo um código. O atual é **solturi2026**.

Para trocar, procure no final do arquivo `index.html` a linha:

```js
var ALVO = 'c29sdHVyaTIwMjY=';
```

Gere o base64 do novo código e substitua o valor entre aspas. No console do navegador (F12):

```js
btoa('novocodigo')
```

Copie o resultado, cole no lugar, salve e envie o arquivo atualizado ao repositório.

## Limite dessa proteção

O código de acesso roda no navegador. Ele impede o acesso casual de quem recebe o link sem
autorização, mas não resiste a quem sabe abrir o código-fonte da página. Se o repositório for
público, o arquivo também fica visível pelo próprio GitHub.

Para bloqueio real, hospede em Cloudflare Pages com Cloudflare Access (gratuito até 50 usuários,
entrada por código enviado por e-mail) ou use a proteção por senha da Netlify ou da Vercel, ambas
em planos pagos. Nesses casos a página só é entregue após a autenticação.

## Atualizar as taxas

Este arquivo não tem painel do gestor. As tabelas de retenção do Santander e de acréscimo do cartão
estão embutidas no código. Para alterá-las, use a versão completa do simulador, ajuste no painel do
gestor e gere um novo arquivo.
