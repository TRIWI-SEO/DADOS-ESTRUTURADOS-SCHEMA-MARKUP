# Dicionário de Dados: Tipos de Dados Estruturados do Google, pela TRIWI

Este dicionário descreve a base [tipos-de-dados-estruturados.csv](tipos-de-dados-estruturados.csv), a versão em dados da biblioteca [Dados Estruturados e Schema Markup](../README.md): o que cada coluna significa, como o arquivo é formatado e como a base é mantida. A base está sob licença [CC BY 4.0](../LICENSE): o reuso é livre, inclusive comercial, desde que a TRIWI seja citada como fonte.

*Por equipe de SEO da TRIWI. Atualizado em 09/11/2026.*

## Quais bases existem?

| Arquivo | O que traz | Linhas |
|:---|:---|:---|
| [tipos-de-dados-estruturados.csv](tipos-de-dados-estruturados.csv) | Cada recurso de dados estruturados da Pesquisa Google, ativo ou descontinuado, com tipo schema.org, situação, campos e fonte oficial | 43 |

## Como abrir o arquivo?

O arquivo segue o mesmo padrão das outras bases abertas da TRIWI: codificação UTF-8, colunas separadas por vírgula, quebra de linha CRLF, datas no formato AAAA-MM-DD e listas dentro de uma célula separadas por ponto e vírgula.

Se o Excel mostrar os acentos embaralhados, abra pelo menu Dados, opção De Texto/CSV, e escolha a codificação UTF-8.

## O que significa cada coluna?

| Coluna | Significado |
|:---|:---|
| id | Identificador curto do recurso, em minúsculas e com hífen |
| recurso_google | Nome do recurso em português, como a documentação do Google o apresenta |
| tipo_schema | Tipo ou tipos do schema.org usados pelo recurso |
| schema_org | Endereço do tipo principal no vocabulário do schema.org |
| situacao_no_google | Ativo; Ativo com restrição; Em retirada; Descontinuado (ver abaixo) |
| mudanca_em | Data da última mudança de situação ou de exigência registrada pelo Google; n/d quando não há registro relevante |
| o_que_aparece | O que o recurso gera na Pesquisa Google, ou o que deixou de gerar |
| campos_obrigatorios | Propriedades que o Google exige, com o nome exato; "nenhum" quando não há exigência e "não se aplica" para recurso descontinuado |
| campos_recomendados | Propriedades que o Google recomenda; n/d quando a documentação não traz a lista |
| para_ias | Avaliação da TRIWI sobre o valor do tipo fora do Google, em especial para as IAs (ver abaixo) |
| observacao | Restrições, regras e divergências entre fontes |
| modelo | Página desta biblioteca com o modelo de JSON-LD; vazio quando não há modelo |
| documentacao_google | Página do recurso na documentação do Google; n/d quando a documentação foi removida |
| fonte | Página oficial que confirma a situação registrada na linha |
| atualizado_em | Data da última conferência da linha |

## O que significa cada situação?

| Valor | Significado |
|:---|:---|
| Ativo | Recurso disponível na Pesquisa Google, com documentação própria |
| Ativo com restrição | Disponível só para alguns idiomas, países, dispositivos ou parceiros, ou em beta |
| Em retirada | O Google anunciou a saída da Pesquisa, mas a marcação ainda tem uso, como em outra ferramenta do Google |
| Descontinuado | O resultado não aparece mais na Pesquisa Google e a documentação foi removida |

**Critério de contagem:** cada linha é um recurso da Pesquisa Google com documentação própria, ou que teve documentação própria. Recursos de compra que o Google documenta em páginas separadas, como variantes, devolução, frete e programa de fidelidade, contam como linhas separadas. Tipos do schema.org que o Google não usa em nenhum recurso não entram.

**Sobre a coluna para_ias:** o Google diz que dados estruturados não são exigidos para os recursos de IA da Pesquisa, e as empresas de IA não documentam como usam JSON-LD. A coluna é a avaliação da TRIWI, declarada como tal, do quanto cada tipo ajuda a declarar entidade, autoria e dados factuais sem ambiguidade. Começa por Alto, Médio ou Baixo, seguido do motivo.

**Divergências:** quando o registro de mudanças do Google e a página atual do recurso discordam, a base segue a página atual e anota a divergência em observacao.

## Como a base é mantida?

A base é revisada pela equipe da TRIWI a cada mudança no [registro de mudanças da documentação do Google](https://developers.google.com/search/updates). Recurso que muda de situação tem a linha atualizada, com nova data em mudanca_em e atualizado_em; recurso descontinuado continua na base, como histórico. Correções e sugestões chegam por [issue](../../../issues/new).
