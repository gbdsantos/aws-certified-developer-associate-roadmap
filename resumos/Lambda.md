# Lambda

## :pushpin: Índice

- [Lambda Pricing](#lambda-princing)
- [Lambda versions](#lambda-versions)
- [Referências](#book-referências)

<br />

<div align="center">
<img src="./img/cloud-technology-evolution.png" width="70%" />
</div>

Lamba é um serviço AWS com arquitetura ***serverless***, a tradução literal é "sem servidor" mas não quer dizer que a infraestrutura será sem servidores e sim uma arquitetura que permite transferir mais das suas responsabilidades operacionais à AWS.
Este tipo de arquitetura permite criar e executar aplicações e serviços sem preocupações com servidores, como por exemplo o gerenciamento e provisionamento de capacidade (processamento e armazenamento)

<br />

## Lambda Pricing

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

Para uma compreensão mais profunda sobre S3 recomendo a leitura da documentação oficial, os links estão abaixo.
E outros links de referência.

- [Lambda Pricing]()
- :us: [Cloud Jorney](http://www.cyberniti.com/CloudJourney)
