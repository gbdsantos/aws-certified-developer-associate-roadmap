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
- [Lambda e ALB](#lambda-e-alb)
  - [ALB Multi-Header Values](#alb-multi-header-values)
- [Chamadas Síncronas](#chamadas-síncronas)
- [Chamadas Assíncronas](#chamadas-assíncronas)
- [Mapeamento de origem do evento](#mapeamento-de-origem-do-evento)
- [Função de execução do Lambda](#função-de-execução-do-lambda)
- [Rastreamento Lambda com X-Ray](#rastreamento-lambda-com-x-ray)
- [Lambda e VPC](#lambda-e-vpc)
- [Simultaneidade e limitações](#simultaneidade-e-limitações)
- [Camadas Lambda](#camadas-lambda)
- [Imagens de contêiner](#imagens-de-contêiner)
- [Lambdas version](#lambda-versions)
  - [Versões](#versões)
  - [Alias](#alias)
- [Limites do Lambda](#limites-do-lambda)
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

## Lambda e ALB

Para o Lamba e ALB conseguirem trabalhar em conjunto é necessário criar um grupo de destino(target group) e adicionar a função lambda desejada.

### ALB Multi-Header Values

- ALB pode suportar ***multi header values*** (habilitado nas configurações do ALB)
- Quando você habilita o *multi-value headers*, *headers* HTTP e *query strings* que são enviados com múltiplos valores e mostrados como *arrays* dentro do evento AWS Lambda e objetos de resposta. Exemplo:

```bash
# HTTP (ALB)
http://exemplo.com/path?name=Maria&name=João

# JSON (Lambda)
queryStringParameters: {"name": ["foo", "bar"]}
```

<br />

## Chamadas Síncrona

Quando uma função lambda é chamada, a função é executada e aguarda uma resposta.

## Chamadas Assíncronas

Quando uma função lambda é chamada, a função é executada e aguarda uma resposta.

<br />

## Mapeamento de origem do evento

Última categoria de como o Lambda pode processar eventos na AWS. Aplica-se a: Kinesis Data Streams, SQS, SQS FIFO queue e DynamoDB Streams.

A invocação da função lambda é síncrona.

> Quando você usa o mapeamento de origem do evento para invocar a sua função, o Lambda usa a função de execução(IAM Role) para ler os dados do evento
>

<br />

## Função de execução do Lambda

A **função de execução(IAM *Role*)** garante a Lambda permissões para serviços/recursos da AWS.

Uma boa prática é criar uma função de execução por função Lambda.

Se a função lambda for invocada por outros serviços, é utilizado a política baseada em recursos(*Resource Based Policies*), que dá para outras contas AWS e serviços a permissão para usar o seu recurso Lambda.

<br />

## Rastreamento Lambda com X-Ray

Variáveis de Ambiente que se comunicam com o X-Ray:

- _X_AMZN_TRACE_ID
- AWS_XRAY_CONTEXT_MISSING
- AWS_XRAY_DAEMON_ADDRESS

<br />

## Lambda e VPC

Por padrão o Lambda não conseguirá acessar recursos em uma VPC, mas existe uma maneira de fazer com que ele possa. Você deve definir a VPC ID, Subnets e o Grupo de Segurança(Security Group)

Funções Lambda e uma VPC não possuem acesso a internet ou a um IP público.

- AWSLambdaVOCAccessExecutionRole

<br />

## Simultaneidade e limitações

- Simultaneidade reservada
- Simultaneidade provisionada

<br />

## Camadas Lambda

As Camadas Lambda(Lambda Layers) podem ter tempos de execução personalizados, bibliotecas, dados ou arquivos de configuração.

<br />

## Imagens de contêiner

É possível empacotar o seu código e dependências em uma imagem de contêiner do docker.

Implante funções Lambda em uma imagem de contêiner de até 10GB no ECR.

<br />

## Lambda versions

Tem o caso de uso para realizar testes (ex: testes A/B) e migrações de suas APIs.

Versões ARN:

- **Qualified:** Quando a versão de uma função lambda for *qualified* terá um sinal `$latest` do ARN. Aqui é possível criar uma nova versão a partir dela
- **Unqualified:** Se a versão de uma função lambda for *unqualifed* você não conseguirá ver a parte `$latest` no final do ARN. Não é possível fazer mais alterações.

### Versões

Enquanto você estiver trabalhando na sua função lambda a versão será `$LATEST` .

Versões são imutáveis, ou seja, isso significa que você não pode alterar mais nada no código ou em variáveis de ambiente.

Cada versão terá o seu próprio ARN(*Amazon Resource Name*).

Versões ARN:

- **Qualified:** Quando a versão de uma função lambda for *qualified** terá um sinal `$latest` do ARN. Aqui é possível criar uma nova versão a partir dela
- **Unqualified:** Se a versão de uma função lambda for *unqualifed** você não conseguirá ver a parte `$latest` no final do ARN. Não é possível fazer mais alterações

### Alias

São ponteiros que apontam para versões específicadas da sua função lambda. Por exemplo, alias definidos como dev, homol e prod, para utilizarem diferentes versões da função lambda.

Alias habilitam implantações do tipo Blue/Green atribuindo pesos de tráfego.
Aliases também terão os seus próprios ARNs e eles não podem fazer referência a outro alias.

<br />

## Limites do Lambda

- **Execução(*Runtime*)**
  - Alocação de memória: 128 MB - 10GB (incremento de 1 MB)
  - Tempo máximo de execução: 900 segundos (15 minutos)
  - Variáveis de ambiente: 4KB
  - Armazenamento temporário (/tmp): 512 MB
  - 1000 execuções simultâneas de uma função (pode ser aumentado abrindo um *ticket* na aws)
- **Implantação(*Deploy*)**
  - Tamanho máximo de compressão `.zip` de 50 MB
  - Tamanho máximo sem compressão de até 250 MB
  - Variáveis de ambiente: 4KB

<br />

## :books: Referências

Para uma compreensão mais profunda sobre Lambda recomendo a leitura da documentação oficial, os links estão abaixo.
E outros links de referência.

- [O que é o AWS Lambda?](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/welcome.html)
- [Mapeamentos de origem de eventos do Lambda](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/invocation-eventsourcemapping.html)
- [Usar camadas com sua função do Lambda](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/invocation-layers.html)    
- [Usar imagens de contêiner com o Lambda](https://docs.aws.amazon.com/pt_br/lambda/latest/dg/lambda-images.html)
- :us: [Cloud Jorney](http://www.cyberniti.com/CloudJourney)
