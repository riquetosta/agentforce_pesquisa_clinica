# Arquitetura

## Objetivo

Demonstrar um fluxo de apoio à pesquisa clínica com dois agentes Agentforce,
RAG, Salesforce Flow, Person Accounts, Experience Cloud e integração operacional.

## Fluxo de contexto

```text
Usuário autenticado
        ↓
LWC CommunityHome
        ↓
Parâmetro Current_User_Id
        ↓
Routing Flow
        ↓
User.Contact.AccountId
        ↓
MessagingSession.Current_Patient__c
        ↓
Agente Pesquisa Clínica
```

## Fluxo do participante

```text
Participante
        ↓
Agente Pesquisa Clínica
        ├── FAQ
        ├── Estudos potencialmente relevantes
        └── Solicitação relacionada a um estudo
```

## Fluxo operacional

```text
Trial_Enrollment__c criado
        ↓
Flow pós-matrícula
        ↓
Agente Pós-Matrícula
        ├── Consulta atividades do estudo
        ├── Cria Tasks
        └── Envia notificação ao Slack
```

## Observação arquitetural

Na implementação atual, o Flow pós-matrícula é acionado após a criação do
registro de `Trial_Enrollment__c`. Em uma solução empresarial, o acionamento
deveria depender de um status que represente aprovação para onboarding ou
inscrição confirmada.
