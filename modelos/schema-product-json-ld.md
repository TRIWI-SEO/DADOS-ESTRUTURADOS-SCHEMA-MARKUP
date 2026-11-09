# Schema Product em JSON-LD: modelo pronto para copiar

**O schema Product descreve um produto: nome, imagem, valor, disponibilidade, avaliação, frete e devolução. O Google separa dois usos: a listagem do comerciante, para páginas onde o produto é vendido, que exige `name`, `image` e `offers` com valor e moeda; e o trecho de produto, para análises e comparadores.**

*Por equipe de SEO da TRIWI, com revisão de Ricardo Martins, fundador. Publicado em 09/11/2026. Atualizado em 09/11/2026. Campos conferidos na documentação do Google Search Central e no schema.org (versão 30.1) em 09/11/2026.*

> **Situação no Google em 09/11/2026: Ativo.** Valor, frete, devolução e disponibilidade em resultados de compra, painéis de produto e Google Imagens. Última mudança registrada: 07/07/2026. Para páginas em que o produto pode ser comprado. A marcação deve estar no HTML inicial; gerada por JavaScript, deixa o rastreamento de compras menos frequente. Fonte: [documentação oficial do Google](https://developers.google.com/search/docs/appearance/structured-data/merchant-listing).

## Índice

- [Quando usar o schema Product?](#quando-usar-o-schema-product)
- [Quais campos o Google exige e recomenda?](#quais-campos-o-google-exige-e-recomenda)
- [Modelo de JSON-LD para copiar](#modelo-de-json-ld-para-copiar)
- [Modelo completo com frete e devolução](#modelo-completo-com-frete-e-devolução)
- [Modelo de produto com variantes](#modelo-de-produto-com-variantes)
- [Modelo para página de análise de produto](#modelo-para-página-de-análise-de-produto)
- [Como validar o schema Product?](#como-validar-o-schema-product)
- [O que o schema Product vale para as IAs?](#o-que-o-schema-product-vale-para-as-ias)
- [Erros comuns](#erros-comuns)
- [Perguntas frequentes](#perguntas-frequentes)

## Quando usar o schema Product?

| Página | Marcação | Recurso no Google |
|:---|:---|:---|
| Página de produto de loja, onde dá para comprar | `Product` com `offers` | Listagem do comerciante |
| Produto com cores, tamanhos ou voltagens | `ProductGroup` com as variantes | Variantes de produto |
| Análise, comparativo ou página de afiliado que não vende | `Product` com `review` ou `aggregateRating` | Trecho de produto |
| Página de categoria com vários produtos | Nenhuma marcação de Product na categoria | Não se aplica |

A marcação vale para páginas focadas em um produto ou em variantes do mesmo produto. Se cada variante tem URL própria, cada URL ganha a sua marcação.

## Quais campos o Google exige e recomenda?

**Produto (listagem do comerciante)** (Product; Offer), segundo a [documentação do Google](https://developers.google.com/search/docs/appearance/structured-data/merchant-listing):

| Exigência | Campos |
|:---|:---|
| Obrigatórios | `name`; `image`; `offers`; `offers.price` ou `offers.priceSpecification.price`; `offers.priceCurrency` |
| Recomendados | `aggregateRating`; `audience`; `brand.name`; `category`; `color`; `description`; `gtin`; `hasAdultConsideration`; `hasCertification`; `inProductGroupWithID`; `isVariantOf`; `material`; `mpn`; `offers.availability`; `offers.hasMerchantReturnPolicy`; `offers.itemCondition`; `offers.priceValidUntil`; `offers.shippingDetails`; `offers.url`; `offers.validFrom`; `offers.validThrough`; `pattern`; `review`; `size`; `sku`; `subjectOf` |

**Produto (trecho de produto)** (Product; Offer; AggregateRating; Review), segundo a [documentação do Google](https://developers.google.com/search/docs/appearance/structured-data/product-snippet):

| Exigência | Campos |
|:---|:---|
| Obrigatórios | `name`; `review`, `aggregateRating` ou `offers` (um deles); `offers.price` ou `offers.priceSpecification.price` |
| Recomendados | `aggregateRating`; `offers`; `offers.availability`; `offers.priceCurrency`; `offers.priceValidUntil`; `review` |

**Variantes de produto** (ProductGroup; Product), segundo a [documentação do Google](https://developers.google.com/search/docs/appearance/structured-data/product-variants):

| Exigência | Campos |
|:---|:---|
| Obrigatórios | `name` (no ProductGroup); identificador único em cada variante (`sku` ou `gtin`); vínculo da variante ao grupo (`productGroupID`, `inProductGroupWithID` ou `isVariantOf`) |
| Recomendados | `aggregateRating`; `brand`; `description`; `hasAdultConsideration`; `hasVariant`; `productGroupID`; `review`; `url`; `variesBy` |

**Política de devolução** (MerchantReturnPolicy), segundo a [documentação do Google](https://developers.google.com/search/docs/appearance/structured-data/return-policy):

| Exigência | Campos |
|:---|:---|
| Obrigatórios | `applicableCountry` e `returnPolicyCategory` (com `merchantReturnDays` na janela finita), ou `merchantReturnLink` |
| Recomendados | `customerRemorseReturnFees`; `itemCondition`; `itemDefectReturnFees`; `merchantReturnDays`; `refundType`; `restockingFee`; `returnFees`; `returnLabelSource`; `returnMethod`; `returnPolicyCountry`; `returnShippingFeesAmount` |

Na listagem do comerciante, os detalhes de frete (`OfferShippingDetails`) exigem `deliveryTime`, `shippingDestination` e `shippingRate` com moeda e valor. O `gtin` vai só em números, nunca no formato de URL.

## Modelo de JSON-LD para copiar

O mínimo para uma página de produto de loja. Cole dentro de uma tag `<script type="application/ld+json">` no HTML que o servidor entrega, não injetado depois por JavaScript: a documentação diz que marcação gerada por JavaScript deixa o rastreamento de compras menos frequente e menos confiável.

```json
{
  "@context": "https://schema.org",
  "@type": "Product",
  "name": "Cadeira de Escritório Exemplo Ergo",
  "image": [
    "https://www.exemplo.com.br/imagens/cadeira-ergo-1x1.jpg",
    "https://www.exemplo.com.br/imagens/cadeira-ergo-4x3.jpg",
    "https://www.exemplo.com.br/imagens/cadeira-ergo-16x9.jpg"
  ],
  "offers": {
    "@type": "Offer",
    "url": "https://www.exemplo.com.br/cadeira-ergo",
    "price": 1299.90,
    "priceCurrency": "BRL",
    "availability": "https://schema.org/InStock",
    "itemCondition": "https://schema.org/NewCondition"
  }
}
```

O valor vai com ponto como separador decimal e sem símbolo de moeda; a moeda vai em `priceCurrency`, no código ISO (`BRL`). O valor da marcação precisa ser o mesmo mostrado na página.

## Modelo completo com frete e devolução

```json
{
  "@context": "https://schema.org",
  "@type": "Product",
  "name": "Cadeira de Escritório Exemplo Ergo",
  "description": "Cadeira ergonômica com apoio lombar ajustável, braços 3D e encosto em tela.",
  "image": [
    "https://www.exemplo.com.br/imagens/cadeira-ergo-1x1.jpg",
    "https://www.exemplo.com.br/imagens/cadeira-ergo-4x3.jpg",
    "https://www.exemplo.com.br/imagens/cadeira-ergo-16x9.jpg"
  ],
  "sku": "ERGO-PRETA",
  "gtin13": "7890000000000",
  "mpn": "EX-ERGO-01",
  "brand": {
    "@type": "Brand",
    "name": "Exemplo"
  },
  "color": "Preta",
  "material": "Tela e nylon",
  "category": "Móveis > Móveis de escritório > Cadeiras",
  "aggregateRating": {
    "@type": "AggregateRating",
    "ratingValue": 4.6,
    "reviewCount": 128,
    "bestRating": 5,
    "worstRating": 1
  },
  "offers": {
    "@type": "Offer",
    "url": "https://www.exemplo.com.br/cadeira-ergo",
    "price": 1299.90,
    "priceCurrency": "BRL",
    "priceValidUntil": "2026-12-31",
    "availability": "https://schema.org/InStock",
    "itemCondition": "https://schema.org/NewCondition",
    "seller": {
      "@id": "https://www.exemplo.com.br/#organization"
    },
    "shippingDetails": {
      "@type": "OfferShippingDetails",
      "shippingDestination": {
        "@type": "DefinedRegion",
        "addressCountry": "BR"
      },
      "shippingRate": {
        "@type": "MonetaryAmount",
        "value": 0,
        "currency": "BRL"
      },
      "deliveryTime": {
        "@type": "ShippingDeliveryTime",
        "handlingTime": {
          "@type": "QuantitativeValue",
          "minValue": 0,
          "maxValue": 1,
          "unitCode": "DAY"
        },
        "transitTime": {
          "@type": "QuantitativeValue",
          "minValue": 2,
          "maxValue": 7,
          "unitCode": "DAY"
        }
      }
    },
    "hasMerchantReturnPolicy": {
      "@type": "MerchantReturnPolicy",
      "applicableCountry": "BR",
      "returnPolicyCategory": "https://schema.org/MerchantReturnFiniteReturnWindow",
      "merchantReturnDays": 7,
      "returnMethod": "https://schema.org/ReturnByMail",
      "returnFees": "https://schema.org/FreeReturn"
    }
  }
}
```

A nota de 4,6 com 128 avaliações só pode entrar se as avaliações estiverem visíveis na página e forem de clientes reais; as regras estão em [Schema Review e AggregateRating](../modelos/schema-review-aggregaterating-json-ld.md). Quando a política de frete e a de devolução valem para a loja inteira, declare uma vez no `OnlineStore` da página inicial, como em [Schema Organization](../modelos/schema-organization-json-ld.md#modelo-de-onlinestore-para-loja-online), e use a da oferta só para exceções: a da oferta tem precedência sobre a da organização. Promoção com prazo usa `priceValidUntil`, ou `validFrom` e `validThrough`, para o Google saber quando o valor deixa de valer.

## Modelo de produto com variantes

Para um produto em várias cores ou tamanhos, o `ProductGroup` reúne as variantes. Cada variante tem identificador próprio (`sku` ou `gtin`) e os campos obrigatórios de produto.

```json
{
  "@context": "https://schema.org",
  "@type": "ProductGroup",
  "name": "Camiseta Básica Exemplo",
  "description": "Camiseta de algodão com modelagem reta.",
  "brand": {
    "@type": "Brand",
    "name": "Exemplo"
  },
  "productGroupID": "CAM-BASICA",
  "variesBy": [
    "https://schema.org/color",
    "https://schema.org/size"
  ],
  "hasVariant": [
    {
      "@type": "Product",
      "sku": "CAM-BASICA-BRANCA-M",
      "name": "Camiseta Básica Exemplo Branca M",
      "color": "Branca",
      "size": "M",
      "image": "https://www.exemplo.com.br/imagens/camiseta-branca.jpg",
      "offers": {
        "@type": "Offer",
        "url": "https://www.exemplo.com.br/camiseta-basica?cor=branca&tamanho=m",
        "price": 79.90,
        "priceCurrency": "BRL",
        "availability": "https://schema.org/InStock"
      }
    },
    {
      "@type": "Product",
      "sku": "CAM-BASICA-PRETA-G",
      "name": "Camiseta Básica Exemplo Preta G",
      "color": "Preta",
      "size": "G",
      "image": "https://www.exemplo.com.br/imagens/camiseta-preta.jpg",
      "offers": {
        "@type": "Offer",
        "url": "https://www.exemplo.com.br/camiseta-basica?cor=preta&tamanho=g",
        "price": 79.90,
        "priceCurrency": "BRL",
        "availability": "https://schema.org/OutOfStock"
      }
    }
  ]
}
```

O `variesBy` usa a URL completa da propriedade no schema.org. Não use `AggregateOffer` para descrever variantes: a documentação reserva esse tipo para várias ofertas do mesmo produto.

## Modelo para página de análise de produto

Para quem analisa ou compara produtos sem vendê-los. Prós e contras (`positiveNotes` e `negativeNotes`) valem só em análise editorial, com pelo menos duas afirmações, e o português está entre os idiomas aceitos.

```json
{
  "@context": "https://schema.org",
  "@type": "Product",
  "name": "Cadeira de Escritório Exemplo Ergo",
  "review": {
    "@type": "Review",
    "name": "Análise da Cadeira Exemplo Ergo",
    "author": {
      "@type": "Person",
      "name": "Nome do Autor",
      "url": "https://www.exemplo.com.br/autores/nome-do-autor/"
    },
    "datePublished": "2026-11-09",
    "reviewRating": {
      "@type": "Rating",
      "ratingValue": 4,
      "bestRating": 5
    },
    "positiveNotes": {
      "@type": "ItemList",
      "itemListElement": [
        {"@type": "ListItem", "position": 1, "name": "Apoio lombar ajustável em altura"},
        {"@type": "ListItem", "position": 2, "name": "Encosto em tela que não esquenta"}
      ]
    },
    "negativeNotes": {
      "@type": "ItemList",
      "itemListElement": [
        {"@type": "ListItem", "position": 1, "name": "Montagem demorada"}
      ]
    }
  }
}
```

## Como validar o schema Product?

1. Antes de publicar, cole o código ou a URL no [Teste de pesquisa aprimorada](https://search.google.com/test/rich-results), do Google: ele diz se a marcação está elegível e aponta erros e avisos.
2. Confira o vocabulário no [Schema Markup Validator](https://validator.schema.org/), do schema.org, que valida também propriedades que o Google não usa.
3. Depois de publicar, acompanhe os [relatórios de resultados aprimorados do Search Console](https://support.google.com/webmasters/answer/7552505?hl=pt-BR) e use a Inspeção de URL para confirmar que o Google encontrou a marcação.

Os dois relatórios do Search Console são separados: Listagens do comerciante e Trechos de produto. Quem também envia feed ao Google Merchant Center pode conferir se o feed e a página dizem a mesma coisa com o [Revisor de feed de produtos da TRIWI](https://triwi.com.br/ferramentas/revisor-de-feed-de-produtos/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=product).

## O que o schema Product vale para as IAs?

Alto: é a ficha do produto que agentes de compra e assistentes leem para comparar ofertas.

Quando alguém pergunta a um assistente qual cadeira comprar, ou pede para comparar lojas, a resposta depende de dados de produto fáceis de ler: valor, moeda, estoque, frete, prazo, devolução, marca e GTIN. A marcação entrega isso sem que o sistema precise adivinhar a partir do layout. O Google diz que dados estruturados não são exigidos para os recursos de IA da Pesquisa; a leitura da TRIWI é que, em e-commerce, a ficha estruturada do produto é a parte do trabalho que mais se aproveita fora do Google. O tema está no guia aberto [GEO para E-commerce](https://github.com/TRIWI-SEO/SEO-IA/blob/main/geo-seo-para-ia/geo-para-e-commerce-otimizacao-de-produtos-para-ias-generativas.md) e na página [SEO para E-commerce](https://triwi.com.br/seo-para-ecommerce/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=product).

## Erros comuns

| Erro | Correção |
|:---|:---|
| Valor da marcação diferente do valor na página | A marcação sai da mesma fonte de dados da página; promoção muda os dois ao mesmo tempo |
| `price` com vírgula ou símbolo de moeda | Número com ponto decimal e `priceCurrency` separado |
| Produto esgotado marcado como `InStock` | `OutOfStock` ou `BackOrder`, conforme o caso |
| Marcação de Product em página de categoria | Product só em página de um produto ou das variantes dele |
| Marcação injetada por JavaScript depois do carregamento | Product no HTML inicial, como recomenda o Google |
| Nota inventada ou copiada de outro site | Só avaliações reais, visíveis na página |

## Perguntas frequentes

<details>
<summary><strong>Qual a diferença entre trecho de produto e listagem do comerciante?</strong></summary>

A listagem do comerciante é para páginas em que o produto pode ser comprado e exige `offers`, porque o site precisa ser o vendedor. O trecho de produto é para páginas que falam do produto sem vendê-lo, como análises e comparadores, e aceita só `review` ou `aggregateRating`.
</details>

<details>
<summary><strong>O Merchant Center substitui o schema Product?</strong></summary>

Não. O feed do Merchant Center alimenta os anúncios e as listagens gratuitas; a marcação descreve o produto na própria página. O Google usa os dois, e eles devem trazer os mesmos dados.
</details>

<details>
<summary><strong>Preciso marcar o frete em cada produto?</strong></summary>

Não, se a regra vale para a loja inteira. A política de frete e a de devolução podem ir uma vez no `OnlineStore` ou ser configuradas no Search Console; a marcação no produto fica para as exceções.
</details>

<details>
<summary><strong>Plataformas como VTEX, Shopify e Nuvemshop já geram o schema Product?</strong></summary>

Geram uma marcação básica, que costuma precisar de ajuste: faltam campos de frete, devolução, GTIN ou variantes, ou a marcação diverge da página. Vale passar uma página de cada tipo no Teste de pesquisa aprimorada. As particularidades de cada plataforma estão nas páginas [SEO para VTEX](https://triwi.com.br/seo-para-ecommerce/vtex/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=product), [SEO para Shopify](https://triwi.com.br/seo-para-ecommerce/shopify/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=product) e [SEO para Nuvemshop](https://triwi.com.br/seo-para-ecommerce/nuvemshop/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=product).
</details>

**Ver também na Base de Conhecimento da TRIWI:** [Schema Markup e Dados Estruturados para SEO](https://github.com/TRIWI-SEO/SEO-IA/blob/main/seo-tecnico/schema-markup-e-dados-estruturados-para-seo.md), [Dados Estruturados para IA: Schema Markup na Era Generativa](https://github.com/TRIWI-SEO/SEO-IA/blob/main/geo-seo-para-ia/dados-estruturados-para-ia-schema-markup-na-era-generativa.md).

**Na TRIWI:** [Gerador de dados estruturados](https://triwi.com.br/ferramentas/gerador-de-dados-estruturados/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=product), [Guia de SEO Técnico, capítulo Dados estruturados](https://triwi.com.br/guias/seo-tecnico/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=product#dados-estruturados), [Guia de GEO: Otimização para IAs](https://triwi.com.br/guias/geo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=product), [Atualizações do Google](https://triwi.com.br/atualizacoes/google/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=product).

**Ver também no Glossário de SEO da TRIWI:** [Dados estruturados](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=product#seo-dados-estruturados), [Schema.org](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=product#seo-schema-org), [JSON-LD](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=product#seo-json-ld), [Rich results](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=product#seo-rich-results).

[Voltar para a biblioteca completa](../README.md)

---

<p align="center">
  <strong>Quer que sua marca seja a resposta, no Google e nas IAs?</strong><br>
  <a href="https://triwi.com.br/contato/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=product">Que tal um café com a TRIWI?</a>
</p>

<p align="center">
  <sub>Biblioteca publicada e mantida pela equipe da TRIWI, agência 100% especializada em SEO e Otimização para IAs.</sub>
</p>
