<p align="center">
	<img src="./img/aws-icons/aws-EventBridge.png" alt="aws-eventbridge-icon" style="height:150px; width:150px;" /> 
  <br />
	<h1 align="center">
    EventBridge
  </h1>
</p>	

<br />

## :pushpin: Índice

- [Introdução](#introdução)
- [Referências](#books-referências)

<br />

## Introdução

Amazon **EventBridge** é a evolução do CloudWatch Events, é um serviço de barramento de eventos sem servidor.

Anteriormente o EventBridge era chamado de CloudWatch Events, as regras que foram criadas no CloudWatch Events também irão aparecer no console do EventBridge pois este usa a mesma API do CloudWatch Events.

O EventBridge recebe um evento, um indicador de uma mudança no ambiente. As regras correspondem eventos a alvos com base na estrutura do evento, chamada de padrão de evento, ou em um cronograma. Por exemplo, quando uma instância EC2 muda de pendente para em execução, você pode ter uma regra que envia o evento para uma função do Lambda.

Ele também pode receber eventos de um parceiro SaaS que são serviços que de terceiros que não fazer parte da AWS.  

<br />


## :books: Referências

Para uma compreensão mais profunda sobre Amazon EventBridge recomendo a leitura da documentação oficial, os links estão abaixo.

- [O que é o Amazon EventBridge?](https://docs.aws.amazon.com/pt_br/eventbridge/latest/userguide/eb-what-is.html)

<br />

---
Feito com ♥ by :man_astronaut: Guilherme Bezerra :wave: [Entrar em contato!](https://www.linkedin.com/in/gbdsantos/)