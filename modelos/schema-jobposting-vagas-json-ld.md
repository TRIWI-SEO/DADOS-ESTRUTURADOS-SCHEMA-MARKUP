# Schema JobPosting em JSON-LD: modelo para vaga de emprego

**O schema JobPosting marca uma vaga de emprego para ela aparecer na experiência de vagas do Google, disponível em toda a América Latina, inclusive no Brasil. Exige `title`, `description`, `datePosted`, `hiringOrganization` e `jobLocation`. Vaga encerrada precisa sair do ar ou ganhar `validThrough` vencido.**

*Por equipe de SEO da TRIWI, com revisão de Ricardo Martins, fundador. Publicado em 09/11/2026. Atualizado em 09/11/2026. Campos conferidos na documentação do Google Search Central e no schema.org (versão 30.1) em 09/11/2026.*

> **Situação no Google em 09/11/2026: Ativo.** A vaga na experiência de vagas de emprego do Google, disponível na América Latina. Vaga encerrada precisa sair do ar ou ganhar validThrough no passado. Fonte: [documentação oficial do Google](https://developers.google.com/search/docs/appearance/structured-data/job-posting).

## Índice

- [Quando usar o schema JobPosting?](#quando-usar-o-schema-jobposting)
- [Quais campos o Google exige e recomenda?](#quais-campos-o-google-exige-e-recomenda)
- [Modelo de JSON-LD para copiar](#modelo-de-json-ld-para-copiar)
- [Modelo completo com salário e regime](#modelo-completo-com-salário-e-regime)
- [Modelo de vaga remota](#modelo-de-vaga-remota)
- [Como validar o schema JobPosting?](#como-validar-o-schema-jobposting)
- [O que o schema JobPosting vale para as IAs?](#o-que-o-schema-jobposting-vale-para-as-ias)
- [Perguntas frequentes](#perguntas-frequentes)

## Quando usar o schema JobPosting?

Em cada página de vaga do site de carreiras: uma vaga, uma página, uma marcação. A documentação proíbe a marcação em página que lista várias vagas, em vaga que cobra pagamento do candidato e em vaga expirada; coleta de currículos só vale para posições abertas.

## Quais campos o Google exige e recomenda?

**Vaga de emprego** (JobPosting), segundo a [documentação do Google](https://developers.google.com/search/docs/appearance/structured-data/job-posting); o tipo no vocabulário está em [schema.org/JobPosting](https://schema.org/JobPosting):

| Exigência | Campos |
|:---|:---|
| Obrigatórios | `datePosted`; `description`; `hiringOrganization`; `jobLocation`; `title` |
| Recomendados | `applicantLocationRequirements`; `baseSalary`; `directApply`; `employmentType`; `identifier`; `jobLocationType`; `validThrough` |

A `description` vai em HTML, com o texto completo da vaga: atividades, requisitos e benefícios.

## Modelo de JSON-LD para copiar

```json
{
  "@context": "https://schema.org",
  "@type": "JobPosting",
  "title": "Analista de Marketing Pleno",
  "description": "<p>Vaga para planejar e executar campanhas de geração de demanda.</p><p><strong>Requisitos:</strong> experiência com CRM e automação de marketing.</p>",
  "datePosted": "2026-11-09",
  "hiringOrganization": {
    "@type": "Organization",
    "name": "Exemplo",
    "sameAs": "https://www.exemplo.com.br/",
    "logo": "https://www.exemplo.com.br/imagens/logo.png"
  },
  "jobLocation": {
    "@type": "Place",
    "address": {
      "@type": "PostalAddress",
      "streetAddress": "Avenida Exemplo, 1000",
      "addressLocality": "São Paulo",
      "addressRegion": "SP",
      "postalCode": "01000-000",
      "addressCountry": "BR"
    }
  }
}
```

Cole dentro de uma tag `<script type="application/ld+json">` na página da vaga.

## Modelo completo com salário e regime

```json
{
  "@context": "https://schema.org",
  "@type": "JobPosting",
  "title": "Analista de Marketing Pleno",
  "description": "<p>Vaga para planejar e executar campanhas de geração de demanda.</p><p><strong>Requisitos:</strong> experiência com CRM e automação de marketing.</p><p><strong>Benefícios:</strong> plano de saúde e vale-refeição.</p>",
  "identifier": {
    "@type": "PropertyValue",
    "name": "Exemplo",
    "value": "MKT-2026-031"
  },
  "datePosted": "2026-11-09",
  "validThrough": "2026-12-09T23:59:00-03:00",
  "employmentType": "FULL_TIME",
  "hiringOrganization": {
    "@type": "Organization",
    "name": "Exemplo",
    "sameAs": "https://www.exemplo.com.br/",
    "logo": "https://www.exemplo.com.br/imagens/logo.png"
  },
  "jobLocation": {
    "@type": "Place",
    "address": {
      "@type": "PostalAddress",
      "streetAddress": "Avenida Exemplo, 1000",
      "addressLocality": "São Paulo",
      "addressRegion": "SP",
      "postalCode": "01000-000",
      "addressCountry": "BR"
    }
  },
  "baseSalary": {
    "@type": "MonetaryAmount",
    "currency": "BRL",
    "value": {
      "@type": "QuantitativeValue",
      "minValue": 6000,
      "maxValue": 7500,
      "unitText": "MONTH"
    }
  },
  "directApply": true
}
```

As datas do exemplo são ilustrativas: use a data real de publicação e de encerramento da vaga. Os valores de `employmentType` são fixos e em inglês: `FULL_TIME`, `PART_TIME`, `CONTRACTOR`, `TEMPORARY`, `INTERN`, `VOLUNTEER`, `PER_DIEM` e `OTHER`. Estágio usa `INTERN`; contratação como pessoa jurídica costuma usar `CONTRACTOR`. `directApply` é `true` só quando a candidatura é feita no próprio site, sem redirecionar para outra plataforma.

## Modelo de vaga remota

Vaga 100% remota usa `jobLocationType` com `TELECOMMUTE`, diz isso com clareza na descrição e informa em `applicantLocationRequirements` de que país, no mínimo um, o candidato pode trabalhar.

```json
{
  "@context": "https://schema.org",
  "@type": "JobPosting",
  "title": "Desenvolvedora Back-end Sênior (remoto)",
  "description": "<p>Trabalho remoto para candidatos residentes no Brasil.</p>",
  "datePosted": "2026-11-09",
  "hiringOrganization": {
    "@type": "Organization",
    "name": "Exemplo",
    "sameAs": "https://www.exemplo.com.br/"
  },
  "jobLocationType": "TELECOMMUTE",
  "applicantLocationRequirements": {
    "@type": "Country",
    "name": "Brasil"
  }
}
```

Vaga híbrida marca o endereço do escritório em `jobLocation`, como no modelo completo.

## Como validar o schema JobPosting?

1. Antes de publicar, cole o código ou a URL no [Teste de pesquisa aprimorada](https://search.google.com/test/rich-results), do Google: ele diz se a marcação está elegível e aponta erros e avisos.
2. Confira o vocabulário no [Schema Markup Validator](https://validator.schema.org/), do schema.org, que valida também propriedades que o Google não usa.
3. Depois de publicar, acompanhe os [relatórios de resultados aprimorados do Search Console](https://support.google.com/webmasters/answer/7552505?hl=pt-BR) e use a Inspeção de URL para confirmar que o Google encontrou a marcação.

## O que o schema JobPosting vale para as IAs?

Médio: cargo, local, regime e prazo declarados.

Cargo, cidade, modalidade e faixa salarial são as primeiras coisas que um candidato pergunta a um assistente. A vaga marcada, com o texto completo na página, é a fonte mais direta para essa resposta, e o `validThrough` evita que vaga encerrada continue sendo indicada.

## Perguntas frequentes

<details>
<summary><strong>Preciso informar o salário?</strong></summary>

Não é obrigatório para o Google; `baseSalary` é recomendado. Se o salário aparece na página, vale marcar.
</details>

<details>
<summary><strong>O que fazer quando a vaga é preenchida?</strong></summary>

Tirar a página do ar (resposta 404 ou 410), remover a marcação ou colocar o `validThrough` no passado. A documentação avisa que demorar a tratar vaga expirada pode gerar ação manual.
</details>

<details>
<summary><strong>Plataformas de recrutamento já marcam a vaga?</strong></summary>

As principais plataformas de recrutamento costumam gerar a marcação na página da vaga que hospedam. Se a vaga está no seu site, a marcação é sua.
</details>

**Ver também na Base de Conhecimento da TRIWI:** [Schema Markup e Dados Estruturados para SEO](https://github.com/TRIWI-SEO/SEO-IA/blob/main/seo-tecnico/schema-markup-e-dados-estruturados-para-seo.md), [Dados Estruturados para IA: Schema Markup na Era Generativa](https://github.com/TRIWI-SEO/SEO-IA/blob/main/geo-seo-para-ia/dados-estruturados-para-ia-schema-markup-na-era-generativa.md).

**Na TRIWI:** [Gerador de dados estruturados](https://triwi.com.br/ferramentas/gerador-de-dados-estruturados/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=jobposting-vagas), [Guia de SEO Técnico, capítulo Dados estruturados](https://triwi.com.br/guias/seo-tecnico/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=jobposting-vagas#dados-estruturados), [Guia de GEO: Otimização para IAs](https://triwi.com.br/guias/geo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=jobposting-vagas), [Atualizações do Google](https://triwi.com.br/atualizacoes/google/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=jobposting-vagas).

**Ver também no Glossário de SEO da TRIWI:** [Dados estruturados](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=jobposting-vagas#seo-dados-estruturados), [Schema.org](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=jobposting-vagas#seo-schema-org), [JSON-LD](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=jobposting-vagas#seo-json-ld).

[Voltar para a biblioteca completa](../README.md)

---

<p align="center">
  <strong>Quer que sua marca seja a resposta, no Google e nas IAs?</strong><br>
  <a href="https://triwi.com.br/contato/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=jobposting-vagas">Que tal um café com a TRIWI?</a>
</p>

<p align="center">
  <sub>Biblioteca publicada e mantida pela equipe da TRIWI, agência 100% especializada em SEO e Otimização para IAs.</sub>
</p>
