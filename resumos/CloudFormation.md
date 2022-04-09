<p align="center">
	<img src="./img/aws-icons/aws-CloudFormation.png" alt="aws-cloudFormation-icon" style="height:150px; width:150px;" /> 
  <br />
	<h1 align="center">
    Cloudformation
  </h1>
</p>	

<br />

## :pushpin: Índice

- [Introdução](#introdução)
- [Benefícios de utilizar o CloudFormation](#benefícios-de-utilizar-o-cloudformation)
- [Como o CloudFormation funciona](#como-o-cloudformation-funciona)
- [Implantando modelos do CloudFormation](#implantando-modelos-do-cloudformation)
- [Modelos](#modelos)
- [Introdução ao YAML](#introdução-ao-YAML)
- [O que são recursos?](#o-que-são-recursos)
- [O que são parâmetros?](#o-que-são-parâmetros)
- [Configurações de parâmetros](#configurações-de-parâmetros)
- [O que são mapeamentos?](#o-que-são-mapeamentos)
- [O que são saídas?](#o-que-são-saídas)
  - [Referênca de pilha cruzada](#referênca-de-pilha-cruzada)
- [O que são condicionais?](#o-que-são-condicionais)
- [Funções intrínsecas](#funções-intrínsecas)
- [Cross vs Pilhas Aninhadas](#cross-vs-pilhas-aninhadas)
- [StackSets](#stacksets)
- [CloudFormation Drift](#cloudformation-drift)
- [Referências](#books-referências)

<br />

## Introdução

Amazon **CloudFormation** é partir do código você cria modelos(*templates*). É um serviço que ajuda a modelar e configurar recursos da AWS, é muito fácil criar recursos, atualizá-los e apaga-los sem precisar ter que descobrir em qual ordem tem que fazer as coisas. Portanto, fazendo com que você gaste menos tempo para criar e configurar os recursos.

Portanto ao utilizar o CloudFormation você gerencia facilmente um conjunto de recursos como uma unidade.

> ⚠️ O Amazon CloudFormation é gratuito, porém os recursos da AWS que o CloudFormation cria serão cobrados de acordo com os padrões de uso para esses recursos.
> 

<br />

## Benefícios de utilizar o CloudFormation

- Replicação de infraestutura em várias regiões para casos em que é necessário ter mais disponibilidade
- Controlar e rastrear alterações de toda a infraestrutura com facilidade

<br />

## Como o CloudFormation funciona

Os conceitos principais são os **modelos(*templates*)** e **pilhas(stacks)**. Um modelo é um arquivo de texto JSON/YAML que descreve todos os recursos, suas propriedades e parâmetros. Esse modelo é utilizado para criar uma pilha do CloudFormation que efetivamente criará os recursos descritos no modelo.
O CloudFormation precisa que você tenha as permissões para provisionar os recursos que foram declarados no modelo.
Você pode salvar os modelos localmente ou em um *bucket* enviados para o S3. Se você especificar um arquivo de modelo armazenado localmente o CloudFormation fará upload dele em um *bucket* do S3 na sua conta AWS.

<br />

## Implantando modelos do CloudFormation

- **Forma manual:** Editando templates no CloudFormation Designer
- **Forma automatizada:** Editando templates em um **arquivo de texto em JSON/YAML** e usando a AWS CLI(Command Line Interface) para implantar os templates

<br />

## Modelos

No CloudFormation para construir um modelo você pode usar as linguagens JSON ou YAML.

- JSON é péssimo para o CloudFormation, pois fica muito ilegível
- YAML é mais interessante em diversos casos

```yaml
# Exemplo

Resources: # Criar recurso
	WebServers: # Chamado WebServers
		Type: AWS::EC2::Instance # Deste tipo
		Properties:
			AvailabilityZone: us-east-2a
			ImageId: ami-02bcbb802e03574ba
			InstanceType: t2.micro
```

<br />

## Introdução ao YAML

- Chave/Valor
- Objetos aninhados
- Suporta arrays
- Possível incluir comentários (diferentemente do JSON onde não é permitido)

<br />

## O que são recursos?

Recursos(*resources*) são o núcleo do seu modelo do CloudFormation, eles representam diferentes componentes na AWS.
O nome usado em um recurso no modelo é um nome lógico: `AWS::ProductIdentifier::ResourceType`

```yaml
 Resources:
  HelloBucket: # Nome do recurso, definido por você
    Type: AWS::S3::Bucket # Lembre-se, AWS::ProductIdentifier::ResourceType 
```

<br />

## O que são parâmetros?

Um parâmetro(*parameter*) é uma forma eficiente de especificar informações sensíveis como nomes de usuários e senhas que não devem ser armazenadas no próprio modelo e também é interessante para definir informações especificas ou a configurações do que está sendo implantando (ex: o nome de um domínio exclusivo para a aplicação)

<br />

## Configurações de parâmetros

- Type
    - String
    - Number
    - CommaDelimitedList
    - List<Type>
    - AWS Parameter
- Description
- Constraints
- ConstraintDescription (String)
- Min/MaxLength
- Min/MaxValue
- Defaults
- AllowerdValues (array)
- AllowedPattern (regexp)
- NoEcho(Boolean)

<br />

## O que são mapeamentos?

Mapeamentos(*mappings*) são utilizados para declarar valores condicionais. 

- **Sintaxe:** `!Fn [ <MapName>, <TopLevelKey>, <SecondLevelKey ]`

<br />

## O que são saídas?

As seções de saídas(*outputs*) são opcionais, e se a sua saída for exportada é possível importar esses valores para outros modelos(*templates*) do CloudFormation. Entretanto atente-se que ao utilizar os *outputs* e serem refenciadas em outro modelo(*template*) você não poderá excluir modelos que tenham sido referenciados em outro lugar. A seguir um exemplo com a sintaxe utilizando *outputs* com YAML:

```yaml
Outputs:
	StackSSHSecurityGroup:
	Description:
	Value: !Ref MyCompanyWideSSHSecurityGroup
	Export: # Este é um bloco opcional, mas se esse bloco não for especificado o valor não será exportado e logo não poderá ser importado
		Name: SSHSecurityGroup
```
<br />

### Referênca de pilha cruzada

Para importar o valor é utilizado o ***Cross Stack Reference***(Referência de Pilha Cruzada), criando um segundo modelo(*template*).

E novamente, a pilha anterior que contém os valores que foram referenciados não poderá ser excluída até que o segundo modelo(*template*) seja apagado.

```yaml
# Exemplo de Cross Stack Reference
Resources:
	MySecureInstance: 
		Type: AWS::EC2::Instance 
		Properties:
			AvailabilityZone: us-east-1a
			ImageId: ami-02bcbb802e03574ba
			InstanceType: t2.micro
			SecurityGroups: 
				- !ImportValue SSHSecurityGroup # Valor importado a partir de outro modelo(template)
```

<br />

## O que são condicionais?

Condicionais(*conditions*) são utilizadas para controlar a criação de recursos ou saídas com base em algumas instruções. As mais comuns são:

- Ambiente/*Environment* (dev  / test  / prod)
- Região AWS
- Qualquer valor de parâmetro

Cada condicional(*condition*) pode ser referenciada a outra condicional, valor de parâmetro ou *mapping*
Abaixo um exemplo com a sintaxe em YAML:

```yaml
 Conditions:
	CreateProdResources: !Equals [ !Ref EnvType, prod ]
```
<br />

## Funções intrínsecas

Funções intrínsecas(*Intrisic Functions*) serve para fazer referencias a outros recursos e suas propriedas. 

- Condition Functions (Fn:: If, Fn::Not, Fn::Equals, etc)

<br />

## Cross vs Pilhas Aninhadas

- **Cross Stacks**
  - Útil quando pilhas(stacks) possuem diferentes ciclos de vida
  - Usar Outputs Export e Fn::ImportValue
  - Quando é necessário exportar valores para muitas pilhas(*stacks*)
- **Pilhas Aninhadas**(***Nested Stacks*)**
  - Útil quando os componentes devem ser reutilizados e recriados
  - Nested Stacks somente é importantes para a pilha de nível superior (não é compartilhado entre pilhas(*stacks*))

<br />

## StackSets

StackSets é um funcionalidade que permite que você crie, atualize ou apague pilhas em várias contas e regiões em uma única operação. Mas isso só pode ser feito a partir de uma conta de administrador(*root account*).

<br />

## CloudFormation Drift

Cloudformation é excelente para criar insfraestruturas, porém não te protege contra alterações manuais de configuração.
Mas existe uma maneira de você descobrir se os recursos tiveram alterações manuais a partir do **CloudFormation Drift**(*desvio*).

<br />    

## 📚 Referências

Para uma compreensão mais profunda sobre Cloudformation recomendo a leitura da documentação oficial, os links estão abaixo.

<br />
    
- [O que é o AWS CloudFormation?](https://docs.aws.amazon.com/pt_br/AWSCloudFormation/latest/UserGuide/Welcome.html)  
- [Conceitos do AWS CloudFormation](https://docs.aws.amazon.com/pt_br/AWSCloudFormation/latest/UserGuide/cfn-whatis-concepts.html)
- [Detectar alteraçõẽs de configuração não gerenciadas em pilhas e recursos](https://docs.aws.amazon.com/pt_br/AWSCloudFormation/latest/UserGuide/using-cfn-stack-drift.html) 
- [Trabalhar com o StackSets](https://docs.aws.amazon.com/pt_br/AWSCloudFormation/latest/UserGuide/what-is-cfnstacksets.html)

<br />

---
Feito com ♥ by :man_astronaut: Guilherme Bezerra :wave: [Entrar em contato!](https://www.linkedin.com/in/gbdsantos/)
