# Schema BreadcrumbList em JSON-LD: modelo pronto para copiar

**O schema BreadcrumbList marca a trilha de navegação da página, como Início, Categoria e Página, para o Google mostrar o caminho no lugar do endereço. Exige pelo menos dois itens, cada um com `position`, `name` e `item` (a URL), que pode faltar no último. Desde 22/01/2025 a trilha aparece só no computador.**

*Por equipe de SEO da TRIWI, com revisão de Ricardo Martins, fundador. Publicado em 09/11/2026. Atualizado em 09/11/2026. Campos conferidos na documentação do Google Search Central e no schema.org (versão 30.1) em 09/11/2026.*

> **Situação no Google em 09/11/2026: Ativo.** A trilha de navegação no lugar do endereço da página, só nos resultados no computador. Última mudança registrada: 22/01/2025. Desde 22/01/2025 aparece só no computador. Uma página pode ter mais de uma trilha. Fonte: [documentação oficial do Google](https://developers.google.com/search/docs/appearance/structured-data/breadcrumb).

## Índice

- [Quando usar o schema BreadcrumbList?](#quando-usar-o-schema-breadcrumblist)
- [Quais campos o Google exige e recomenda?](#quais-campos-o-google-exige-e-recomenda)
- [Modelo de JSON-LD para copiar](#modelo-de-json-ld-para-copiar)
- [Modelo com mais de uma trilha](#modelo-com-mais-de-uma-trilha)
- [Como validar o schema BreadcrumbList?](#como-validar-o-schema-breadcrumblist)
- [O que o schema BreadcrumbList vale para as IAs?](#o-que-o-schema-breadcrumblist-vale-para-as-ias)
- [Erros comuns](#erros-comuns)
- [Perguntas frequentes](#perguntas-frequentes)

## Quando usar o schema BreadcrumbList?

Em toda página interna que tem trilha de navegação visível: produto, categoria, post de blog, página de serviço, página de unidade. A página inicial não precisa.

A trilha deve mostrar o caminho típico de um usuário até a página, não necessariamente a estrutura de pastas da URL.

## Quais campos o Google exige e recomenda?

**Trilha de navegação** (BreadcrumbList; ListItem), segundo a [documentação do Google](https://developers.google.com/search/docs/appearance/structured-data/breadcrumb):

| Exigência | Campos |
|:---|:---|
| Obrigatórios | `itemListElement` (mínimo de dois ListItem); `ListItem.item` (dispensado no último item); `ListItem.name`; `ListItem.position` |
| Recomendados | Nenhum |

## Modelo de JSON-LD para copiar

Trilha de um produto: Início, Móveis de escritório, Cadeiras e o produto. O último item pode ficar sem `item`; nesse caso o Google usa a URL da própria página.

```json
{
  "@context": "https://schema.org",
  "@type": "BreadcrumbList",
  "itemListElement": [
    {
      "@type": "ListItem",
      "position": 1,
      "name": "Início",
      "item": "https://www.exemplo.com.br/"
    },
    {
      "@type": "ListItem",
      "position": 2,
      "name": "Móveis de escritório",
      "item": "https://www.exemplo.com.br/moveis-de-escritorio/"
    },
    {
      "@type": "ListItem",
      "position": 3,
      "name": "Cadeiras",
      "item": "https://www.exemplo.com.br/moveis-de-escritorio/cadeiras/"
    },
    {
      "@type": "ListItem",
      "position": 4,
      "name": "Cadeira de Escritório Exemplo Ergo"
    }
  ]
}
```

Cole dentro de uma tag `<script type="application/ld+json">`, na mesma página da trilha visível. A numeração começa em 1, no início da trilha.

## Modelo com mais de uma trilha

Quando a página pode ser alcançada por dois caminhos, como um produto que está em duas categorias, a documentação aceita mais de uma trilha. Em JSON-LD, as trilhas vão numa lista.

```json
[
  {
    "@context": "https://schema.org",
    "@type": "BreadcrumbList",
    "itemListElement": [
      {"@type": "ListItem", "position": 1, "name": "Início", "item": "https://www.exemplo.com.br/"},
      {"@type": "ListItem", "position": 2, "name": "Cadeiras", "item": "https://www.exemplo.com.br/moveis-de-escritorio/cadeiras/"},
      {"@type": "ListItem", "position": 3, "name": "Cadeira de Escritório Exemplo Ergo"}
    ]
  },
  {
    "@context": "https://schema.org",
    "@type": "BreadcrumbList",
    "itemListElement": [
      {"@type": "ListItem", "position": 1, "name": "Início", "item": "https://www.exemplo.com.br/"},
      {"@type": "ListItem", "position": 2, "name": "Home office", "item": "https://www.exemplo.com.br/home-office/"},
      {"@type": "ListItem", "position": 3, "name": "Cadeira de Escritório Exemplo Ergo"}
    ]
  }
]
```

## Como validar o schema BreadcrumbList?

1. Antes de publicar, cole o código ou a URL no [Teste de pesquisa aprimorada](https://search.google.com/test/rich-results), do Google: ele diz se a marcação está elegível e aponta erros e avisos.
2. Confira o vocabulário no [Schema Markup Validator](https://validator.schema.org/), do schema.org, que valida também propriedades que o Google não usa.
3. Depois de publicar, acompanhe os [relatórios de resultados aprimorados do Search Console](https://support.google.com/webmasters/answer/7552505?hl=pt-BR) e use a Inspeção de URL para confirmar que o Google encontrou a marcação.

O [Gerador de dados estruturados da TRIWI](https://triwi.com.br/ferramentas/gerador-de-dados-estruturados/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=breadcrumblist) monta a BreadcrumbList a partir dos nomes e endereços de cada nível, e o [Planejador de arquitetura SEO](https://triwi.com.br/ferramentas/planejador-de-arquitetura-seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=breadcrumblist) ajuda a desenhar a hierarquia antes.

## O que o schema BreadcrumbList vale para as IAs?

Médio: mostra onde a página está na hierarquia do site.

A trilha diz em que parte do site a página mora e a que assunto maior ela pertence. Para quem lê, isso orienta a navegação; para qualquer sistema que monta o mapa do site, reforça a hierarquia entre categoria e página. A trilha marcada só ajuda se refletir uma [arquitetura de site](https://github.com/TRIWI-SEO/SEO-IA/blob/main/seo-tecnico/arquitetura-de-site-para-seo.md) coerente.

## Erros comuns

| Erro | Correção |
|:---|:---|
| Trilha marcada que não aparece na página | Marcar só a trilha visível |
| `position` começando em 0 | Começa em 1 |
| Uma trilha de um item só | Pelo menos dois itens |
| URL de categoria com parâmetro de filtro ou de sessão | A URL canônica de cada nível |
| Nome do item diferente do texto da trilha visível | O mesmo texto nos dois lugares |

## Perguntas frequentes

<details>
<summary><strong>Por que a trilha não aparece no resultado do meu celular?</strong></summary>

Desde 22/01/2025 o Google mostra a trilha de navegação só nos resultados no computador. A marcação continua valendo e segue sendo lida.
</details>

<details>
<summary><strong>O último item precisa de URL?</strong></summary>

Não. A documentação dispensa o `item` no último elemento; sem ele, o Google usa a URL da página que contém a marcação.
</details>

<details>
<summary><strong>A trilha precisa seguir as pastas da URL?</strong></summary>

Não. A documentação pede que a trilha represente o caminho típico do usuário até a página. Em muitos sites os dois coincidem, mas não é exigência.
</details>

**Ver também na Base de Conhecimento da TRIWI:** [Schema Markup e Dados Estruturados para SEO](https://github.com/TRIWI-SEO/SEO-IA/blob/main/seo-tecnico/schema-markup-e-dados-estruturados-para-seo.md), [Dados Estruturados para IA: Schema Markup na Era Generativa](https://github.com/TRIWI-SEO/SEO-IA/blob/main/geo-seo-para-ia/dados-estruturados-para-ia-schema-markup-na-era-generativa.md).

**Na TRIWI:** [Gerador de dados estruturados](https://triwi.com.br/ferramentas/gerador-de-dados-estruturados/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=breadcrumblist), [Guia de SEO Técnico, capítulo Dados estruturados](https://triwi.com.br/guias/seo-tecnico/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=breadcrumblist#dados-estruturados), [Guia de GEO: Otimização para IAs](https://triwi.com.br/guias/geo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=breadcrumblist), [Atualizações do Google](https://triwi.com.br/atualizacoes/google/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=breadcrumblist).

**Ver também no Glossário de SEO da TRIWI:** [Dados estruturados](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=breadcrumblist#seo-dados-estruturados), [Schema.org](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=breadcrumblist#seo-schema-org), [JSON-LD](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=breadcrumblist#seo-json-ld), [Rich results](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=breadcrumblist#seo-rich-results).

[Voltar para a biblioteca completa](../README.md)

---

<p align="center">
  <strong>Quer que sua marca seja a resposta, no Google e nas IAs?</strong><br>
  <a href="https://triwi.com.br/contato/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=breadcrumblist">Que tal um café com a TRIWI?</a>
</p>

<p align="center">
  <sub>Biblioteca publicada e mantida pela equipe da TRIWI, agência 100% especializada em SEO e Otimização para IAs.</sub>
</p>
