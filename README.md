# Simulador de Parcelamento · Solturi Energia Solar

Ferramentas comerciais do time de representantes, construídas em torno da Cessão de Crédito
Santander (CSC). Arquivos independentes, sem servidor e sem dependências além da fonte do Google.

Atualizado em 23/11/2026.

## Arquivos

| Arquivo | Para que serve |
|---|---|
| `index.html` | **Página principal.** Simulador do representante, com tela de acesso. É o que a equipe usa. |
| `simulador.html` | Mesmo simulador, sem tela de acesso, para rodar embutido no painel. |
| `painel.html` | Painel do representante (menu lateral, mural de avisos, links, telefones). Opcional. |
| `schema.sql` | Banco de dados do painel, para rodar no Supabase. Só é necessário se usar o painel. |

Para publicar só o simulador, `index.html` basta.

## Publicar no GitHub Pages

1. Crie um repositório em github.com/new (nome sugerido: `simulador`). Pode ser privado — o Pages
   funciona em contas Free desde 2021.
2. **Add file → Upload files** e envie o `index.html` na raiz. Se for usar o painel, envie também
   `simulador.html` e `painel.html` na mesma pasta.
3. **Settings → Pages** → em *Source* escolha **Deploy from a branch**, branch `main`, pasta
   `/ (root)`. Salve.
4. Em 1 a 3 minutos o link aparece no topo dessa tela:
   `https://SEU-USUARIO.github.io/simulador/`

Para atualizar depois, basta enviar o arquivo novo por cima — o Pages republica em cerca de um minuto.

## Acesso

A página abre pedindo um código. O atual é:

```
Solturi@parcelamento
```

Diferencia maiúsculas de minúsculas. Para trocar, localize no fim do `index.html`:

```js
var ALVO = 'U29sdHVyaUBwYXJjZWxhbWVudG8=';
```

Gere o base64 do novo código e substitua. No console do navegador (F12):

```js
btoa('NovaSenha@123')
```

**Limite dessa proteção:** o código roda no navegador. Ele evita o acesso casual de quem recebe o
link sem autorização, mas não resiste a quem abre o código-fonte da página. Se o repositório for
público, o arquivo também fica visível pelo próprio GitHub. Para bloqueio real, hospede em
Cloudflare Pages com Cloudflare Access (gratuito até 50 usuários, entrada por código enviado por
e-mail).

## As quatro modalidades

**Cessão de crédito** — Tabela CSC Santander. O banco retém um percentual do valor financiado e
repassa o restante. O representante escolhe como a Solturi deve receber: sobre o valor de tabela,
sobre o negociado, ou no mínimo possível (tabela −8%). A entrada é calculada para o líquido fechar
no alvo, e pode ser aumentada — aí o financiado cai e a parcela junto.

**Promoção** — Mesma tabela de retenção, para projetos já com preço promocional. A entrada repõe a
retenção inteira e o líquido fecha sempre no preço da venda.

**Cartão de crédito** — Acréscimo somado ao valor e diluído nas parcelas. Sem entrada. Até 21x.

**Boleto Solturi** — Entrada mínima obrigatória de 30%; abaixo disso a simulação trava. Saldo com
juros simples de 2% ao mês a partir da 6ª parcela. Até 15x.

## Tabela de retenção vigente (CSC Santander)

Prazos de 1x a 24x e o 30x vêm da tabela oficial. **Os prazos de 25x a 29x não constam da tabela do
banco** e estão preenchidos por interpolação linear entre o 24x e o 30x — são estimativas, pendentes
de confirmação com o Santander.

A condição de 30x tem validade informada até **30/11/2026**. Se não for renovada, apagar a linha 30
na tabela do gestor.

## Alterar taxas e regras

O `index.html` carrega as tabelas embutidas no código. Para mudanças de taxa, use a versão de gestor
do simulador (não publicada aqui), ajuste no painel e gere o arquivo novo. O painel do gestor
controla: tabela de retenção por prazo e carência, acréscimo do cartão, juros do boleto, desconto
máximo, entrada mínima do boleto e percentual de comissão.
