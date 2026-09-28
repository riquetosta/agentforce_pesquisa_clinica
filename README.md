# Agentforce Pesquisa Clínica

Prova de conceito educacional em Salesforce Agentforce para apoio à descoberta,
pré-triagem informativa e coordenação operacional de participantes em pesquisa
clínica.

## Visão geral

O projeto combina Salesforce Agentforce, Experience Cloud, Messaging,
Person Accounts, Data Cloud/Data Libraries, Prompt Builder, Salesforce Flow,
Apex, Lightning Web Components e integração com Slack.

A solução possui dois agentes:

- Um agente voltado ao participante, responsável por responder dúvidas e
  apresentar estudos potencialmente relevantes.
- Um agente operacional, responsável por consultar atividades pós-inscrição,
  criar Tasks e notificar a equipe.

## Fluxo principal

```text
Participante autenticado
        ↓
Experience Cloud + LWC
        ↓
MessagingSession
        ↓
Routing Flow
        ↓
Agente Pesquisa Clínica
        ├── FAQ com RAG
        ├── Recomendação de estudos
        └── Registro relacionado ao estudo
                ↓
        Trial_Enrollment__c
                ↓
        Flow pós-matrícula
                ↓
        Agente Pós-Matrícula
                ├── Criação de Tasks
                └── Notificação Slack
```

## Funcionalidades

- Respostas sobre pesquisa clínica usando uma Data Library.
- Recomendação de estudos potencialmente relevantes.
- Uso do contexto do participante autenticado.
- Integração entre Experience Cloud, Messaging e Person Account.
- Registro de relação entre participante e estudo.
- Automação de atividades pós-inscrição.
- Criação de Tasks para uma fila clínica.
- Notificação operacional via Slack.

## Tecnologias

- Salesforce Agentforce.
- Experience Cloud.
- Messaging.
- Person Accounts.
- Data Cloud e Data Libraries.
- Prompt Builder.
- Salesforce Flow.
- Apex.
- Lightning Web Components.
- Integração HTTP.
- Slack.
- GitHub.


## Agentes

### Agente Pesquisa Clínica

Atende o participante, responde perguntas gerais, apresenta estudos
potencialmente relevantes e registra a solicitação relacionada a um estudo.

### Agente Pós-Matrícula

Executa atividades operacionais associadas a um estudo, criando Tasks para a
equipe e enviando notificações internas.

## Modelo de dados

- `Clinical_Trial__c`: representa um ensaio clínico.
- `Trial_Enrollment__c`: relaciona um participante a um ensaio clínico.
- `Trial_Enrollment__c.Participant__c`: Lookup para `Account`.
- `Trial_Enrollment__c.Clinical_Trials__c`: Lookup para `Clinical_Trial__c`.
- `MessagingSession.Current_Patient__c`: Lookup para `Account`.

## Segurança e limitações

Este é um projeto educacional com dados fictícios.

O sistema:

- Não diagnostica.
- Não prescreve tratamentos.
- Não confirma elegibilidade clínica.
- Não substitui a equipe de pesquisa.
- Não representa um CTMS ou EDC de produção.
- Utiliza regras simplificadas para demonstrar RAG e automação.
- Ainda requer testes automatizados e melhorias de governança antes de qualquer
  uso produtivo.

Não publique credenciais, tokens, webhooks, URLs assinadas, IDs reais ou dados
de participantes.

## Roadmap

- Adicionar prevenção de inscrições duplicadas.
- Impedir criação automática de estudos inexistentes.
- Adicionar validações de entrada.
- Criar testes Apex.
- Usar Named Credential para Slack.
- Adicionar status ao processo de inscrição.
- Separar manifestação de interesse de inscrição confirmada.
- Adicionar logs e auditoria.
- Avaliar o matching dos estudos.
- Implementar aprovação humana antes das atividades pós-inscrição.

## Status

Projeto em evolução. A implementação atual reproduz uma prova de conceito
desenvolvida em treinamento, com melhorias empresariais registradas no roadmap.
