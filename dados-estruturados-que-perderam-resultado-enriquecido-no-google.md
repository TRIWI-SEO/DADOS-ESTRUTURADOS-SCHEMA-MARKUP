# Dados estruturados que perderam o resultado enriquecido no Google, e o que continua valendo para as IAs

**Desde 2023 o Google tirou da Pesquisa 10 resultados enriquecidos, do How-to, em 2023, ao FAQ, em maio de 2026. A lista completa, com data e fonte, está abaixo. O vocabulário do schema.org segue válido. Para as IAs, vale o conteúdo visível; a marcação é reforço.**

*Por equipe de SEO da TRIWI, com revisão de Ricardo Martins, fundador. Publicado em 09/11/2026. Atualizado em 09/11/2026. Campos conferidos na documentação do Google Search Central e no schema.org (versão 30.1) em 09/11/2026.*

## Índice

- [Quais resultados enriquecidos saíram do Google?](#quais-resultados-enriquecidos-saíram-do-google)
- [Quais tipos continuam, mas com restrição?](#quais-tipos-continuam-mas-com-restrição)
- [O que continua valendo para as IAs?](#o-que-continua-valendo-para-as-ias)
- [O que fazer com a marcação antiga?](#o-que-fazer-com-a-marcação-antiga)
- [Modelo de HowTo, para quem quer manter](#modelo-de-howto-para-quem-quer-manter)
- [Quais tipos continuam gerando resultado no Google?](#quais-tipos-continuam-gerando-resultado-no-google)
- [Perguntas frequentes](#perguntas-frequentes)

## Quais resultados enriquecidos saíram do Google?

São 10 recursos, do mais recente para o mais antigo. As datas vêm do [registro oficial de mudanças da documentação do Google Search Central](https://developers.google.com/search/updates), conferido em 09/11/2026.

| Recurso no Google | Tipo schema.org | Saiu em | O que mudou | Para as IAs |
|:---|:---|:---|:---|:---|
| [Perguntas frequentes (FAQ)](https://developers.google.com/search/updates) | FAQPage; Question; Answer | 07/05/2026 | Desde 14/09/2023 aparecia só para sites de governo e de saúde reconhecidos. Saiu da Pesquisa em 07/05/2026 e a documentação foi removida em 15/06/2026 | Alto, no texto: pergunta e resposta visíveis na página continuam fáceis de extrair para quem lê e para a IA; a marcação vira opcional |
| [Problemas de prática](https://developers.google.com/search/updates) | Quiz | 06/01/2026 | Aviso de retirada em 05/11/2025; documentação removida em 06/01/2026 | Baixo: os exercícios seguem úteis como texto; a marcação não tem uso documentado fora do recurso |
| [Informações do curso](https://developers.google.com/search/updates) | Course; CourseInstance | 09/09/2025 | Aviso de retirada em 12/06/2025; documentação removida em 09/09/2025 | Médio: modalidade, carga horária e instituição seguem úteis como texto visível na página do curso |
| [Salário estimado](https://developers.google.com/search/updates) | Occupation | 09/09/2025 | Aviso de retirada em 12/06/2025; documentação removida em 09/09/2025 | Baixo: faixa salarial estimada por terceiros; o salário real da vaga vai em JobPosting com baseSalary |
| [Vídeo educacional](https://developers.google.com/search/updates) | VideoObject; LearningResource | 09/09/2025 | Aviso de retirada em 12/06/2025; documentação removida em 09/09/2025 | Médio: assunto e nível de ensino do vídeo seguem úteis como texto visível na página |
| [Anúncio de veículo](https://developers.google.com/search/updates) | Car; Vehicle | 09/09/2025 | Aviso de retirada em 12/06/2025; documentação removida em 09/09/2025 | Médio: marca, modelo, ano e quilometragem seguem úteis como texto visível no anúncio |
| [Anúncio especial](https://developers.google.com/search/updates) | SpecialAnnouncement | 31/07/2025 | Retirada anunciada em 23/04/2025, efetiva em 31/07/2025; documentação removida em 09/09/2025 | Baixo: avisos temporários, criados para a pandemia, sem informação durável sobre a marca |
| [Caixa de pesquisa de sitelinks](https://developers.google.com/search/updates) | WebSite; SearchAction | 29/11/2024 | Documentação removida em 29/11/2024 | Baixo: descrevia só a busca interna do site; o nome oficial da marca vai no WebSite, que segue ativo |
| [Atividades em casa](https://developers.google.com/search/updates) | Event; VideoObject | 11/06/2024 | Documentação removida em 11/06/2024 | Baixo: atividades online datadas, criadas para a pandemia, sem informação durável sobre a marca |
| [Instruções passo a passo (How-to)](https://developers.google.com/search/updates) | HowTo | 14/09/2023 | Documentação removida em 14/09/2023 | Médio, no texto: passos numerados visíveis continuam úteis para quem lê e para a IA |

O movimento tem nome no próprio Google: em junho de 2025 ele anunciou a [simplificação da página de resultados](https://developers.google.com/search/blog/2025/06/simplifying-search-results) e, em novembro de 2025, publicou uma [atualização desse esforço](https://developers.google.com/search/blog/2025/11/update-on-our-efforts). Saem recursos pouco usados; os que descrevem a entidade, o produto e o conteúdo seguem ativos.

## Quais tipos continuam, mas com restrição?

Não saíram, mas aparecem só para alguns sites, idiomas ou parceiros, ou estão em retirada.

| Recurso no Google | Tipo schema.org | Situação | Restrição | Para as IAs |
|:---|:---|:---|:---|:---|
| [Lista de cursos](https://developers.google.com/search/docs/appearance/structured-data/course) | Course; ItemList | Ativo com restrição | Disponível só em inglês. Exige pelo menos três cursos marcados e a marcação de carrossel | Médio: nome, descrição e instituição de cada curso declarados |
| [Carrossel](https://developers.google.com/search/docs/appearance/structured-data/carousel) | ItemList; ListItem | Ativo com restrição | Só funciona combinado com Lista de cursos, Filme, Receita ou Restaurante; todos os itens da lista precisam ser do mesmo tipo | Baixo: só funciona combinado com os tipos aceitos |
| [Filme](https://developers.google.com/search/docs/appearance/structured-data/movie) | Movie | Ativo com restrição | Aparece só no celular, combinado com a marcação de carrossel | Baixo: nicho de sites de cinema |
| [Leitura em voz (Speakable)](https://developers.google.com/search/docs/appearance/structured-data/speakable) | SpeakableSpecification | Ativo com restrição | Em beta | Baixo: marca trechos para leitura em voz, sem uso documentado fora do Google Assistente |
| [Aluguel por temporada](https://developers.google.com/search/docs/appearance/structured-data/vacation-rental) | VacationRental; Accommodation | Ativo com restrição | Exige contato com gerente técnico do Google e acesso ao Hotel Center | Baixo: o imóvel se descreve melhor pelo texto da página; o recurso depende de parceria com o Google |
| [Ações de livro](https://developers.google.com/search/docs/appearance/structured-data/book) | Book | Ativo com restrição | Chegou a ter aviso de retirada em 12/06/2025, retirado em 05/11/2025 porque um recurso da busca ainda usa a marcação. Funciona por feed para parceiros | Baixo: o livro se descreve melhor pelo texto da página; o recurso depende de feed de parceiro |
| [Conjunto de dados](https://developers.google.com/search/docs/appearance/structured-data/dataset) | Dataset; DataDownload; DataCatalog | Em retirada | Em 05/11/2025 o Google esclareceu que Dataset é usado só pelo Dataset Search e anunciou a retirada da Pesquisa Google. A description deve ter de 50 a 5000 caracteres | Médio: descreve bases abertas com licença e criador, o que ajuda quem cita dados |
| [Checagem de fatos](https://developers.google.com/search/docs/appearance/structured-data/factcheck) | ClaimReview | Em retirada | A documentação do Google traz o aviso de retirada da Pesquisa e diz que a marcação continua aceita no Fact Check Explorer | Médio: declara a afirmação checada, quem checou e o veredito, dados úteis para quem verifica fatos |

## O que continua valendo para as IAs?

A resposta curta está no [guia de otimização para IA da Pesquisa Google](https://developers.google.com/search/docs/fundamentals/ai-optimization-guide?hl=pt-br): dados estruturados não são exigidos para aparecer nos recursos de IA, não existe marcação especial para isso, e vale continuar usando como parte do SEO. As empresas de IA, como OpenAI, Anthropic e Perplexity, não publicam como usam JSON-LD.

A leitura da TRIWI, a partir disso:

| O que | Para o Google | Para as IAs |
|:---|:---|:---|
| Pergunta e resposta escritas na página | Conteúdo comum, ranqueia como qualquer texto | É o formato mais fácil de extrair e citar |
| Passo a passo em lista numerada | Conteúdo comum | Fácil de reaproveitar como instrução |
| Marcação FAQPage ou HowTo | Ignorada para resultado enriquecido | Reforço opcional do que já está no texto |
| Organization, Article com autor, Product, LocalBusiness | Seguem ativos | Declaram entidade, autoria, valor e endereço sem ambiguidade |

O que perdeu o resultado no Google não perdeu o valor do conteúdo. Uma boa seção de perguntas frequentes continua respondendo o leitor e sendo extraída; só deixou de ganhar espaço extra na página de resultados. O método está no [Guia de GEO: Otimização para IAs](https://triwi.com.br/guias/geo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=dados-estruturados-que-perderam-resultado-enriquecido-no-google) e no guia aberto [Dados Estruturados para IA](https://github.com/TRIWI-SEO/SEO-IA/blob/main/geo-seo-para-ia/dados-estruturados-para-ia-schema-markup-na-era-generativa.md).

## O que fazer com a marcação antiga?

| Marcação antiga | Decisão recomendada |
|:---|:---|
| FAQPage com perguntas visíveis | Pode manter; ver [Schema FAQPage](modelos/schema-faqpage-json-ld.md#devo-remover-o-schema-faqpage-do-site) |
| FAQPage ou HowTo com conteúdo que não aparece na página | Remover |
| `SearchAction` no WebSite | Pode sair; o `WebSite` com `name` e `url` fica, ver [Schema WebSite](modelos/schema-website-nome-do-site-json-ld.md) |
| `Course` com `CourseInstance` | Fica como descrição; o carrossel de [lista de cursos](modelos/schema-course-cursos-json-ld.md) usa só `Course` e `ItemList` |
| `VideoObject` com `LearningResource` | O `VideoObject` fica e segue gerando resultado de vídeo, ver [Schema VideoObject](modelos/schema-videoobject-json-ld.md) |
| `SpecialAnnouncement`, `Occupation` de salário estimado, `Car` de anúncio | Pode sair sem efeito no Google |
| `ClaimReview` | Manter se o site faz checagem de fatos: segue aceito no Fact Check Explorer |

Antes de remover qualquer coisa, confira se o mesmo bloco não carrega outra marcação ainda ativa, como o `Organization` dentro de um `@graph`.

## Modelo de HowTo, para quem quer manter

O HowTo não gera resultado no Google desde 14/09/2023. O tipo segue válido no schema.org e descreve um tutorial com material e passos.

```json
{
  "@context": "https://schema.org",
  "@type": "HowTo",
  "name": "Como trocar o refil do filtro de água",
  "totalTime": "PT5M",
  "supply": [
    {"@type": "HowToSupply", "name": "Refil compatível"}
  ],
  "step": [
    {"@type": "HowToStep", "position": 1, "text": "Feche o registro de água."},
    {"@type": "HowToStep", "position": 2, "text": "Gire o refil antigo no sentido anti-horário e retire."},
    {"@type": "HowToStep", "position": 3, "text": "Encaixe o refil novo, gire no sentido horário e abra o registro."}
  ]
}
```

Mais útil do que a marcação é o passo a passo escrito como lista numerada na página, que vale para quem lê e para qualquer sistema que extraia o conteúdo.

## Quais tipos continuam gerando resultado no Google?

25 recursos seguem ativos sem restrição relevante, entre eles Organization, LocalBusiness, Product, Article, BreadcrumbList, nome do site, avaliações, vídeo, evento e vaga. A lista com o que cada um gera no Google está em [Quais dados estruturados o Google ainda usa](README.md#quais-dados-estruturados-o-google-ainda-usa), na página principal desta biblioteca.

A base completa, com campos obrigatórios e recomendados de cada um, está em [dados/tipos-de-dados-estruturados.csv](dados/tipos-de-dados-estruturados.csv).

## Perguntas frequentes

<details>
<summary><strong>Por que o Google tirou o FAQ e o How-to dos resultados?</strong></summary>

O Google ligou as retiradas de 2025 ao esforço de simplificar a página de resultados, tirando recursos pouco usados. O FAQ saiu em 2026 sem post explicativo, só com o aviso no registro de mudanças, e já estava restrito a sites de governo e de saúde desde 2023.
</details>

<details>
<summary><strong>Marcação de tipo descontinuado gera erro no Search Console?</strong></summary>

No caso dos problemas de prática, o registro de mudanças do Google anunciou junto com a retirada o fim do suporte nos relatórios do Search Console e no Teste de pesquisa aprimorada. A marcação continua sendo JSON-LD válido para o schema.org e pode ser conferida no [Schema Markup Validator](https://validator.schema.org/).
</details>

<details>
<summary><strong>Dados estruturados ainda valem a pena?</strong></summary>

Sim, para os tipos que descrevem a empresa, o produto, o conteúdo e o endereço, que seguem ativos no Google e reforçam a identificação da marca. O erro é investir em marcação de recurso que já saiu, esperando resultado que não vem mais.
</details>

<details>
<summary><strong>Onde acompanhar as próximas mudanças?</strong></summary>

No [registro de mudanças da documentação do Google](https://developers.google.com/search/updates) e nas [Atualizações do Google da TRIWI](https://triwi.com.br/atualizacoes/google/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=dados-estruturados-que-perderam-resultado-enriquecido-no-google), linha do tempo datada com a fonte oficial de cada mudança e o que ela significa para empresas.
</details>

**Ver também na Base de Conhecimento da TRIWI:** [Schema Markup e Dados Estruturados para SEO](https://github.com/TRIWI-SEO/SEO-IA/blob/main/seo-tecnico/schema-markup-e-dados-estruturados-para-seo.md), [Dados Estruturados para IA: Schema Markup na Era Generativa](https://github.com/TRIWI-SEO/SEO-IA/blob/main/geo-seo-para-ia/dados-estruturados-para-ia-schema-markup-na-era-generativa.md).

**Na TRIWI:** [Gerador de dados estruturados](https://triwi.com.br/ferramentas/gerador-de-dados-estruturados/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=dados-estruturados-que-perderam-resultado-enriquecido-no-google), [Guia de SEO Técnico, capítulo Dados estruturados](https://triwi.com.br/guias/seo-tecnico/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=dados-estruturados-que-perderam-resultado-enriquecido-no-google#dados-estruturados), [Guia de GEO: Otimização para IAs](https://triwi.com.br/guias/geo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=dados-estruturados-que-perderam-resultado-enriquecido-no-google), [Atualizações do Google](https://triwi.com.br/atualizacoes/google/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=dados-estruturados-que-perderam-resultado-enriquecido-no-google).

**Ver também no Glossário de SEO da TRIWI:** [Dados estruturados](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=dados-estruturados-que-perderam-resultado-enriquecido-no-google#seo-dados-estruturados), [Rich results](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=dados-estruturados-que-perderam-resultado-enriquecido-no-google#seo-rich-results), [AI Overviews](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=dados-estruturados-que-perderam-resultado-enriquecido-no-google#seo-ai-overviews), [Schema.org](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=dados-estruturados-que-perderam-resultado-enriquecido-no-google#seo-schema-org), [JSON-LD](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=dados-estruturados-que-perderam-resultado-enriquecido-no-google#seo-json-ld).

[Voltar para a biblioteca completa](README.md)

---

<p align="center">
  <strong>Quer que sua marca seja a resposta, no Google e nas IAs?</strong><br>
  <a href="https://triwi.com.br/contato/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=dados-estruturados-que-perderam-resultado-enriquecido-no-google">Que tal um café com a TRIWI?</a>
</p>

<p align="center">
  <sub>Biblioteca publicada e mantida pela equipe da TRIWI, agência 100% especializada em SEO e Otimização para IAs.</sub>
</p>
