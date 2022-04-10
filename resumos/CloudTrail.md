<p align="center">
	<img src="./img/aws-icons/aws-CloudTrail.png" alt="aws-cloudtrail-icon" style="height:150px; width:150px;" /> 
  <br />
	<h1 align="center">
    CloudTrail
  </h1>
</p>	

<br />

## :pushpin: Índice

- [Introdução](#introdução)
- [Eventos do CloudTrail](#eventos-do-cloudtrail)
- [Referências](#books-referências)

<br />

## Introdução

Amazon **CloudTrail** prover governança, *compliance* e auditoria da sua conta AWS, ele é habilitado por padrão.

Ele te permiter ver todo o histórico de eventos e chamadas de API feitas em sua conta AWS (Console, SDK, CLI, Serviços AWS). Você pode enviar os logs do CloudTrail para o CloudWatch Logs ou S3.

- Monitoramento interno das chamadas de API que estão sendo feitas
- Auditar mudanças feitas nos recursos da AWS por seus usuários

# Eventos do CloudTrail

Existem três tipos de eventos no CloudTrail e por padrão eles são armazenados durante 90 dias no CloudTrail e depois são excluídos. Para manter os eventos além deste período você precisa armazena-los em um *bucket* no S3 e usar o Athena que é um serviço *serverless*(sem servidor) para consultar os dados e analisá-los.

- **Eventos de Gerenciamento(Management Events):** Fornece informações sobre operações de gerenciamento realizadas em recursos da sua conta AWS. Por padrão **trilhas** são configuradas para registrar os logs de eventos de gerenciamento.
- **Eventos de Dados:** Fornecem informações sobre as operações do recurso executadas em um recurso ou dentro de um recurso. Por padrão os eventos de dados não são registrados por causa de seu grande volume de operações.
- **Eventos do Insight:** Analisa os seus eventos e detecta atividade incomum na conta AWS. Os eventos do Insights são desabilitados por padrão quando você cria uma trilha e **existe uma cobrança adicional para o registro de logs de eventos do CloudTrail Insights**.

<br />

## :books: Referências

Para uma compreensão mais profunda sobre Amazon CloudTrail recomendo a leitura da documentação oficial, os links estão abaixo.

- [O que é o Amazon CloudTrail?](https://docs.aws.amazon.com/pt_br/awscloudtrail/latest/userguide/cloudtrail-user-guide.html)    
- [Conceitos do CloudTrail](https://docs.aws.amazon.com/pt_br/awscloudtrail/latest/userguide/cloudtrail-concepts.html#cloudtrail-concepts-events)

<br />

---
Feito com ♥ by :man_astronaut: Guilherme Bezerra :wave: [Entrar em contato!](https://www.linkedin.com/in/gbdsantos/)