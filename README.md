# B1-T3 — Kanban para Sustentação do Sistema de Agendamento de Barbearia

**Trello:** https://trello.com/b/lywxrGlD/kambam-trabalho

---

## Contexto

O trabalho utiliza como base o backlog do B1-T2 (sistema de agendamento de barbearia), já em produção. O time representado é o time de sustentação responsável pelo sistema: a demanda vem de incidentes, chamados de suporte e melhorias técnicas motivadas pelo uso real.

## O quadro

O fluxo foi organizado em três colunas: **Fila de Atendimento**, **Em Atendimento** e **Resolvido**.

Quando um item sai da Fila de Atendimento para Em Atendimento, o time se compromete a resolvê-lo — esse é o ponto de compromisso. Quando o item chega a Resolvido, significa que o resultado já foi confirmado e finalizado junto a quem solicitou — esse é o ponto de entrega.

## Tipos de trabalho e classes de serviço

Cada cartão indica seu tipo:

| Sigla | Tipo | Exemplo |
|---|---|---|
| **I** | Incidente | Conflito de horário duplicado em produção |
| **S** | Solicitação/Chamado de suporte | Cliente pergunta sobre escolha de barbeiro |
| **M** | Melhoria técnica | Otimizar carregamento da agenda |
| **F** | Funcionalidade | Lembrete automático via WhatsApp |

Além do tipo, cada cartão traz uma **classe de serviço**, que define a política de tratamento:

| Classe | Significado | Exemplo no quadro |
|---|---|---|
| **Padrão** | Fluxo normal, sem urgência especial | Maioria dos incidentes e chamados |
| **Prioridade** | Atraso gera impacto alto e imediato | Falha na API do WhatsApp (bloqueado) |
| **Data fixa** | Valor depende de uma data específica | Relatório mensal para o dono da barbearia |
| **Intangível** | Benefício do atraso é pouco evidente | Escolha de barbeiro preferido |

Classificar por tipo e por classe de serviço evita que toda demanda seja tratada como "urgente" sem critério, e deixa explícito qual item deve furar a fila em caso de necessidade real.

## Limite de WIP

O limite inicial definido para a coluna Em Atendimento é de **seis itens simultâneos**, considerando o tamanho do time. É um valor de partida — não definitivo — que será revisado com base em evidência da simulação e de rodadas futuras.

## Políticas explícitas

- **Triagem de entrada:** item só sai da fila quando o motivo e o resultado esperado estão claros.
- **Puxada:** só se puxa um novo item quando há espaço no limite de WIP — exceto Prioridade, que pode furar a fila com justificativa.
- **Bloqueio:** item bloqueado é marcado com motivo, tempo e próxima ação; continua contando no WIP até ser resolvido.
- **Dependência:** item que depende de outro fica na fila até o item de origem ser resolvido.
- **Resolução:** item só é considerado resolvido quando confirmado com quem solicitou, não apenas corrigido tecnicamente.

## Simulação do fluxo

Durante o uso do sistema, ocorreu um erro real de integração com a API do WhatsApp, que interrompeu o envio de confirmações e lembretes. Esse incidente foi classificado como Prioridade — a classe de serviço usada para itens cujo atraso tem impacto alto e imediato — e passou a ser tratado antes dos demais itens em atendimento, mostrando na prática como o quadro reage a um evento urgente.

## Gargalo observado

O gargalo apareceu na coluna Em Atendimento: o incidente da API do WhatsApp ocupou uma vaga do limite de WIP sem previsão de solução, por depender de um provedor externo. Isso reduziu a capacidade do time para os demais chamados e travou, em cascata, o pedido de lembrete automático via WhatsApp, que depende diretamente dessa integração.
