# Schema Organization em JSON-LD: modelo pronto para copiar

**O schema Organization diz ao Google e às IAs quem é a empresa: nome oficial, logo, site, CNPJ, contato e perfis oficiais. Vai na página inicial ou na página Sobre, não precisa estar em todas as páginas, e o Google não exige nenhum campo. Loja online usa o subtipo OnlineStore, com frete e devolução.**

*Por equipe de SEO da TRIWI, com revisão de Ricardo Martins, fundador. Publicado em 09/11/2026. Atualizado em 09/11/2026. Campos conferidos na documentação do Google Search Central e no schema.org (versão 30.1) em 09/11/2026.*

> **Situação no Google em 09/11/2026: Ativo.** Ajuda o Google a escolher o logo e os dados do painel de conhecimento da empresa e a diferenciá-la de outras com nome parecido. Vai na página inicial ou na página Sobre; não precisa estar em todas as páginas. Para loja online, o Google recomenda o subtipo OnlineStore. Fonte: [documentação oficial do Google](https://developers.google.com/search/docs/appearance/structured-data/organization).

## Índice

- [Quando usar o schema Organization?](#quando-usar-o-schema-organization)
- [Quais campos o Google exige e recomenda?](#quais-campos-o-google-exige-e-recomenda)
- [Modelo de JSON-LD para copiar](#modelo-de-json-ld-para-copiar)
- [Modelo completo de Organization](#modelo-completo-de-organization)
- [Modelo de OnlineStore para loja online](#modelo-de-onlinestore-para-loja-online)
- [Modelo de programa de fidelidade](#modelo-de-programa-de-fidelidade)
- [Como validar o schema Organization?](#como-validar-o-schema-organization)
- [O que o schema Organization vale para as IAs?](#o-que-o-schema-organization-vale-para-as-ias)
- [Erros comuns](#erros-comuns)
- [Perguntas frequentes](#perguntas-frequentes)

## Quando usar o schema Organization?

Em todo site de empresa. É a marcação que identifica a entidade por trás do site, e as outras marcações apontam para ela: o `publisher` de um artigo, o `brand` de um produto, o `hiringOrganization` de uma vaga.

| Situação | Tipo indicado |
|:---|:---|
| Empresa sem atendimento presencial: indústria, B2B, SaaS, consultoria | `Organization` |
| Loja online | `OnlineStore` (subtipo recomendado pelo Google para e-commerce) |
| Empresa com endereço que recebe cliente: clínica, loja física, restaurante | Subtipo de `LocalBusiness`, ver [Schema LocalBusiness](../modelos/schema-local-business-json-ld.md) |
| Grupo com várias marcas ou unidades | Uma `Organization` para o grupo, com `subOrganization` ou `parentOrganization` ligando as marcas |

O Google recomenda usar o subtipo mais específico que existir no schema.org.

## Quais campos o Google exige e recomenda?

O Google não exige nenhum campo e pede que você inclua todos os que se aplicam ao negócio.

**Organização** (Organization; OnlineStore), segundo a [documentação do Google](https://developers.google.com/search/docs/appearance/structured-data/organization); o tipo no vocabulário está em [schema.org/Organization](https://schema.org/Organization):

| Exigência | Campos |
|:---|:---|
| Obrigatórios | Nenhum |
| Recomendados | `address`; `alternateName`; `contactPoint`; `description`; `duns`; `email`; `foundingDate`; `globalLocationNumber`; `hasMemberProgram`; `hasMerchantReturnPolicy`; `hasShippingService`; `iso6523Code`; `legalName`; `leiCode`; `logo`; `naics`; `name`; `numberOfEmployees`; `sameAs`; `taxID`; `telephone`; `url`; `vatID` |

**Política de frete** (ShippingService (em Organization.hasShippingService)), segundo a [documentação do Google](https://developers.google.com/search/docs/appearance/structured-data/shipping-policy); o tipo no vocabulário está em [schema.org/ShippingService](https://schema.org/ShippingService):

| Exigência | Campos |
|:---|:---|
| Obrigatórios | `shippingConditions` |
| Recomendados | `description`; `fulfillmentType`; `handlingTime`; `name`; `validForMemberTier` |

**Programa de fidelidade** (MemberProgram; MemberProgramTier), segundo a [documentação do Google](https://developers.google.com/search/docs/appearance/structured-data/loyalty-program); o tipo no vocabulário está em [schema.org/MemberProgram](https://schema.org/MemberProgram):

| Exigência | Campos |
|:---|:---|
| Obrigatórios | `description`; `hasTiers`; `name` |
| Recomendados | `url` |

Três detalhes da documentação que costumam passar despercebidos: o `logo` precisa ter pelo menos 112x112 pixels e uma URL rastreável; o `name` deve ser igual ao nome do site; e o `taxID` precisa corresponder ao país do `address`, o que no Brasil significa o CNPJ.

## Modelo de JSON-LD para copiar

O mínimo que vale a pena publicar. Troque os valores de exemplo pelos da sua empresa e cole dentro de uma tag `<script type="application/ld+json">`, no `<head>` ou no `<body>` da página inicial.

```json
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "@id": "https://www.exemplo.com.br/#organization",
  "name": "Exemplo",
  "url": "https://www.exemplo.com.br/",
  "logo": "https://www.exemplo.com.br/imagens/logo.png",
  "sameAs": [
    "https://www.linkedin.com/company/exemplo",
    "https://www.instagram.com/exemplo"
  ]
}
```

O `@id` é um identificador da entidade dentro do seu site. Ele não aparece para ninguém, mas permite que o artigo, o produto e a vaga apontem para a mesma organização com `"publisher": {"@id": "https://www.exemplo.com.br/#organization"}`, sem repetir os dados.

## Modelo completo de Organization

Com razão social, CNPJ, endereço, contato e data de fundação. Use só os campos que estão corretos e visíveis em algum lugar do site.

```json
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "@id": "https://www.exemplo.com.br/#organization",
  "name": "Exemplo",
  "alternateName": "Exemplo Soluções",
  "legalName": "Exemplo Soluções em Tecnologia Ltda.",
  "url": "https://www.exemplo.com.br/",
  "logo": {
    "@type": "ImageObject",
    "url": "https://www.exemplo.com.br/imagens/logo.png",
    "width": 512,
    "height": 512
  },
  "description": "Empresa brasileira de software de gestão para clínicas, fundada em 2015 em São Paulo.",
  "foundingDate": "2015-03-10",
  "taxID": "00.000.000/0001-00",
  "email": "contato@exemplo.com.br",
  "telephone": "+55-11-0000-0000",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "Avenida Exemplo, 1000, sala 10",
    "addressLocality": "São Paulo",
    "addressRegion": "SP",
    "postalCode": "01000-000",
    "addressCountry": "BR"
  },
  "contactPoint": {
    "@type": "ContactPoint",
    "contactType": "customer service",
    "telephone": "+55-11-0000-0000",
    "email": "atendimento@exemplo.com.br",
    "availableLanguage": "pt-BR"
  },
  "numberOfEmployees": {
    "@type": "QuantitativeValue",
    "minValue": 50,
    "maxValue": 100
  },
  "founder": {
    "@type": "Person",
    "name": "Nome do Fundador",
    "url": "https://www.exemplo.com.br/sobre/nome-do-fundador/"
  },
  "sameAs": [
    "https://www.linkedin.com/company/exemplo",
    "https://www.instagram.com/exemplo",
    "https://www.youtube.com/@exemplo"
  ]
}
```

`founder` não está na lista do Google, mas é propriedade válida do schema.org e ajuda a ligar a empresa às pessoas que a representam. O `numberOfEmployees` aceita número exato ou faixa.

## Modelo de OnlineStore para loja online

Para e-commerce, o Google recomenda `OnlineStore` no lugar de `Organization`, com a política de devolução e a de frete da loja inteira. A política de devolução geral precisa morar aqui, na organização; na oferta de cada produto só cabe um subconjunto dela.

```json
{
  "@context": "https://schema.org",
  "@type": "OnlineStore",
  "@id": "https://www.exemplo.com.br/#organization",
  "name": "Loja Exemplo",
  "url": "https://www.exemplo.com.br/",
  "logo": "https://www.exemplo.com.br/imagens/logo.png",
  "taxID": "00.000.000/0001-00",
  "telephone": "+55-11-0000-0000",
  "sameAs": ["https://www.instagram.com/lojaexemplo"],
  "hasMerchantReturnPolicy": {
    "@type": "MerchantReturnPolicy",
    "applicableCountry": "BR",
    "returnPolicyCountry": "BR",
    "returnPolicyCategory": "https://schema.org/MerchantReturnFiniteReturnWindow",
    "merchantReturnDays": 7,
    "returnMethod": "https://schema.org/ReturnByMail",
    "returnFees": "https://schema.org/FreeReturn"
  },
  "hasShippingService": {
    "@type": "ShippingService",
    "name": "Entrega padrão",
    "shippingConditions": {
      "@type": "ShippingConditions",
      "shippingDestination": {
        "@type": "DefinedRegion",
        "addressCountry": "BR"
      },
      "shippingRate": {
        "@type": "MonetaryAmount",
        "value": 0,
        "currency": "BRL"
      },
      "transitTime": {
        "@type": "ServicePeriod",
        "duration": {
          "@type": "QuantitativeValue",
          "minValue": 2,
          "maxValue": 7,
          "unitCode": "DAY"
        }
      }
    }
  }
}
```

O prazo de 7 dias do exemplo é o direito de arrependimento do Código de Defesa do Consumidor para compras fora da loja física; se a sua loja aceita mais tempo, declare o prazo real. Frete e devolução também podem ser configurados no Search Console, e, havendo as duas coisas, o Google usa a configuração do Search Console. O código de cada produto está em [Schema Product](../modelos/schema-product-json-ld.md).

## Modelo de programa de fidelidade

Loja com clube de vantagens ou programa de pontos declara o programa no `OnlineStore`, com `hasMemberProgram`, e cada nível ganha um `@id` para os produtos apontarem. O recurso de programa de fidelidade do Google está disponível no Brasil, segundo a [documentação](https://developers.google.com/search/docs/appearance/structured-data/loyalty-program).

```json
{
  "@context": "https://schema.org",
  "@type": "OnlineStore",
  "@id": "https://www.exemplo.com.br/#organization",
  "name": "Loja Exemplo",
  "url": "https://www.exemplo.com.br/",
  "hasMemberProgram": {
    "@type": "MemberProgram",
    "name": "Clube Exemplo",
    "description": "Valores exclusivos e pontos em cada compra para quem é do clube.",
    "url": "https://www.exemplo.com.br/clube",
    "hasTiers": [
      {
        "@type": "MemberProgramTier",
        "@id": "https://www.exemplo.com.br/clube#nivel-prata",
        "name": "Prata",
        "hasTierBenefit": "https://schema.org/TierBenefitLoyaltyPoints",
        "membershipPointsEarned": {
          "@type": "QuantitativeValue",
          "value": 1
        }
      },
      {
        "@type": "MemberProgramTier",
        "@id": "https://www.exemplo.com.br/clube#nivel-ouro",
        "name": "Ouro",
        "hasTierBenefit": [
          "https://schema.org/TierBenefitLoyaltyPoints",
          "https://schema.org/TierBenefitLoyaltyPrice"
        ],
        "membershipPointsEarned": {
          "@type": "QuantitativeValue",
          "value": 2
        },
        "hasTierRequirement": {
          "@type": "CreditCard",
          "name": "Cartão Loja Exemplo"
        }
      }
    ]
  }
}
```

`membershipPointsEarned` é quantos pontos o membro ganha por unidade de moeda gasta. Sem `hasTierRequirement`, o nível é aberto a qualquer pessoa, sem custo; no exemplo, o nível Ouro exige o cartão de crédito da loja. A documentação aceita como requisito também uma mensalidade (`UnitPriceSpecification`), um valor (`MonetaryAmount`) ou um texto. O valor de membro em cada produto está em [Schema Product](../modelos/schema-product-json-ld.md#modelo-de-valor-para-membro-do-programa-de-fidelidade).

## Como validar o schema Organization?

1. Antes de publicar, cole o código ou a URL no [Teste de pesquisa aprimorada](https://search.google.com/test/rich-results), do Google: ele diz se a marcação está elegível e aponta erros e avisos.
2. Confira o vocabulário no [Schema Markup Validator](https://validator.schema.org/), do schema.org, que valida também propriedades que o Google não usa.
3. Depois de publicar, acompanhe os [relatórios de resultados aprimorados do Search Console](https://support.google.com/webmasters/answer/7552505?hl=pt-BR) e use a Inspeção de URL para confirmar que o Google encontrou a marcação.

O [Gerador de dados estruturados da TRIWI](https://triwi.com.br/ferramentas/gerador-de-dados-estruturados/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=organization) monta o Organization preenchendo um formulário, sem escrever código.

## O que o schema Organization vale para as IAs?

Alto: declara quem é a empresa, com nome, logo, CNPJ e perfis oficiais, a base para a IA não confundir a marca com outra.

O Google diz, no [guia de otimização para IA da Pesquisa](https://developers.google.com/search/docs/fundamentals/ai-optimization-guide?hl=pt-br), que dados estruturados não são exigidos para os recursos de IA e que vale continuar usando como parte do SEO. As empresas de IA não publicam como usam JSON-LD. A leitura da TRIWI: o Organization não faz a marca aparecer sozinho, mas tira a ambiguidade. Quando o nome, o CNPJ, o logo e os perfis em `sameAs` batem com o que está no site, no LinkedIn e no Perfil da Empresa no Google, fica mais fácil para qualquer sistema reconhecer que tudo aquilo é a mesma empresa. O tema está no [Guia de GEO: Otimização para IAs](https://triwi.com.br/guias/geo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=organization).

## Erros comuns

| Erro | Correção |
|:---|:---|
| Organization em todas as páginas com dados diferentes | Uma marcação completa na página inicial ou na Sobre; nas outras, só a referência por `@id` |
| `sameAs` apontando para perfis abandonados ou de terceiros | Só perfis oficiais e ativos da própria empresa |
| `name` diferente do nome usado no site e no `WebSite` | O mesmo nome nos três lugares; a variação vai em `alternateName` |
| Logo em SVG muito pequeno ou atrás de login | Imagem rastreável de pelo menos 112x112 pixels |
| `aggregateRating` da própria empresa na própria página | O Google não mostra estrelas de empresa avaliando a si mesma; ver [Schema Review e AggregateRating](../modelos/schema-review-aggregaterating-json-ld.md) |

## Perguntas frequentes

<details>
<summary><strong>O schema Organization faz aparecer o painel de conhecimento?</strong></summary>

Não garante. O Google diz que a marcação ajuda a entender e a diferenciar a organização e pode definir qual logo aparece nos resultados e no painel de conhecimento, mas o painel depende de outros sinais sobre a empresa na web.
</details>

<details>
<summary><strong>Qual a diferença entre Organization e LocalBusiness?</strong></summary>

`LocalBusiness` é um subtipo de `Organization` para empresas com endereço físico que atendem clientes no local. Uma clínica usa um subtipo de `LocalBusiness`; uma empresa de software que só atende online usa `Organization`. Uma rede pode usar os dois: `Organization` para a marca e `LocalBusiness` em cada página de unidade.
</details>

<details>
<summary><strong>Posso colocar o CNPJ no schema?</strong></summary>

Sim, em `taxID`. A documentação do Google lista o campo como recomendado e pede que ele corresponda ao país do endereço. Por ser dado público da empresa, ajuda a diferenciar marcas com nome parecido.
</details>

<details>
<summary><strong>Preciso de Organization se já tenho o Perfil da Empresa no Google?</strong></summary>

São coisas diferentes. O Perfil da Empresa é cadastro na plataforma do Google; o Organization é declaração no seu próprio site, que qualquer buscador ou IA pode ler. O ideal é que os dois tragam exatamente os mesmos dados.
</details>

**Ver também na Base de Conhecimento da TRIWI:** [Schema Markup e Dados Estruturados para SEO](https://github.com/TRIWI-SEO/SEO-IA/blob/main/seo-tecnico/schema-markup-e-dados-estruturados-para-seo.md), [Dados Estruturados para IA: Schema Markup na Era Generativa](https://github.com/TRIWI-SEO/SEO-IA/blob/main/geo-seo-para-ia/dados-estruturados-para-ia-schema-markup-na-era-generativa.md).

**Na TRIWI:** [Gerador de dados estruturados](https://triwi.com.br/ferramentas/gerador-de-dados-estruturados/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=organization), [Guia de SEO Técnico, capítulo Dados estruturados](https://triwi.com.br/guias/seo-tecnico/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=organization#dados-estruturados), [Guia de GEO: Otimização para IAs](https://triwi.com.br/guias/geo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=organization), [Atualizações do Google](https://triwi.com.br/atualizacoes/google/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=organization).

**Ver também no Glossário de SEO da TRIWI:** [Dados estruturados](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=organization#seo-dados-estruturados), [Schema.org](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=organization#seo-schema-org), [JSON-LD](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=organization#seo-json-ld), [Entidade](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=organization#seo-entidade), [Knowledge Graph](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=organization#seo-knowledge-graph).

[Voltar para a biblioteca completa](../README.md)

---

<p align="center">
  <strong>Quer que sua marca seja a resposta, no Google e nas IAs?</strong><br>
  <a href="https://triwi.com.br/contato/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=organization">Que tal um café com a TRIWI?</a>
</p>

<p align="center">
  <sub>Biblioteca publicada e mantida pela equipe da TRIWI, agência 100% especializada em SEO e Otimização para IAs.</sub>
</p>
