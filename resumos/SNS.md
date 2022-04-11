<p align="center">
	<img src="./img/aws-icons/aws-SNS.png" alt="aws-sns-icon" style="height:150px; width:150px;" /> 
  <br />
	<h1 align="center">
    SNS
  </h1>
</p>	

<br />

## :pushpin: Índice

- [Introdução](#introdução)
- [Como funciona?](#como-funciona)
  - [Publicação direta](#publicação-direta)
- [Filtragem de mensagens](#filtragem-de-mensagens)
- [Referências](#books-referências)

<br />

## Introdução

SNS é uma sigla para **Simple Notification Service**.

O produtor de eventos(*event producer*) enviará mensagens somente para um tópico do SNS, e o vários recebedores de eventos(*subscriptions*) irão ouvir as notificações do tópico SNS.

Cada assinante(*subscriber*) irá pegar todas as mensagens, existem um recurso para filtrar as mensagens.

- 10.000.000 de assinantes por tópico
- Limite de 100.000 tópicos no SNS
- Assinantes podem ser:
    - Email
    - HTTP/HTTPS
    - Kinesis Data Firehose
    - Lambda
    - Notificações mobile
    - SMS
    - SQS

O SNS possuem integração com muitos serviços da AWS, muitos serviços podem enviar dados ou notificações diretamente para o SNS.

<br />

## Como funciona?

Para publicar um tópico use a SDK, a partir disso pode-ser criar uma ou várias assinaturas.

### Publicação direta

Isso é para o caso de aplicativos mobile com a SDK.

<br />

## Filtragem de mensagens

Por padrão os assinantes recebem todas as mensagens publicadas no tópico, para receber um subconjunto de mensagens um assinante deve atribuir uma política de filtro.
A política de filtro é um arquivo JSON usado para filtar as mensagens que são enviadas para os assinantes do tópico SNS.
Por padrão se uma assinatura não tiver uma política de filtro, ela receberá todas as mensagens.

<br />

## :books: Referências

Para uma compreensão mais profunda sobre SNS recomendo a leitura da documentação oficial, os links estão abaixo.

- [O que é o Amazon SNS?](https://docs.aws.amazon.com/pt_br/sns/latest/dg/welcome.html)
- [Fanout para filas do Amazon SQS](https://docs.aws.amazon.com/pt_br/sns/latest/dg/sns-sqs-as-subscriber.html)    
- [Filtragem de mensagens do Amazon SNS](https://docs.aws.amazon.com/pt_br/sns/latest/dg/sns-message-filtering.html)