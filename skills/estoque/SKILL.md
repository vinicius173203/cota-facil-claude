---
name: estoque
description: Use quando o usuário perguntar pelo saldo do estoque, itens abaixo do mínimo ou da reposição, quiser registrar uma contagem, receber um pedido no estoque, cotar a cesta de reposição ou cadastrar um produto novo no Cota Fácil.
---

# Estoque e cadastro no Cota Fácil

Depende do módulo de estoque e das permissões de estoque do usuário.

## Consultar

- `estoque_saldos`: saldo por produto e local, com mínimo e máximo. `situacao` filtra
  `abaixo_minimo` ou `contagem_pendente`; `busca` filtra pelo nome ou código.
- `estoque_reposicao`: a **cesta** de cada grupo de compra. Os itens abaixo do mínimo se somam e,
  quando a soma atinge o valor mínimo do grupo, a cesta fica pronta para cotar.

## Registrar (sempre em dois passos)

| O quê | Preparar | Confirmar |
|---|---|---|
| Contagem (saldo físico encontrado) | `preparar_contagem` | `confirmar_contagem` |
| Receber um pedido de compra | `preparar_recebimento` | `confirmar_recebimento` |
| Cotar a cesta pronta | `preparar_cotacao_reposicao` | `confirmar_cotacao_reposicao` |
| Cadastrar produto | `preparar_cadastro_produto` | `confirmar_cadastro_produto` |

- **Contagem**: informe o que foi contado de fato (a quantidade encontrada, não a diferença). O resumo
  mostra a diferença para o sistema.
- **Recebimento**: sem `itens`, recebe tudo o que falta do pedido; com `itens`, só o que chegou.
- **Cotar a cesta**: cria a cotação automática e manda aos fornecedores, igual ao botão Cotar do site.
- **Produto**: escolha o subgrupo com `listar_grupos_subgrupos`; informe a unidade e ao menos uma
  referência. O código é gerado pelo sistema. Antes, confira com `buscar_produtos_duplicados` se já
  existe.

Mostre o resumo e só confirme depois do "sim" do usuário, com os mesmos parâmetros e o código.

## Contratos

`contratos_ver` e `negociacoes_contrato` consultam cotações de contrato, contratos e as rodadas de
negociação. Criar e negociar contratos é feito pelo site.
