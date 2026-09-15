# 📋 B1-T3 — Kanban para Sustentação do Sistema de Agendamento de Barbearia

**Quadro Trello:** [lywxrGlD/kambam-trabalho](https://trello.com/b/lywxrGlD/kambam-trabalho)

---

## 🎯 Contexto

O trabalho parte do backlog do B1-T2 (sistema de agendamento de barbearia), agora **já em produção**. O time representado é o **time de sustentação**: a demanda vem de incidentes, chamados de suporte e melhorias motivadas pelo uso real — não de funcionalidades planejadas em backlog.

---

## 🗂️ O Quadro

| Coluna | Significado |
|---|---|
| **Fila de Atendimento** | Itens triados, aguardando capacidade do time |
| **Em Atendimento** | Itens sendo tratados agora (sujeitos ao WIP) |
| **Resolvido** | Resultado confirmado com quem solicitou |

> **Ponto de compromisso:** quando o item sai da fila e entra em Em Atendimento — o time assume a responsabilidade.
> **Ponto de entrega:** quando o item chega a Resolvido — não basta estar corrigido tecnicamente, precisa estar **confirmado com o solicitante**.

---

## 🏷️ Tipos de Trabalho

| Sigla | Tipo | Exemplo |
|:---:|---|---|
| **I** | Incidente | Conflito de horário duplicado em produção |
| **S** | Solicitação/Suporte | Cliente pergunta sobre escolha de barbeiro |
| **M** | Melhoria técnica | Otimizar carregamento da agenda |
| **F** | Funcionalidade | Lembrete automático via WhatsApp |

## ⚡ Classes de Serviço

| Classe | Significado | Exemplo |
|---|---|---|
| **Padrão** | Fluxo normal | Maioria dos chamados |
| **Expedite** | Impacto alto e imediato | Falha na API do WhatsApp |
| **Data fixa** | Valor ligado a uma data | Relatório mensal ao dono |
| **Intangível** | Benefício do atraso pouco visível | Escolha de barbeiro preferido |

> Classificar por tipo e classe evita tratar tudo como "urgente" sem critério — e deixa claro o que deve furar a fila quando necessário.

---

## 🔢 Limite de WIP

**6 itens simultâneos** em Em Atendimento — valor de partida, a ser revisado com mais rodadas de dados.

---

## 📜 Políticas Explícitas

- **Triagem:** item só sai da fila com motivo e resultado esperado claros
- **Puxada:** só se assume item novo se houver vaga no WIP — exceto Expedite justificado
- **Bloqueio:** marcado com motivo, tempo e próxima ação; continua ocupando vaga
- **Dependência:** fica na fila até o item de origem ser resolvido
- **Resolução:** só conta quando confirmado com o solicitante, não só corrigido

---

## 🔥 Simulação — O Evento Real

Durante o uso do sistema, ocorreu uma **falha real na API do WhatsApp**, interrompendo confirmações e lembretes. O item foi reclassificado como **Expedite** pelo impacto imediato sobre os clientes, passando à frente dos demais em atendimento — mostrando na prática como o quadro reage a uma urgência real.

## 🚧 Gargalo Observado

O incidente do WhatsApp ocupou uma vaga do WIP **sem previsão de solução**, por depender de um provedor externo. Isso reduziu a capacidade do time e travou em cascata o pedido de **lembrete automático via WhatsApp**, que depende diretamente dessa integração.

---

> 💡 **Princípio central demonstrado:** o Kanban torna visível *onde* o trabalho trava — permitindo agir antes que o problema se espalhe pelo fluxo.
