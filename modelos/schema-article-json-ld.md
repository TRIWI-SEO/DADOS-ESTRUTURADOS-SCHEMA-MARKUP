# Schema Article em JSON-LD: modelo pronto para copiar

**O schema Article marca artigos, posts de blog e notícias com título, imagem, autor e datas de publicação e de atualização. O Google não exige nenhum campo e recomenda `headline`, `image`, `author` com nome e URL, `datePublished` e `dateModified`. Use BlogPosting para blog e NewsArticle para notícia.**

*Por equipe de SEO da TRIWI, com revisão de Ricardo Martins, fundador. Publicado em 09/11/2026. Atualizado em 09/11/2026. Campos conferidos na documentação do Google Search Central e no schema.org (versão 30.1) em 09/11/2026.*

> **Situação no Google em 09/11/2026: Ativo.** Ajuda o Google a mostrar o título, a imagem e a data certos do artigo. Um author por pessoa, com url ou sameAs; datas em ISO 8601 com fuso horário. Fonte: [documentação oficial do Google](https://developers.google.com/search/docs/appearance/structured-data/article).

## Índice

- [Quando usar o schema Article?](#quando-usar-o-schema-article)
- [Quais campos o Google exige e recomenda?](#quais-campos-o-google-exige-e-recomenda)
- [Modelo de JSON-LD para copiar](#modelo-de-json-ld-para-copiar)
- [Modelo completo de BlogPosting](#modelo-completo-de-blogposting)
- [Como marcar o autor do artigo?](#como-marcar-o-autor-do-artigo)
- [Como validar o schema Article?](#como-validar-o-schema-article)
- [O que o schema Article vale para as IAs?](#o-que-o-schema-article-vale-para-as-ias)
- [Erros comuns](#erros-comuns)
- [Perguntas frequentes](#perguntas-frequentes)

## Quando usar o schema Article?

| Página | Tipo indicado |
|:---|:---|
| Post de blog corporativo | `BlogPosting` |
| Notícia de portal ou de assessoria | `NewsArticle` |
| Guia, artigo técnico, página de conteúdo | `Article` |

A marcação não é exclusiva de sites de notícia: a documentação do Google cobre notícias, posts de blog e artigos de qualquer site.

## Quais campos o Google exige e recomenda?

**Artigo** (Article; NewsArticle; BlogPosting), segundo a [documentação do Google](https://developers.google.com/search/docs/appearance/structured-data/article); o tipo no vocabulário está em [schema.org/Article](https://schema.org/Article):

| Exigência | Campos |
|:---|:---|
| Obrigatórios | Nenhum |
| Recomendados | `author`; `author.name`; `author.url`; `dateModified`; `datePublished`; `headline`; `image` |

As datas vão em ISO 8601 e com fuso horário, por exemplo `2026-11-09T09:00:00-03:00`; sem o fuso, o Google assume o do Googlebot. As imagens precisam ser rastreáveis e indexáveis, de preferência em três proporções (16x9, 4x3 e 1x1), cada uma com pelo menos 50 mil pixels (largura vezes altura).

## Modelo de JSON-LD para copiar

```json
{
  "@context": "https://schema.org",
  "@type": "BlogPosting",
  "headline": "Como escolher um software de gestão para clínicas",
  "image": "https://www.exemplo.com.br/imagens/software-clinicas-16x9.jpg",
  "datePublished": "2026-11-09T09:00:00-03:00",
  "dateModified": "2026-11-09T09:00:00-03:00",
  "author": {
    "@type": "Person",
    "name": "Nome do Autor",
    "url": "https://www.exemplo.com.br/autores/nome-do-autor/"
  }
}
```

Cole dentro de uma tag `<script type="application/ld+json">` na página do artigo. Em WordPress, plugins de SEO costumam gerar essa marcação; confira se o autor e as datas saem certos.

## Modelo completo de BlogPosting

```json
{
  "@context": "https://schema.org",
  "@type": "BlogPosting",
  "@id": "https://www.exemplo.com.br/blog/software-de-gestao-para-clinicas/#article",
  "mainEntityOfPage": "https://www.exemplo.com.br/blog/software-de-gestao-para-clinicas/",
  "headline": "Como escolher um software de gestão para clínicas",
  "description": "Os critérios que mais pesam na escolha: agenda, prontuário, faturamento de convênios e LGPD.",
  "image": [
    "https://www.exemplo.com.br/imagens/software-clinicas-1x1.jpg",
    "https://www.exemplo.com.br/imagens/software-clinicas-4x3.jpg",
    "https://www.exemplo.com.br/imagens/software-clinicas-16x9.jpg"
  ],
  "datePublished": "2026-11-09T09:00:00-03:00",
  "dateModified": "2026-11-20T14:30:00-03:00",
  "inLanguage": "pt-BR",
  "author": [
    {
      "@type": "Person",
      "name": "Nome do Autor",
      "url": "https://www.exemplo.com.br/autores/nome-do-autor/",
      "jobTitle": "Especialista em gestão de clínicas",
      "sameAs": ["https://www.linkedin.com/in/nome-do-autor"]
    },
    {
      "@type": "Person",
      "name": "Nome da Revisora",
      "url": "https://www.exemplo.com.br/autores/nome-da-revisora/"
    }
  ],
  "publisher": {
    "@id": "https://www.exemplo.com.br/#organization"
  },
  "isPartOf": {
    "@type": "Blog",
    "name": "Blog Exemplo",
    "url": "https://www.exemplo.com.br/blog/"
  }
}
```

O `publisher` aponta para o `@id` da organização declarada na página inicial, como em [Schema Organization](../modelos/schema-organization-json-ld.md). Junto do Article, quase toda página de conteúdo leva também a [trilha de navegação](../modelos/schema-breadcrumblist-json-ld.md).

## Como marcar o autor do artigo?

As boas práticas da documentação do Google:

| Regra | Como fica no código |
|:---|:---|
| Todos os autores que aparecem na página entram na marcação | Um objeto por autor, numa lista em `author` |
| Um autor por objeto | Nunca `"name": "Ana e João"` |
| `name` só com o nome | Cargo vai em `jobTitle`, editora vai em `publisher` |
| URL que identifica a pessoa | `url` para a página do autor no site ou `sameAs` para perfis externos |
| Tipo certo | `Person` para pessoa, `Organization` para empresa |

A página de autor para onde o `url` aponta pode ter a própria marcação, descrita em [Schema ProfilePage e Person](../modelos/schema-profilepage-person-autor-json-ld.md).

## Como validar o schema Article?

1. Antes de publicar, cole o código ou a URL no [Teste de pesquisa aprimorada](https://search.google.com/test/rich-results), do Google: ele diz se a marcação está elegível e aponta erros e avisos.
2. Confira o vocabulário no [Schema Markup Validator](https://validator.schema.org/), do schema.org, que valida também propriedades que o Google não usa.
3. Depois de publicar, acompanhe os [relatórios de resultados aprimorados do Search Console](https://support.google.com/webmasters/answer/7552505?hl=pt-BR) e use a Inspeção de URL para confirmar que o Google encontrou a marcação.

O [Gerador de dados estruturados da TRIWI](https://triwi.com.br/ferramentas/gerador-de-dados-estruturados/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=article) monta o Article com autor e datas por formulário.

## O que o schema Article vale para as IAs?

Alto: autoria e datas declaradas, os sinais de quem escreveu e de quando que a IA usa para escolher a fonte.

Quem escreveu, com que credencial e quando o texto foi revisado são perguntas que o leitor faz antes de confiar, e são as mesmas que um sistema de busca faz antes de usar uma fonte. A marcação não cria autoridade, mas declara esses sinais de forma inequívoca, desde que eles também estejam visíveis na página: o nome do autor no topo, a data de atualização perto do título. O tema está no [Guia de Conteúdo para SEO e IA](https://triwi.com.br/guias/conteudo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=article) e no guia aberto [E-E-A-T](https://github.com/TRIWI-SEO/SEO-IA/blob/main/seo-de-conteudo/e-e-a-t-o-framework-do-google-para-qualidade-de-conteudo.md).

## Erros comuns

| Erro | Correção |
|:---|:---|
| `dateModified` atualizado sem mudança real no texto | Só mude a data quando o conteúdo mudar de fato |
| Data sem fuso horário | ISO 8601 com o fuso, `-03:00` para Brasília |
| Nome da empresa no `author` de todos os posts | O autor real como `Person`; a empresa vai em `publisher` |
| Autor na marcação que não aparece na página | Todo autor marcado também aparece no texto visível |
| Imagem do artigo bloqueada no robots.txt | Imagens rastreáveis e indexáveis |

## Perguntas frequentes

<details>
<summary><strong>O schema Article é fator de ranqueamento?</strong></summary>

Não. John Mueller, do Google, disse em abril de 2025 que dados estruturados não fazem o site ranquear melhor ([Search Engine Journal](https://www.searchenginejournal.com/google-confirms-that-structured-data-wont-make-a-site-rank-better/544433/)). A marcação ajuda o Google a entender a página e a mostrar título, imagem e data com mais precisão.
</details>

<details>
<summary><strong>Article, BlogPosting ou NewsArticle: qual usar?</strong></summary>

Os três são aceitos pelo Google. Use o mais específico: `BlogPosting` para post de blog, `NewsArticle` para notícia e `Article` para os demais conteúdos editoriais.
</details>

<details>
<summary><strong>Preciso marcar o publisher?</strong></summary>

O `publisher` não está entre os campos recomendados do Google, mas é propriedade válida do schema.org e liga o artigo à empresa. Apontar para o `@id` da organização custa uma linha.
</details>

<details>
<summary><strong>Posso usar o schema Article em página de serviço?</strong></summary>

Só se a página for conteúdo editorial. Página de serviço comercial fica melhor com a marcação da organização e a trilha de navegação; marcar como artigo uma página que não é artigo contraria a regra de relevância das diretrizes de dados estruturados.
</details>

**Ver também na Base de Conhecimento da TRIWI:** [Schema Markup e Dados Estruturados para SEO](https://github.com/TRIWI-SEO/SEO-IA/blob/main/seo-tecnico/schema-markup-e-dados-estruturados-para-seo.md), [Dados Estruturados para IA: Schema Markup na Era Generativa](https://github.com/TRIWI-SEO/SEO-IA/blob/main/geo-seo-para-ia/dados-estruturados-para-ia-schema-markup-na-era-generativa.md).

**Na TRIWI:** [Gerador de dados estruturados](https://triwi.com.br/ferramentas/gerador-de-dados-estruturados/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=article), [Guia de SEO Técnico, capítulo Dados estruturados](https://triwi.com.br/guias/seo-tecnico/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=article#dados-estruturados), [Guia de GEO: Otimização para IAs](https://triwi.com.br/guias/geo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=article), [Atualizações do Google](https://triwi.com.br/atualizacoes/google/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=article).

**Ver também no Glossário de SEO da TRIWI:** [Dados estruturados](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=article#seo-dados-estruturados), [JSON-LD](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=article#seo-json-ld), [E-E-A-T](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=article#seo-e-e-a-t), [AI Overviews](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=article#seo-ai-overviews).

[Voltar para a biblioteca completa](../README.md)

---

<p align="center">
  <strong>Quer que sua marca seja a resposta, no Google e nas IAs?</strong><br>
  <a href="https://triwi.com.br/contato/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=article">Que tal um café com a TRIWI?</a>
</p>

<p align="center">
  <sub>Biblioteca publicada e mantida pela equipe da TRIWI, agência 100% especializada em SEO e Otimização para IAs.</sub>
</p>
