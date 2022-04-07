# Amazon CodeCommit

## :pushpin: Índice

- [Introdução](#introdução)
  - [Continous Integration (CI)](#continous-integration-ci)
  - [Continous Delivery (CD)](#continous-delivery-cd)
- [Referências](#books-referências)

<br />

## Introdução

O CodeCommit é um serviço de controle de versão de código-fonte similar ao Bitbucket/Github/GitLab, que hospeda repositórios privados.

- Controle de origem
- Versões
- Atualizações
- Colaboração

Abaixo um breve resumo de conceitos importantes de se entender para os estudos posteriores dos serviços CodeCommit, CodeBuild, Code Deploy, CodePipeline, CodeStar, CodeArtifact e CodeGuru da AWS, todas ferramentas do desenvolvedor.

### Continous Integration (CI)

Os desenvolvedores enviam o seu código com muita frequência para um repositório central de código (ex: Bitbucket, **AWS CodeCommit**, Github, etc).
Em seguida existirá um servidor para testes onde será verificado se o código está funcionando e se comportando conforme o esperado (ex: **AWS CodeBuild**, Jenkins, etc).
Se no código existir algum problema, volta-se para a etapa anterior para realizar as correções de bugs e erros.
Não encontrado nenhum problema nos testes ou após a correções de bugs/erros o código está pronto para o deploy (ex: **AWS CodeDeploy**, **AWS Elastic Beanstalk**).  

### Continous Delivery (CD)

O primeiro ponto é que Continuous Delivery !== Continuous Deploy, as pessoas confudem bastante ambos os termos, achando até que são nomenclaturas diferentes para um mesmo significado.

A ideia do CD (Entrega contínua / *Continous Delivery*) é mudar a mentalidade de a equipe tem publicações de versão mais demoradas como por exemplo uma versão nova a cada seis meses para publicação de novas versões diariamente.

<br />

## :books: Referências

Para uma compreensão mais profunda sobre S3 recomendo a leitura da documentação oficial, os links estão abaixo.

- [O que é o AWS CodeCommit?](https://docs.aws.amazon.com/pt_br/codecommit/latest/userguide/welcome.html)
- [Praticando Integração Contínua e Entrega Contínua na AWS](https://d0.awsstatic.com/whitepapers/DevOps/practicing-continuous-integration-continuous-delivery-on-AWS.pdf) :us: