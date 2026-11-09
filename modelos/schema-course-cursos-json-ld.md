# Schema Course em JSON-LD: modelo para lista de cursos

**O schema Course descreve cursos com nome, descrição e instituição. No Google, gera a lista de cursos em carrossel, que exige pelo menos três cursos marcados e está disponível só em inglês. As informações detalhadas de curso, com modalidade e carga horária, saíram da Pesquisa em 2025.**

*Por equipe de SEO da TRIWI, com revisão de Ricardo Martins, fundador. Publicado em 09/11/2026. Atualizado em 09/11/2026. Campos conferidos na documentação do Google Search Central e no schema.org (versão 30.1) em 09/11/2026.*

> **Situação no Google em 09/11/2026: Ativo com restrição.** Carrossel com os cursos de um mesmo provedor. Disponível só em inglês. Exige pelo menos três cursos marcados e a marcação de carrossel. Fonte: [documentação oficial do Google](https://developers.google.com/search/docs/appearance/structured-data/course).

## Índice

- [Quando usar o schema Course?](#quando-usar-o-schema-course)
- [Quais campos o Google exige e recomenda?](#quais-campos-o-google-exige-e-recomenda)
- [Modelo de JSON-LD para copiar](#modelo-de-json-ld-para-copiar)
- [Modelo de lista de cursos em carrossel](#modelo-de-lista-de-cursos-em-carrossel)
- [Como validar o schema Course?](#como-validar-o-schema-course)
- [O que o schema Course vale para as IAs?](#o-que-o-schema-course-vale-para-as-ias)
- [Perguntas frequentes](#perguntas-frequentes)

## Quando usar o schema Course?

Na página de cada curso de uma escola, faculdade, plataforma de cursos livres ou empresa de treinamento. Para o carrossel, a página que lista os cursos ganha a marcação de lista (`ItemList`) e cada curso tem a sua página com o `Course`.

Para sites em português, o carrossel não aparece hoje, porque o recurso está disponível só em inglês. A marcação continua descrevendo o curso para qualquer sistema que leia a página.

## Quais campos o Google exige e recomenda?

**Lista de cursos** (Course; ItemList), segundo a [documentação do Google](https://developers.google.com/search/docs/appearance/structured-data/course):

| Exigência | Campos |
|:---|:---|
| Obrigatórios | `Course.name`; `Course.description`; `ItemList.itemListElement`; `ListItem.position`; `ListItem.url` |
| Recomendados | `Course.provider` |

**Carrossel** (ItemList; ListItem), segundo a [documentação do Google](https://developers.google.com/search/docs/appearance/structured-data/carousel):

| Exigência | Campos |
|:---|:---|
| Obrigatórios | `itemListElement` (mínimo de dois ListItem do mesmo tipo); `ListItem.position`; `ListItem.url` (página de resumo) ou `ListItem.item`, `item.name` e `item.url` (página com tudo) |
| Recomendados | Nenhum |

A descrição do curso aparece com até 60 caracteres no carrossel.

## Modelo de JSON-LD para copiar

Na página de cada curso:

```json
{
  "@context": "https://schema.org",
  "@type": "Course",
  "name": "Pós-graduação em Gestão de Clínicas",
  "description": "Gestão financeira, faturamento de convênios e marketing para clínicas.",
  "provider": {
    "@type": "Organization",
    "name": "Faculdade Exemplo",
    "sameAs": "https://www.exemplo.edu.br/"
  }
}
```

Cole dentro de uma tag `<script type="application/ld+json">`.

## Modelo de lista de cursos em carrossel

Na página que lista os cursos, a marcação de carrossel aponta para a página de cada um. São pelo menos três cursos, cada um com URL única.

```json
{
  "@context": "https://schema.org",
  "@type": "ItemList",
  "itemListElement": [
    {
      "@type": "ListItem",
      "position": 1,
      "url": "https://www.exemplo.edu.br/pos/gestao-de-clinicas/"
    },
    {
      "@type": "ListItem",
      "position": 2,
      "url": "https://www.exemplo.edu.br/pos/auditoria-em-saude/"
    },
    {
      "@type": "ListItem",
      "position": 3,
      "url": "https://www.exemplo.edu.br/pos/marketing-para-saude/"
    }
  ]
}
```

Avaliações de alunos podem entrar no `Course` com `aggregateRating`, seguindo as regras de [Review e AggregateRating](../modelos/schema-review-aggregaterating-json-ld.md#modelo-de-aggregaterating-para-copiar).

## Como validar o schema Course?

1. Antes de publicar, cole o código ou a URL no [Teste de pesquisa aprimorada](https://search.google.com/test/rich-results), do Google: ele diz se a marcação está elegível e aponta erros e avisos.
2. Confira o vocabulário no [Schema Markup Validator](https://validator.schema.org/), do schema.org, que valida também propriedades que o Google não usa.
3. Depois de publicar, acompanhe os [relatórios de resultados aprimorados do Search Console](https://support.google.com/webmasters/answer/7552505?hl=pt-BR) e use a Inspeção de URL para confirmar que o Google encontrou a marcação.

## O que o schema Course vale para as IAs?

Médio: nome, descrição e instituição de cada curso declarados.

Quem pergunta a um assistente por cursos de uma área quer nome, instituição, modalidade, duração e investimento. O Google deixou de exibir as informações detalhadas de curso, mas os dados continuam úteis na página: escritos de forma clara, visíveis e, se você quiser, descritos com propriedades do schema.org como `hasCourseInstance`, `courseMode` e `timeRequired`. O tema está na página [SEO para Educação](https://triwi.com.br/seo-para-educacao/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=course-cursos).

## Perguntas frequentes

<details>
<summary><strong>O que eram as informações do curso, que saíram do Google?</strong></summary>

Era um resultado com detalhes como modalidade, carga horária e avaliações, marcado com `Course` e `CourseInstance`. O Google anunciou a retirada em 12/06/2025 e removeu a documentação em 09/09/2025. A lista de cursos em carrossel continua.
</details>

<details>
<summary><strong>Curso gratuito ou pago muda a marcação?</strong></summary>

Não na parte exigida pelo Google. O valor do curso pode ser descrito com `offers` no schema.org, mas não é campo do recurso de lista de cursos.
</details>

<details>
<summary><strong>Posso marcar um curso só?</strong></summary>

Pode descrever, mas o carrossel exige pelo menos três cursos marcados, em páginas separadas ou numa página com todos.
</details>

**Ver também na Base de Conhecimento da TRIWI:** [Schema Markup e Dados Estruturados para SEO](https://github.com/TRIWI-SEO/SEO-IA/blob/main/seo-tecnico/schema-markup-e-dados-estruturados-para-seo.md), [Dados Estruturados para IA: Schema Markup na Era Generativa](https://github.com/TRIWI-SEO/SEO-IA/blob/main/geo-seo-para-ia/dados-estruturados-para-ia-schema-markup-na-era-generativa.md).

**Na TRIWI:** [Gerador de dados estruturados](https://triwi.com.br/ferramentas/gerador-de-dados-estruturados/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=course-cursos), [Guia de SEO Técnico, capítulo Dados estruturados](https://triwi.com.br/guias/seo-tecnico/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=course-cursos#dados-estruturados), [Guia de GEO: Otimização para IAs](https://triwi.com.br/guias/geo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=course-cursos), [Atualizações do Google](https://triwi.com.br/atualizacoes/google/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=course-cursos).

**Ver também no Glossário de SEO da TRIWI:** [Dados estruturados](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=course-cursos#seo-dados-estruturados), [Schema.org](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=course-cursos#seo-schema-org), [JSON-LD](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=course-cursos#seo-json-ld).

[Voltar para a biblioteca completa](../README.md)

---

<p align="center">
  <strong>Quer que sua marca seja a resposta, no Google e nas IAs?</strong><br>
  <a href="https://triwi.com.br/contato/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=course-cursos">Que tal um café com a TRIWI?</a>
</p>

<p align="center">
  <sub>Biblioteca publicada e mantida pela equipe da TRIWI, agência 100% especializada em SEO e Otimização para IAs.</sub>
</p>
