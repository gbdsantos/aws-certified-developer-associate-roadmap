<p align="center">
	<img src="./img/aws-icons/aws-EC2.png" alt="aws-ec2-icon" style="height:150px; width:150px;" /> 
  <br />
	<h1 align="center">
    EC2
  </h1>
</p>	

<br />

## :pushpin: Índice

- [Tipos de instâncias EC2](#tipos-de-instâncias-ec2)
- [Opções de compra de instâncias do EC2](#opções-de-compra-de-instâncias-do-ec2)
- [EBS Volume](#ebs-volume)
  - [Tipos de volume EBS](#tipos-de-volume-ebs)
- [AMI](#ami)
- [Instance Store](#instance-store)
- [ASG](#asg)

<br />

EC2 é uma sigla para o ***Elastic Compute Cloud***, é um serviço da web que fornece capacidade de computação redimensionável na nuvem.
O serviço torna possível a criação de instâncias de máquinas virtuais para utilização, eliminando assim a necessidade de ser ter um *hardware* físico. Portanto sendo o hardware o nível de abstração.
Este é um dos primeiros serviços que foi disponibilizado na AWS.

Provavelmente a maior vantagem ao se usar EC2 é o custo, pois atualmente é muito caro você ter e manter uma infraestrutura própria aliado a isso tem sua facilidade de escabilidade, por exemplo aumento do número de máquinas (escabilidade horizontal) ou de aumento de recursos como aumento de memória ram e processamento (escabilidade vertical).

<br />

## Tipos de instâncias EC2

Existem cinco tipos principais conforme relacionado na tabela abaixo:

| Instance Family | Casos de Uso |
|:--------------- |:------------- |
| Proposta Geral (*General purpose*) <br /> ( A1, T3, T3A, T2, M6g, M5, M5a, M5n, M4) | - Baixo tráfego para websites e aplicações web <br /> - Pequenos e médios bancos de dados |
| Computação otimizada (*Compute optimized*) <br /> (C5, C5n, C4, C6) | - Alta performance para servidores web <br />- *video-enconding* |
| Memória otimizada (*Memory optimized*) <br /> (R5, R5a, R5n, R4, X1e, X1, High Memory, z1d) | - Alta performance para banco de dados <br />- Cache de memória distribuídos |
| Armazenamento otimizado (*Storage optimized*) <br /> (I3, I3en, D2, H1 ) | - Data warehousing <br />- Logs ou aplicações de processamento de dados |
| Computação Acelerada (*Accelerated Computing*) <br /> (P3, P2, Inf1, G4, G3, F1) | - Visualização 3D <br />- Machine Learning |

<br />

## Opções de compra de instâncias do EC2

Em questão de cobrança na AWS você pode optar pelas opções abaixo.

- **Free tier:** 12 meses para utilizar instâncias t2.micro gratuitamente.

- **On Demand:** Ligar ou desligar um *virtual machine* (VM) e pagar por hora/minuto/segundo. A cobrança é feita após utilização.
- **Reserved:** Contrato com AWS entre 1~3 anos de uma máquina. A cobrança é feita antes da utilização, por exemplo, você irá adquirir um contrato de 3 anos já será pago antecipadamente por todas as máquinas que serão disponibilizados por todo esse prazo.
- **Spot:** Ou chamados de *Bid*, são para aplicações específicas que tem que ficar ligar por determinado período de tempo (ex: ficarem ligadas somente durante o horário comercial), tem um dimensionamento mais fixo de alocação de recursos (memória, processamento e armazenamento)
- **Dedicated Hosts:** São máquinas/servidores físicos que são dedicados para você. São principalmente utilizados por exemplos por empresas do setor financeiro ou empresas que devem proteger muito o dados do seu cliente.

As que são mais comuns de serem utilizadas são *on demand* e *reserved*.

<br />

## EBS volume

EBS é uma sigla para ***Elastic Block Store***. Basicamente é uma virtualização de disco (armazenamento) depois esse volume EBS é anexado ao sistema operacional. 
Existem **dois tipos de disco**, **HDD** (*Hard Disk Drive*) e **SSD** (*Solid State Drive*). Casos de uso para o EBS é para armazenamento de longo prazo.

Um volume EBS  **é uma unidade de rede que você pode anexar** a suas instâncias enquanto elas são executadas. 
Permite que suas instâncias persistam dados, mesmo após o término. **Só podem ser montados em uma instância por vez (no nível CCP - Certified Cloud Practitioner)**
Os **volumes EBS estão vinculados a uma zona de disponibilidade específica**.

Analogia: Pense neles como um "pendrive USB de rede", é uma unidade de rede (ou seja, não uma unidade física), ele usa a rede para comunicar a instância, o que significa que pode haver um pouco de latência.

Mais alguns detalhes sobre volumes EBS:

- Pode ser desanexado de uma instância do EC2 e anexado a outra rapidamente

- Está **bloqueado em uma zona de disponibilidade (A-Z)** ( ex: você não consegue acessar o volume EBS que está na zona de disponibilidade us-east-1a a partir da zona de disponibilidade us-east-1b)

- Um volume EBS em us-east-1 não pode ser anexado a us-east-1b
- Para mover um volume, primeiro você precisa fazer um *snapshot*
- Ter uma capacidade provisionada (tamanho em GBs e IOPS)

Observação:
- **Para o exame CPP (Certified Cloud Practitioner):** Um EBS só pode ser montado em uma instância do EC2
- **Para o exame Associate (Arquiteto de Soluções, Desenvolvedor, SysOps):**  Existe o recurso **"multi-attach"** para alguns tipos de volumes EBS(io1/io2)

Alguns termos importantes para entender o que significa:

- ***IOPS***(*Input/Output per Second*): Quantidade de operação por segundo.

- ***Throughput***: Tamanho em megabits que é possível escrever no disco.

- ***Multi-Attach:*** Funcionalidade em que se pode anexar um único volume EBS em múltiplas instâncias EC2, entretanto isso só é possível em volumes EBS do tipo io1 e io2.

<br />

### Tipos de volume EBS

- **HDD**
  - ST1: Categoria para *throughput* otimizado, os discos possuem um valor mais baixo.
  - SC1: Também chamado de *code disk*, os discos dessa categoria também possuem um valor mais baixo.
- **SSD**
  - IO1/IO2: Atualmente este é a categoria de disco mais cara da AWS, pois ele é destina para alta performance.
  - GP2/GP3: Este é um pouco caro, mas não tanto quanto o IO1.

<br />

## AMI

AMI é um acrônimo para ***Amazon Machine Image***. É uma imagem compatível do Linux, entenda que não é que o sistema operacional é instalado do zero, a instância já existe, a AWS faz uma cópia dessa instância.
Seu objetivo é fornecer uma ambiente de execução estável e seguro para o Amazon EC2.
Portanto tem integração as ferramentas da AWS com pacotes pré-instalados e configuração segura e um conjunto menor de pacotes, entretanto fornecendo uma base funcional, pois tendo uma base menor de pacotes significa que há menos componentes para manter, consequentemente uma área menor para possíveis brechas e/ou violações de segurança.

É possível criar suas próprias AMI, com os seus sofwares e configurações mais utilizados para se ter tempo de inicialização e configuração mais rápida.

<br />

## Instance Store

O armazenamento de instância( *instance store* ) **fornece armazenamento temporário**, esse armazenamento está localizado em discos físicos anexado a instância do EC2.
A instância **perderá todos os dados se for parada (*stop*), hibernada(*hibernate*) ou encerrada (*terminate*)**, portanto é chamado de armazenamento efêmero. Casos de uso são para buffer, cache e conteúdo temporário.

<br />

## ASG

É um acrônimo para o **Auto Scaling Group** é utilizado para aumentar e reduzir cargas (adicionando ou removendo instâncias EC2) realizando a escalabilidade automática, podendo ser definido um número mínimo e máximo de instâncias.

Um grupos de Auto Scaling pode conter instâncias EC2 em zonas de disponibilidade diferentes em uma mesma região, porém não podem ter grupos de Auto Scaling em múltiplas regiões para uma mesma aplicação.

Existem quatro formas de realizar a escalabilidade horizontal com o ASG. Escalabilidade manual, dinâmica,preditiva e programada.

- **Escalabilidade manual:** Você pode alterar o tamanho de um grupo do Auto Scaling manualmente, esta forma é utilizada quando a escalabilidade automática não é necessária ou quando você quer manter a capacidade computacional em um número fixo.

- Escalabilidade dinâmica: É definido como a escala será feita a partir de uma demanda alterada. Existem três tipos de escalabilidade dinâmica, simples, em etapas e com monitoramento do objetivo.

- **Escalabilidade preditiva:** Para aumentar o número de instâncias EC2 no ASG antecipando padrões diários e semanais a partir do fluxo de tráfego.

- **Escalabilidade programada:** Esta forma permite que você defina a sua própria programação (leia-se data) de escalabilidade, com mudanças previsíveis.

<br />

## :books: Referências

Para uma compreensão mais profunda sobre EC2 + ASG recomendo a leitura da documentação oficial, os links estão abaixo.

- [Documentação Oficial - Amazon Elastic Compute Cloud (EC2)](https://docs.aws.amazon.com/pt_br/pt_br/AWSEC2/latest/WindowsGuide/concepts.html)
- [Tipos de instância do Amazon EC2](https://aws.amazon.com/pt/ec2/instance-types/)
- [EC2 - Preço sob demanda](https://aws.amazon.com/pt/ec2/pricing/on-demand/)
- [O que é o Amazon EC2 Auto Scaling?](https://docs.aws.amazon.com/pt_br/autoscaling/ec2/userguide/what-is-amazon-ec2-auto-scaling.html)
- [Opções de Escalabilidade](https://docs.aws.amazon.com/pt_br/autoscaling/ec2/userguide/scaling_plan.html#scaling_typesof)

---
Feito com ♥ by :man_astronaut: Guilherme Bezerra :wave: [Entrar em contato!](https://www.linkedin.com/in/gbdsantos/)
