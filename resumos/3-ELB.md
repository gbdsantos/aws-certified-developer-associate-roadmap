# ELB

## :pushpin: Índice

- [Application Load Balancer](#application-load-balancer)
  - [Grupos de destino](#grupos-de-destino)
- [Network Load Balancer](#network-load-balancer)
- [Gateway Load Balancer](#gateway-load-balancer)
- [Referências](#book-referências)

<br />

ELB é um acrônimo para **Elastic Load Balancing** é o **balanceador de carga do tráfego** para seus múltiplos servidores (ex: instâncias EC2).

Um *load balancer* serve como **ponto único de contato para os clientes**. 

Até o momento presente onde isto foi escrito a AWS disponibiliza quatro tipos de balanceadores, que são os seguintes:

1. **Application Load Balancers (ALB):** Atua somente na camada de aplicação (*Layer 7*) com os protocolos http/https. Consegue identificar a origem e destino de pacotes.

2. **Network Load Balancers (NLB):** É específico para redes, atua na camada de transporte (*Layer 4*) com o protocolo TCP.

3. **Gateway Load Balancers (GWLB):** Atua na camada de rede (*Layer 3*) com o protocolo IP. 

4. **Classic Load Balancers:** É um load balancer legado e hoje a AWS não recomenda a sua utilização.

Os load balancers utilizam um sistema chamado ***x-foward for header***. No cabeçalho http/https tem um campo que ele preenche com o endereçamento de IP de origem, isso serve para o servidor requisitado e para o load balancer saber para quem retornar a resposta da requisição.

<br />

## Application Load Balancer 

-:pencil: [Visão geral do Application Load Balancer](https://docs.aws.amazon.com/pt_br/elasticloadbalancing/latest/application/introduction.html#application-load-balancer-overview)

<br />

Um **Application Load Balancer (ALB)** funciona na camada de aplicação (*Layer 7*) do modelo OSI (*Open Systems Interconnection*).

- Permite realizar o balanceamento de carga para vários aplicativos HTTP entre máquinas (grupos de destino / *target groups*)

- Permite realizar o balanceamento de carga para vários aplicativos na mesma máquina (ex: containers)

- Suporte para HTTP/2 e Websocket

- Suporta redirecionamento (de HTTP para HTTPS)

- Tabelas de roteamento para diferentes grupos de destino:
  - Roteamento baseado no path da URL (exemplo.com **/users** exemplo.com **/posts**)
  - Roteamento baseado na URL do hostname (exemplo.com e outro.exemplo.com)
  - Roteamento baseado em query strings e headers (exemplo.com/users? **id=123&order=false**)

O ALB é uma ótima opção para microsserviços e aplicativos baseados em contêiner (exemplo: Docker e Amazon ECS).
Em comparação é necessário multiplos CLB por aplicação.

### Grupos de destino

Os grupos de destino podem conter os seguintes items.

- Instâncias EC2 (podem ser gerenciadas pelo Auto Scaling Group)
- ECS tasks (gerenciado pelo próprio ECS)
- Funções Lambda

<br />

## Network Load Balancer

- :pencil: [Visão geral do Network Load Balancer](https://docs.aws.amazon.com/pt_br/elasticloadbalancing/latest/network/introduction.html#network-load-balancer-overview)

<br />

Um **Network Load Balancer (NLB)** funciona na camada de transporte (*Layer 4*) do modelo OSI (*Open Systems Interconnection*).

- Permite encaminhar tráfego TCP/UDP para suas instâncias.

- Processa milhões de requisições por segundo, portanto possui desempenho extremamente alto

- Menor latência ~100ms (*versus* 400ms para ALB)

- NLB tem **um IP estático por Zona de Disponibilidade** e suporta a atribuição de IP elástico

<br />

## Gateway Load Balancer

Um **Gateway Load Balancer (NLB)** funciona na camada de rede (*Layer 3*) do modelo OSI (*Open Systems Interconnection*). É o mais novo tipo balanceador de carga da AWS.

Exemplos de caso de uso, você gostaria que todo o seu tráfego de rede passe por um firewall ou por um sistema de detecção e prevenção de intrusão em nível de rede.

<br />

## Sticky Session

- :pencil: [Stick Sessions](https://docs.aws.amazon.com/pt_br/elasticloadbalancing/latest/application/sticky-sessions.html)

Sessões adesivas (*sticky sessions*) conhecida também como afinidade de sessão, para permitir que o load balancer vincule uma sessão de um usuário a um destino. É aplicado em Classic Load Balancers e Application Load Balancers.

Os Application Load Balancers suportam **cookies baseados em duração** e **cookies baseados em aplicativos**.

<br />

## Cross-Zone Load Balancing

- :pencil: [Balanceamento de carga entre zonas](https://docs.aws.amazon.com/pt_br/elasticloadbalancing/latest/classic/enable-disable-crosszone-lb.html)

Com balanceamento de carga entre zonas habilitado, o tráfego será distribuído uniformemente entre todas as instâncias EC2 uniformemente.

Já com o balanceamento de carga entre zonas de disponibilidade desabilitado as requisições são distribuídas nas instâncias a partir do nó do Elastic Load Balancer.

- Application Load Balancer
  - Sempre ativado e não pode ser desativado
  - Sem cobranças para dados entre AZ's

- Network Load Balancer
  - Desabilitado por padrão
  - É cobrado para dados entre AZs, se ativado

- Classic Load Balancer
  - Desabilitado por padrão
  - Sem cobranças para dados entre AZ, se ativado

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
