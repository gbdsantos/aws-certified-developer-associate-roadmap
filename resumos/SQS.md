<p align="center">
	<img src="./img/aws-icons/aws-SQS.png" alt="aws-sqs-icon" style="height:150px; width:150px;" /> 
  <br />
	<h1 align="center">
    SQS
  </h1>
</p>	

<br />

## :pushpin: Índice

- [Introdução](#introdução)
- [O que é uma fila?](#o-que-é-uma-fila)
  - [Produtores(*producers*)](#produtoresproducers)
  - [Consumidores(*consumers*)](#consumidoresconsumers)
- [Tipos de filas](#tipos-de-filas)
  - [Filas Padrão(*Standard Queue*)](#filas-padrãostandard-queue)
  - [Filas FIFO](#filas-fifofirst-in-first-out-queue)
- [Fila de Mensagem Morta(*Dead Letter Queue*)](#fila-de-mensagem-mortadead-letter-queue)
- [Fila de Atraso(*Delay Queue*)](#fila-de-atrasodelay-queue)
- [Sondagem curta e longa(*Short and Long Polling*)](#sondagem-curta-e-longashort-and-long-polling)
- [Referências](#books-referências)

<br />

## Introdução

**SQS** é uma sigla para **Simple Queue Service**.

É um sistema de armazenamento de fila/processos que devem ser executados, **ele funciona 100% em pull**, isso significa que todos os serviços puxam informação do SQS.

As **mensagens dos SQS tem um tamanho máximo de 256K** e podem ser armazenadas entre 1 minuto para até 14 dias (por padrão ela fica 4 dias). Mas é possível armazenar o conteúdo de mensagens maiores que 256 KB usando S3 usando o *SQS Extended Client* que é uma biblioteca em Java que pode ser implementada em outras linguagens ou DynamoDB, o SQS criará um ponteiro no objeto do Amazon S3 por exemplo, ou pode dividir uma mensagem grande em mensagens menores.

Na prova se você observar sobre **desacoplamento de aplicativos** pense em SQS.

## O que é uma fila?

Existe uma fila SQS e ela conterá mensagens, e para conter mensagens alguma coisa precisa enviar essas mensagens para a fila do SQS e tudo que envia uma mensagem para o SQS é chamado de **Produtor(*Producer*)**, é possível ter um único produtor ou múltiplos produtores enviando mensagens para uma fila SQS. E alguma coisa precisa receber as mensagens para processa-lás e estes são chamados de **Consumidores(*consumers*)**.

### Produtores(*producers*)

Os produtores enviarão as mensagens usando a SDK, a mensagem será persistida no SQS enquanto o consumidor não a deletar. As mensagens estarão armazenadas no SQS entre 1 minuto para até 14 dias (por padrão ela fica 4 dias até no máximo 14 dias).

### Consumidores(*consumers*)

Os consumidores são aplicações(software) e eles podem estar sendo executados em instâncias EC2, servidores ou com Lambda. É ele que possui a responsabilidade de processar as mensagens.

- Recebem até 10 mensagens por vez da fila no SQS
- Apagam a mensagem na fila do SQS após finalizar o processamento dela
- Quando uma mensagem é pega pelo consumidor ela se torna invísivel para outros consumidores (*Message Visibility Timeout*), por padrão o tempo de expiração de invisibilidade da mensagem é de 30 segundos

<br />

## Tipos de filas

### Filas Padrão(*Standard Queue*)

**Filas padrão (***Standard Queue***):** Aqui é onde tem o *high throughput* (**TPS**: *transactions per second*) você pode enviar quantas mensagens quiser por segundo e a flia pode armazenar um número ilimitado de transações (*nearly-unlimited*). 

Garante que a mensagem ou processo vai ser entregue no mínimo uma vez. É a oferta mais antiga da AWS, foi um dos primeiros serviços na AWS.

- **Taxa de transferência ilimitada**, **número ilimitado de mensagens na fila**
- Retenção padrão de mensagens: 4 dias, máximo 14 dias. Isso significa que se você envia uma mensagem para a fila ela deve ser lida pelo consumidor e excluída da fila dentro deste período de retenção
- Baixa latência (< 10ms na publicação e recebimento)
- Limite de envio de 256KB por mensagem
- **Entrega pelo menos uma vez(*At-Least-Once Delivery*): U**ma mensagem é entregue pelo menos uma vez, mas às vezes, mais de uma cópia da mensagem é entregue. Por isso é possível ter mensagens duplicadas
- **Melhor Ordenação Possível(*Best-Effort Ordering*):** As mensagens podem ser entregues em uma ordem diferente do que elas foram enviadas

### Filas FIFO(*First in, First Out Queue*)

As filas FIFO(Primeiro a entrar, primeiro a sair) garante que o primeiro que chegar vai ser o primeiro que vai sair, isso significa que as mensagens são ordenadas, **a primeira mensagem que chegar na fila será a primeira a sair da fila** e também o **o*ne time processing***, ou seja, uma mensagem será processada somente uma vez diferente do tipo de fila *Standard Queue*. Com isso existe a limitação de 300 transações por segundo (TPS).
Neste tipo de fila você tem mais garantias e mais restrições.

- **Taxa de transferência LIMITADA** de 300 ou 3000 mensagens enviadas por lotes por segundo
- **Exactly-once:** A mensagem será processada somente uma vez garantido assim que não haverá duplicidades
- As mensagens são processadas pelo consumidor na mesma ordem em que foram enviadas pelo produtor

<br />

## Fila de Mensagem Morta(*Dead Letter Queue*)

Se o consumidor processar uma mensagem e fallhar a mensagem voltará para a fila do SQS e o mesmo consumidor ou outro pode tentar processa-lá e falhar novamente, perceba que isso acarreta em um loop de falha e para impedir isso vem o conceito de **Fila de Mensagem Morta(*Dead Letter Queue*)** onde é definido um limite para a quantidade de vezes em que o processamento de uma mensagem pode falhar, depois desse limite ser excedido a messabem vai para o DLQ(*Dead Letter Queue*), isto é útil para por exemplo fazer depuração(*debugging*)

<br />

## Fila de Atraso(*Delay Queue*)

Essa fila deve atrasar as mensagens para que os consumidores não as vejam imediatamente e isso pode ser um atraso de até 15 minutos, por padrão o parâmetro de atraso é de zero segundos e esse período pode ser sobrescrito por uma mensagem em específico.

<br />

## Sondagem curta e longa(*Short and Long Polling*)

- **Sondagam longa:** Quando um consumidor solicita mensagens da fila no SQS, ele pode opcionalmente aguardar a chegada das mensagens se não houver nenhuma na fila. Isso traz o benefício de diminuir chamadas de API na fila do SQS e portanto há um **diminuição de custo** computacional e logo de dinheiro. A sondagem longa pode ser definida em 1 até 20 segundos
- **Sondagem curta:** Quando um consumidor solicita mensagens da fila o SQS responde imediatamente mesmo que na consulta não exista qualquer mensagem. Por padrão, as filas usam a sondagem curta.

<br />

## :books: Referências

Para uma compreensão mais profunda sobre S3 recomendo a leitura da documentação oficial, os links estão abaixo.

- [O que é o Amazon SQS?](https://docs.aws.amazon.com/pt_br/AWSSimpleQueueService/latest/SQSDeveloperGuide/welcome.html)
- [Filas de atraso do Amazon SQS](https://docs.aws.amazon.com/pt_br/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-delay-queues.html)
- [Sondagem curta e longa do Amazon SQS](https://docs.aws.amazon.com/pt_br/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-short-and-long-polling.html)
