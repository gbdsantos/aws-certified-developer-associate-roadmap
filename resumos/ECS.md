# Amazon ECS

## :pushpin: Índice

- [ECS Clusters](#ecs-clusters)
- [Fargate](#fargate)
- [Estratégias de posicionamento de tarefas do Amazon ECS](#estratégias-de-posicionamento-de-tarefas-do-amazon-ecs)
- [Referências](#books-referências)

<br />

 Amazon ECS é o acrônimo para **Amazon Elastic Container Service, é um serviço de gerenciamento de containers.
 
<br />

## ECS Clusters

São um agrupamento lógico de instâncias do EC2 que são executadas no ECS agent (container do Docker).
As instâncias EC2 executam uma AMI feita especialmente para o ECS. 

<br />

## ECR

ECR é o acrônimo para **Elastic Container Registry** é o repositório de imagens Docker privadas da AWS.

Para se autenticar no ECR via CLI existem duas maneiras. Se você estiver usando a versão 1 da CLI da AWS o comando será diferente do da versão 2.

```Bash
# AWS CLI v1 login command, with parenthesis and $
$(aws ecr get-login --no-include-email --region eu-west-I)

# AWS CLI v2
aws ecr get-login-password --region eu-west-I | docker login --username AWS --password-stdin 123456890.dkr.ecr.eu-west-I.amazonaws.com
```
<br />

## Fargate

É um serviço da AWS serverless, onde você não precisa provisionar instâncias EC2 no caso de querer escalonar o seu ECS Cluster.

<br />

## Estratégias de posicionamento de tarefas do Amazon ECS

A estratégia de posicionamento de tarefas é um algoritmo para escolher as instâncias e definir as tarefas para ela.

### Tipos de estratégia

- Binpack: As tarefas são alocadas para deixar a menor quantidade de CPU ou memória não utilizada.
- Random: AS tarefas são dispostas aleatoriamente, não há uma lógica.
- Spread: As tarefas são colocadas uniformemente de acordo com o valor especificado.

<br />

## Volumes ECS

Existem algumas opções que podem ser utilizadas como volumes para armazenamento de acordo com o seu objetivo.

- EFS
- Docker: Um volume de docker na instância host do EC2
- FSx for Windows File Server
- Montagens bind: Um arquivo ou diretório no host(ex: Uma instância EC2), é montado em um contêiner.


<br />

## :books: Referências

Para uma compreensão mais profunda sobre ECS recomendo a leitura da documentação oficial, os links estão abaixo.

- [O que é o Amazon Elastic Container Service?](https://docs.aws.amazon.com/pt_br/AmazonECS/latest/developerguide/Welcome.html)
- [Amazon ECS no AWS Fargate](https://docs.aws.amazon.com/pt_br/AmazonECS/latest/developerguide/AWS_Fargate.html)
- [Estratégias de posicionamento de tarefas do Amazon ECS](https://docs.aws.amazon.com/pt_br/AmazonECS/latest/developerguide/task-placement-strategies.html)
- [Usar volumes de dados em tarefas](https://docs.aws.amazon.com/pt_br/AmazonECS/latest/developerguide/using_data_volumes.html)

---
Feito com ♥ by :man_astronaut: Guilherme Bezerra :wave: [Entrar em contato!](https://www.linkedin.com/in/gbdsantos/)
