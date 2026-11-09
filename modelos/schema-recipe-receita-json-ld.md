# Schema Recipe em JSON-LD: modelo de receita pronto para copiar

**O schema Recipe marca uma receita com foto, ingredientes, modo de preparo, tempos, rendimento e calorias, o que pode gerar imagem, nota e tempo de preparo no resultado e carrossel de receitas. O Google exige só `name` e `image` e recomenda os demais campos. A página precisa mostrar a receita, não só falar dela.**

*Por equipe de SEO da TRIWI, com revisão de Ricardo Martins, fundador. Publicado em 09/11/2026. Atualizado em 09/11/2026. Campos conferidos na documentação do Google Search Central e no schema.org (versão 30.1) em 09/11/2026.*

> **Situação no Google em 09/11/2026: Ativo.** Imagem, nota, tempo de preparo e calorias da receita, inclusive em carrossel. Última mudança registrada: 06/03/2024. As receitas guiadas do Assistente saíram em 06/03/2024. Fonte: [documentação oficial do Google](https://developers.google.com/search/docs/appearance/structured-data/recipe).

## Índice

- [Quando usar o schema Recipe?](#quando-usar-o-schema-recipe)
- [Quais campos o Google exige e recomenda?](#quais-campos-o-google-exige-e-recomenda)
- [Modelo de JSON-LD para copiar](#modelo-de-json-ld-para-copiar)
- [Modelo completo de receita](#modelo-completo-de-receita)
- [Como validar o schema Recipe?](#como-validar-o-schema-recipe)
- [O que o schema Recipe vale para as IAs?](#o-que-o-schema-recipe-vale-para-as-ias)
- [Perguntas frequentes](#perguntas-frequentes)

## Quando usar o schema Recipe?

Na página de uma receita com ingredientes e modo de preparo visíveis: blog de culinária, portal de receitas, marca de alimentos que publica receitas com os próprios produtos. Página que só lista receitas leva a marcação de carrossel (`ItemList`) apontando para a página de cada uma, como em [Schema Course](../modelos/schema-course-cursos-json-ld.md#modelo-de-lista-de-cursos-em-carrossel).

## Quais campos o Google exige e recomenda?

**Receita** (Recipe), segundo a [documentação do Google](https://developers.google.com/search/docs/appearance/structured-data/recipe):

| Exigência | Campos |
|:---|:---|
| Obrigatórios | `image`; `name` |
| Recomendados | `aggregateRating`; `author`; `cookTime`; `datePublished`; `description`; `keywords`; `nutrition.calories`; `prepTime`; `recipeCategory`; `recipeCuisine`; `recipeIngredient`; `recipeInstructions`; `recipeYield`; `totalTime` |

Tempos em ISO 8601 (`PT20M` são 20 minutos, `PT1H10M` uma hora e dez minutos), sempre como valor exato, nunca faixa.

## Modelo de JSON-LD para copiar

```json
{
  "@context": "https://schema.org",
  "@type": "Recipe",
  "name": "Pão de queijo de liquidificador",
  "image": [
    "https://www.exemplo.com.br/imagens/pao-de-queijo-1x1.jpg",
    "https://www.exemplo.com.br/imagens/pao-de-queijo-4x3.jpg",
    "https://www.exemplo.com.br/imagens/pao-de-queijo-16x9.jpg"
  ],
  "recipeIngredient": [
    "2 ovos",
    "1 xícara de leite",
    "1/2 xícara de óleo",
    "2 xícaras de polvilho azedo",
    "1 xícara de queijo meia cura ralado",
    "1 colher de chá de sal"
  ],
  "recipeInstructions": [
    {"@type": "HowToStep", "text": "Bata no liquidificador os ovos, o leite, o óleo e o sal."},
    {"@type": "HowToStep", "text": "Acrescente o polvilho e o queijo e bata até ficar homogêneo."},
    {"@type": "HowToStep", "text": "Distribua em forminhas untadas e asse em forno a 200 graus por 25 minutos."}
  ]
}
```

Cole dentro de uma tag `<script type="application/ld+json">`. Os passos usam `HowToStep`, tipo do schema.org que segue válido dentro da receita, mesmo depois que o resultado de passo a passo (`HowTo`) saiu do Google.

## Modelo completo de receita

```json
{
  "@context": "https://schema.org",
  "@type": "Recipe",
  "name": "Pão de queijo de liquidificador",
  "description": "Pão de queijo fácil, batido no liquidificador e assado em forminhas.",
  "image": [
    "https://www.exemplo.com.br/imagens/pao-de-queijo-1x1.jpg",
    "https://www.exemplo.com.br/imagens/pao-de-queijo-4x3.jpg",
    "https://www.exemplo.com.br/imagens/pao-de-queijo-16x9.jpg"
  ],
  "author": {
    "@type": "Person",
    "name": "Nome da Autora",
    "url": "https://www.exemplo.com.br/autores/nome-da-autora/"
  },
  "datePublished": "2026-11-09",
  "prepTime": "PT10M",
  "cookTime": "PT25M",
  "totalTime": "PT35M",
  "recipeYield": "20 unidades",
  "recipeCategory": "Lanche",
  "recipeCuisine": "Brasileira",
  "keywords": "pão de queijo, polvilho, lanche mineiro",
  "nutrition": {
    "@type": "NutritionInformation",
    "calories": "90 calorias"
  },
  "recipeIngredient": [
    "2 ovos",
    "1 xícara de leite",
    "1/2 xícara de óleo",
    "2 xícaras de polvilho azedo",
    "1 xícara de queijo meia cura ralado",
    "1 colher de chá de sal"
  ],
  "recipeInstructions": [
    {"@type": "HowToStep", "name": "Bater", "text": "Bata no liquidificador os ovos, o leite, o óleo e o sal.", "url": "https://www.exemplo.com.br/receitas/pao-de-queijo#passo1"},
    {"@type": "HowToStep", "name": "Misturar", "text": "Acrescente o polvilho e o queijo e bata até ficar homogêneo.", "url": "https://www.exemplo.com.br/receitas/pao-de-queijo#passo2"},
    {"@type": "HowToStep", "name": "Assar", "text": "Distribua em forminhas untadas e asse em forno a 200 graus por 25 minutos.", "url": "https://www.exemplo.com.br/receitas/pao-de-queijo#passo3"}
  ],
  "aggregateRating": {
    "@type": "AggregateRating",
    "ratingValue": 4.8,
    "ratingCount": 96
  }
}
```

As calorias são por porção e o `recipeYield` diz quantas porções a receita rende. A nota só entra se as avaliações estiverem visíveis na página.

## Como validar o schema Recipe?

1. Antes de publicar, cole o código ou a URL no [Teste de pesquisa aprimorada](https://search.google.com/test/rich-results), do Google: ele diz se a marcação está elegível e aponta erros e avisos.
2. Confira o vocabulário no [Schema Markup Validator](https://validator.schema.org/), do schema.org, que valida também propriedades que o Google não usa.
3. Depois de publicar, acompanhe os [relatórios de resultados aprimorados do Search Console](https://support.google.com/webmasters/answer/7552505?hl=pt-BR) e use a Inspeção de URL para confirmar que o Google encontrou a marcação.

## O que o schema Recipe vale para as IAs?

Médio: ingredientes, passos e tempos em formato que qualquer assistente lê.

"O que dá para fazer com polvilho e queijo em meia hora" é o tipo de pergunta que assistentes respondem combinando ingredientes e tempo. A receita com ingredientes em lista, passos numerados e tempos declarados é fácil de reaproveitar e de atribuir à fonte.

## Perguntas frequentes

<details>
<summary><strong>Preciso de todas as fotos em três proporções?</strong></summary>

Só `image` é obrigatório. As três proporções (1x1, 4x3 e 16x9) são recomendação do Google para a imagem caber nos formatos de resultado. A documentação esclarece que a imagem da receita não muda a imagem do resultado em texto.
</details>

<details>
<summary><strong>Marca de alimentos pode usar o schema Recipe?</strong></summary>

Pode, em página de receita completa, com ingredientes e preparo visíveis. Página de produto que só sugere uma receita não é página de receita.
</details>

<details>
<summary><strong>O que eram as receitas guiadas?</strong></summary>

Um recurso do Google Assistente que lia a receita passo a passo. Ele saiu, e a documentação foi atualizada em 06/03/2024. A marcação de receita continua ativa.
</details>

**Ver também na Base de Conhecimento da TRIWI:** [Schema Markup e Dados Estruturados para SEO](https://github.com/TRIWI-SEO/SEO-IA/blob/main/seo-tecnico/schema-markup-e-dados-estruturados-para-seo.md), [Dados Estruturados para IA: Schema Markup na Era Generativa](https://github.com/TRIWI-SEO/SEO-IA/blob/main/geo-seo-para-ia/dados-estruturados-para-ia-schema-markup-na-era-generativa.md).

**Na TRIWI:** [Gerador de dados estruturados](https://triwi.com.br/ferramentas/gerador-de-dados-estruturados/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=recipe-receita), [Guia de SEO Técnico, capítulo Dados estruturados](https://triwi.com.br/guias/seo-tecnico/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=recipe-receita#dados-estruturados), [Guia de GEO: Otimização para IAs](https://triwi.com.br/guias/geo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=recipe-receita), [Atualizações do Google](https://triwi.com.br/atualizacoes/google/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=recipe-receita).

**Ver também no Glossário de SEO da TRIWI:** [Dados estruturados](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=recipe-receita#seo-dados-estruturados), [Schema.org](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=recipe-receita#seo-schema-org), [JSON-LD](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=recipe-receita#seo-json-ld), [Rich results](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=recipe-receita#seo-rich-results).

[Voltar para a biblioteca completa](../README.md)

---

<p align="center">
  <strong>Quer que sua marca seja a resposta, no Google e nas IAs?</strong><br>
  <a href="https://triwi.com.br/contato/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=recipe-receita">Que tal um café com a TRIWI?</a>
</p>

<p align="center">
  <sub>Biblioteca publicada e mantida pela equipe da TRIWI, agência 100% especializada em SEO e Otimização para IAs.</sub>
</p>
