# Schema VideoObject em JSON-LD: modelo pronto para copiar

**O schema VideoObject descreve um vídeo publicado na página: título, miniatura, data de envio, duração e descrição, e pode marcar os momentos-chave. Exige `name`, `thumbnailUrl` e `uploadDate`. O vídeo educacional, variação com nível de ensino, saiu do Google em 2025; o VideoObject segue ativo.**

*Por equipe de SEO da TRIWI, com revisão de Ricardo Martins, fundador. Publicado em 09/11/2026. Atualizado em 09/11/2026. Campos conferidos na documentação do Google Search Central e no schema.org (versão 30.1) em 09/11/2026.*

> **Situação no Google em 09/11/2026: Ativo.** Miniatura, duração, data e momentos-chave do vídeo nos resultados e na aba Vídeos. Última mudança registrada: 24/09/2026. Momentos-chave: Clip exige name, startOffset e url; SeekToAction exige potentialAction, startOffset-input e target. creator entrou em 24/09/2026. Fonte: [documentação oficial do Google](https://developers.google.com/search/docs/appearance/structured-data/video).

## Índice

- [Quando usar o schema VideoObject?](#quando-usar-o-schema-videoobject)
- [Quais campos o Google exige e recomenda?](#quais-campos-o-google-exige-e-recomenda)
- [Modelo de JSON-LD para copiar](#modelo-de-json-ld-para-copiar)
- [Modelo completo com momentos-chave](#modelo-completo-com-momentos-chave)
- [Como validar o schema VideoObject?](#como-validar-o-schema-videoobject)
- [O que o schema VideoObject vale para as IAs?](#o-que-o-schema-videoobject-vale-para-as-ias)
- [Perguntas frequentes](#perguntas-frequentes)

## Quando usar o schema VideoObject?

Na página do seu site em que o vídeo é o conteúdo principal ou um conteúdo importante: aula, demonstração de produto, depoimento, tutorial. O vídeo pode estar hospedado no próprio site ou incorporado de uma plataforma como o YouTube; o que se marca é a página do seu site que mostra o vídeo.

## Quais campos o Google exige e recomenda?

**Vídeo** (VideoObject; Clip; SeekToAction), segundo a [documentação do Google](https://developers.google.com/search/docs/appearance/structured-data/video); o tipo no vocabulário está em [schema.org/VideoObject](https://schema.org/VideoObject):

| Exigência | Campos |
|:---|:---|
| Obrigatórios | `name`; `thumbnailUrl`; `uploadDate` |
| Recomendados | `contentUrl`; `creator` (ou `author`); `description`; `duration`; `embedUrl`; `expires`; `hasPart`; `ineligibleRegion`; `interactionStatistic`; `publication`; `regionsAllowed` |

## Modelo de JSON-LD para copiar

```json
{
  "@context": "https://schema.org",
  "@type": "VideoObject",
  "name": "Como configurar a agenda online da clínica",
  "description": "Passo a passo para abrir horários, bloquear feriados e enviar lembretes aos pacientes.",
  "thumbnailUrl": "https://www.exemplo.com.br/imagens/video-agenda-16x9.jpg",
  "uploadDate": "2026-11-09T10:00:00-03:00",
  "duration": "PT6M30S",
  "embedUrl": "https://www.youtube.com/embed/CODIGO_DO_VIDEO"
}
```

Cole dentro de uma tag `<script type="application/ld+json">` na página que mostra o vídeo. A duração vai em ISO 8601: `PT6M30S` são 6 minutos e 30 segundos.

## Modelo completo com momentos-chave

Os momentos-chave podem ser marcados à mão com `Clip`, um por trecho, cada um com nome, início e a URL que abre o vídeo naquele ponto.

```json
{
  "@context": "https://schema.org",
  "@type": "VideoObject",
  "name": "Como configurar a agenda online da clínica",
  "description": "Passo a passo para abrir horários, bloquear feriados e enviar lembretes aos pacientes.",
  "thumbnailUrl": [
    "https://www.exemplo.com.br/imagens/video-agenda-1x1.jpg",
    "https://www.exemplo.com.br/imagens/video-agenda-4x3.jpg",
    "https://www.exemplo.com.br/imagens/video-agenda-16x9.jpg"
  ],
  "uploadDate": "2026-11-09T10:00:00-03:00",
  "duration": "PT6M30S",
  "contentUrl": "https://www.exemplo.com.br/videos/agenda-online.mp4",
  "embedUrl": "https://www.exemplo.com.br/videos/player/agenda-online",
  "inLanguage": "pt-BR",
  "creator": {
    "@type": "Organization",
    "name": "Exemplo",
    "url": "https://www.exemplo.com.br/"
  },
  "interactionStatistic": {
    "@type": "InteractionCounter",
    "interactionType": {"@type": "WatchAction"},
    "userInteractionCount": 1520
  },
  "hasPart": [
    {
      "@type": "Clip",
      "name": "Abrir horários",
      "startOffset": 15,
      "endOffset": 140,
      "url": "https://www.exemplo.com.br/tutoriais/agenda-online?t=15"
    },
    {
      "@type": "Clip",
      "name": "Bloquear feriados",
      "startOffset": 140,
      "endOffset": 260,
      "url": "https://www.exemplo.com.br/tutoriais/agenda-online?t=140"
    },
    {
      "@type": "Clip",
      "name": "Enviar lembretes",
      "startOffset": 260,
      "endOffset": 390,
      "url": "https://www.exemplo.com.br/tutoriais/agenda-online?t=260"
    }
  ]
}
```

`startOffset` e `endOffset` são segundos desde o início do vídeo. A alternativa ao `Clip` é o `SeekToAction`, que deixa o Google identificar os trechos sozinho a partir de um modelo de URL. O `creator` foi incluído na documentação em 24/09/2026; o `author` continua aceito.

## Como validar o schema VideoObject?

1. Antes de publicar, cole o código ou a URL no [Teste de pesquisa aprimorada](https://search.google.com/test/rich-results), do Google: ele diz se a marcação está elegível e aponta erros e avisos.
2. Confira o vocabulário no [Schema Markup Validator](https://validator.schema.org/), do schema.org, que valida também propriedades que o Google não usa.
3. Depois de publicar, acompanhe os [relatórios de resultados aprimorados do Search Console](https://support.google.com/webmasters/answer/7552505?hl=pt-BR) e use a Inspeção de URL para confirmar que o Google encontrou a marcação.

O relatório de Indexação de vídeo do Search Console mostra se o Google encontrou o vídeo como conteúdo principal da página.

## O que o schema VideoObject vale para as IAs?

Médio: título, duração e descrição do vídeo declarados para quem não assiste.

Um sistema que não assiste ao vídeo depende do que está escrito sobre ele. Título, descrição, duração, data e trechos nomeados dizem do que o vídeo trata e em que ponto está cada resposta. A transcrição publicada na página faz o resto.

## Perguntas frequentes

<details>
<summary><strong>Vídeo do YouTube incorporado no site precisa de marcação?</strong></summary>

O YouTube marca o vídeo na página dele. Se você quer que a página do seu site também seja encontrada pelo vídeo, marque a sua página, com o `embedUrl` do player.
</details>

<details>
<summary><strong>O que aconteceu com o vídeo educacional?</strong></summary>

O resultado de vídeo educacional, que usava `LearningResource` junto com `VideoObject`, saiu da Pesquisa Google, e a documentação foi removida em 09/09/2025. A marcação de vídeo comum continua ativa. A lista do que saiu está em [O que perdeu o resultado enriquecido no Google](../dados-estruturados-que-perderam-resultado-enriquecido-no-google.md).
</details>

<details>
<summary><strong>Preciso marcar vídeo curto, de rede social?</strong></summary>

Se ele está na sua página e é parte importante dela, sim. A marcação é a mesma para qualquer duração.
</details>

**Ver também na Base de Conhecimento da TRIWI:** [Schema Markup e Dados Estruturados para SEO](https://github.com/TRIWI-SEO/SEO-IA/blob/main/seo-tecnico/schema-markup-e-dados-estruturados-para-seo.md), [Dados Estruturados para IA: Schema Markup na Era Generativa](https://github.com/TRIWI-SEO/SEO-IA/blob/main/geo-seo-para-ia/dados-estruturados-para-ia-schema-markup-na-era-generativa.md).

**Na TRIWI:** [Gerador de dados estruturados](https://triwi.com.br/ferramentas/gerador-de-dados-estruturados/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=videoobject), [Guia de SEO Técnico, capítulo Dados estruturados](https://triwi.com.br/guias/seo-tecnico/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=videoobject#dados-estruturados), [Guia de GEO: Otimização para IAs](https://triwi.com.br/guias/geo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=videoobject), [Atualizações do Google](https://triwi.com.br/atualizacoes/google/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=videoobject).

**Ver também no Glossário de SEO da TRIWI:** [Dados estruturados](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=videoobject#seo-dados-estruturados), [Schema.org](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=videoobject#seo-schema-org), [JSON-LD](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=videoobject#seo-json-ld).

[Voltar para a biblioteca completa](../README.md)

---

<p align="center">
  <strong>Quer que sua marca seja a resposta, no Google e nas IAs?</strong><br>
  <a href="https://triwi.com.br/contato/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=videoobject">Que tal um café com a TRIWI?</a>
</p>

<p align="center">
  <sub>Biblioteca publicada e mantida pela equipe da TRIWI, agência 100% especializada em SEO e Otimização para IAs.</sub>
</p>
