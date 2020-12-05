---
layout: default
title: Operações de Integração
parent: Fluxo de informação
nav_order: 1
has_children: true
has_toc: false
---

# Operações de Integração
{: .fs-6 .fw-500 .mb-lg-5 }

O Quadro 1 apresenta as operações de integração pretendidas, com seus respectivos triggers e esquemas de dados. Esses elementos deverão estar disponíveis na fachada de integração, para viabilizar a construção dos adaptadores.

Quadro 1 - Operações de Integração
{: .text-center .fs-2 .text-grey-dk-000 .mb-0 }

| Operação                                | Trigger                           | Esquema (request)                               | Esquema (request)       |
|:----------------------------------------|:----------------------------------|:------------------------------------------------||:-----------------------|
| buscaDadosGuiaSadt                      | PesquisaGuias<sup>`1`</sup>       | IdentificacaoGuiaSadt                           | GuiaSadt                |
| buscaPedidoMedicoLiberado               | SolicitacoesExames<sup>`1`</sup>  | IdentificacaoBeneficiarioPrestador              | List<SolicitacaoExame>  |
| cancelaGuiaSadtExterna                  | CancelaGuia<sup>`1`</sup>         | IdentificacaoPrestadorGuiaSadtSolicitacaoExame  | n/a                     |
| enviaResultadoExameExterno              | ExamesRealizados<sup>`2`</sup>    | List<ResultadoExame>                            | n/a                     |
| enviaResultadoExameParametrizadoExterno | ExamesRealizados<sup>`2`</sup>    | List<ResultadoExameEstruturado>                 | n/a                     |
| obtemVizualizadorExame                  | n/a                               | IdentificacaoSolicitacaoExame                   | UrlResultadoExame       |
| realizaPedidoMedico                     | EmissaoGuias<sup>`1`</sup>        | IdentificacaoPrestadorSolicitacoesExames        | List<GuiaSadt>          |

<sup>`1`</sup> Esses triggers devem conter a identificação do usuário (login do prestador no sistema PreventWeb).
{: .fs-3 }

<sup>`2`</sup> Resultados de exames não precisam estar agrupados do mesmo modo que as solicitações de exames. Assim, é possível que existam triggers diferentes para cada exame realizado, acarretando na realização da respectiva operação de integração para cada resultado de exame disponibilizado. É importante que esse trigger identifique corretamente qual a solicitação de exame (identificador) referente ao exame cujo resultado está sendo comunicado.
{: .fs-3 }
