# Schema SoftwareApplication em JSON-LD: modelo para aplicativo e SaaS

**O schema SoftwareApplication descreve um aplicativo ou software, com nota, valor e sistema operacional abaixo do resultado. O Google exige `name`, `offers.price` (0 para gratuito) e uma avaliação (`aggregateRating` ou `review`), e aceita os subtipos MobileApplication e WebApplication. Sem avaliação real visível, não há resultado enriquecido.**

*Por equipe de SEO da TRIWI, com revisão de Ricardo Martins, fundador. Publicado em 09/11/2026. Atualizado em 09/11/2026. Campos conferidos na documentação do Google Search Central e no schema.org (versão 30.1) em 09/11/2026.*

> **Situação no Google em 09/11/2026: Ativo.** Nota, valor e sistema do aplicativo abaixo do resultado. Aplicativo gratuito usa offers.price igual a 0. VideoGame sozinho não basta: combine com MobileApplication ou outro tipo. Fonte: [documentação oficial do Google](https://developers.google.com/search/docs/appearance/structured-data/software-app).

## Índice

- [Quando usar o schema SoftwareApplication?](#quando-usar-o-schema-softwareapplication)
- [Quais campos o Google exige e recomenda?](#quais-campos-o-google-exige-e-recomenda)
- [Modelo de JSON-LD para copiar](#modelo-de-json-ld-para-copiar)
- [Modelo de SaaS com planos](#modelo-de-saas-com-planos)
- [Como validar o schema SoftwareApplication?](#como-validar-o-schema-softwareapplication)
- [O que o schema SoftwareApplication vale para as IAs?](#o-que-o-schema-softwareapplication-vale-para-as-ias)
- [Perguntas frequentes](#perguntas-frequentes)

## Quando usar o schema SoftwareApplication?

Na página de um aplicativo ou software: página de download, página do produto de um SaaS, ficha de um app. Use o subtipo certo: `MobileApplication` para app de celular e `WebApplication` para software que roda no navegador. Jogo usa `VideoGame` junto com outro tipo, porque `VideoGame` sozinho não gera o resultado.

## Quais campos o Google exige e recomenda?

**Aplicativo de software** (SoftwareApplication; MobileApplication; WebApplication), segundo a [documentação do Google](https://developers.google.com/search/docs/appearance/structured-data/software-app); o tipo no vocabulário está em [schema.org/SoftwareApplication](https://schema.org/SoftwareApplication):

| Exigência | Campos |
|:---|:---|
| Obrigatórios | `aggregateRating` ou `review`; `name`; `offers.price` |
| Recomendados | `applicationCategory`; `operatingSystem` |

Por exigir avaliação, o resultado enriquecido depende de nota real de usuários, visível na página. Sem isso, a marcação continua descrevendo o software, mas não gera estrelas.

## Modelo de JSON-LD para copiar

```json
{
  "@context": "https://schema.org",
  "@type": "MobileApplication",
  "name": "Exemplo Agenda",
  "operatingSystem": "Android, iOS",
  "applicationCategory": "BusinessApplication",
  "offers": {
    "@type": "Offer",
    "price": 0,
    "priceCurrency": "BRL"
  },
  "aggregateRating": {
    "@type": "AggregateRating",
    "ratingValue": 4.6,
    "ratingCount": 870
  }
}
```

Cole dentro de uma tag `<script type="application/ld+json">`. O `applicationCategory` usa os valores do schema.org, como `BusinessApplication`, `FinanceApplication`, `HealthApplication`, `EducationalApplication` e `GameApplication`.

## Modelo de SaaS com planos

Software vendido por assinatura, com mais de um plano. Cada plano é uma oferta; o valor mensal vai em `UnitPriceSpecification`.

```json
{
  "@context": "https://schema.org",
  "@type": "WebApplication",
  "name": "Exemplo Gestão",
  "description": "Software de gestão para clínicas: agenda, prontuário eletrônico e faturamento de convênios.",
  "url": "https://www.exemplo.com.br/software/",
  "applicationCategory": "BusinessApplication",
  "operatingSystem": "Web",
  "publisher": {"@id": "https://www.exemplo.com.br/#organization"},
  "offers": [
    {
      "@type": "Offer",
      "name": "Plano Essencial",
      "price": 199.00,
      "priceCurrency": "BRL",
      "priceSpecification": {
        "@type": "UnitPriceSpecification",
        "price": 199.00,
        "priceCurrency": "BRL",
        "unitCode": "MON"
      }
    },
    {
      "@type": "Offer",
      "name": "Plano Completo",
      "price": 399.00,
      "priceCurrency": "BRL",
      "priceSpecification": {
        "@type": "UnitPriceSpecification",
        "price": 399.00,
        "priceCurrency": "BRL",
        "unitCode": "MON"
      }
    }
  ],
  "aggregateRating": {
    "@type": "AggregateRating",
    "ratingValue": 4.8,
    "reviewCount": 154
  }
}
```

`MON` é o código de mês da tabela UN/CEFACT usada pelo schema.org. Se o valor só é informado sob consulta, não invente: deixe `offers` de fora e saiba que, sem ele, a marcação não atende ao requisito do Google.

## Como validar o schema SoftwareApplication?

1. Antes de publicar, cole o código ou a URL no [Teste de pesquisa aprimorada](https://search.google.com/test/rich-results), do Google: ele diz se a marcação está elegível e aponta erros e avisos.
2. Confira o vocabulário no [Schema Markup Validator](https://validator.schema.org/), do schema.org, que valida também propriedades que o Google não usa.
3. Depois de publicar, acompanhe os [relatórios de resultados aprimorados do Search Console](https://support.google.com/webmasters/answer/7552505?hl=pt-BR) e use a Inspeção de URL para confirmar que o Google encontrou a marcação.

## O que o schema SoftwareApplication vale para as IAs?

Médio: categoria, plataforma e modelo de acesso do software declarados.

Pergunta do tipo "qual software de gestão para clínicas tem agenda e prontuário" é decidida pela comparação de categoria, plataforma, planos e avaliação. A marcação ajuda, mas o que mais pesa para ser citado é o conteúdo comparável e verificável: página de recursos, página de planos, integrações e avaliações em sites independentes. O tema está na página [SEO para SaaS](https://triwi.com.br/seo-para-saas/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=softwareapplication) e no guia aberto [SEO para SaaS](https://github.com/TRIWI-SEO/SEO-IA/blob/main/seo-por-segmento/seo-para-saas-crescimento-organico-para-empresas-de-software.md).

## Perguntas frequentes

<details>
<summary><strong>SaaS B2B sem avaliações públicas deve usar SoftwareApplication?</strong></summary>

Pode, para descrever o software, mas não terá resultado enriquecido enquanto não houver avaliação real visível na página. Uma alternativa é publicar as avaliações de clientes com nome e empresa, com autorização, e marcá-las.
</details>

<details>
<summary><strong>Posso usar a nota da loja de aplicativos?</strong></summary>

A marcação deve refletir avaliações visíveis na página. Copiar a nota de outra plataforma sem mostrar as avaliações contraria as regras de [Review e AggregateRating](../modelos/schema-review-aggregaterating-json-ld.md).
</details>

<details>
<summary><strong>Qual a diferença entre WebApplication e SoftwareApplication?</strong></summary>

`WebApplication` é subtipo de `SoftwareApplication` para software que roda no navegador. Use o subtipo quando ele descreve melhor o produto; o Google aceita os dois.
</details>

**Ver também na Base de Conhecimento da TRIWI:** [Schema Markup e Dados Estruturados para SEO](https://github.com/TRIWI-SEO/SEO-IA/blob/main/seo-tecnico/schema-markup-e-dados-estruturados-para-seo.md), [Dados Estruturados para IA: Schema Markup na Era Generativa](https://github.com/TRIWI-SEO/SEO-IA/blob/main/geo-seo-para-ia/dados-estruturados-para-ia-schema-markup-na-era-generativa.md).

**Na TRIWI:** [Gerador de dados estruturados](https://triwi.com.br/ferramentas/gerador-de-dados-estruturados/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=softwareapplication), [Guia de SEO Técnico, capítulo Dados estruturados](https://triwi.com.br/guias/seo-tecnico/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=softwareapplication#dados-estruturados), [Guia de GEO: Otimização para IAs](https://triwi.com.br/guias/geo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=softwareapplication), [Atualizações do Google](https://triwi.com.br/atualizacoes/google/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=softwareapplication).

**Ver também no Glossário de SEO da TRIWI:** [Dados estruturados](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=softwareapplication#seo-dados-estruturados), [Schema.org](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=softwareapplication#seo-schema-org), [JSON-LD](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=softwareapplication#seo-json-ld), [Rich results](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=softwareapplication#seo-rich-results).

[Voltar para a biblioteca completa](../README.md)

---

<p align="center">
  <strong>Quer que sua marca seja a resposta, no Google e nas IAs?</strong><br>
  <a href="https://triwi.com.br/contato/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=softwareapplication">Que tal um café com a TRIWI?</a>
</p>

<p align="center">
  <sub>Biblioteca publicada e mantida pela equipe da TRIWI, agência 100% especializada em SEO e Otimização para IAs.</sub>
</p>
