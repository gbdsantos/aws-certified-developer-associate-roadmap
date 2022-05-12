<p align="center">
	<img src="./img/aws-icons/aws-Cognito.png" alt="aws-cognito-icon" style="height:150px; width:150px;" /> 
  <br />
	<h1 align="center">
    Cognito
  </h1>
</p>	

<br />

## :pushpin: Índice

- [Introdução](#introdução)
- [Cognito User Pools](#cognito-user-pools)
- [Cognito Identity Pools](#cognito-identity-pools)
- [Cognito Sync](#cognito-sync)
- [Referências](#books-referências)

<br />

## Introdução

O Amazon Cognito fornece autenticação, autorização e gerenciamento de usuários para aplicativos móveis e web.

É possível fazer login diretamente com um nome de usuário e senha ou por meio de terceiros como por exemplo Facebook, Google e etc.
É um *Identity Broker*, faz tudo que um Web Identity Federator faz mas melhor.

Os dois componentes principais do Amazon Cognito são os **grupos de usuários (*user pool*)** e **grupos de identidades (*identity pool*)**.
Os grupos de usuários fornece opções de cadastro e login para usuários enquanto que os grupos de identidade permite que você conceda acesso a serviços da AWS.

É possível utilizar os dois componentes separadamente ou em conjunto.

- **Cognito User Pools**
  - Funcionalidade de login
  - Integrado com API Gateway e Application Load Balancer (ALB)
- **Cognito Identity Pools**
  - Permite que usuários externos possam acessar e utilizar recursos/serviços da AWS
- **Cognito Sync**: Sincronização de dados de dispositivos móveis no Cognito, mas ele **foi depreciado e substituído por um novo serviço** chamado **AppSync**

<br />

## Cognito User Pools

Cria um banco de dados serverless para usuários de aplicativos web e móveis. Possui reset de senha e também MFA(Multi-factor authentication).

Tem o recurso de *Federated Identities* do Facebook, Google, SAML, e etc. Que são os chamados *third party identity provider*(IdP).

<br />

## Cognito Identity Pools

É utilizado para fornecer credenciais temporárias para conseguir acessar e utilizar recursos/serviços da AWS.

Também é possui permitir usuários não autenticados(convidado) façam acesso.

<br />

## Cognito Sync

Conforme já mencionado é um serviço depreciado, utilize o AWS AppSync.

Ele é usado para armazenar as preferências de usuário, configuração e estado atual da aplicação mobile/web e oferece sincronização de dados entre dispositivos em qualquer plataforma (android, iOS, etc).

<br />

## :books: Referências

Para uma compreensão mais profunda sobre o Amazon Cognito recomendo a leitura da documentação oficial, os links estão abaixo.

- [O que é o Amazon Cognito](https://docs.aws.amazon.com/cognito/latest/developerguide/what-is-amazon-cognito.html) :us:

<br />

---
Feito com ♥ by :man_astronaut: Guilherme Bezerra :wave: [Entrar em contato!](https://www.linkedin.com/in/gbdsantos/)