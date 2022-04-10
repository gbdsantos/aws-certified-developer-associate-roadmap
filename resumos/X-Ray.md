<p align="center">
	<img src="./img/aws-icons/aws-X-Ray.png" alt="aws-x-ray-icon" style="height:150px; width:150px;" /> 
  <br />
	<h1 align="center">
    X-Ray
  </h1>
</p>	

<br />

## :pushpin: Índice

- [Introdução](#introdução)
- [Compatibilidade do X-Ray](#compatibilidade-do-x-ray)
- [Como habilitar o X-Ray](#como-habilitar-o-x-ray)
- [Referências](#books-referências)

<br />

## Introdução

Amazon **X-Ray** é utilizada para realizar o debug das suas aplicações. Ele fornece uma análise visual da sua aplicação, resolução de problemas de performance, entender dependências em arquiteturas de micro-serviços, como cada solicitação(*request*) está se comportando e a sua resposta, qual serviço está causando problema, etc.

Debugar monolitos é muito mais fácil se comparado a serviços distribuídos e micro-serviços .

- Resolução de problemas de performance e erros
- Rastreamento distribuído de microsserviços

Disponível nas linguagens:

- C# .NET
- Go
- Java
- Node
- Python

O Amazon X-Ray recebe os dados dos serviços como *segmentos.*

## Compatibilidade do X-Ray

- API Gateway
- Elastic Beanstalk
- EC2 tanto em Cloud como servidores locais(*on-premise*)
- ECS
- ELB
- Lambda

## Como habilitar o X-Ray

1. O seu código deve importar a SDK do X-Ray
2. Executar o AWS X-Ray daemon no servidor em que estará a aplicação

<br />

## :books: Referências

Para uma compreensão mais profunda sobre Amazon X-Ray recomendo a leitura da documentação oficial, os links estão abaixo.

- [O que é o Amazon X-Ray?](https://docs.aws.amazon.com/pt_br/xray/latest/devguide/aws-xray.html)

<br />

---
Feito com ♥ by :man_astronaut: Guilherme Bezerra :wave: [Entrar em contato!](https://www.linkedin.com/in/gbdsantos/)