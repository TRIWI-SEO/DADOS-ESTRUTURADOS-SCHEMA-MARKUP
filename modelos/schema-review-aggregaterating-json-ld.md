# Schema Review e AggregateRating em JSON-LD: modelo pronto para copiar

**Review marca uma avaliação e AggregateRating marca a nota média, que podem gerar estrelas abaixo do resultado. A avaliação exige `author`, `reviewRating` e o item avaliado; a nota média exige `ratingValue` e `ratingCount` ou `reviewCount`. Empresa avaliando a si mesma não ganha estrelas, e avaliação falsa ou incentivada sem aviso é proibida.**

*Por equipe de SEO da TRIWI, com revisão de Ricardo Martins, fundador. Publicado em 09/11/2026. Atualizado em 09/11/2026. Campos conferidos na documentação do Google Search Central e no schema.org (versão 30.1) em 09/11/2026.*

> **Situação no Google em 09/11/2026: Ativo.** Estrelas e nota abaixo do resultado. Última mudança registrada: 24/07/2026. Empresa avaliando a si mesma (LocalBusiness ou Organization) não tem estrelas, nem com widget de terceiros. Avaliação falsa ou incentivada sem aviso claro é proibida (regra incluída em 24/07/2026). Fonte: [documentação oficial do Google](https://developers.google.com/search/docs/appearance/structured-data/review-snippet).

## Índice

- [Quando usar Review e AggregateRating?](#quando-usar-review-e-aggregaterating)
- [Quais campos o Google exige e recomenda?](#quais-campos-o-google-exige-e-recomenda)
- [Modelo de AggregateRating para copiar](#modelo-de-aggregaterating-para-copiar)
- [Modelo de Review com avaliações individuais](#modelo-de-review-com-avaliações-individuais)
- [Quais avaliações não podem ser marcadas?](#quais-avaliações-não-podem-ser-marcadas)
- [Como validar Review e AggregateRating?](#como-validar-review-e-aggregaterating)
- [O que as avaliações marcadas valem para as IAs?](#o-que-as-avaliações-marcadas-valem-para-as-ias)
- [Perguntas frequentes](#perguntas-frequentes)

## Quando usar Review e AggregateRating?

Quando a página mostra avaliações de usuários ou uma análise editorial sobre um destes tipos aceitos pelo Google: `Book`, `Course`, `CreativeWorkSeason`, `CreativeWorkSeries`, `Episode`, `Event`, `Game`, `HowTo`, `LocalBusiness`, `MediaObject`, `Movie`, `MusicPlaylist`, `MusicRecording`, `Organization`, `Product`, `Recipe` e `SoftwareApplication`.

Na prática, os casos mais comuns são produto em loja online, curso, aplicativo e receita. Serviço B2B, por exemplo, não está na lista.

## Quais campos o Google exige e recomenda?

**Trecho de avaliação** (Review; AggregateRating), segundo a [documentação do Google](https://developers.google.com/search/docs/appearance/structured-data/review-snippet); o tipo no vocabulário está em [schema.org/Review](https://schema.org/Review):

| Exigência | Campos |
|:---|:---|
| Obrigatórios | **Review:** `author`; `itemReviewed` (fora de aninhamento); `itemReviewed.name`; `reviewRating`; `reviewRating.ratingValue`<br>**AggregateRating:** `itemReviewed` (fora de aninhamento); `itemReviewed.name`; `ratingValue`; `ratingCount` ou `reviewCount` |
| Recomendados | `bestRating`; `datePublished`; `reviewRating.bestRating`; `reviewRating.worstRating`; `worstRating` |

Quando a avaliação ou a nota vem dentro do item avaliado, como no modelo abaixo, o `itemReviewed` não precisa ser repetido. Notas decimais usam ponto (`4.6`), e a escala padrão é de 1 a 5; se a sua for outra, declare `bestRating` e `worstRating`.

## Modelo de AggregateRating para copiar

A nota média de um curso, aninhada no próprio curso.

```json
{
  "@context": "https://schema.org",
  "@type": "Course",
  "name": "Curso de Excel para Finanças",
  "description": "Do básico às tabelas dinâmicas aplicadas a fluxo de caixa.",
  "provider": {
    "@type": "Organization",
    "name": "Escola Exemplo",
    "url": "https://www.exemplo.com.br/"
  },
  "aggregateRating": {
    "@type": "AggregateRating",
    "ratingValue": 4.7,
    "ratingCount": 312,
    "bestRating": 5,
    "worstRating": 1
  }
}
```

## Modelo de Review com avaliações individuais

Duas avaliações de clientes de um produto, com autor e data. As mesmas avaliações precisam estar visíveis na página.

```json
{
  "@context": "https://schema.org",
  "@type": "Product",
  "name": "Cafeteira Exemplo Prima",
  "image": "https://www.exemplo.com.br/imagens/cafeteira-prima.jpg",
  "review": [
    {
      "@type": "Review",
      "author": {"@type": "Person", "name": "Mariana S."},
      "datePublished": "2026-10-02",
      "reviewBody": "Faz o café rápido e é fácil de limpar. A jarra poderia ser maior.",
      "reviewRating": {"@type": "Rating", "ratingValue": 4, "bestRating": 5, "worstRating": 1}
    },
    {
      "@type": "Review",
      "author": {"@type": "Person", "name": "Carlos P."},
      "datePublished": "2026-09-18",
      "reviewBody": "Uso todo dia há um mês, sem nenhum problema.",
      "reviewRating": {"@type": "Rating", "ratingValue": 5, "bestRating": 5, "worstRating": 1}
    }
  ],
  "aggregateRating": {
    "@type": "AggregateRating",
    "ratingValue": 4.5,
    "reviewCount": 2
  }
}
```

O nome do autor precisa ser de uma pessoa ou de uma equipe; texto como "Cliente satisfeito" ou uma frase promocional não vale. A documentação também recomenda aceitar só avaliações que tenham comentário e nome do autor.

## Quais avaliações não podem ser marcadas?

| Caso | Por quê |
|:---|:---|
| A empresa marcando as próprias avaliações em `LocalBusiness` ou `Organization` | A documentação chama de avaliação em causa própria e tira a elegibilidade, inclusive quando as avaliações vêm de um widget de terceiros |
| Avaliações que não aparecem na página | Toda marcação precisa refletir conteúdo visível |
| Avaliação falsa, sem experiência real ou escrita em troca de benefício sem aviso claro | Regra incluída nas diretrizes do Google em 24/07/2026 |
| Nota agregada de outro site copiada para o seu | A nota precisa ser das avaliações coletadas e mostradas na página |
| Mais de uma forma de indicar o item avaliado na mesma marcação | A documentação pede uma forma só (orientação de 12/11/2025) |

Sites que avaliam outras empresas, como guias de restaurantes, podem marcar avaliações de `LocalBusiness`: a restrição vale para quem avalia a si mesmo.

## Como validar Review e AggregateRating?

1. Antes de publicar, cole o código ou a URL no [Teste de pesquisa aprimorada](https://search.google.com/test/rich-results), do Google: ele diz se a marcação está elegível e aponta erros e avisos.
2. Confira o vocabulário no [Schema Markup Validator](https://validator.schema.org/), do schema.org, que valida também propriedades que o Google não usa.
3. Depois de publicar, acompanhe os [relatórios de resultados aprimorados do Search Console](https://support.google.com/webmasters/answer/7552505?hl=pt-BR) e use a Inspeção de URL para confirmar que o Google encontrou a marcação.

## O que as avaliações marcadas valem para as IAs?

Médio: a nota só vale se as avaliações estiverem visíveis e forem reais.

Nota média e número de avaliações são dados que um assistente usa para comparar opções, e a marcação os entrega sem ambiguidade. Mas o que sustenta a recomendação é a reputação fora do site: avaliações no Perfil da Empresa, em marketplaces e em sites independentes. Marcar nota inflada no próprio site não muda isso e ainda tira a elegibilidade para as estrelas. O tema está no [Guia de GEO: Otimização para IAs](https://triwi.com.br/guias/geo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=review-aggregaterating).

## Perguntas frequentes

<details>
<summary><strong>Posso mostrar estrelas da minha empresa no resultado do Google?</strong></summary>

Não pela marcação no próprio site. O Google não mostra estrelas de `LocalBusiness` e `Organization` quando a própria empresa controla as avaliações. As estrelas de produto, curso, receita e aplicativo continuam elegíveis.
</details>

<details>
<summary><strong>Qual a diferença entre ratingCount e reviewCount?</strong></summary>

`ratingCount` é o total de notas dadas, com ou sem comentário; `reviewCount` é o total de avaliações com texto. O Google exige pelo menos um dos dois.
</details>

<details>
<summary><strong>Avaliação vinda de plataforma de reviews conta?</strong></summary>

Para produto, pode ser marcada se as avaliações forem dos clientes daquele produto e estiverem visíveis na página. Para a própria empresa, não gera estrelas, mesmo vindo de widget de terceiros.
</details>

**Ver também na Base de Conhecimento da TRIWI:** [Schema Markup e Dados Estruturados para SEO](https://github.com/TRIWI-SEO/SEO-IA/blob/main/seo-tecnico/schema-markup-e-dados-estruturados-para-seo.md), [Dados Estruturados para IA: Schema Markup na Era Generativa](https://github.com/TRIWI-SEO/SEO-IA/blob/main/geo-seo-para-ia/dados-estruturados-para-ia-schema-markup-na-era-generativa.md).

**Na TRIWI:** [Gerador de dados estruturados](https://triwi.com.br/ferramentas/gerador-de-dados-estruturados/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=review-aggregaterating), [Guia de SEO Técnico, capítulo Dados estruturados](https://triwi.com.br/guias/seo-tecnico/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=review-aggregaterating#dados-estruturados), [Guia de GEO: Otimização para IAs](https://triwi.com.br/guias/geo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=review-aggregaterating), [Atualizações do Google](https://triwi.com.br/atualizacoes/google/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=review-aggregaterating).

**Ver também no Glossário de SEO da TRIWI:** [Dados estruturados](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=review-aggregaterating#seo-dados-estruturados), [Schema.org](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=review-aggregaterating#seo-schema-org), [Rich results](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=review-aggregaterating#seo-rich-results), [E-E-A-T](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=review-aggregaterating#seo-e-e-a-t).

[Voltar para a biblioteca completa](../README.md)

---

<p align="center">
  <strong>Quer que sua marca seja a resposta, no Google e nas IAs?</strong><br>
  <a href="https://triwi.com.br/contato/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=review-aggregaterating">Que tal um café com a TRIWI?</a>
</p>

<p align="center">
  <sub>Biblioteca publicada e mantida pela equipe da TRIWI, agência 100% especializada em SEO e Otimização para IAs.</sub>
</p>
