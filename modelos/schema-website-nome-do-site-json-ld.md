# Schema WebSite em JSON-LD: modelo para o nome do site no Google

**O schema WebSite informa ao Google o nome do site que aparece acima do título nos resultados. Exige `name` e `url`, aceita variações em `alternateName` e vai só na página inicial do domínio ou subdomínio. A caixa de pesquisa de sitelinks, que usava o mesmo tipo, saiu do Google em 2024.**

*Por equipe de SEO da TRIWI, com revisão de Ricardo Martins, fundador. Publicado em 09/11/2026. Atualizado em 09/11/2026. Campos conferidos na documentação do Google Search Central e no schema.org (versão 30.1) em 09/11/2026.*

> **Situação no Google em 09/11/2026: Ativo.** O nome do site mostrado acima do título nos resultados. Só na página inicial do domínio ou subdomínio; subpasta não pode ter nome próprio. Fonte: [documentação oficial do Google](https://developers.google.com/search/docs/appearance/site-names).

## Índice

- [Quando usar o schema WebSite?](#quando-usar-o-schema-website)
- [Quais campos o Google exige e recomenda?](#quais-campos-o-google-exige-e-recomenda)
- [Modelo de JSON-LD para copiar](#modelo-de-json-ld-para-copiar)
- [Modelo junto com a organização](#modelo-junto-com-a-organização)
- [O que aconteceu com a caixa de pesquisa de sitelinks?](#o-que-aconteceu-com-a-caixa-de-pesquisa-de-sitelinks)
- [Como validar o schema WebSite?](#como-validar-o-schema-website)
- [O que o schema WebSite vale para as IAs?](#o-que-o-schema-website-vale-para-as-ias)
- [Perguntas frequentes](#perguntas-frequentes)

## Quando usar o schema WebSite?

Em todo site, uma vez, na página inicial. O nome do site vale para o domínio (`exemplo.com.br`) ou para um subdomínio (`loja.exemplo.com.br`); subpastas, como `exemplo.com.br/blog`, não podem ter nome próprio. Subdomínios `www` e `m` contam como o próprio domínio.

## Quais campos o Google exige e recomenda?

**Nome do site** (WebSite), segundo a [documentação do Google](https://developers.google.com/search/docs/appearance/site-names):

| Exigência | Campos |
|:---|:---|
| Obrigatórios | `name`; `url` |
| Recomendados | `alternateName` |

A `url` é a página inicial canônica do domínio ou subdomínio. As variações em `alternateName` vão em ordem de preferência, a mais importante primeiro.

## Modelo de JSON-LD para copiar

```json
{
  "@context": "https://schema.org",
  "@type": "WebSite",
  "name": "Exemplo",
  "alternateName": ["Exemplo Soluções", "exemplo.com.br"],
  "url": "https://www.exemplo.com.br/"
}
```

Cole dentro de uma tag `<script type="application/ld+json">` na página inicial. O `name` deve ser o mesmo do [Organization](../modelos/schema-organization-json-ld.md) e o mesmo que aparece no título da página inicial.

## Modelo junto com a organização

Na página inicial, o WebSite e o Organization podem ir num bloco só, com `@graph`, ligados pelo `publisher`.

```json
{
  "@context": "https://schema.org",
  "@graph": [
    {
      "@type": "Organization",
      "@id": "https://www.exemplo.com.br/#organization",
      "name": "Exemplo",
      "url": "https://www.exemplo.com.br/",
      "logo": "https://www.exemplo.com.br/imagens/logo.png"
    },
    {
      "@type": "WebSite",
      "@id": "https://www.exemplo.com.br/#website",
      "name": "Exemplo",
      "alternateName": "Exemplo Soluções",
      "url": "https://www.exemplo.com.br/",
      "inLanguage": "pt-BR",
      "publisher": {"@id": "https://www.exemplo.com.br/#organization"}
    }
  ]
}
```

## O que aconteceu com a caixa de pesquisa de sitelinks?

A caixa de busca interna que aparecia abaixo de alguns resultados usava o mesmo `WebSite`, com uma `potentialAction` do tipo `SearchAction`. O recurso saiu da Pesquisa Google e a documentação foi removida em 29/11/2024. A `SearchAction` pode ficar ou sair do código sem efeito no Google; o `WebSite` com `name` e `url` continua valendo para o nome do site. A lista completa do que saiu está em [O que perdeu o resultado enriquecido no Google](../dados-estruturados-que-perderam-resultado-enriquecido-no-google.md).

## Como validar o schema WebSite?

1. Cole o código no [Schema Markup Validator](https://validator.schema.org/) para conferir a sintaxe; o nome do site não tem relatório próprio no Teste de pesquisa aprimorada.
2. Use a Inspeção de URL do Search Console na página inicial para confirmar que o Google leu a marcação.
3. Mudanças de nome levam tempo para aparecer: o Google precisa rastrear a página inicial de novo.

## O que o schema WebSite vale para as IAs?

Médio: fixa o nome oficial da marca e as variações aceitas.

O nome que a marca usa, as variações aceitas e o domínio oficial são a primeira coisa que qualquer sistema precisa acertar para atribuir uma citação. Repetir o mesmo nome no `WebSite`, no `Organization`, no título da página inicial e nos perfis oficiais tira a dúvida.

## Perguntas frequentes

<details>
<summary><strong>O Google mostra um nome errado para o meu site. O que fazer?</strong></summary>

Confira se o `name` do WebSite é igual ao título da página inicial, ao nome no Organization e ao que aparece nos perfis oficiais. A documentação lista outras fontes que o Google considera, como o título e os cabeçalhos da página inicial; quanto mais consistentes elas forem, mais chance de o nome certo aparecer.
</details>

<details>
<summary><strong>Posso ter um nome diferente para o blog em subpasta?</strong></summary>

Não. Nome de site vale para domínio e subdomínio; subpasta herda o nome do domínio.
</details>

<details>
<summary><strong>Ainda preciso da SearchAction?</strong></summary>

Não para o Google, que retirou a caixa de pesquisa de sitelinks. A propriedade continua válida no schema.org.
</details>

**Ver também na Base de Conhecimento da TRIWI:** [Schema Markup e Dados Estruturados para SEO](https://github.com/TRIWI-SEO/SEO-IA/blob/main/seo-tecnico/schema-markup-e-dados-estruturados-para-seo.md), [Dados Estruturados para IA: Schema Markup na Era Generativa](https://github.com/TRIWI-SEO/SEO-IA/blob/main/geo-seo-para-ia/dados-estruturados-para-ia-schema-markup-na-era-generativa.md).

**Na TRIWI:** [Gerador de dados estruturados](https://triwi.com.br/ferramentas/gerador-de-dados-estruturados/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=website-nome-do-site), [Guia de SEO Técnico, capítulo Dados estruturados](https://triwi.com.br/guias/seo-tecnico/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=website-nome-do-site#dados-estruturados), [Guia de GEO: Otimização para IAs](https://triwi.com.br/guias/geo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=website-nome-do-site), [Atualizações do Google](https://triwi.com.br/atualizacoes/google/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=website-nome-do-site).

**Ver também no Glossário de SEO da TRIWI:** [Dados estruturados](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=website-nome-do-site#seo-dados-estruturados), [Schema.org](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=website-nome-do-site#seo-schema-org), [Entidade](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=website-nome-do-site#seo-entidade).

[Voltar para a biblioteca completa](../README.md)

---

<p align="center">
  <strong>Quer que sua marca seja a resposta, no Google e nas IAs?</strong><br>
  <a href="https://triwi.com.br/contato/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=website-nome-do-site">Que tal um café com a TRIWI?</a>
</p>

<p align="center">
  <sub>Biblioteca publicada e mantida pela equipe da TRIWI, agência 100% especializada em SEO e Otimização para IAs.</sub>
</p>
