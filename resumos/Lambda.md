<p align="center">
	<img src="./img/aws-icons/aws-Lambda.png" alt="aws-lambda-icon" style="height:150px; width:150px;" /> 
  <br />
	<h1 align="center">
    Lambda
  </h1>
</p>	

## :pushpin: Índice

- [Introdução](#introdução)
- [O que é *serverless*](#o-que-é-serverless)
  - [Serverless na AWS](#serverless-na-aws)
- [Compatibilidade de linguagens do Lambda](#compatibilidade-de-linguagens-do-lambda)  
- [Principais integrações do Lambda](#principais-integrações-do-lambda)
- [Cobrança](#lambda-princing)
- [Lambda versions](#lambda-versions)
- [Referências](#book-referências)

<br />

## Introdução

<div align="center">
<img src="./img/cloud-technology-evolution.png" width="70%" />
</div>

Lamba é um serviço AWS com arquitetura ***serverless***, a tradução literal é "sem servidor" mas não quer dizer que a infraestrutura será sem servidores e sim uma arquitetura que permite transferir mais das suas responsabilidades operacionais à AWS.
Este tipo de arquitetura permite criar e executar aplicações e serviços sem preocupações com servidores, como por exemplo o gerenciamento e provisionamento de capacidade (processamento e armazenamento)

<br />

## O que é *serverless*?

É um novo paradigma onde não existe mais a necessidade de gerenciar servidores. Então, não é que não tem mais servidor e sim que apenas você não precisa gerenciá-lo.

É somente implantar o código/funções.

### Serverless na AWS

- Amazon S3
- Aurora Serverless
- AWS API Gateway
- AWS Cognito
- AWS Kinesis Data Firehose
- AWS Lambda
- AWS SNS & SQS
- DynamoDB
- Fargate
- Step Functions

<br />

## Compatibilidade de linguagens do Lambda

- C# (.NET Core)
- C# / Powershell
- Golang
- Java
- Node.js
- Python
- Ruby
- API de Tempo de Execução Customizada (Custom Runtime API): É suportada pela comunidade

<br />

## Principais integrações do Lambda

Principais integrações com outros serviços da AWS.

- API Gateway
- Cognito
- CloudFront
- CloudWatch Events / EventBridge
- CloudWatch Logs
- DynamoDB
- Kinesis
- S3
- SNS
- SQS

<br />

## Cobrança

A cobrança é feito por requisição (*requests*).
O primeiro milhão de requisições a AWS são gratuitas, a partir dessa quantidade é cobrado R$ 0,20 por cada milhão de requisições

<br />

## Lambda versions

Tem o caso de uso para realizar testes (ex: testes A/B) e migrações de suas APIs.

Versões ARN:

- **Qualified:** Quando a versão de uma função lambda for *qualified* terá um sinal `$latest` do ARN. Aqui é possível criar uma nova versão a partir dela
- **Unqualified:** Se a versão de uma função lambda for *unqualifed* você não conseguirá ver a parte `$latest` no final do ARN. Não é possível fazer mais alterações

<br />

## :books: Referências

Para uma compreensão mais profunda sobre Lambda recomendo a leitura da documentação oficial, os links estão abaixo.
E outros links de referência.

- [Lambda Pricing]()
- :us: [Cloud Jorney](http://www.cyberniti.com/CloudJourney)
