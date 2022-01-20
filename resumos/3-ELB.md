# ELB

## :pushpin: Índice

- [Referências](#book-referências)

<br />

ELB é um acrônimo para **Elastic Load Balancing** é o **balanceador de carga do tráfego** para seus múltiplos servidores (ex: instâncias EC2).
Até o momento presente onde isto foi escrito a AWS disponibiliza quatro tipos de balanceadores, que são os seguintes:

1. **Application Load Balancers (ALB):** Atua somente na camada de aplicação (*Layer 7*) com os protocolos http/https. Consegue identificar a origem e destino de pacotes.

2. **Network Load Balancers (NLB):** É específico para redes, atua na camada de transporte (*Layer 4*) com o protocolo TCP.

3. **Gateway Load Balancers (GWLB):** Atua na camada de rede (*Layer 3*) com o protocolo IP. 

4. **Classic Load Balancers:** É um load balancer legado e hoje a AWS não recomenda a sua utilização.

Os load balancers utilizam um sistema chamado ***x-foward for header***. No cabeçalho http/https tem um campo que ele preenche com o endereçamento de IP de origem, isso serve para o servidor requisitado e para o load balancer saber para quem retornar a resposta da requisição.


<br />

## :books: Referências

Para uma compreensão mais profunda sobre ELB recomendo a leitura da documentação oficial, os links estão abaixo.

- [O que é o Elastic Load Balancing?](https://docs.aws.amazon.com/pt_br/elasticloadbalancing/latest/userguide/what-is-load-balancing.html)
- [O que é Application Load Balancer?](https://docs.aws.amazon.com/pt_br/elasticloadbalancing/latest/application/introduction.html)
- [O que é um Network Load Balancer?](https://docs.aws.amazon.com/pt_br/elasticloadbalancing/latest/network/introduction.html)
- [O que é um Gateway Load Balancer](https://docs.aws.amazon.com/pt_br/elasticloadbalancing/latest/gateway/introduction.html)
- [O que é um Classic Load Balancer?](https://docs.aws.amazon.com/pt_br/elasticloadbalancing/latest/classic/introduction.html)


<br />

---
Feito com ♥ by :man_astronaut: Guilherme Bezerra :wave: [Entrar em contato!](https://www.linkedin.com/in/gbdsantos/)
