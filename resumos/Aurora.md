# Amazon Aurora

Não é necessário ter um conhecimento profundo sobre o Aurora, mas precisa ter uma visão geral de alto nível suficiente para entender o seu funcionamento.

Aurora é uma tecnologia proprietária da AWS, isto é, não é open-source.
Postgres e MySQL são compatíveis com o Aurora, além de que é uma tecnologia otimizada para ser usada na nuvem tendo performance superior em 5x do que o MySQL no RDS e 3x superior em comparação ao Postgres no RDS.

Mais algumas informações interessantes de se saber:

- Pode ter 15 réplicas enquanto MySQL tem 5 e o processo de replicação é mais rápido

- *Failover* no Aurora é instantâneo, por ele ser nativo em nuvem por padrão

- Possui um custo de 20% ou mais do que o RDS, mas é mais eficiente


- 6 cópias dos dados em 3 zonas de disponibilidades

- *Endpoint* de escrita (apontamento para a instância *master*) e *endpoint* de leitura

- Um volume de cluster do Aurora pode aumentar até o tamanho máximo de 128 tebibytes (TiB)

- Não possui utilização gratuita (*free-tier*)

<br />

## :books: Referências

Para uma compreensão mais profunda sobre Aurora recomendo a leitura da documentação oficial, os links estão abaixo.

- [O que é o Amazon Aurora?](https://docs.aws.amazon.com/pt_br/pt_br/AmazonRDS/latest/AuroraUserGuide/CHAP_AuroraOverview.html)

---
Feito com ♥ by :man_astronaut: Guilherme Bezerra :wave: [Entrar em contato!](https://www.linkedin.com/in/gbdsantos/)
