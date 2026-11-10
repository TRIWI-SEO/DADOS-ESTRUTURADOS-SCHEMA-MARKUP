# Schema LocalBusiness em JSON-LD: modelo pronto para copiar

**O schema LocalBusiness descreve uma empresa com endereço físico que recebe clientes: nome, endereço, telefone, horário e localização. O Google exige só `name` e `address` e recomenda usar o subtipo mais específico, como Dentist, Restaurant ou Store. Avaliações da própria empresa não geram estrelas.**

*Por equipe de SEO da TRIWI, com revisão de Ricardo Martins, fundador. Publicado em 09/11/2026. Atualizado em 09/11/2026. Campos conferidos na documentação do Google Search Central e no schema.org (versão 30.1) em 09/11/2026.*

> **Situação no Google em 09/11/2026: Ativo.** Dados da empresa, como horário, endereço e telefone, em resultados de busca local. review e aggregateRating só valem para sites que avaliam outras empresas, nunca para a empresa falando de si. O carrossel de restaurantes exige cadastro de parceiro. Fonte: [documentação oficial do Google](https://developers.google.com/search/docs/appearance/structured-data/local-business).

## Índice

- [Quando usar o schema LocalBusiness?](#quando-usar-o-schema-localbusiness)
- [Quais campos o Google exige e recomenda?](#quais-campos-o-google-exige-e-recomenda)
- [Modelo de JSON-LD para copiar](#modelo-de-json-ld-para-copiar)
- [Modelo completo com horário e localização](#modelo-completo-com-horário-e-localização)
- [Como marcar uma rede com várias unidades?](#como-marcar-uma-rede-com-várias-unidades)
- [Quais subtipos de LocalBusiness usar?](#quais-subtipos-de-localbusiness-usar)
- [Como validar o schema LocalBusiness?](#como-validar-o-schema-localbusiness)
- [O que o schema LocalBusiness vale para as IAs?](#o-que-o-schema-localbusiness-vale-para-as-ias)
- [Erros comuns](#erros-comuns)
- [Perguntas frequentes](#perguntas-frequentes)

## Quando usar o schema LocalBusiness?

Quando a empresa tem um endereço onde o cliente vai: clínica, consultório, loja, restaurante, academia, escritório de advocacia com atendimento presencial, hotel, concessionária. Empresa que só atende online usa [Organization](../modelos/schema-organization-json-ld.md).

A marcação faz mais sentido na página que descreve a empresa ou a unidade: a página inicial, no caso de um endereço só, ou a página de cada unidade, no caso de rede.

## Quais campos o Google exige e recomenda?

**Empresa local** (LocalBusiness e subtipos (Restaurant, Dentist, Store e outros)), segundo a [documentação do Google](https://developers.google.com/search/docs/appearance/structured-data/local-business); o tipo no vocabulário está em [schema.org/LocalBusiness](https://schema.org/LocalBusiness):

| Exigência | Campos |
|:---|:---|
| Obrigatórios | `address`; `name` |
| Recomendados | `aggregateRating`; `department`; `geo.latitude`; `geo.longitude`; `menu`; `openingHoursSpecification`; `priceRange`; `review`; `servesCuisine`; `telephone`; `url` |

Regras da documentação: o horário usa os dias da semana em inglês do schema.org (`Monday`, `Tuesday`) e o formato `hh:mm:ss`; a latitude e a longitude precisam de pelo menos cinco casas decimais; `priceRange` acima de 100 caracteres é ignorado; e mais de um tipo vai em lista, porque `additionalType` não é aceito.

## Modelo de JSON-LD para copiar

```json
{
  "@context": "https://schema.org",
  "@type": "Dentist",
  "name": "Clínica Odontológica Exemplo",
  "url": "https://www.exemplo.com.br/",
  "telephone": "+55-11-0000-0000",
  "image": "https://www.exemplo.com.br/imagens/fachada.jpg",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "Rua Exemplo, 100",
    "addressLocality": "São Paulo",
    "addressRegion": "SP",
    "postalCode": "01000-000",
    "addressCountry": "BR"
  }
}
```

Troque `Dentist` pelo subtipo do seu negócio (lista abaixo) e cole dentro de uma tag `<script type="application/ld+json">`.

## Modelo completo com horário e localização

```json
{
  "@context": "https://schema.org",
  "@type": "Dentist",
  "@id": "https://www.exemplo.com.br/#clinica",
  "name": "Clínica Odontológica Exemplo",
  "url": "https://www.exemplo.com.br/",
  "telephone": "+55-11-0000-0000",
  "email": "contato@exemplo.com.br",
  "image": [
    "https://www.exemplo.com.br/imagens/fachada-1x1.jpg",
    "https://www.exemplo.com.br/imagens/fachada-4x3.jpg",
    "https://www.exemplo.com.br/imagens/fachada-16x9.jpg"
  ],
  "priceRange": "$$",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "Rua Exemplo, 100, conjunto 12",
    "addressLocality": "São Paulo",
    "addressRegion": "SP",
    "postalCode": "01000-000",
    "addressCountry": "BR"
  },
  "geo": {
    "@type": "GeoCoordinates",
    "latitude": -23.56168,
    "longitude": -46.65598
  },
  "openingHoursSpecification": [
    {
      "@type": "OpeningHoursSpecification",
      "dayOfWeek": ["Monday", "Tuesday", "Wednesday", "Thursday", "Friday"],
      "opens": "08:00:00",
      "closes": "19:00:00"
    },
    {
      "@type": "OpeningHoursSpecification",
      "dayOfWeek": "Saturday",
      "opens": "08:00:00",
      "closes": "12:00:00"
    }
  ],
  "sameAs": [
    "https://www.instagram.com/clinicaexemplo"
  ],
  "parentOrganization": {
    "@id": "https://www.exemplo.com.br/#organization"
  }
}
```

Para fechar em um feriado ou numa temporada, acrescente uma `OpeningHoursSpecification` com `validFrom` e `validThrough` (datas no formato AAAA-MM-DD) e `opens` e `closes` iguais a `00:00`. Para aberto 24 horas, `opens` igual a `00:00` e `closes` igual a `23:59`. As duas regras estão na seção de horários da [documentação do Google](https://developers.google.com/search/docs/appearance/structured-data/local-business). Restaurante usa ainda `servesCuisine` e `menu` (a URL do cardápio).

## Como marcar uma rede com várias unidades?

Uma página por unidade, cada uma com o próprio `LocalBusiness`: nome da unidade, endereço, telefone e horário daquela unidade. A marca vai num `Organization` na página inicial, e cada unidade aponta para ela com `parentOrganization`, como no modelo completo.

Departamentos dentro da mesma unidade, como a farmácia de um supermercado, vão em `department`. A documentação sugere o nome no formato "nome da loja e nome do departamento", a não ser que o departamento tenha marca própria.

## Quais subtipos de LocalBusiness usar?

O schema.org tem dezenas de subtipos. Os mais comuns em sites brasileiros:

| Negócio | Tipo schema.org |
|:---|:---|
| Clínica médica, consultório | `MedicalClinic`, `Physician` |
| Clínica odontológica | `Dentist` |
| Clínica de estética, salão | `BeautySalon`, `DaySpa` |
| Farmácia | `Pharmacy` |
| Loja física | `Store` ou subtipos como `ClothingStore`, `ElectronicsStore`, `FurnitureStore` |
| Restaurante, bar, café | `Restaurant`, `BarOrPub`, `CafeOrCoffeeShop` |
| Hotel, pousada | `Hotel`, `BedAndBreakfast` |
| Escritório de advocacia | `LegalService` |
| Escritório de contabilidade | `AccountingService` |
| Imobiliária | `RealEstateAgent` |
| Academia | `ExerciseGym` |
| Concessionária | `AutoDealer` |
| Escola | `School` (subtipo de `EducationalOrganization`, use junto com `LocalBusiness` em lista) |

A lista completa está em [schema.org/LocalBusiness](https://schema.org/LocalBusiness). Quando nenhum subtipo serve, use `LocalBusiness`.

## Como validar o schema LocalBusiness?

1. Antes de publicar, cole o código ou a URL no [Teste de pesquisa aprimorada](https://search.google.com/test/rich-results), do Google: ele diz se a marcação está elegível e aponta erros e avisos.
2. Confira o vocabulário no [Schema Markup Validator](https://validator.schema.org/), do schema.org, que valida também propriedades que o Google não usa.
3. Depois de publicar, acompanhe os [relatórios de resultados aprimorados do Search Console](https://support.google.com/webmasters/answer/7552505?hl=pt-BR) e use a Inspeção de URL para confirmar que o Google encontrou a marcação.

O [Gerador de dados estruturados da TRIWI](https://triwi.com.br/ferramentas/gerador-de-dados-estruturados/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=local-business) monta o LocalBusiness com endereço e horário por formulário.

## O que o schema LocalBusiness vale para as IAs?

Alto: endereço, horário e telefone declarados de forma inequívoca, iguais aos do Perfil da Empresa no Google.

Pergunta local é das que mais aparecem nos assistentes ("clínica odontológica perto da Paulista que abre sábado"). A resposta depende de dados que batem entre si: o nome, o endereço e o horário do site, do Perfil da Empresa no Google e dos diretórios. A marcação não substitui o Perfil da Empresa, mas é a versão desses dados que você controla no seu próprio site. O tema está no guia aberto [SEO Local](https://github.com/TRIWI-SEO/SEO-IA/blob/main/fundamentos-de-seo/seo-local-como-aparecer-nas-buscas-da-sua-regiao.md).

## Erros comuns

| Erro | Correção |
|:---|:---|
| `aggregateRating` com a nota da própria empresa | O Google não mostra estrelas de empresa que marca as próprias avaliações, nem vindas de widget de terceiros; retire |
| Horário do site diferente do Perfil da Empresa no Google | Uma fonte de verdade, atualizada nos dois lugares no mesmo dia |
| Dias da semana em português | `Monday` a `Sunday`, como manda o schema.org |
| Uma marcação com todas as unidades na página inicial | Uma página por unidade, cada uma com a própria marcação |
| Coordenadas com duas casas decimais | Pelo menos cinco casas decimais |

## Perguntas frequentes

<details>
<summary><strong>O schema LocalBusiness ajuda a aparecer no Google Maps?</strong></summary>

O Maps usa principalmente o Perfil da Empresa no Google. A marcação no site ajuda o Google a confirmar que o site e o perfil são da mesma empresa, mas não substitui o perfil.
</details>

<details>
<summary><strong>Posso marcar as avaliações do Google na minha página?</strong></summary>

Não para gerar estrelas. A documentação de trechos de avaliação diz que a empresa que controla as próprias avaliações não é elegível, inclusive quando elas vêm de um widget de terceiros. Mostrar as avaliações para o visitante continua valendo.
</details>

<details>
<summary><strong>Empresa que atende em domicílio, sem endereço aberto ao público, usa LocalBusiness?</strong></summary>

O campo `address` é obrigatório no LocalBusiness. Se o endereço não pode ser mostrado no site, use `Organization` com `areaServed` indicando as cidades atendidas.
</details>

<details>
<summary><strong>Clínica usa MedicalClinic ou MedicalBusiness?</strong></summary>

`MedicalClinic` para clínica com atendimento presencial e `Physician` para consultório de um médico. `MedicalBusiness` é o tipo genérico, para quando nenhum dos específicos serve.
</details>

**Ver também nas páginas da TRIWI por segmento:** [SEO para Médicos e Clínicas](https://triwi.com.br/seo-para-medicos-e-clinicas/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=local-business), [SEO para Dentistas e Clínicas Odontológicas](https://triwi.com.br/seo-para-dentistas-e-clinicas-odontologicas/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=local-business), [SEO para Varejo](https://triwi.com.br/seo-para-varejo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=local-business), [SEO para Hotéis e Pousadas](https://triwi.com.br/seo-para-hoteis-e-pousadas/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=local-business).

**Ver também na Base de Conhecimento da TRIWI:** [Schema Markup e Dados Estruturados para SEO](https://github.com/TRIWI-SEO/SEO-IA/blob/main/seo-tecnico/schema-markup-e-dados-estruturados-para-seo.md), [Dados Estruturados para IA: Schema Markup na Era Generativa](https://github.com/TRIWI-SEO/SEO-IA/blob/main/geo-seo-para-ia/dados-estruturados-para-ia-schema-markup-na-era-generativa.md).

**Na TRIWI:** [Gerador de dados estruturados](https://triwi.com.br/ferramentas/gerador-de-dados-estruturados/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=local-business), [Guia de SEO Técnico, capítulo Dados estruturados](https://triwi.com.br/guias/seo-tecnico/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=local-business#dados-estruturados), [Guia de GEO: Otimização para IAs](https://triwi.com.br/guias/geo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=local-business), [Atualizações do Google](https://triwi.com.br/atualizacoes/google/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=local-business).

**Ver também no Glossário de SEO da TRIWI:** [Dados estruturados](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=local-business#seo-dados-estruturados), [Schema.org](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=local-business#seo-schema-org), [JSON-LD](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=local-business#seo-json-ld), [Entidade](https://triwi.com.br/glossario/seo/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=local-business#seo-entidade).

[Voltar para a biblioteca completa](../README.md)

---

<p align="center">
  <strong>Quer que sua marca seja a resposta, no Google e nas IAs?</strong><br>
  <a href="https://triwi.com.br/contato/?utm_source=github&utm_medium=referral&utm_campaign=repo-dados-estruturados&utm_content=local-business">Que tal um café com a TRIWI?</a>
</p>

<p align="center">
  <sub>Biblioteca publicada e mantida pela equipe da TRIWI, agência 100% especializada em SEO e Otimização para IAs.</sub>
</p>
