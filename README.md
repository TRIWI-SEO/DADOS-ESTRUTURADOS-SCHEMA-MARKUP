<p align="center">
  <img src="assets/logo-triwi.svg" alt="TRIWI, agência de SEO e Otimização para IAs" height="72">
</p>

<h1 align="center">Dados Estruturados e Schema Markup: modelos de JSON-LD em português, pela TRIWI</h1>

<p align="center">
  <strong>15 modelos de JSON-LD prontos para copiar, por tipo de página e de negócio,<br>
  com os campos que o Google exige, o que perdeu o resultado enriquecido e o que continua valendo para as IAs.</strong>
</p>

<p align="center">
  <a href="https://triwi.com.br/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=readme"><img src="https://img.shields.io/badge/mantido%20pela-TRIWI-FF03ED?style=flat-square" alt="Mantido pela TRIWI"></a>
  <img src="https://img.shields.io/badge/modelos-15-30363d?style=flat-square" alt="15 modelos de JSON-LD">
  <img src="https://img.shields.io/badge/tipos%20mapeados-43-30363d?style=flat-square" alt="43 tipos de dados estruturados mapeados">
  <img src="https://img.shields.io/github/last-commit/TRIWI-SEO/DADOS-ESTRUTURADOS-SCHEMA-MARKUP?style=flat-square&label=atualizado&color=30363d" alt="Última atualização">
  <a href="LICENSE"><img src="https://img.shields.io/badge/licen%C3%A7a-CC%20BY%204.0-30363d?style=flat-square" alt="Licença CC BY 4.0"></a>
  <img src="https://img.shields.io/badge/idioma-portugu%C3%AAs-30363d?style=flat-square" alt="Conteúdo em português">
</p>

<p align="center">
  <sub>Atualizado em 09/11/2026</sub>
</p>

<p align="center">
  <a href="#modelos-de-json-ld-prontos-para-copiar">Modelos</a>
  &nbsp;|&nbsp;
  <a href="dados-estruturados-por-tipo-de-negocio.md">Por tipo de negócio</a>
  &nbsp;|&nbsp;
  <a href="dados-estruturados-que-perderam-resultado-enriquecido-no-google.md">O que saiu do Google</a>
  &nbsp;|&nbsp;
  <a href="https://triwi.com.br/ferramentas/gerador-de-dados-estruturados/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=readme">Gerador da TRIWI</a>
  &nbsp;|&nbsp;
  <a href="https://triwi.com.br/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=readme">triwi.com.br</a>
</p>

---

## O que é esta biblioteca?

**Dados estruturados são um código, em geral JSON-LD com o vocabulário do schema.org, que descreve a página para buscadores e IAs: quem é a empresa, qual o produto, quem escreveu o artigo. Esta biblioteca da TRIWI reúne modelos prontos para copiar, com os campos conferidos na documentação do Google e o que ainda gera resultado.**

São 15 modelos, cada um com quando usar, campos obrigatórios e recomendados, código básico e completo, como validar e erros comuns, e uma base aberta com 43 tipos de dados estruturados do Google: 25 ativos, 8 ativos com restrição ou em retirada e 10 que perderam o resultado enriquecido. Campos conferidos em 09/11/2026 na documentação do Google Search Central e no schema.org (versão 30.1).

## Quem publica esta biblioteca?

A [TRIWI](https://triwi.com.br/sobre-a-triwi/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=readme) é a agência brasileira 100% especializada em SEO e Otimização para IAs (SEO + GEO) e uma das referências do setor no país. Fundada em 2018 por Ricardo Martins, trabalha com metodologia própria de 12 etapas e mais de 300 atividades. Contato Seguro, Sem Parar, Valid, Flexdoc e Polishop estão entre as marcas atendidas pela TRIWI.

Quem procura um modelo de schema em português encontra trechos soltos, desatualizados e, muitas vezes, com tipos que o Google já não usa, como o FAQ, que saiu da Pesquisa em maio de 2026. A documentação oficial é boa, mas está em inglês na maior parte, espalhada por dezenas de páginas e com exemplos de outros países.

Esta biblioteca resolve isso num lugar só: modelos com endereço, telefone, moeda e CNPJ no padrão brasileiro, a situação de cada tipo no Google com data e fonte, e a leitura do que cada marcação vale para as IAs. Ela complementa três recursos gratuitos da TRIWI:

| Recurso | Para que serve |
|:---|:---|
| [Schema Markup e Dados Estruturados para SEO](https://github.com/TRIWI-SEO/SEO-IA/blob/main/seo-tecnico/schema-markup-e-dados-estruturados-para-seo.md) e [Dados Estruturados para IA](https://github.com/TRIWI-SEO/SEO-IA/blob/main/geo-seo-para-ia/dados-estruturados-para-ia-schema-markup-na-era-generativa.md), na [Base de Conhecimento de SEO e GEO](https://github.com/TRIWI-SEO/SEO-IA) | Explicam o que são dados estruturados e por que importam para o Google e para as IAs |
| [Guia de SEO Técnico](https://triwi.com.br/guias/seo-tecnico/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=readme#dados-estruturados) | Põe os dados estruturados no contexto do SEO técnico: rastreamento, indexação, arquitetura e velocidade |
| [Gerador de dados estruturados](https://triwi.com.br/ferramentas/gerador-de-dados-estruturados/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=readme) | Monta o código de Organization, LocalBusiness, Article e BreadcrumbList por formulário, sem cadastro |

## Índice

- [O que é esta biblioteca](#o-que-é-esta-biblioteca)
- [Quem publica](#quem-publica-esta-biblioteca)
- [Modelos de JSON-LD prontos para copiar](#modelos-de-json-ld-prontos-para-copiar)
- [Guias desta biblioteca](#guias-desta-biblioteca)
- [Como usar um modelo](#como-usar-um-modelo)
- [Como instalar o JSON-LD no seu site](#como-instalar-o-json-ld-no-seu-site)
- [Quais dados estruturados o Google ainda usa](#quais-dados-estruturados-o-google-ainda-usa)
- [O que perdeu o resultado enriquecido](#o-que-perdeu-o-resultado-enriquecido)
- [Como validar dados estruturados](#como-validar-dados-estruturados)
- [O que os dados estruturados valem para as IAs](#o-que-os-dados-estruturados-valem-para-as-ias)
- [Dados abertos](#dados-abertos)
- [Fontes e metodologia](#fontes-e-metodologia)
- [Perguntas frequentes](#perguntas-frequentes)
- [Como citar](#como-citar)

## Modelos de JSON-LD prontos para copiar

| Modelo | Quando usar | Situação no Google |
|:---|:---|:---|
| [Organization e OnlineStore](modelos/schema-organization-json-ld.md) | Identidade da empresa ou da loja online: nome, logo, CNPJ, contato, perfis, frete, devolução e programa de fidelidade | Ativo |
| [LocalBusiness](modelos/schema-local-business-json-ld.md) | Empresa com endereço físico: clínica, loja, restaurante, escritório | Ativo |
| [Product](modelos/schema-product-json-ld.md) | Página de produto: valor, valor de membro, estoque, avaliação, variantes, frete e devolução | Ativo |
| [Article e BlogPosting](modelos/schema-article-json-ld.md) | Artigo, post de blog ou notícia, com autor e datas | Ativo |
| [BreadcrumbList](modelos/schema-breadcrumblist-json-ld.md) | Trilha de navegação de qualquer página interna | Ativo |
| [WebSite](modelos/schema-website-nome-do-site-json-ld.md) | Nome do site nos resultados, na página inicial | Ativo |
| [Review e AggregateRating](modelos/schema-review-aggregaterating-json-ld.md) | Avaliações e nota média, com as regras que evitam penalidade | Ativo |
| [ProfilePage e Person](modelos/schema-profilepage-person-autor-json-ld.md) | Página de autor ou de especialista | Ativo |
| [Event](modelos/schema-event-json-ld.md) | Evento presencial com data, local e ingresso | Ativo |
| [JobPosting](modelos/schema-jobposting-vagas-json-ld.md) | Vaga de emprego na página de carreiras | Ativo |
| [VideoObject](modelos/schema-videoobject-json-ld.md) | Vídeo na página, com miniatura, duração e momentos-chave | Ativo |
| [SoftwareApplication](modelos/schema-softwareapplication-json-ld.md) | Aplicativo, software ou SaaS | Ativo |
| [Course e Quiz](modelos/schema-course-cursos-json-ld.md) | Lista de cursos de uma instituição e flashcards educacionais | Ativo; Ativo com restrição |
| [Recipe](modelos/schema-recipe-receita-json-ld.md) | Receita com ingredientes, passos e tempos | Ativo |
| [FAQPage](modelos/schema-faqpage-json-ld.md) | Perguntas frequentes: sem resultado enriquecido no Google desde 07/05/2026 | Descontinuado |

## Guias desta biblioteca

| Página | O que resolve |
|:---|:---|
| [Dados estruturados por tipo de negócio](dados-estruturados-por-tipo-de-negocio.md) | Quais tipos usar em e-commerce, negócio local, B2B, SaaS, blog, educação, eventos e vagas, com o código combinado de cada caso |
| [O que perdeu o resultado enriquecido no Google](dados-estruturados-que-perderam-resultado-enriquecido-no-google.md) | FAQ, How-to, caixa de pesquisa e outros tipos que saíram da Pesquisa Google, com data, e o que continua valendo para as IAs |

## Como usar um modelo?

1. Escolha o modelo do tipo de página: produto, artigo, empresa, unidade, vaga.
2. Copie o código e troque cada valor de exemplo (`exemplo.com.br`, nomes, endereço, telefone, valores e datas) pelos dados reais, os mesmos que aparecem na página. As datas dos modelos são ilustrativas.
3. Apague as propriedades que você não tem como preencher com verdade. Campo vazio ou inventado é pior do que campo ausente.
4. Cole o código dentro de uma tag de script, no `<head>` ou no `<body>` da página:

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "Exemplo",
  "url": "https://www.exemplo.com.br/"
}
</script>
```

5. Valide antes de publicar, como explicado em [Como validar dados estruturados](#como-validar-dados-estruturados).

A regra que vale para todos os modelos: a marcação descreve o que está visível na página. O Google pede isso nas [diretrizes gerais de dados estruturados](https://developers.google.com/search/docs/appearance/structured-data/sd-policies?hl=pt-br), e marcação de conteúdo invisível ou enganoso pode gerar ação manual, que tira a página dos resultados enriquecidos.

## Como instalar o JSON-LD no seu site?

O código é o mesmo em qualquer plataforma; o que muda é onde colar. Antes de colar, passe uma página no [Teste de pesquisa aprimorada](https://search.google.com/test/rich-results) para ver o que o site já gera: plugins, temas e plataformas de loja costumam criar parte da marcação sozinhos, e duas versões da mesma entidade com dados diferentes confundem quem lê.

| Onde o site roda | Onde colar | Cuidado |
|:---|:---|:---|
| WordPress | O plugin de SEO gera a base (Organization, WebSite, Article, BreadcrumbList); tipos extras vão num campo de código do cabeçalho ou num plugin de inserção de código | Desligue no plugin o tipo que você for colar à mão, para não duplicar |
| Shopify | No código do tema, nos arquivos da página de produto ou do layout | Muitos temas já trazem a marcação de produto; ajuste a existente em vez de colar outra |
| VTEX, Nuvemshop e outras plataformas de loja | Na área de código do tema ou da loja, conforme a plataforma | Confira o Product que a plataforma já gera e complete o que falta, como frete, devolução e GTIN |
| Google Tag Manager | Numa tag de HTML personalizado com o script | O Google lê JSON-LD inserido por JavaScript, mas pede o Product no HTML inicial; use para tipos de identidade, não para produto |
| Site próprio | No template de cada tipo de página, gerado pelo mesmo banco de dados que monta a página | É o jeito que mantém valor, estoque e datas sempre iguais aos da página |

As particularidades de SEO de cada plataforma de loja estão nas páginas da TRIWI [SEO para VTEX](https://triwi.com.br/seo-para-ecommerce/vtex/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=readme), [SEO para Shopify](https://triwi.com.br/seo-para-ecommerce/shopify/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=readme), [SEO para Nuvemshop](https://triwi.com.br/seo-para-ecommerce/nuvemshop/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=readme) e [SEO para WooCommerce](https://triwi.com.br/seo-para-ecommerce/woocommerce/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=readme).

## Quais dados estruturados o Google ainda usa?

25 recursos de dados estruturados seguem ativos na Pesquisa Google, segundo a [galeria oficial](https://developers.google.com/search/docs/appearance/structured-data/search-gallery?hl=pt-br) e as páginas de cada recurso, conferidas em 09/11/2026. O Google não garante o resultado enriquecido nem com a marcação perfeita: ela torna a página elegível.

| Recurso no Google | Tipo schema.org | O que aparece | Para as IAs | Modelo |
|:---|:---|:---|:---|:---|
| [Organização](https://developers.google.com/search/docs/appearance/structured-data/organization) | Organization; OnlineStore | Ajuda o Google a escolher o logo e os dados do painel de conhecimento da empresa e a diferenciá-la de outras com nome parecido | Alto: declara quem é a empresa, com nome, logo, CNPJ e perfis oficiais, a base para a IA não confundir a marca com outra | [ver modelo](modelos/schema-organization-json-ld.md) |
| [Empresa local](https://developers.google.com/search/docs/appearance/structured-data/local-business) | LocalBusiness e subtipos (Restaurant, Dentist, Store e outros) | Dados da empresa, como horário, endereço e telefone, em resultados de busca local | Alto: endereço, horário e telefone declarados de forma inequívoca, iguais aos do Perfil da Empresa no Google | [ver modelo](modelos/schema-local-business-json-ld.md) |
| [Produto (trecho de produto)](https://developers.google.com/search/docs/appearance/structured-data/product-snippet) | Product; Offer; AggregateRating; Review | Nota, avaliações, valor e disponibilidade abaixo do resultado; prós e contras em páginas de análise editorial | Alto: valor, disponibilidade e avaliação declarados sem depender de interpretar o texto | [ver modelo](modelos/schema-product-json-ld.md) |
| [Produto (listagem do comerciante)](https://developers.google.com/search/docs/appearance/structured-data/merchant-listing) | Product; Offer | Valor, frete, devolução e disponibilidade em resultados de compra, painéis de produto e Google Imagens | Alto: é a ficha do produto que agentes de compra e assistentes leem para comparar ofertas | [ver modelo](modelos/schema-product-json-ld.md) |
| [Variantes de produto](https://developers.google.com/search/docs/appearance/structured-data/product-variants) | ProductGroup; Product | Agrupa variantes (cor, tamanho) do mesmo produto nos resultados de compra | Médio: evita que cada cor ou tamanho pareça um produto diferente | [ver modelo](modelos/schema-product-json-ld.md) |
| [Política de devolução](https://developers.google.com/search/docs/appearance/structured-data/return-policy) | MerchantReturnPolicy | Condições de devolução junto do produto e no painel do comerciante | Médio: responde a pergunta de compra que o assistente faz antes de recomendar uma loja | [ver modelo](modelos/schema-product-json-ld.md) |
| [Política de frete](https://developers.google.com/search/docs/appearance/structured-data/shipping-policy) | ShippingService (em Organization.hasShippingService) | Condições de frete da loja nos resultados de compra | Médio: prazo e custo de entrega declarados para comparação | [ver modelo](modelos/schema-organization-json-ld.md) |
| [Programa de fidelidade](https://developers.google.com/search/docs/appearance/structured-data/loyalty-program) | MemberProgram; MemberProgramTier | Benefícios e valores de membro junto da oferta; disponível no Brasil | Baixo: útil só para varejo com programa de pontos ou clube | [ver modelo](modelos/schema-organization-json-ld.md) |
| [Artigo](https://developers.google.com/search/docs/appearance/structured-data/article) | Article; NewsArticle; BlogPosting | Ajuda o Google a mostrar o título, a imagem e a data certos do artigo | Alto: autoria e datas declaradas, os sinais de quem escreveu e de quando que a IA usa para escolher a fonte | [ver modelo](modelos/schema-article-json-ld.md) |
| [Trilha de navegação](https://developers.google.com/search/docs/appearance/structured-data/breadcrumb) | BreadcrumbList; ListItem | A trilha de navegação no lugar do endereço da página, só nos resultados no computador | Médio: mostra onde a página está na hierarquia do site | [ver modelo](modelos/schema-breadcrumblist-json-ld.md) |
| [Nome do site](https://developers.google.com/search/docs/appearance/site-names) | WebSite | O nome do site mostrado acima do título nos resultados | Médio: fixa o nome oficial da marca e as variações aceitas | [ver modelo](modelos/schema-website-nome-do-site-json-ld.md) |
| [Trecho de avaliação](https://developers.google.com/search/docs/appearance/structured-data/review-snippet) | Review; AggregateRating | Estrelas e nota abaixo do resultado | Médio: a nota só vale se as avaliações estiverem visíveis e forem reais | [ver modelo](modelos/schema-review-aggregaterating-json-ld.md) |
| [Evento](https://developers.google.com/search/docs/appearance/structured-data/event) | Event | Eventos com data e local na experiência de eventos do Google, disponível no Brasil em português | Médio: data, local e status do evento sem ambiguidade | [ver modelo](modelos/schema-event-json-ld.md) |
| [Vaga de emprego](https://developers.google.com/search/docs/appearance/structured-data/job-posting) | JobPosting | A vaga na experiência de vagas de emprego do Google, disponível na América Latina | Médio: cargo, local, regime e prazo declarados | [ver modelo](modelos/schema-jobposting-vagas-json-ld.md) |
| [Avaliação agregada do empregador](https://developers.google.com/search/docs/appearance/structured-data/employer-rating) | EmployerAggregateRating | Nota da empresa como empregadora na experiência de vagas | Baixo: nicho de sites de avaliação de empregadores |  |
| [Vídeo](https://developers.google.com/search/docs/appearance/structured-data/video) | VideoObject; Clip; SeekToAction | Miniatura, duração, data e momentos-chave do vídeo nos resultados e na aba Vídeos | Médio: título, duração e descrição do vídeo declarados para quem não assiste | [ver modelo](modelos/schema-videoobject-json-ld.md) |
| [Receita](https://developers.google.com/search/docs/appearance/structured-data/recipe) | Recipe | Imagem, nota, tempo de preparo e calorias da receita, inclusive em carrossel | Médio: ingredientes, passos e tempos em formato que qualquer assistente lê | [ver modelo](modelos/schema-recipe-receita-json-ld.md) |
| [Aplicativo de software](https://developers.google.com/search/docs/appearance/structured-data/software-app) | SoftwareApplication; MobileApplication; WebApplication | Nota, valor e sistema do aplicativo abaixo do resultado | Médio: categoria, plataforma e modelo de acesso do software declarados | [ver modelo](modelos/schema-softwareapplication-json-ld.md) |
| [Página de perfil](https://developers.google.com/search/docs/appearance/structured-data/profile-page) | ProfilePage; Person; Organization | Ajuda o Google a identificar o autor ou o usuário por trás do conteúdo, em fóruns e sites sociais | Alto: a página de autor com credencial e perfis externos é o que liga o conteúdo a uma pessoa real | [ver modelo](modelos/schema-profilepage-person-autor-json-ld.md) |
| [Fórum de discussão](https://developers.google.com/search/docs/appearance/structured-data/discussion-forum) | DiscussionForumPosting; SocialMediaPosting | Conversas de fórum nos resultados de fóruns | Médio: separa autor, data e resposta em discussões de usuários |  |
| [Página de perguntas e respostas](https://developers.google.com/search/docs/appearance/structured-data/qapage) | QAPage; Question; Answer | A pergunta e as respostas de usuários em destaque no resultado | Médio: só para páginas em que usuários enviam respostas |  |
| [Perguntas educacionais (flashcards)](https://developers.google.com/search/docs/appearance/structured-data/education-qa) | Quiz; Question; Answer | Carrossel de flashcards em buscas educacionais, com suporte a português | Baixo: nicho de sites de estudo | [ver modelo](modelos/schema-course-cursos-json-ld.md) |
| [Resolvedor de matemática](https://developers.google.com/search/docs/appearance/structured-data/math-solvers) | MathSolver; LearningResource | Ferramenta de resolver expressões matemáticas em destaque | Baixo: nicho de ferramentas educacionais |  |
| [Metadados de imagem](https://developers.google.com/search/docs/appearance/structured-data/image-license-metadata) | ImageObject | Autor, crédito e selo de licença da imagem no Google Imagens | Baixo: útil para quem licencia imagens |  |
| [Conteúdo com assinatura (paywall)](https://developers.google.com/search/docs/appearance/structured-data/paywalled-content) | CreativeWork e subtipos (Article, NewsArticle e outros) | Não gera visual próprio: separa conteúdo com paywall de cloaking | Médio: declara o que é fechado para assinantes |  |

Outros 8 seguem ativos com restrição de idioma, país, dispositivo ou parceiro, ou estão em retirada; a lista está em [O que perdeu o resultado enriquecido no Google](dados-estruturados-que-perderam-resultado-enriquecido-no-google.md#quais-tipos-continuam-mas-com-restrição).

## O que perdeu o resultado enriquecido?

Desde 2023, 10 recursos saíram da Pesquisa Google, do mais recente para o mais antigo:

| Recurso no Google | Saiu em | O que fica para as IAs |
|:---|:---|:---|
| Perguntas frequentes (FAQ) | 07/05/2026 | Alto, no texto: pergunta e resposta visíveis na página continuam fáceis de extrair para quem lê e para a IA; a marcação vira opcional. Ver [modelo](modelos/schema-faqpage-json-ld.md). |
| Problemas de prática | 06/01/2026 | Baixo: os exercícios seguem úteis como texto; a marcação não tem uso documentado fora do recurso. |
| Informações do curso | 09/09/2025 | Médio: modalidade, carga horária e instituição seguem úteis como texto visível na página do curso. Ver [modelo](modelos/schema-course-cursos-json-ld.md). |
| Salário estimado | 09/09/2025 | Baixo: faixa salarial estimada por terceiros; o salário real da vaga vai em JobPosting com baseSalary. |
| Vídeo educacional | 09/09/2025 | Médio: assunto e nível de ensino do vídeo seguem úteis como texto visível na página. Ver [modelo](modelos/schema-videoobject-json-ld.md). |
| Anúncio de veículo | 09/09/2025 | Médio: marca, modelo, ano e quilometragem seguem úteis como texto visível no anúncio. |
| Anúncio especial | 31/07/2025 | Baixo: avisos temporários, criados para a pandemia, sem informação durável sobre a marca. |
| Caixa de pesquisa de sitelinks | 29/11/2024 | Baixo: descrevia só a busca interna do site; o nome oficial da marca vai no WebSite, que segue ativo. Ver [modelo](modelos/schema-website-nome-do-site-json-ld.md). |
| Atividades em casa | 11/06/2024 | Baixo: atividades online datadas, criadas para a pandemia, sem informação durável sobre a marca. |
| Instruções passo a passo (How-to) | 14/09/2023 | Médio, no texto: passos numerados visíveis continuam úteis para quem lê e para a IA. Ver [modelo](dados-estruturados-que-perderam-resultado-enriquecido-no-google.md). |

A tabela completa, com fonte de cada data e o que fazer com a marcação antiga, está em [Dados estruturados que perderam o resultado enriquecido no Google](dados-estruturados-que-perderam-resultado-enriquecido-no-google.md).

## Como validar dados estruturados?

| Ferramenta | Para que serve | Quando usar |
|:---|:---|:---|
| [Teste de pesquisa aprimorada](https://search.google.com/test/rich-results) | Diz se a marcação está elegível aos resultados do Google, com erros e avisos | Antes de publicar, para os tipos ativos no Google |
| [Schema Markup Validator](https://validator.schema.org/) | Confere sintaxe e vocabulário de qualquer tipo do schema.org | Para todos os tipos, inclusive os que o Google não usa |
| [Relatórios do Search Console](https://support.google.com/webmasters/answer/7552505?hl=pt-BR) | Mostram páginas válidas e com erro em todo o site | Depois de publicar, acompanhamento mensal |
| Inspeção de URL do Search Console | Confirma que o Google leu a marcação de uma página | Depois de publicar ou alterar |
| [Gerador de dados estruturados da TRIWI](https://triwi.com.br/ferramentas/gerador-de-dados-estruturados/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=readme) | Monta Organization, LocalBusiness, Article e BreadcrumbList por formulário | Antes de tudo, para quem não quer editar código |

## O que os dados estruturados valem para as IAs?

O Google diz, no [guia de otimização para IA da Pesquisa](https://developers.google.com/search/docs/fundamentals/ai-optimization-guide?hl=pt-br), que dados estruturados não são exigidos para os recursos de IA, que não existe marcação especial para eles e que vale continuar usando como parte do SEO. As empresas de IA não documentam como usam JSON-LD.

A leitura da TRIWI: a marcação não faz uma marca ser citada sozinha, mas tira a ambiguidade do que a página já diz. Organization, Article com autor, Product e LocalBusiness declaram entidade, autoria, valor e endereço de forma inequívoca, e isso ajuda qualquer sistema a ligar o conteúdo à empresa certa. O que decide a citação continua sendo o conteúdo visível, claro e verificável. Cada modelo desta biblioteca traz a avaliação do tipo para as IAs, e a coluna `para_ias` da [base aberta](dados/tipos-de-dados-estruturados.csv) reúne todas. O método completo está no [Guia de GEO: Otimização para IAs](https://triwi.com.br/guias/geo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=readme).

## Dados abertos

| Arquivo | O que traz | Linhas |
|:---|:---|:---|
| [dados/tipos-de-dados-estruturados.csv](dados/tipos-de-dados-estruturados.csv) | Cada recurso de dados estruturados do Google com tipo schema.org, situação, data da última mudança, campos obrigatórios e recomendados, valor para as IAs, modelo e fonte oficial | 43 |

O significado de cada coluna e o formato do arquivo estão no [dicionário de dados](dados/dicionario-de-dados.md). Outras bases abertas da TRIWI, como o [glossário de SEO, marketing e IA](https://github.com/TRIWI-SEO/SEO-IA/blob/main/dados/glossario-triwi.csv) e as [atualizações do Google e das IAs](https://github.com/TRIWI-SEO/SEO-IA/blob/main/dados/atualizacoes-google-e-ias.csv), estão na Base de Conhecimento.

## Fontes e metodologia

| Fonte | O que traz |
|:---|:---|
| [Galeria de dados estruturados do Google](https://developers.google.com/search/docs/appearance/structured-data/search-gallery?hl=pt-br) | Os recursos ativos na Pesquisa Google e a página de cada um |
| [Registro de mudanças da documentação do Google](https://developers.google.com/search/updates) | Datas de inclusão, mudança e retirada de cada recurso |
| [Diretrizes gerais de dados estruturados](https://developers.google.com/search/docs/appearance/structured-data/sd-policies?hl=pt-br) | As regras que valem para toda marcação |
| [Schema.org](https://schema.org/) | O vocabulário: tipos, propriedades e valores |

| Critério | Como funciona |
|:---|:---|
| Campos obrigatórios e recomendados | Copiados da página de cada recurso no Google, com o nome exato da propriedade |
| Situação no Google | Ativo, ativo com restrição, em retirada ou descontinuado, com a data da última mudança registrada |
| Divergência | Quando o registro de mudanças e a página do recurso discordam, vale a página atual, e a divergência fica anotada na coluna `observacao` |
| Valor para as IAs | Avaliação da TRIWI, declarada como tal; as empresas de IA não documentam o uso de JSON-LD |
| Exemplos | Dados fictícios no padrão brasileiro; nenhum dado de empresa real |
| Revisão | Cada linha da base tem a data da última conferência; correções chegam por [issue](../../issues/new) |

Os modelos são informativos e não substituem a documentação oficial: em caso de divergência, vale a documentação do Google e do schema.org. A biblioteca não cobre resultados que dependem de cadastro de parceiro, como aluguel por temporada e ações de livro, além de listá-los na base.

## Perguntas frequentes

<details>
<summary><strong>O que são dados estruturados?</strong></summary>

São informações sobre a página escritas num formato padronizado, que buscadores e outros sistemas leem sem precisar interpretar o texto. O formato mais usado é o JSON-LD, com o vocabulário do [schema.org](https://schema.org/). A explicação completa está no guia aberto [Schema Markup e Dados Estruturados para SEO](https://github.com/TRIWI-SEO/SEO-IA/blob/main/seo-tecnico/schema-markup-e-dados-estruturados-para-seo.md).
</details>

<details>
<summary><strong>Qual a diferença entre schema markup, schema.org e JSON-LD?</strong></summary>

Schema.org é o vocabulário, com os tipos e as propriedades. JSON-LD é o formato em que o código é escrito. Schema markup é o nome comum para a marcação pronta na página. O Google aceita também Microdata e RDFa e recomenda o JSON-LD, por ser o mais fácil de manter.
</details>

<details>
<summary><strong>Dados estruturados melhoram a posição no Google?</strong></summary>

Não diretamente. John Mueller, do Google, disse em abril de 2025 que dados estruturados não fazem o site ranquear melhor ([Search Engine Journal](https://www.searchenginejournal.com/google-confirms-that-structured-data-wont-make-a-site-rank-better/544433/)). Eles tornam a página elegível a resultados enriquecidos, como estrelas, valor e trilha de navegação, que podem atrair mais cliques, e ajudam o Google a entender a página.
</details>

<details>
<summary><strong>Quais dados estruturados todo site deveria ter?</strong></summary>

[Organization](modelos/schema-organization-json-ld.md) e [WebSite](modelos/schema-website-nome-do-site-json-ld.md) na página inicial e [BreadcrumbList](modelos/schema-breadcrumblist-json-ld.md) nas páginas internas. O resto depende do negócio, como mostra [Dados estruturados por tipo de negócio](dados-estruturados-por-tipo-de-negocio.md).
</details>

<details>
<summary><strong>O schema FAQ ainda funciona?</strong></summary>

Não no Google: o resultado de perguntas frequentes saiu da Pesquisa em 07/05/2026. As perguntas e respostas continuam valendo como texto da página, para o leitor e para as IAs. Detalhes em [Schema FAQPage](modelos/schema-faqpage-json-ld.md).
</details>

<details>
<summary><strong>Onde colocar o código JSON-LD?</strong></summary>

Dentro de uma tag `<script type="application/ld+json">`, no `<head>` ou no `<body>` da página que ele descreve. O Google lê também marcação inserida por JavaScript, mas recomenda a de produto no HTML inicial.
</details>

<details>
<summary><strong>Existe ferramenta gratuita para gerar dados estruturados?</strong></summary>

Sim. O [Gerador de dados estruturados da TRIWI](https://triwi.com.br/ferramentas/gerador-de-dados-estruturados/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=readme) monta Organization, LocalBusiness, Article e BreadcrumbList por formulário, sem cadastro. Para os demais tipos, os modelos desta biblioteca. As outras [ferramentas gratuitas da TRIWI](https://triwi.com.br/ferramentas/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=readme) cobrem sitemap, robots.txt, hreflang e metatags sociais.
</details>

<details>
<summary><strong>Posso reutilizar estes modelos?</strong></summary>

Sim. Os modelos, os textos e a base de dados estão sob licença [CC BY 4.0](LICENSE): você pode copiar, adaptar e usar, inclusive comercialmente, desde que cite a TRIWI e este repositório como fonte. O formato sugerido está em [Como citar](#como-citar).
</details>

## Histórico de atualizações

| Data | O que mudou |
|:---|:---|
| 09/11/2026 | Programa de fidelidade e valor de membro nos modelos de Organization e Product; flashcards educacionais no modelo de Course; coluna schema_org na base; seção de instalação por plataforma; fonte oficial nas regras de horário, nome do site e trilha de navegação |
| 09/11/2026 | Publicação da biblioteca com 15 modelos, dois guias e a base aberta com 43 tipos de dados estruturados |

## Como citar

> TRIWI. **Dados Estruturados e Schema Markup: modelos de JSON-LD em português.** GitHub, 2026. Disponível em: https://github.com/TRIWI-SEO/DADOS-ESTRUTURADOS-SCHEMA-MARKUP. Acesso em: dia, mês e ano.

## Licença

Os modelos, os textos e a base de dados estão sob a licença [Creative Commons Atribuição 4.0 Internacional (CC BY 4.0)](LICENSE): reuso livre, inclusive comercial, desde que citada a TRIWI como fonte. Schema.org é uma iniciativa colaborativa; Google e Search Console são marcas do Google.

---

<p align="center">
  <strong>Quer que sua marca seja a resposta, no Google e nas IAs?</strong><br>
  <a href="https://triwi.com.br/contato/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=readme">Que tal um café com a TRIWI?</a>
</p>

<p align="center">
  <sub>Biblioteca publicada e mantida pela equipe da TRIWI, agência 100% especializada em SEO e Otimização para IAs.</sub>
</p>
