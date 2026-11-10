# Schema ProfilePage e Person em JSON-LD: modelo para página de autor

**O schema ProfilePage marca a página de perfil de uma pessoa ou organização, como a página de autor de um blog ou de um especialista da empresa. Exige `mainEntity` com o `name` da pessoa e recomenda descrição, foto, perfis externos em `sameAs` e datas. É o destino do link de autor dos artigos.**

*Por equipe de SEO da TRIWI, com revisão de Ricardo Martins, fundador. Publicado em 09/11/2026. Atualizado em 09/11/2026. Campos conferidos na documentação do Google Search Central e no schema.org (versão 30.1) em 09/11/2026.*

> **Situação no Google em 09/11/2026: Ativo.** Ajuda o Google a identificar o autor ou o usuário por trás do conteúdo, em fóruns e sites sociais. Para página de autor, perfil de usuário, Sobre mim de blog e página de funcionário; não para a página inicial da loja. Fonte: [documentação oficial do Google](https://developers.google.com/search/docs/appearance/structured-data/profile-page).

## Índice

- [Quando usar o schema ProfilePage?](#quando-usar-o-schema-profilepage)
- [Quais campos o Google exige e recomenda?](#quais-campos-o-google-exige-e-recomenda)
- [Modelo de JSON-LD para copiar](#modelo-de-json-ld-para-copiar)
- [Modelo completo de página de autor](#modelo-completo-de-página-de-autor)
- [Como validar o schema ProfilePage?](#como-validar-o-schema-profilepage)
- [O que a página de autor vale para as IAs?](#o-que-a-página-de-autor-vale-para-as-ias)
- [Perguntas frequentes](#perguntas-frequentes)

## Quando usar o schema ProfilePage?

A documentação do Google lista quatro usos: perfil de usuário em fórum ou rede social, página de autor em site de notícias, página "Sobre mim" de blog e página de funcionário em site de empresa. Não serve para a página inicial de uma loja nem para página de avaliação de uma empresa sem vínculo com o site.

Para empresas, o uso mais valioso é a página de autor: cada especialista que assina conteúdo ganha uma página com credencial, foto e perfis, e o `author.url` dos artigos aponta para ela, como em [Schema Article](../modelos/schema-article-json-ld.md#como-marcar-o-autor-do-artigo).

## Quais campos o Google exige e recomenda?

**Página de perfil** (ProfilePage; Person; Organization), segundo a [documentação do Google](https://developers.google.com/search/docs/appearance/structured-data/profile-page); o tipo no vocabulário está em [schema.org/ProfilePage](https://schema.org/ProfilePage):

| Exigência | Campos |
|:---|:---|
| Obrigatórios | `mainEntity`; `mainEntity.name` (ou `alternateName`) |
| Recomendados | `agentInteractionStatistic`; `alternateName`; `dateCreated`; `dateModified`; `description`; `identifier`; `image`; `interactionStatistic`; `sameAs` |

A foto do perfil precisa ser da pessoa, não uma imagem genérica de placeholder.

## Modelo de JSON-LD para copiar

```json
{
  "@context": "https://schema.org",
  "@type": "ProfilePage",
  "mainEntity": {
    "@type": "Person",
    "name": "Nome da Especialista",
    "description": "Cirurgiã-dentista, especialista em implantodontia, CRO-SP 00000.",
    "image": "https://www.exemplo.com.br/imagens/autores/nome-da-especialista.jpg",
    "sameAs": ["https://www.linkedin.com/in/nome-da-especialista"]
  }
}
```

Cole dentro de uma tag `<script type="application/ld+json">` na página do autor.

## Modelo completo de página de autor

```json
{
  "@context": "https://schema.org",
  "@type": "ProfilePage",
  "url": "https://www.exemplo.com.br/autores/nome-da-especialista/",
  "dateCreated": "2024-02-01T10:00:00-03:00",
  "dateModified": "2026-11-09T10:00:00-03:00",
  "mainEntity": {
    "@type": "Person",
    "@id": "https://www.exemplo.com.br/autores/nome-da-especialista/#person",
    "name": "Nome da Especialista",
    "alternateName": "@nomedaespecialista",
    "identifier": "autor-0042",
    "jobTitle": "Diretora clínica",
    "description": "Cirurgiã-dentista, especialista em implantodontia, CRO-SP 00000. Escreve sobre implantes e reabilitação oral.",
    "image": "https://www.exemplo.com.br/imagens/autores/nome-da-especialista.jpg",
    "worksFor": {"@id": "https://www.exemplo.com.br/#clinica"},
    "alumniOf": {
      "@type": "CollegeOrUniversity",
      "name": "Universidade Exemplo"
    },
    "knowsAbout": ["Implantodontia", "Reabilitação oral"],
    "sameAs": [
      "https://www.linkedin.com/in/nome-da-especialista",
      "https://www.instagram.com/nomedaespecialista"
    ]
  }
}
```

`jobTitle`, `worksFor`, `alumniOf` e `knowsAbout` não estão na lista do Google para ProfilePage, mas são propriedades válidas de `Person` no schema.org e descrevem a credencial que a página mostra. Use só o que está escrito na página.

## Como validar o schema ProfilePage?

1. Antes de publicar, cole o código ou a URL no [Teste de pesquisa aprimorada](https://search.google.com/test/rich-results), do Google: ele diz se a marcação está elegível e aponta erros e avisos.
2. Confira o vocabulário no [Schema Markup Validator](https://validator.schema.org/), do schema.org, que valida também propriedades que o Google não usa.
3. Depois de publicar, acompanhe os [relatórios de resultados aprimorados do Search Console](https://support.google.com/webmasters/answer/7552505?hl=pt-BR) e use a Inspeção de URL para confirmar que o Google encontrou a marcação.

## O que a página de autor vale para as IAs?

Alto: a página de autor com credencial e perfis externos é o que liga o conteúdo a uma pessoa real.

Conteúdo assinado por uma pessoa identificável, com formação e registro profissional visíveis, é o que o Google descreve como experiência e especialidade nas [diretrizes de qualidade](https://static.googleusercontent.com/media/guidelines.raterhub.com/en//searchqualityevaluatorguidelines.pdf). A página de autor com marcação consistente, ligada aos artigos e aos perfis externos, é a forma mais direta de deixar isso verificável. Em saúde, direito e finanças, onde a credencial pesa mais, ela é indispensável. O tema está no guia aberto [E-E-A-T](https://github.com/TRIWI-SEO/SEO-IA/blob/main/seo-de-conteudo/e-e-a-t-o-framework-do-google-para-qualidade-de-conteudo.md).

## Perguntas frequentes

<details>
<summary><strong>Toda empresa precisa de página de autor?</strong></summary>

Toda empresa que publica conteúdo assinado se beneficia. Sem página de autor, o `author.url` dos artigos não tem para onde apontar, e a credencial de quem escreveu fica sem lugar para ser conferida.
</details>

<details>
<summary><strong>Posso usar Organization como mainEntity?</strong></summary>

Sim. A documentação aceita `Person` ou `Organization`. Para a página institucional da própria empresa, o comum é usar o [Organization](../modelos/schema-organization-json-ld.md) direto.
</details>

<details>
<summary><strong>Registro profissional, como CRM, OAB ou CRO, pode entrar na marcação?</strong></summary>

Pode, no texto da `description` ou com `hasCredential`, propriedade de `Person` no schema.org, desde que o registro também apareça na página. As regras de cada conselho sobre divulgação continuam valendo.
</details>

**Ver também na Base de Conhecimento da TRIWI:** [Schema Markup e Dados Estruturados para SEO](https://github.com/TRIWI-SEO/SEO-IA/blob/main/seo-tecnico/schema-markup-e-dados-estruturados-para-seo.md), [Dados Estruturados para IA: Schema Markup na Era Generativa](https://github.com/TRIWI-SEO/SEO-IA/blob/main/geo-seo-para-ia/dados-estruturados-para-ia-schema-markup-na-era-generativa.md).

**Na TRIWI:** [Gerador de dados estruturados](https://triwi.com.br/ferramentas/gerador-de-dados-estruturados/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=profilepage-person-autor), [Guia de SEO Técnico, capítulo Dados estruturados](https://triwi.com.br/guias/seo-tecnico/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=profilepage-person-autor#dados-estruturados), [Guia de GEO: Otimização para IAs](https://triwi.com.br/guias/geo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=profilepage-person-autor), [Atualizações do Google](https://triwi.com.br/atualizacoes/google/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=profilepage-person-autor).

**Ver também no Glossário de SEO da TRIWI:** [E-E-A-T](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=profilepage-person-autor#seo-e-e-a-t), [Entidade](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=profilepage-person-autor#seo-entidade), [Dados estruturados](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=profilepage-person-autor#seo-dados-estruturados), [Schema.org](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=profilepage-person-autor#seo-schema-org).

[Voltar para a biblioteca completa](../README.md)

---

<p align="center">
  <strong>Quer que sua marca seja a resposta, no Google e nas IAs?</strong><br>
  <a href="https://triwi.com.br/contato/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=profilepage-person-autor">Que tal um café com a TRIWI?</a>
</p>

<p align="center">
  <sub>Biblioteca publicada e mantida pela equipe da TRIWI, agência 100% especializada em SEO e Otimização para IAs.</sub>
</p>
