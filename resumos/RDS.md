# Amazon RDS

## :pushpin: Índice

- [RDS Réplicas de Leitura](#rds-réplicas-de-leitura)
- [Cobrança](#cobrança)
- [Criptografia](#criptografia)
  - [Operações de criptografia RDS](#operações-de-criptografia-RDS)
- [Referências](#books-referências)

<br />

É um acrônimo para **Amazon Relational Database Service**, este é um serviço para gerenciamento de banco de dados que usa SQL como linguagem de consulta e permite que você crie banco de dados relacionais na nuvem que serão gerenciados pela AWS.

Bancos de dados disponíveis:

- Aurora (Banco de dados proprietário AWS)
- MariaDB
- Microsoft SQL Server
- MySQL
- Oracle
- Postgres

A vantagem de se utilizar esse serviço é que a AWS assume algumas responsabilidades de gerenciamento mais complicadas e maçantes, como por exemplo o controle e gerenciamento de *backups*.

<br />

## RDS Réplicas de Leitura

- É possível criar <span style="background-color: #FFFF00; border-radius: 8%; color: #000; font-weight: bold; padding: 2px">5 Réplicas de Leitura</span>

- Elas podem estar na **mesma zona de disponibilidade (AZ)**, em **zona de disponibilidade cruzada** ou em **região cruzada**. São **três opções**

- A replicação é assíncrona entre a instância principal RDS e das réplicas de leitura. Isso significa que as leituras são eventualmente consistentes
- Recuperação contra desastres com Multi AZ (*Disaster Recovery*)

<br />

## Cobrança

Na AWS normalmente há um custo quando os dados vão de uma zona de disponibilidade (AZ) para outra, mas há execeções e essas excessões são para serviços gerenciados.
O RDS é um serviço gerenciado. Sobre o custo de rede associado à réplica de leitura no RDS,  se a sua réplica de leitura estiver na mesma região e zona de disponibilidade diferente você não terá custo de tráfego de dados, ou seja <span style="background-color: #FFFF00; border-radius: 8%; color: #000; font-weight: bold; padding: 2px">a replicação assíncrona é gratuita quando RDS réplica de leitura estão na mesma região mesma quando o tráfego vá de uma zona de disponibilidade para outra</span>.
Mas se você estiver usando uma réplica de região cruzada isso causará em um custo de replicação para sua rede.

<br />

## Criptografia

- :pencil: [Limitações de instâncias criptografadas de banco de dados do Amazon RDS](https://docs.aws.amazon.com/pt_br/AmazonRDS/latest/UserGuide/Overview.Encryption.html#Overview.Encryption.Limitations)

- **Criptografia em repouso** (*At rest encryption*)
  - É possível criptografar a instância principal (*master*) e as réplicas de leitura (*slave*) com AWS KMS AES-256 encryption

  - **É feito somente quando você cria o seu primeiro banco de dados**

  - Ou quando o <span style="background-color: #FFFF00; border-radius: 8%; color: #000; font-weight: bold; padding: 2px">banco de dados está descriptografado > criar  *snapshot* > copiar o *snapshot* criptografado > criar banco de dados a partir do *snapshot* criptografado</span>

  - Se o <span style="background-color: #FFFF00; border-radius: 8%; color: #000; font-weight: bold; padding: 2px">master não estiver criptografado, as réplicas de leitura não estarão criptografadas</span>

  - Transparent Data Encryption (TDE) disponível somente para Oracle e SQL Server

- **Criptografia em voo** (*In-flight encryption*)
  - Certificados SSL para criptografar os dados para o RDS em voo. Portanto, ao ser enviado do cliente para o banco de dados
  
  - Fornece opções SSL de certificados confiáveis quando conectado no banco de dados
  
  - Para impor o SSL para garantir que todos usem SSL:
    - PostgreSQL: `rds.force_ssl=1` no console AWS RDS (Grupos de Parametros)
    
    - MySQL: Dentro do banco de dados executar o comando: `GRANT USAGE ON *.* TO 'mysqluser'@'%' REQUIRE SSL;`

### Operações de criptografia RDS

- Criptografia em backups RDS
  - *Snapshots* estarão descriptografados se o banco de dados RDS estiver descriptografado por padrão

  - Assim como as *snapshots* estarão criptogradas se o banco de dados RDS estiver criptografado por padrão


<br />

## :books: Referências

Para uma compreensão mais profunda sobre RDS recomendo a leitura da documentação oficial, os links estão abaixo.

- [O que é o Amazon RDS?](https://docs.aws.amazon.com/pt_br/AmazonRDS/latest/UserGuide/Welcome.html)
- [Criptografar recursos do Amazon RDS](https://docs.aws.amazon.com/pt_br/AmazonRDS/latest/UserGuide/Overview.Encryption.html)
- [Limitações de instâncias criptografadas de banco de dados do Amazon RDS](https://docs.aws.amazon.com/pt_br/AmazonRDS/latest/UserGuide/Overview.Encryption.html#Overview.Encryption.Limitations)

---
Feito com ♥ by :man_astronaut: Guilherme Bezerra :wave: [Entrar em contato!](https://www.linkedin.com/in/gbdsantos/)
