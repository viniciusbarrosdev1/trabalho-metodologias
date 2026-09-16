# 🪒 B1-T3 — Kanban para Sustentação do Sistema de Agendamento de Barbearia

**🔗 Trello:** https://trello.com/b/lywxrGlD/kambam-trabalho

---

## 📋 Contexto

O trabalho utiliza como base o backlog do B1-T2 (sistema de agendamento de barbearia), já em produção. O time representado é o time de sustentação responsável pelo sistema: a demanda vem de incidentes, chamados de suporte e melhorias técnicas motivadas pelo uso real.

## 🗂️ O quadro

O fluxo foi organizado em seis colunas: **Entrada**, **Análise**, **Em Desenvolvimento**, **Review**, **Finalizado** e **Reprovado**.

- 📥 **Entrada** — o que acabou de chegar, ainda sem triagem.
- 🔍 **Análise** — o time avalia se aceita, recusa ou pede mais informação antes de comprometer capacidade.
- 🛠️ **Em Desenvolvimento** — implementação ativa, sujeita ao limite de WIP.
- ✅ **Review** — validação por outro integrante antes de considerar resolvido.
- 🏁 **Finalizado** — resultado confirmado com quem solicitou.
- ❌ **Reprovado** — log de itens recusados na análise; fica arquivado, fora do fluxo ativo.

O ponto de compromisso ocorre quando um item sai da Análise e é puxado para Em Desenvolvimento — a partir daí o time assume a responsabilidade por resolvê-lo. O ponto de entrega ocorre quando o item chega a Finalizado, com o resultado confirmado.

## 🏷️ Tipos de trabalho e classes de serviço

Cada cartão indica seu tipo:

| Sigla | Tipo | Exemplo |
|---|---|---|
| 🔥 **I** | Incidente | Conflito de horário duplicado em produção |
| 💬 **S** | Solicitação/Chamado de suporte | Cliente pergunta sobre escolha de barbeiro |
| ⚙️ **M** | Melhoria técnica | Otimizar carregamento da agenda |
| ✨ **F** | Funcionalidade | Lembrete automático via WhatsApp |

Além do tipo, cada cartão traz uma **classe de serviço**:

| Classe | Significado | Exemplo |
|---|---|---|
| ⬜ **Padrão** | Fluxo normal | Maioria dos chamados |
| 🚨 **Prioridade** | Impacto alto e imediato | Falha na API do WhatsApp |
| 📅 **Data fixa** | Valor ligado a uma data | Relatório mensal ao dono |
| 🌫️ **Intangível** | Benefício do atraso pouco visível | Escolha de barbeiro preferido |

A classe de serviço aparece diretamente no título do cartão quando foge do padrão — por exemplo, "(Data fixa)" ou "(Intangível)" — para não depender de abrir a descrição pra saber que um item é exceção.

## 🚦 Limite de WIP

O limite definido para a coluna Em Desenvolvimento é de **seis itens simultâneos**, considerando o tamanho do time. É um valor de partida — não definitivo — que será revisado com base em evidência da simulação e de rodadas futuras.

## 📜 Políticas explícitas

- 🔍 **Triagem:** todo item passa por Análise antes de qualquer compromisso; a saída é aceitar (segue para Em Desenvolvimento) ou recusar (vai para Reprovado, com motivo registrado).
- 🤝 **Puxada:** só se puxa um novo item para Em Desenvolvimento quando há espaço no limite de WIP — exceto Prioridade, que pode furar a fila com justificativa.
- 🚧 **Bloqueio:** item bloqueado é marcado no título e na descrição, com motivo, tempo e próxima ação; continua contando no WIP até ser resolvido.
- 🔗 **Dependência:** item que depende de outro fica retido até o item de origem ser resolvido ou desbloqueado.
- ✅ **Revisão:** todo item passa por Review antes de Finalizado, com validação de outro integrante.
- 🏁 **Resolução:** item só é considerado Finalizado quando confirmado com quem solicitou, não apenas corrigido tecnicamente.

## 🗃️ Cartões

Cada cartão traz Tipo, Classe de serviço e Origem (cliente, barbeiro ou dono da barbearia) logo no início da descrição, seguidos do contexto do chamado e do critério de aceitação. Esse critério também aparece como checklist no próprio cartão, permitindo acompanhar visualmente o que falta para considerar o item pronto. Cartões de classe Data fixa têm data de vencimento definida no Trello.

## 🎬 Simulação do fluxo

Durante o uso do sistema, ocorreu um erro real de integração com a API do WhatsApp, que interrompeu o envio de confirmações e lembretes. Esse incidente foi classificado como Prioridade — a classe de serviço usada para itens cujo atraso tem impacto alto e imediato — e passou a ser tratado antes dos demais itens em Em Desenvolvimento, mostrando na prática como o quadro reage a um evento urgente.

## 🧱 Gargalo observado

O gargalo apareceu na coluna Em Desenvolvimento: o incidente da API do WhatsApp ocupou uma vaga do limite de WIP sem previsão de solução, por depender de um provedor externo. Isso reduziu a capacidade do time para os demais chamados e travou, em cascata, o pedido de lembrete automático via WhatsApp, que depende diretamente dessa integração e por isso permanece retido em Entrada.
