<p align="center">
	<img src="./img/aws-icons/aws-Route-53.png" alt="aws-Route-53-icon" style="height:150px; width:150px;" /> 
  <br />
	<h1 align="center">
    Route 53
  </h1>
</p>	

<br />

## :pushpin: Índice

- [Política de Roteamento](#política-de-roteamento)
- [TTL](#ttl)
- [Referências](#book-referências)

Route 53 é o serviço de Domain Name System DNS da AWS altamente disponível, escalonável e totalmente gerenciado e DNS autoritativo, desempenha três papéis principais: é um registrador de domínio(Domain Register), roteamento de DNS e também pode fazer verificações de integridadade(health check) se os recursos estão disponíveis e funcionais.

Para esse serviço é importante ter conhecimento básico sobre o que é o DNS e como ele funciona e sobre conceitos de registro de domínio. Leia [Conceitos do Amazon Route 53](https://docs.aws.amazon.com/pt_br/Route53/latest/DeveloperGuide/route-53-concepts.html), nele contém breve explicação sobre registro de domínio e também do DNS(*Domain Name System*).

- O registro de domínio não é vinculado a uma região
- Autoritativo = Que você pode atualizar os registros DNS para que tenha control total sobre o DNS

Route 53 suporta os seguintes tipos de registros DNS:

- A, AAAA, CNAME, NS

<br />

## TTL

É uma sigla para ***Time to Live**,* basicamente é o **tempo em que o endereço do servidor ficará armazenado em cache no cliente**(ex: browser) para que o mesmo não faça uma nova solicitação para o Route 53. 

Com um prazo longo de TTL é provavél que em uma mudança nos registros de domínio o cliente seja ainda direcionado para recursos antigos, enquanto que com um TTL com prazo de expiração mais curto você garante que os clientes acessaram os recursos sempre mais atualizados.

Claro que isto também impactará no custo, quanto mais requisições feitas para o Route 53 de consulta de DNS maior será o seu gasto assim como se o contrário ocorrer será mais barato. Ou seja, quanto maior o prazo de expiração do TTL menor será a ocorrência de consultas e menor será o custo com o Route 53 e quanto menor for o prazo de expiração do TTL for maior será a ocorrência de consultas e maior será o custo com o Route 53.

<br />

## Política de Roteamento

Política de roteamento(*routing policy*) é uma configuração para registros para como o Route 53 vai responder as consultas DNS.

- **Política de roteamento simples(*Simple routing policy*):** Será enviado uma requisição de DNS para cada servidor
- **Política de roteamento de failover(*Failover routing policy*):** Quando um servidor fica indisponível é feito o roteamento para outro servidor.
- **Política de roteamento de localização geográfica(*Geolocation routing policy*):** Rotear usuários baseado nas suas localizações enviando a requisição para o servidor mais próximo geograficamente
- **Política de roteamento de proximidade geográfica(Geoproximity routing policy):** Este é de acordo com os recursos que você tem disponíveis, e então o direcionamento é feito para o servidor mais próximo
- **Política de roteamento de latência(*Latency routing policy*):** Direciona o tráfego para o servidor de menor latência e não pela menor distância
- **Política de roteamento de resposta com vários valores(*Multivalue Answer Routing)*:** É semelhante ao Simple Routing
- **Política de roteamento ponderado(*Weighted routing policy*):** Você define o peso de tráfego para cada servidor (ex: servidor 1 50%, servidor 2 50%)

<br />

## :books: Referências

Para uma compreensão mais profunda sobre Route 53 recomendo a leitura da documentação oficial, os links estão abaixo.

- [O que é o Amazon Route 53?](https://docs.aws.amazon.com/pt_br/Route53/latest/DeveloperGuide/Welcome.html)    
- [Conceitos do Amazon Route 53](https://docs.aws.amazon.com/pt_br/Route53/latest/DeveloperGuide/route-53-concepts.html)   
- *[Time to Live*(TTL)](https://docs.aws.amazon.com/pt_br/Route53/latest/DeveloperGuide/route-53-concepts.html#route-53-concepts-time-to-live)  
- [Política de roteamento](https://docs.aws.amazon.com/pt_br/Route53/latest/DeveloperGuide/route-53-concepts.html#route-53-concepts-routing-policy)

<br />

---
Feito com ♥ by :man_astronaut: Guilherme Bezerra :wave: [Entrar em contato!](https://www.linkedin.com/in/gbdsantos/)