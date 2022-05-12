<p align="center">
	<img src="./img/aws-icons/aws-SAM.png" alt="aws-SAM-icon" style="height:150px; width:150px;" /> 
  <br />
	<h1 align="center">
    SAM
  </h1>
</p>	

<br />

## :pushpin: Índice

- [Introdução](#introdução)
- [Receita](#receita)
  - [Comandos](#comandos)
- [Executando funções lambda localmente](#executando-funções-lambda-localmente)
- [Template](#template)
- [Passo a passo para implantar](#passo-a-passo-para-implantar)  
- [SAR](#sar)
- [Referências](#books-referências)

<br />

## Introdução

Amazon SAM é uma acrônimo para **Serverless Application Model** é um framework focado para desenvolvimento e implantação de aplicações serverless. Sua configuração é feita por via de um arquivo YAML.

<br />

## Receita

O Transform Header indica que é um template `SAM: Transform: ‘AWS::Serverless-2016-10-31’`

Assim o Cloudformation saberá transformar esse modelo.

**Código:**

- AWS::Serverless::Function: Uma função lambda
- AWS::Serverless::Api: Define um API Gateway
- AWS::Serverless::SimpleTable: Uma tabela no DynamoDB

### Comandos

```Bash

sam build # Compilação da aplicação localmente, transforma um SAM template em um Cloudformation template (YAML)
aws cloudformation package or sam package # Pacote da aplicação, compacta em zip e pode enviar para um bucket no S3
aws cloudformation deploy or sam deploy # Implatanção da aplicação no CloudFormation
```

<br />

## Executando funções lambda localmente

Você pode complilar, testar e debugar as suas aplicações serverless que são definidas usando AWS SAM templates utilizando a SAM CLI.

<br />

## Template

```YAML
# SAM FILE
AWSTemplateFormatVersion: '2010-09-09'
Transform: 'AWS::Serverless-2016-10-31' # Essa linha define que é um SAM template
Description: A starter AWS Lambda function.
Resources:
  helloworldpython3:
    Type: 'AWS::Serverless::Function'
    Properties:
      Handler: app.lambda_handler
      Runtime: python3.6
      CodeUri: src/
      Description: A starter AWS Lambda function.
      MemorySize: 128
      Timeout: 3
      Environment:
        Variables:
          TABLE_NAME: !Ref Table
          REGION_NAME: !Ref AWS::Region
      Events:
        HelloWorldSAMAPI:
          Type: Api
          Properties:
            Path: /hello
            Method: GET
      Policies:
        - DynamoDBCrudPolicy:
            TableName: !Ref Table  

  Table:
    Type: AWS::Serverless::SimpleTable
    Properties:
      PrimaryKey:
        Name: greeting
        Type: String
      ProvisionedThroughput:
        ReadCapacityUnits: 2
        WriteCapacityUnits: 2
```        

<br />

## Passo a passo para implantar 

```Bash
# Criar um bucket s3
aws s3 s3://nome-do-bucket

# Pacote do Cloudformation
aws cloudformation package --s3-bucket nome-do-bucket --template-file template.yaml --output template-file gen/template-genereated.yaml
# ou
aws sam package --s3-bucket nome-do-bucket --template-file template.yaml --output template-file gen/template-genereated.yaml

# Implantação
aws cloudformation deploy --template-file <path-do-arquivo-template>.yaml --stack-name <nome-da-stack> --capabilities CAPABILITY_IAM
```

<br />

## SAR

SAR é um acrônimo para **Serverless Application Repository** é utilizado para montar, publicar e compartilhar repositórios de suas aplicações SAM.


<br />

## :books: Referências

Para uma compreensão mais profunda sobre SAM recomendo a leitura da documentação oficial, os links estão abaixo.

- [O que é AWS SAM?](https://docs.aws.amazon.com/pt_br/pt_br/serverless-application-model/latest/developerguide/what-is-sam.html)

<br />

---
Feito com ♥ by :man_astronaut: Guilherme Bezerra :wave: [Entrar em contato!](https://www.linkedin.com/in/gbdsantos/)