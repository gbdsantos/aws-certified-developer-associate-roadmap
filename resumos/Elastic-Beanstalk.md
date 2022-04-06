# Elastic Beanstalk

## :pushpin: Índice

- [Introdução](#introdução)
- [Política de implantação](#política-de-implantação)
- [Política de ciclo de vida Beanstalk](#política-de-ciclo-de-vida-beanstalk)
- [Referências](#books-referências)

<br />

## Introdução

Este serviço gerencia e realiza o deployment de aplicações.
É possível implantar e gerenciar aplicações sem necessitar conhecer a infraestrutura que executa esses aplicativos.

O Elastic Beanstalk oferece suporte a aplicativos desenvolvidos em Go, Java, .NET, Node.js, PHP, Python e Ruby.

<br />

## Política de implantação

- **All at once (Tudo de uma vez):** O método de implantação mais rápido. O Elastic Beanstalk atualiza a nova versão em todas as instâncias. Nessa política a sua aplicação ficará indisponível(*downtime*) para os usuários.

- **Rolling (Contínua):** Nessa método é evitado o tempo de indisponibilidade(*downtime*) entretanto tem um tempo de implantação mais longo. A nova versão da aplicação é atualizada parcialmente(em lotes) por vez.

- **Rolling with additional batch (Contínua com lote adicional):** Nessa política é evitado uma disponibilidade reduzida mas com um tempo maior de implantação do que a *Rolling (Contínuo)*. A nova versão da aplicação é adicionada a lotes extras de instâncias.

- **Immutable (Imutável):** Um método mais lento e garante qque a nova versão da aplicação seja implantada em novas instâncias ao invés de atualizar as instâncias existentes como é o caso dos métodos anteriores.

- **Traffic splitting (Divisão de tráfego):** Usado quando é desejado testar a integridade da nova versão usando uma parte do tráfego recebido e mantendo a versão antiga.

<br />

## Política de ciclo de vida Beanstalk

Elastic Beanstalk **pode armazenar no máximo 1000 versões de aplicações**, portanto se você não remover as versões antigas não será possível fazer mais deploys. Então é necessário ir apagando as versões antigas das aplicações gradualmente e para fazer isso é  utilizado uma política de ciclo de vida do Beanstalk.
São baseadas no tempo, onde versões antigas serão removidas ou em espaço para quando existir muitas versões.

<br />

## :books: Referências

Para uma compreensão mais profunda sobre Elastic Beanstalk recomendo a leitura da documentação oficial, os links estão abaixo.


- [O que é o AWS Elastic Beanstalk?](https://docs.aws.amazon.com/pt_br/elasticbeanstalk/latest/dg/Welcome.html)
- [Como escolher uma política de implantação](https://docs.aws.amazon.com/pt_br/elasticbeanstalk/latest/dg/using-features.deploy-existing-version.html#deployments-scenarios)
- [Definir as configurações de ciclo de vida da versão do aplicativo](https://docs.aws.amazon.com/pt_br/elasticbeanstalk/latest/dg/applications-lifecycle.html)