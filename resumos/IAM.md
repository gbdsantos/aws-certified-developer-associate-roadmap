<p align="center">
	<img src="./img/aws-icons/aws-IAM.png" alt="aws-IAM-icon" style="height:150px; width:150px;" /> 
  <br />
	<h1 align="center">
    IAM
  </h1>
</p>	

<br />

## :pushpin: Índice

- [Características](#características)
- [Boas práticas](#boas-práticas)
- [STS](#sts)
- [Referências](#books-referências)

<br />

Acrônimo para *Identity and Access Management* (IAM), é onde é possível criar usuários (*users*), grupos (*groups*), funções (*roles*), políticas (*policies*) e permissões (*permissions*) para controlar qual serviço/recurso os usuários podem acessar. 
Segue o **modelo de responsabilidade compartilhada** da AWS.

O IAM possui compatibilidade com o **PCI DSS Compliance** (*Payment Card Industry Data Security Standard*) que basicamente é um padrão de segurança da informação para empresas que lidam com cartões de crédito. Logo, todos os usuários estão nos conformes do PCI DSS então você tem a garantia de que por exemplo os dados do seu cliente não serão compartilhados.

<br />

## Características

- **Usuários (*users*):** Contas que se autenticam por meio de login (nome de usuário/email, senha e MFA caso habilitado)
- **Grupos (*groups*):** Quando existem muitas contas surge a necessidade de organizar essas contas e é aí que entram os grupos, **os usuários podem pertencer a um ou mais grupos**. Pode-se associar os grupos aos departamentos (Ex: financeiro, recursos humanos, tecnologia da informação, vendas, etc) existentes dentro da empresa ou a funções de trabalho (Ex: arquitetos, banco de dados, desenvolvedores, devops, etc) para segmentar os usuários por exemplo. 
- **Funções (*roles*):** Uma função permite de uma forma simples de adicionar grupos de permissões/regras para usuários específicos e grupos ou para serviços AWS.
- **Políticas (*policies*):** Você pode aplicar *policies* em usuários, grupos e funções. Ou seja a *policy* será vinculada/anexada a um usuário, grupo ou função.

### Exemplo de uma *policy*

Exemplo da estrutura de uma *policy* no formato JSON

```JSON

```

<br />

## Boas práticas

- Habilitar o MFA (*Multifactor Authorization*)
- Criar política de senha para os usuários com o *set password policy*
- *Identity Federation*: Linkar conta da AWS com *active directory* da empresa ou com redes sociais (facebook, github, linkedin, twitter, etc)
- Não utilizar a conta *root*. Use a conta *root* para criar o seu primeiro usuário IAM e somente para fazer tarefas de gerenciamento de conta que exijam o privilégio de *root* para demais casos e operações rotineiras utilize um usuário IAM.
- Utilizar o princípio do menor privilégio (*principle of least privilege*) ao conceder permissões de acesso.

<br />

## STS

**AWS STS** é uma sigla para *Security Token Service* ele permite que se obtenha credenciais temporárias para acessar recursos da AWS diretamente.

- **AssumeRole:** Permite assumir funções(*roles*) na sua conta AWS ou entre outras contas AWS
- **AssumeRoleWIthSAML:**  Retorna credenciais para usuários logados com SAML
- **AssumeRoleWithWebIdentity:** Retorna funções(*roles*) para usuários logados com um IdP (Facebook, Google, e etc) entretanto não utilize mais essa API e sim Cognito Identity Pools
- **GetSessionToken:** Para usuários com MFA ou uma conta *root* da AWS
- **GetFederationToken:** Para obter credenciais temporárias para um *federated user*
- **GetCallerIdentity:** Para retornar detalhes sobre o usuário IAM e a sua função(*role*) usada na chamada da API
- **DecodeAuthorizationMessage:** Para descriptografar mensagens de erro quando uma API da AWS é negada

As que considero **mais importante para lembrar no exame** são as: AssumeRole, GetSessionToken, GetCallerIdentity e DecodeAuthorizationMessage.

<br />

## :books: Referências

Para uma compreensão mais profunda sobre IAM recomendo a leitura da documentação oficial, os links estão abaixo.

- [O que é IAM?](https://docs.aws.amazon.com/pt_br/IAM/latest/UserGuide/introduction.html)
- [Credenciais de segurança temporárias no IAM](https://docs.aws.amazon.com/pt_br/pt_br/IAM/latest/UserGuide/id_credentials_temp.html)

---
Feito com ♥ by :man_astronaut: Guilherme Bezerra :wave: [Entrar em contato!](https://www.linkedin.com/in/gbdsantos/)
