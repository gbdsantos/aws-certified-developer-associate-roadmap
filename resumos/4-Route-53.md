# Route 53

## :pushpin: Índice

- [Política de Roteamento](#política-de-roteamento)
- [Referências](#book-referências)

Route 53 é o serviço de **Domain Name System DNS** da AWS. 

- O registro de domínio não é vinculado a uma região

## Política de Roteamento

- **Simple Routing:** Será enviado uma requisição de DNS para cada servidor
- **Failover Routing:** Quando um servidor fica indisponível é feito o roteamento para outro servidor.
- **Geolocation Routing:** Rotear usuários baseado nas suas localizações enviando a requisição para o servidor mais próximo geograficamente
- **Geoproximity Routing (Traffic Flow Only):** Este é de acordo com os recursos que você tem disponíveis, e então o direcionamento é feito para o servidor mais próximo
- **Latency-based Routing:** Direciona o tráfego para o servidor de menor latência e não pela menor distância
- **Multivalue Answer Routing:** É semelhante ao Simple Routing 
- **Weighted Routing:** Você define o peso de tráfego para cada servidor (ex: servidor 1 50%, servidor 2 50%)

<br />

## :books: Referências

Para uma compreensão mais profunda sobre Route 53 recomendo a leitura da documentação oficial, os links estão abaixo.

- [Documentação do Amazon Route 53](https://docs.aws.amazon.com/pt_br/route53/?id=docs_gateway)
