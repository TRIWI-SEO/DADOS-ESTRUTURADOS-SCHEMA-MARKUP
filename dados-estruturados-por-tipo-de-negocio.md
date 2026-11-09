# Dados estruturados por tipo de negócio: quais schemas usar em cada site

**Todo site começa por Organization e WebSite na página inicial e BreadcrumbList nas páginas internas. Depois, o tipo de negócio decide o resto: Product e OnlineStore no e-commerce, LocalBusiness em clínica e loja física, Article e página de autor em B2B e blog, SoftwareApplication em SaaS, Course em educação, Event em eventos e JobPosting em vagas.**

*Por equipe de SEO da TRIWI, com revisão de Ricardo Martins, fundador. Publicado em 09/11/2026. Atualizado em 09/11/2026. Campos conferidos na documentação do Google Search Central e no schema.org (versão 30.1) em 09/11/2026.*

## Índice

- [Qual a base comum a todo site?](#qual-a-base-comum-a-todo-site)
- [Quais schemas usar em cada tipo de negócio?](#quais-schemas-usar-em-cada-tipo-de-negócio)
- [E-commerce](#e-commerce)
- [Clínica, consultório e negócio local](#clínica-consultório-e-negócio-local)
- [B2B, indústria e serviços](#b2b-indústria-e-serviços)
- [SaaS e software](#saas-e-software)
- [Blog e portal de conteúdo](#blog-e-portal-de-conteúdo)
- [Educação](#educação)
- [Restaurante](#restaurante)
- [Como juntar vários schemas na mesma página?](#como-juntar-vários-schemas-na-mesma-página)
- [Perguntas frequentes](#perguntas-frequentes)

## Qual a base comum a todo site?

| Página | Marcação | Modelo |
|:---|:---|:---|
| Página inicial | `Organization` (ou subtipo) e `WebSite` | [Organization](modelos/schema-organization-json-ld.md), [WebSite](modelos/schema-website-nome-do-site-json-ld.md) |
| Páginas internas | `BreadcrumbList` | [BreadcrumbList](modelos/schema-breadcrumblist-json-ld.md) |
| Artigos e posts | `Article` ou `BlogPosting`, com autor | [Article](modelos/schema-article-json-ld.md) |
| Página de autor ou especialista | `ProfilePage` com `Person` | [ProfilePage](modelos/schema-profilepage-person-autor-json-ld.md) |

O [Gerador de dados estruturados da TRIWI](https://triwi.com.br/ferramentas/gerador-de-dados-estruturados/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=dados-estruturados-por-tipo-de-negocio) monta quatro desses blocos por formulário: Organization, LocalBusiness, Article e BreadcrumbList.

## Quais schemas usar em cada tipo de negócio?

| Negócio | Além da base | Página da TRIWI sobre o segmento |
|:---|:---|:---|
| E-commerce | `OnlineStore` com frete e devolução; `Product` ou `ProductGroup` em cada produto | [SEO para E-commerce](https://triwi.com.br/seo-para-ecommerce/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=dados-estruturados-por-tipo-de-negocio) |
| Clínica, consultório, loja física | Subtipo de `LocalBusiness` em cada unidade | [SEO para Médicos e Clínicas](https://triwi.com.br/seo-para-medicos-e-clinicas/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=dados-estruturados-por-tipo-de-negocio) |
| B2B, indústria, serviços | `Organization` completo; `Article` e `ProfilePage` no conteúdo | [SEO para B2B](https://triwi.com.br/seo-para-b2b/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=dados-estruturados-por-tipo-de-negocio) |
| SaaS e software | `SoftwareApplication` ou `WebApplication` na página do produto | [SEO para SaaS](https://triwi.com.br/seo-para-saas/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=dados-estruturados-por-tipo-de-negocio) |
| Blog e portal | `BlogPosting` ou `NewsArticle`; `ProfilePage` por autor | [Guia de Conteúdo para SEO e IA](https://triwi.com.br/guias/conteudo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=dados-estruturados-por-tipo-de-negocio) |
| Escola, faculdade, cursos | `EducationalOrganization` ou subtipo; `Course` em cada curso | [SEO para Educação](https://triwi.com.br/seo-para-educacao/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=dados-estruturados-por-tipo-de-negocio) |
| Restaurante | `Restaurant` com `menu` e `servesCuisine` | [Schema LocalBusiness](modelos/schema-local-business-json-ld.md) |
| Eventos | `Event` em cada evento presencial | [Schema Event](modelos/schema-event-json-ld.md) |
| Página de carreiras | `JobPosting` em cada vaga | [Schema JobPosting](modelos/schema-jobposting-vagas-json-ld.md) |
| Hotel e pousada | `Hotel` ou `BedAndBreakfast` (subtipos de `LocalBusiness`) | [SEO para Hotéis e Pousadas](https://triwi.com.br/seo-para-hoteis-e-pousadas/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=dados-estruturados-por-tipo-de-negocio) |
| Imobiliária | `RealEstateAgent` (subtipo de `LocalBusiness`) | [SEO para Imobiliárias](https://triwi.com.br/seo-para-imobiliarias/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=dados-estruturados-por-tipo-de-negocio) |

Imóvel à venda ou para alugar não tem resultado enriquecido próprio no Google; a imobiliária marca a empresa e as unidades, e o anúncio fica no texto.

## E-commerce

Página inicial com `OnlineStore` e `WebSite`; página de produto com `Product` e a trilha. O frete e a devolução gerais ficam na loja, e o produto aponta para ela pelo `@id`.

```json
{
  "@context": "https://schema.org",
  "@graph": [
    {
      "@type": "Product",
      "name": "Cadeira de Escritório Exemplo Ergo",
      "image": "https://www.exemplo.com.br/imagens/cadeira-ergo-16x9.jpg",
      "sku": "ERGO-PRETA",
      "brand": {"@type": "Brand", "name": "Exemplo"},
      "offers": {
        "@type": "Offer",
        "url": "https://www.exemplo.com.br/cadeira-ergo",
        "price": 1299.90,
        "priceCurrency": "BRL",
        "availability": "https://schema.org/InStock",
        "seller": {"@id": "https://www.exemplo.com.br/#organization"}
      }
    },
    {
      "@type": "BreadcrumbList",
      "itemListElement": [
        {"@type": "ListItem", "position": 1, "name": "Início", "item": "https://www.exemplo.com.br/"},
        {"@type": "ListItem", "position": 2, "name": "Cadeiras", "item": "https://www.exemplo.com.br/cadeiras/"},
        {"@type": "ListItem", "position": 3, "name": "Cadeira de Escritório Exemplo Ergo"}
      ]
    }
  ]
}
```

O `OnlineStore` completo, com frete e devolução, está em [Schema Organization](modelos/schema-organization-json-ld.md#modelo-de-onlinestore-para-loja-online); variantes, análise e frete por produto, em [Schema Product](modelos/schema-product-json-ld.md).

## Clínica, consultório e negócio local

Uma marcação por unidade, com o subtipo certo, ligada à marca. Os profissionais ganham página própria com `ProfilePage`.

```json
{
  "@context": "https://schema.org",
  "@graph": [
    {
      "@type": "MedicalClinic",
      "@id": "https://www.exemplo.com.br/unidades/moema/#clinica",
      "name": "Clínica Exemplo Moema",
      "url": "https://www.exemplo.com.br/unidades/moema/",
      "telephone": "+55-11-0000-0000",
      "address": {
        "@type": "PostalAddress",
        "streetAddress": "Avenida Exemplo, 200",
        "addressLocality": "São Paulo",
        "addressRegion": "SP",
        "postalCode": "04000-000",
        "addressCountry": "BR"
      },
      "openingHoursSpecification": {
        "@type": "OpeningHoursSpecification",
        "dayOfWeek": ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday"],
        "opens": "07:00:00",
        "closes": "20:00:00"
      },
      "parentOrganization": {"@id": "https://www.exemplo.com.br/#organization"}
    },
    {
      "@type": "BreadcrumbList",
      "itemListElement": [
        {"@type": "ListItem", "position": 1, "name": "Início", "item": "https://www.exemplo.com.br/"},
        {"@type": "ListItem", "position": 2, "name": "Unidades", "item": "https://www.exemplo.com.br/unidades/"},
        {"@type": "ListItem", "position": 3, "name": "Moema"}
      ]
    }
  ]
}
```

Subtipos, horários especiais e rede com várias unidades estão em [Schema LocalBusiness](modelos/schema-local-business-json-ld.md). Para odontologia, a TRIWI mantém a página [SEO para Dentistas e Clínicas Odontológicas](https://triwi.com.br/seo-para-dentistas-e-clinicas-odontologicas/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=dados-estruturados-por-tipo-de-negocio).

## B2B, indústria e serviços

Empresa B2B raramente tem resultado enriquecido próprio, e o trabalho da marcação aqui é de identidade: o `Organization` completo na página inicial e o conteúdo técnico assinado por especialistas.

```json
{
  "@context": "https://schema.org",
  "@graph": [
    {
      "@type": "Article",
      "headline": "Como dimensionar um sistema de ar comprimido industrial",
      "image": "https://www.exemplo.com.br/imagens/ar-comprimido-16x9.jpg",
      "datePublished": "2026-11-09T09:00:00-03:00",
      "dateModified": "2026-11-09T09:00:00-03:00",
      "author": {
        "@type": "Person",
        "name": "Nome do Engenheiro",
        "url": "https://www.exemplo.com.br/especialistas/nome-do-engenheiro/"
      },
      "publisher": {"@id": "https://www.exemplo.com.br/#organization"}
    },
    {
      "@type": "BreadcrumbList",
      "itemListElement": [
        {"@type": "ListItem", "position": 1, "name": "Início", "item": "https://www.exemplo.com.br/"},
        {"@type": "ListItem", "position": 2, "name": "Conteúdos técnicos", "item": "https://www.exemplo.com.br/conteudos/"},
        {"@type": "ListItem", "position": 3, "name": "Como dimensionar um sistema de ar comprimido industrial"}
      ]
    }
  ]
}
```

Página de serviço não leva `Article`. O schema.org tem o tipo `Service`, que descreve o serviço com `provider` e `areaServed`, mas ele não gera resultado no Google; use só se a página descreve o serviço de fato. O tema está nas páginas [SEO para B2B](https://triwi.com.br/seo-para-b2b/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=dados-estruturados-por-tipo-de-negocio), [SEO para Indústria](https://triwi.com.br/seo-para-industria/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=dados-estruturados-por-tipo-de-negocio) e [SEO para Serviços](https://triwi.com.br/seo-para-servicos/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=dados-estruturados-por-tipo-de-negocio).

## SaaS e software

Página do produto com `WebApplication`, ligada à empresa. Sem avaliação real visível, não há estrelas, mas a marcação descreve categoria, plataforma e planos.

```json
{
  "@context": "https://schema.org",
  "@type": "WebApplication",
  "name": "Exemplo Gestão",
  "url": "https://www.exemplo.com.br/software/",
  "applicationCategory": "BusinessApplication",
  "operatingSystem": "Web",
  "offers": {
    "@type": "Offer",
    "price": 199.00,
    "priceCurrency": "BRL"
  },
  "publisher": {"@id": "https://www.exemplo.com.br/#organization"}
}
```

Planos, avaliações e aplicativo de celular estão em [Schema SoftwareApplication](modelos/schema-softwareapplication-json-ld.md).

## Blog e portal de conteúdo

Cada post com `BlogPosting` e autor; cada autor com página própria. O `Blog` liga os posts ao blog, e o `publisher`, à empresa.

```json
{
  "@context": "https://schema.org",
  "@graph": [
    {
      "@type": "BlogPosting",
      "headline": "O que muda na declaração do imposto de renda em 2027",
      "image": "https://www.exemplo.com.br/imagens/ir-2027-16x9.jpg",
      "datePublished": "2026-11-09T09:00:00-03:00",
      "dateModified": "2026-11-09T09:00:00-03:00",
      "author": {
        "@type": "Person",
        "name": "Nome da Contadora",
        "url": "https://www.exemplo.com.br/autores/nome-da-contadora/"
      },
      "publisher": {"@id": "https://www.exemplo.com.br/#organization"},
      "isPartOf": {"@type": "Blog", "name": "Blog Exemplo", "url": "https://www.exemplo.com.br/blog/"}
    },
    {
      "@type": "BreadcrumbList",
      "itemListElement": [
        {"@type": "ListItem", "position": 1, "name": "Início", "item": "https://www.exemplo.com.br/"},
        {"@type": "ListItem", "position": 2, "name": "Blog", "item": "https://www.exemplo.com.br/blog/"},
        {"@type": "ListItem", "position": 3, "name": "O que muda na declaração do imposto de renda em 2027"}
      ]
    }
  ]
}
```

Perguntas frequentes no fim do post ficam como texto: o resultado de FAQ saiu do Google, como explica [Schema FAQPage](modelos/schema-faqpage-json-ld.md).

## Educação

A instituição com o subtipo de `EducationalOrganization` e cada curso com `Course`. Se a escola recebe alunos num endereço, o tipo vai em lista com `LocalBusiness`.

```json
{
  "@context": "https://schema.org",
  "@graph": [
    {
      "@type": ["CollegeOrUniversity", "LocalBusiness"],
      "@id": "https://www.exemplo.edu.br/#organization",
      "name": "Faculdade Exemplo",
      "url": "https://www.exemplo.edu.br/",
      "logo": "https://www.exemplo.edu.br/imagens/logo.png",
      "telephone": "+55-31-0000-0000",
      "address": {
        "@type": "PostalAddress",
        "streetAddress": "Rua Exemplo, 300",
        "addressLocality": "Belo Horizonte",
        "addressRegion": "MG",
        "postalCode": "30000-000",
        "addressCountry": "BR"
      }
    },
    {
      "@type": "Course",
      "name": "Pós-graduação em Gestão de Clínicas",
      "description": "Gestão financeira, faturamento de convênios e marketing para clínicas.",
      "provider": {"@id": "https://www.exemplo.edu.br/#organization"}
    }
  ]
}
```

O carrossel de cursos e o que saiu do Google em 2025 estão em [Schema Course](modelos/schema-course-cursos-json-ld.md).

## Restaurante

`Restaurant` com cardápio, tipo de cozinha e horário. Avaliações da própria casa não geram estrelas.

```json
{
  "@context": "https://schema.org",
  "@type": "Restaurant",
  "name": "Cantina Exemplo",
  "url": "https://www.exemplo.com.br/",
  "telephone": "+55-21-0000-0000",
  "servesCuisine": "Italiana",
  "menu": "https://www.exemplo.com.br/cardapio/",
  "priceRange": "$$",
  "acceptsReservations": true,
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "Rua Exemplo, 45",
    "addressLocality": "Rio de Janeiro",
    "addressRegion": "RJ",
    "postalCode": "22000-000",
    "addressCountry": "BR"
  },
  "openingHoursSpecification": {
    "@type": "OpeningHoursSpecification",
    "dayOfWeek": ["Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday"],
    "opens": "12:00:00",
    "closes": "23:00:00"
  }
}
```

O carrossel de restaurantes no Google é limitado a provedores cadastrados; para o restaurante, o que vale é a marcação correta e o Perfil da Empresa no Google com os mesmos dados.

## Como juntar vários schemas na mesma página?

Três formas, todas aceitas pelo Google:

| Forma | Quando usar |
|:---|:---|
| Um bloco com `@graph`, como nos exemplos desta página | Várias entidades na mesma página, ligadas por `@id` |
| Vários blocos `<script type="application/ld+json">` | Quando partes diferentes do site geram cada marcação, como tema e plugin |
| Uma entidade aninhada na outra | Quando uma é propriedade da outra, como a `Offer` dentro do `Product` |

O `@id` é o que mantém tudo coerente: a organização é declarada uma vez, com `"@id": "https://www.exemplo.com.br/#organization"`, e as outras marcações apontam para ela. O que não pode é a mesma entidade aparecer com dados diferentes em blocos diferentes.

## Perguntas frequentes

<details>
<summary><strong>Qual schema todo site deveria ter?</strong></summary>

`Organization` e `WebSite` na página inicial e `BreadcrumbList` nas páginas internas. Daí em diante, só os tipos que correspondem ao que a página realmente mostra.
</details>

<details>
<summary><strong>Plugin de SEO resolve os dados estruturados?</strong></summary>

Resolve a base, como Organization, WebSite, Article e BreadcrumbList, e às vezes gera tipos que não correspondem à página. Vale conferir as páginas principais no [Teste de pesquisa aprimorada](https://search.google.com/test/rich-results) e completar o que falta.
</details>

<details>
<summary><strong>Mais schemas na página melhoram a posição no Google?</strong></summary>

Não. Dados estruturados não são fator de ranqueamento, e marcar tipos que não correspondem à página contraria as diretrizes. O ganho vem da marcação certa e completa, não da quantidade.
</details>

**Ver também na Base de Conhecimento da TRIWI:** [Schema Markup e Dados Estruturados para SEO](https://github.com/TRIWI-SEO/SEO-IA/blob/main/seo-tecnico/schema-markup-e-dados-estruturados-para-seo.md), [Dados Estruturados para IA: Schema Markup na Era Generativa](https://github.com/TRIWI-SEO/SEO-IA/blob/main/geo-seo-para-ia/dados-estruturados-para-ia-schema-markup-na-era-generativa.md).

**Na TRIWI:** [Gerador de dados estruturados](https://triwi.com.br/ferramentas/gerador-de-dados-estruturados/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=dados-estruturados-por-tipo-de-negocio), [Guia de SEO Técnico, capítulo Dados estruturados](https://triwi.com.br/guias/seo-tecnico/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=dados-estruturados-por-tipo-de-negocio#dados-estruturados), [Guia de GEO: Otimização para IAs](https://triwi.com.br/guias/geo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=dados-estruturados-por-tipo-de-negocio), [Atualizações do Google](https://triwi.com.br/atualizacoes/google/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=dados-estruturados-por-tipo-de-negocio).

**Ver também no Glossário de SEO da TRIWI:** [Dados estruturados](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=dados-estruturados-por-tipo-de-negocio#seo-dados-estruturados), [Schema.org](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=dados-estruturados-por-tipo-de-negocio#seo-schema-org), [JSON-LD](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=dados-estruturados-por-tipo-de-negocio#seo-json-ld), [Entidade](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=dados-estruturados-por-tipo-de-negocio#seo-entidade), [Knowledge Graph](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=dados-estruturados-por-tipo-de-negocio#seo-knowledge-graph).

[Voltar para a biblioteca completa](README.md)

---

<p align="center">
  <strong>Quer que sua marca seja a resposta, no Google e nas IAs?</strong><br>
  <a href="https://triwi.com.br/contato/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=dados-estruturados-por-tipo-de-negocio">Que tal um café com a TRIWI?</a>
</p>

<p align="center">
  <sub>Biblioteca publicada e mantida pela equipe da TRIWI, agência 100% especializada em SEO e Otimização para IAs.</sub>
</p>
