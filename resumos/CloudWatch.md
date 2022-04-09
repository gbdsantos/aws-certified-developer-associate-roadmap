<p align="center">
	<img src="./img/aws-icons/aws-CloudWatch.png" alt="aws-cloudwatch-icon" style="height:150px; width:150px;" /> 
  <br />
	<h1 align="center">
    CloudWatch
  </h1>
</p>	

<br />

## :pushpin: Índice

- [Introdução](#introdução)
- [Métricas](#métricas)
- [Métricas personalizadas](#métricas-personalizadas)
- [Logs](#logs)
  - [Filtros de métricas](#filtros-de-métricas)
- [Alarmes](#alarmes)
- [CloudWatch logs para EC2](#cloudwatch-logs-para-ec2)
- [Eventos](#eventos)
- [Referências](#books-referências)

<br />

## Introdução

Amazon **CloudWatch** permite coletar métricas e logs para fins de monitoramento e análise, enviar notificações quando algo acontece no seu ambiente AWS, alarmes para reagir em tempo real a métricas e eventos. Conceitos chaves:

- Métricas
- Logs
- Eventos
- Alarmes

<br />

## Métricas

CloudWatch fornecerá métricas para cada serviço em andamento e o que cada uma delas significa. 
Métrica é uma variável para se monitorar ao longo do tempo (ex: Utilização de CPU, Latência, etc). As **métricas pertencem a um *namespace***, podem existir no máximo 10 **dimensões** em uma métrica e as métricas existem somente na região em que são criadas.

<br />

## Métricas personalizadas

É possível definir as suas próprias métricas customizadas. 

Para publicar uma métrica personalizada no Amazon CloudWatch com o seguinte comando:

```bash
 aws cloudwatch put-metric-data --namespace "Usage Metrics" --metric-data file:://metric.js
```

```json
// metric.js
[
	{
		"MetricName": "NewPosts",
		"Timestamp":  "Wednesday, April 09, 2022 8:28:20 PM",
		"Value": 0.50,
		"Unit": "Count"
	}
]
```

⚠️ É importante estar atento ao carimbo de data/hora(*timestamp*) que pode ser de **até duas semanas no passado e até duas horas no futuro**. Se você não fornecer um carimbo de data/hora, o CloudWatch criará um carimbo de data/hora para você com base no momento em que o ponto de dados foi recebido.
Se você fornecer um carimbo de data/hora que não está sincronizado com o seu serviço os dados da métrica personalizada ficaram incosistentes.

<br />

## Logs

Funcionalidade do CloudWatch onde os logs são agrupados em **grupos de logs*(Log groups*)**  e dentro de cada grupo de logs existe o **fluxo de logs(*Log stream*)**. 

Pode ser definido uma política de expiração de logs (ex: nunca expira, 1 dia,  1 semana, etc).
Estes logs podem ser enviados para o Amazon S3, Kinesis Data Streams, Kinesis Data Firehose, Lambda e ElasticSearch.

### Filtros de métricas

Filtros de métricas permitem usar empressões de filtro para procurar alguma informação dentro de um log ou contar o número de ocorrências de qualquer coisa definida como o parâmetro e esses filtros métricos podem ser usados para acionar Alarmes se atingir um determinado limite inicialmente definido.

<br />

## Alarmes

Alarmes são usados para acionar notificações por qualquer métrica, eles possuem três estados: 

- Ok
- INSUFFICIENT_DATA
- ALARM

Os alarmes têm três alvos principais: 

1. Instâncias EC2(Parar, Encerrar, Reiniciar ou Recuperar)
2. Acionar  ação do ASG
3. Enviar notificações para SNS

Para fins de testes dos alarmes e notificações de alarmes, pode-se uitlizar a CLI:

```bash
aws cloudwatch set-alarm-state --alarm-name "myalarm" --state-value ALARM --state-reason "testing purposes" 
```

<br />

## CloudWatch logs para EC2

- Por padrão os logs de instâncias EC2 não são enviados para o CloudWatch
- É necessário executar o CloudWatch agent na instância EC2 para enviar os arquivos de logs. O agente de log do CloudWatch também pode ser configurado em servidores locais.
- Verifique se as permissões IAM estão corretas.

## Eventos

CloudWatch Events você pode interceptar eventos que acontecem de dentro dos serviços AWS, também é possível interceptar qualquer chamada de API com intregração com o CloudTrail.

Para esse serviço existem uma versão aprimorada dele chamada Amazon EventBridge.

<br />

## 📚 Referências

- [O que é o Amazon CloudWatch?](https://docs.aws.amazon.com/pt_br/AmazonCloudWatch/latest/monitoring/WhatIsCloudWatch.html)
- [Conceitos do Amazon CloudWatch](https://docs.aws.amazon.com/pt_br/AmazonCloudWatch/latest/monitoring/cloudwatch_concepts.html)

<br />

---
Feito com ♥ by :man_astronaut: Guilherme Bezerra :wave: [Entrar em contato!](https://www.linkedin.com/in/gbdsantos/)
