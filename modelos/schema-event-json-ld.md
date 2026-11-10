# Schema Event em JSON-LD: modelo pronto para copiar

**O schema Event marca um evento presencial com nome, data, local e ingresso, para ele aparecer na experiência de eventos do Google, disponível no Brasil em português. Exige `name`, `startDate`, `location` e o endereço do local. Desde 05/06/2025 o Google aceita só eventos presenciais e abertos ao público.**

*Por equipe de SEO da TRIWI, com revisão de Ricardo Martins, fundador. Publicado em 09/11/2026. Atualizado em 09/11/2026. Campos conferidos na documentação do Google Search Central e no schema.org (versão 30.1) em 09/11/2026.*

> **Situação no Google em 09/11/2026: Ativo.** Eventos com data e local na experiência de eventos do Google, disponível no Brasil em português. Última mudança registrada: 05/06/2025. Só eventos presenciais e abertos ao público; as propriedades de evento online saíram em 05/06/2025. Fonte: [documentação oficial do Google](https://developers.google.com/search/docs/appearance/structured-data/event).

## Índice

- [Quando usar o schema Event?](#quando-usar-o-schema-event)
- [Quais campos o Google exige e recomenda?](#quais-campos-o-google-exige-e-recomenda)
- [Modelo de JSON-LD para copiar](#modelo-de-json-ld-para-copiar)
- [Modelo completo com ingresso e organizador](#modelo-completo-com-ingresso-e-organizador)
- [Como marcar evento adiado ou cancelado?](#como-marcar-evento-adiado-ou-cancelado)
- [Como validar o schema Event?](#como-validar-o-schema-event)
- [O que o schema Event vale para as IAs?](#o-que-o-schema-event-vale-para-as-ias)
- [Perguntas frequentes](#perguntas-frequentes)

## Quando usar o schema Event?

Em página de evento presencial que qualquer pessoa pode frequentar ou comprar ingresso: show, feira, congresso, curso presencial com data marcada, palestra aberta. Webinar e evento só online não são mais aceitos pelo Google, e evento que exige convite ou associação antes da compra do ingresso também fica de fora. Cada evento precisa de uma página própria, com URL única.

## Quais campos o Google exige e recomenda?

**Evento** (Event), segundo a [documentação do Google](https://developers.google.com/search/docs/appearance/structured-data/event); o tipo no vocabulário está em [schema.org/Event](https://schema.org/Event):

| Exigência | Campos |
|:---|:---|
| Obrigatórios | `location`; `location.address`; `name`; `startDate` |
| Recomendados | `description`; `endDate`; `eventStatus`; `image`; `location.name`; `offers`; `offers.availability`; `offers.price`; `offers.priceCurrency`; `offers.url`; `offers.validFrom`; `organizer`; `organizer.name`; `organizer.url`; `performer`; `performer.name`; `previousStartDate` |

## Modelo de JSON-LD para copiar

```json
{
  "@context": "https://schema.org",
  "@type": "Event",
  "name": "Congresso Exemplo de Gestão em Saúde",
  "startDate": "2027-03-18T09:00:00-03:00",
  "endDate": "2027-03-19T18:00:00-03:00",
  "location": {
    "@type": "Place",
    "name": "Centro de Convenções Exemplo",
    "address": {
      "@type": "PostalAddress",
      "streetAddress": "Avenida Exemplo, 500",
      "addressLocality": "São Paulo",
      "addressRegion": "SP",
      "postalCode": "01000-000",
      "addressCountry": "BR"
    }
  }
}
```

Cole dentro de uma tag `<script type="application/ld+json">` na página do evento. Use um tipo mais específico quando existir, como `BusinessEvent`, `EducationEvent` ou `MusicEvent`.

## Modelo completo com ingresso e organizador

```json
{
  "@context": "https://schema.org",
  "@type": "BusinessEvent",
  "name": "Congresso Exemplo de Gestão em Saúde",
  "description": "Dois dias de palestras sobre gestão de clínicas, faturamento de convênios e tecnologia em saúde.",
  "image": [
    "https://www.exemplo.com.br/imagens/congresso-1x1.jpg",
    "https://www.exemplo.com.br/imagens/congresso-4x3.jpg",
    "https://www.exemplo.com.br/imagens/congresso-16x9.jpg"
  ],
  "startDate": "2027-03-18T09:00:00-03:00",
  "endDate": "2027-03-19T18:00:00-03:00",
  "eventStatus": "https://schema.org/EventScheduled",
  "location": {
    "@type": "Place",
    "name": "Centro de Convenções Exemplo",
    "address": {
      "@type": "PostalAddress",
      "streetAddress": "Avenida Exemplo, 500",
      "addressLocality": "São Paulo",
      "addressRegion": "SP",
      "postalCode": "01000-000",
      "addressCountry": "BR"
    }
  },
  "offers": {
    "@type": "Offer",
    "url": "https://www.exemplo.com.br/congresso/ingressos/",
    "price": 450.00,
    "priceCurrency": "BRL",
    "availability": "https://schema.org/InStock",
    "validFrom": "2026-11-09T00:00:00-03:00"
  },
  "organizer": {
    "@type": "Organization",
    "name": "Exemplo Eventos",
    "url": "https://www.exemplo.com.br/"
  },
  "performer": {
    "@type": "Person",
    "name": "Nome do Palestrante"
  }
}
```

As datas do exemplo são ilustrativas: troque pelas datas reais do evento, com o fuso horário. Evento gratuito usa `"price": 0`. Evento de vários dias leva `startDate` e `endDate`; apresentações em dias diferentes, cada uma com o próprio ingresso, ganham um `Event` para cada data.

## Como marcar evento adiado ou cancelado?

Não apague a página nem a marcação: mude o `eventStatus`.

| Situação | `eventStatus` | O que mais muda |
|:---|:---|:---|
| Confirmado | `EventScheduled` | Nada |
| Adiado sem nova data | `EventPostponed` | Mantenha a `startDate` original até ter a nova data |
| Remarcado | `EventRescheduled` | `startDate` e `endDate` novas; a data antiga pode ir em `previousStartDate` |
| Cancelado | `EventCancelled` | Mantenha as datas originais |

## Como validar o schema Event?

1. Antes de publicar, cole o código ou a URL no [Teste de pesquisa aprimorada](https://search.google.com/test/rich-results), do Google: ele diz se a marcação está elegível e aponta erros e avisos.
2. Confira o vocabulário no [Schema Markup Validator](https://validator.schema.org/), do schema.org, que valida também propriedades que o Google não usa.
3. Depois de publicar, acompanhe os [relatórios de resultados aprimorados do Search Console](https://support.google.com/webmasters/answer/7552505?hl=pt-BR) e use a Inspeção de URL para confirmar que o Google encontrou a marcação.

## O que o schema Event vale para as IAs?

Médio: data, local e status do evento sem ambiguidade.

Perguntas como "que eventos de gestão em saúde acontecem em São Paulo em março" dependem de data, cidade e status certos. A marcação entrega esses dados sem que o sistema precise interpretar um banner, e o `eventStatus` atualizado evita que um evento cancelado continue sendo recomendado.

## Perguntas frequentes

<details>
<summary><strong>Webinar pode usar o schema Event?</strong></summary>

Pode usar o tipo no schema.org, mas não aparece mais na experiência de eventos do Google: desde 05/06/2025 a documentação exige local físico e removeu as propriedades de evento online.
</details>

<details>
<summary><strong>Evento híbrido entra?</strong></summary>

Entra pela parte presencial: marque o local físico em `location`. O que o Google deixou de aceitar foi o evento sem nenhum componente presencial.
</details>

<details>
<summary><strong>Página que lista vários eventos marca todos?</strong></summary>

Não. A documentação exige que cada evento tenha a própria página, com URL única e a marcação nela, e diz que a experiência de eventos do Google só aceita páginas focadas em um evento. A agenda que lista os eventos fica sem a marcação.
</details>

**Ver também na Base de Conhecimento da TRIWI:** [Schema Markup e Dados Estruturados para SEO](https://github.com/TRIWI-SEO/SEO-IA/blob/main/seo-tecnico/schema-markup-e-dados-estruturados-para-seo.md), [Dados Estruturados para IA: Schema Markup na Era Generativa](https://github.com/TRIWI-SEO/SEO-IA/blob/main/geo-seo-para-ia/dados-estruturados-para-ia-schema-markup-na-era-generativa.md).

**Na TRIWI:** [Gerador de dados estruturados](https://triwi.com.br/ferramentas/gerador-de-dados-estruturados/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=event), [Guia de SEO Técnico, capítulo Dados estruturados](https://triwi.com.br/guias/seo-tecnico/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=event#dados-estruturados), [Guia de GEO: Otimização para IAs](https://triwi.com.br/guias/geo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=event), [Atualizações do Google](https://triwi.com.br/atualizacoes/google/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=event).

**Ver também no Glossário de SEO da TRIWI:** [Dados estruturados](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=event#seo-dados-estruturados), [Schema.org](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=event#seo-schema-org), [JSON-LD](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=event#seo-json-ld).

[Voltar para a biblioteca completa](../README.md)

---

<p align="center">
  <strong>Quer que sua marca seja a resposta, no Google e nas IAs?</strong><br>
  <a href="https://triwi.com.br/contato/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=event">Que tal um café com a TRIWI?</a>
</p>

<p align="center">
  <sub>Biblioteca publicada e mantida pela equipe da TRIWI, agência 100% especializada em SEO e Otimização para IAs.</sub>
</p>
