---
slug: pt-br/real-world-development/cloud
title: "Agente do GitHub Copilot na nuvem"
authors:
  - geektrainer
lastUpdated: 2026-06-30
---

O **[agente do GitHub Copilot na nuvem](https://docs.github.com/copilot/concepts/agents/cloud-agent/about-cloud-agent)** permite que o GitHub Copilot trabalhe de forma assíncrona na nuvem. Você atribui uma tarefa no GitHub e o agente na nuvem a executa em segundo plano — explorando o repositório, fazendo alterações e abrindo um pull request — enquanto você fica livre para cuidar de outras atividades.

Ao longo destes exercícios, você adicionará instruções personalizadas para o agente na nuvem e, em seguida, atribuirá uma issue do GitHub para que ele implemente o trabalho. Você revisará e usará agentes personalizados para orientar a abordagem, monitorará e direcionará sessões pelo painel de agentes e, por fim, revisará os pull requests e iterará sobre os resultados.

## Exercícios

| Exercício | Tópico | Descrição |
|----------|-------|-------------|
| [0. Pré-requisitos][ex0] | Configuração | Crie o repositório e o Codespace |
| [1. Instruções personalizadas][ex1] | Contexto | Adicione instruções personalizadas para o agente na nuvem |
| [2. Agente na nuvem][ex2] | Agente assíncrono | Atribua issues ao agente do Copilot na nuvem |
| [3. Agentes personalizados][ex3] | Agentes especializados | Revise e use agentes personalizados |
| [4. Gerenciamento de agentes][ex4] | Monitoramento | Monitore e direcione sessões de agentes |
| [5. Iteração][ex5] | Revisão | Revise PRs, itere sobre o trabalho do Copilot e escolha os próximos passos |

## Pré-requisitos

Antes de participar deste workshop, confirme que você tem:

- [ ] Uma conta do GitHub com um plano **Copilot Student, Pro, Pro+, Business ou Enterprise** ativo
- [ ] O agente do Copilot na nuvem habilitado para sua conta ou organização

> [!TIP]
> Não tem um plano pago? Estudantes verificados podem obter o GitHub Copilot gratuitamente pelo [GitHub Education][callout-student-plan-education]. O plano **Copilot Student** inclui o agente, MCP, revisão de código e os recursos do Copilot CLI usados neste workshop — assim, você pode concluir todos os roteiros com ele.

[callout-student-plan-education]: https://github.com/education/students

> [!NOTE]
> O agente na nuvem está disponível nos planos **Copilot Student, Pro, Pro+, Business e Enterprise** — todos, exceto o Copilot Free. No Copilot Business ou Enterprise, um administrador precisa habilitá-lo para a organização.

> [!NOTE]
> Este roteiro não aborda MCP. Para explorar o uso de servidores MCP com o Copilot, consulte o [roteiro de CLI](../cli/) ou o [roteiro do VS Code](../vscode/).

## Comece

**[Comece pelo Exercício 0: Pré-requisitos →][ex0]**

[ex0]: 0-prerequisites/
[ex1]: 1-custom-instructions/
[ex2]: 2-cloud-agent/
[ex3]: 3-custom-agents/
[ex4]: 4-managing-agents/
[ex5]: 5-iterating/
