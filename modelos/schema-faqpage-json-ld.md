# Schema FAQPage em JSON-LD: modelo e o que mudou em 2026

**O resultado enriquecido de perguntas frequentes saiu da Pesquisa Google em 07/05/2026, e a documentação foi removida em 15/06/2026. O FAQPage segue válido no schema.org, mas não gera mais nada no Google. O que continua valendo, para o Google e para as IAs, são a pergunta e a resposta escritas no texto visível da página.**

*Por equipe de SEO da TRIWI, com revisão de Ricardo Martins, fundador. Publicado em 09/11/2026. Atualizado em 09/11/2026. Campos conferidos na documentação do Google Search Central e no schema.org (versão 30.1) em 09/11/2026.*

> **Situação no Google em 09/11/2026: Descontinuado.** Nada: o resultado de perguntas frequentes saiu da Pesquisa Google. Última mudança registrada: 07/05/2026. Desde 14/09/2023 aparecia só para sites de governo e de saúde reconhecidos. Saiu da Pesquisa em 07/05/2026 e a documentação foi removida em 15/06/2026. Fonte: [registro oficial de mudanças do Google](https://developers.google.com/search/updates).

## Índice

- [O que aconteceu com o FAQ no Google?](#o-que-aconteceu-com-o-faq-no-google)
- [Devo remover o schema FAQPage do site?](#devo-remover-o-schema-faqpage-do-site)
- [Modelo de JSON-LD para copiar](#modelo-de-json-ld-para-copiar)
- [Como escrever perguntas frequentes que as IAs aproveitam?](#como-escrever-perguntas-frequentes-que-as-ias-aproveitam)
- [Qual a diferença entre FAQPage e QAPage?](#qual-a-diferença-entre-faqpage-e-qapage)
- [Como validar o schema FAQPage?](#como-validar-o-schema-faqpage)
- [Perguntas frequentes](#perguntas-frequentes)

## O que aconteceu com o FAQ no Google?

| Data | Mudança | Fonte |
|:---|:---|:---|
| 14/09/2023 | O resultado de FAQ passa a aparecer só para sites de governo e de saúde reconhecidos | [Registro de mudanças do Google](https://developers.google.com/search/updates) |
| 08/05/2026 | Aviso de retirada na documentação: o FAQ deixa de aparecer na Pesquisa a partir de 07/05/2026 | [Registro de mudanças do Google](https://developers.google.com/search/updates) |
| 15/06/2026 | Documentação do resultado de FAQ removida | [Registro de mudanças do Google](https://developers.google.com/search/updates) |

Na prática, para a maioria dos sites o FAQ já tinha sumido dos resultados em 2023. Em 2026 ele saiu para todos os sites.

## Devo remover o schema FAQPage do site?

Não há urgência. A marcação não gera mais resultado no Google, e o Google não anunciou penalidade para quem a mantém. A decisão prática:

| Situação | O que fazer |
|:---|:---|
| FAQ marcado e com as perguntas visíveis na página | Pode manter; não ajuda no Google, e o código é pequeno |
| FAQ marcado com perguntas que não aparecem na página | Remover: marcação de conteúdo invisível contraria as diretrizes de dados estruturados |
| Plugin gerando FAQPage em toda página, inclusive sem FAQ | Desligar o recurso no plugin |
| Página nova | Escrever as perguntas no texto; a marcação é opcional |

O que não deve sair são as perguntas e respostas do texto, se elas respondem ao que o leitor procura.

## Modelo de JSON-LD para copiar

Para quem quer manter a marcação pelo vocabulário do schema.org. Cada pergunta da marcação precisa estar visível na página, com a mesma resposta.

```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "Quanto tempo leva a entrega para o Nordeste?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "De 5 a 9 dias úteis depois da confirmação do pagamento, conforme a cidade."
      }
    },
    {
      "@type": "Question",
      "name": "Posso trocar um produto usado?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "A troca vale para produtos sem sinais de uso, em até 7 dias após o recebimento."
      }
    }
  ]
}
```

Se a página for, por exemplo, um artigo, o mais útil é marcar o [Article](../modelos/schema-article-json-ld.md) e deixar as perguntas como texto.

## Como escrever perguntas frequentes que as IAs aproveitam?

Alto, no texto: pergunta e resposta visíveis na página continuam fáceis de extrair para quem lê e para a IA; a marcação vira opcional.

O Google diz, no [guia de otimização para IA da Pesquisa](https://developers.google.com/search/docs/fundamentals/ai-optimization-guide?hl=pt-br), que nenhuma marcação especial é necessária para aparecer nos recursos de IA. O que faz uma pergunta frequente ser aproveitada é o texto:

| Regra | Exemplo |
|:---|:---|
| Pergunta escrita como o cliente pergunta | "Quanto tempo leva a entrega para o Nordeste?", não "Prazos" |
| Resposta logo abaixo da pergunta, completa na primeira frase | "De 5 a 9 dias úteis..." antes de qualquer explicação |
| Uma pergunta por tema | Nada de juntar troca, devolução e garantia numa resposta só |
| Dado concreto e verificável | Prazo, condição, documento, sem promessa vaga |
| Pergunta em título (H2, H3 ou `summary`) | A estrutura da página separa uma pergunta da outra |

O tema está no [Guia de Conteúdo para SEO e IA](https://triwi.com.br/guias/conteudo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=faqpage) e no guia aberto [Conteúdo Citável](https://github.com/TRIWI-SEO/SEO-IA/blob/main/geo-seo-para-ia/conteudo-citavel-como-escrever-para-ser-referenciado-por-llms.md).

## Qual a diferença entre FAQPage e QAPage?

| | FAQPage | QAPage |
|:---|:---|:---|
| Quem responde | O próprio site | Usuários |
| Quantas perguntas | Várias | Uma pergunta principal |
| Situação no Google | Sem resultado desde 07/05/2026 | Ativo |
| Exemplo | Página de dúvidas da loja | Tópico de fórum, página de suporte da comunidade |

A documentação do QAPage exclui expressamente o FAQ escrito pelo próprio site. Trocar FAQPage por QAPage para recuperar o resultado contraria as diretrizes.

## Como validar o schema FAQPage?

1. Cole o código ou a URL no [Schema Markup Validator](https://validator.schema.org/), do schema.org, que confere a sintaxe e o vocabulário de qualquer tipo.
2. Não espere aviso no [Teste de pesquisa aprimorada](https://search.google.com/test/rich-results) nem relatório no Search Console: o Google não gera mais resultado enriquecido para este tipo.
3. Confira se a pergunta, a resposta ou o passo marcados aparecem no texto visível da página.

## Perguntas frequentes

<details>
<summary><strong>O FAQ ainda aparece no Google para sites de governo e de saúde?</strong></summary>

Não. A restrição a governo e saúde valia desde 2023; em 07/05/2026 o resultado de FAQ saiu da Pesquisa para todos os sites.
</details>

<details>
<summary><strong>Manter o FAQPage prejudica o site?</strong></summary>

O Google não anunciou penalidade para a marcação mantida. O que continua proibido é marcar conteúdo que não aparece na página.
</details>

<details>
<summary><strong>As IAs leem o schema FAQPage?</strong></summary>

As empresas de IA não documentam o uso de JSON-LD. O Google diz que marcação não é necessária para os recursos de IA. O que todas leem é o texto da página, e é nele que a pergunta e a resposta precisam estar.
</details>

**Ver também na Base de Conhecimento da TRIWI:** [Schema Markup e Dados Estruturados para SEO](https://github.com/TRIWI-SEO/SEO-IA/blob/main/seo-tecnico/schema-markup-e-dados-estruturados-para-seo.md), [Dados Estruturados para IA: Schema Markup na Era Generativa](https://github.com/TRIWI-SEO/SEO-IA/blob/main/geo-seo-para-ia/dados-estruturados-para-ia-schema-markup-na-era-generativa.md).

**Na TRIWI:** [Gerador de dados estruturados](https://triwi.com.br/ferramentas/gerador-de-dados-estruturados/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=faqpage), [Guia de SEO Técnico, capítulo Dados estruturados](https://triwi.com.br/guias/seo-tecnico/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=faqpage#dados-estruturados), [Guia de GEO: Otimização para IAs](https://triwi.com.br/guias/geo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=faqpage), [Atualizações do Google](https://triwi.com.br/atualizacoes/google/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=faqpage).

**Ver também no Glossário de SEO da TRIWI:** [Dados estruturados](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=faqpage#seo-dados-estruturados), [Rich results](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=faqpage#seo-rich-results), [AI Overviews](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=faqpage#seo-ai-overviews), [Schema.org](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=faqpage#seo-schema-org).

[Voltar para a biblioteca completa](../README.md)

---

<p align="center">
  <strong>Quer que sua marca seja a resposta, no Google e nas IAs?</strong><br>
  <a href="https://triwi.com.br/contato/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=faqpage">Que tal um café com a TRIWI?</a>
</p>

<p align="center">
  <sub>Biblioteca publicada e mantida pela equipe da TRIWI, agência 100% especializada em SEO e Otimização para IAs.</sub>
</p>
