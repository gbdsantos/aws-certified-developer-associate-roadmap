# IAM

## :pushpin: Índice

- [Características](#características)
- [Boas práticas](#boas-práticas)

<br />

Acrônimo para *Identity and Access Management* (IAM), é onde é possível criar usuários (*users*), grupos (*groups*), funções (*roles*), políticas (*policies*) e permissões (*permissions*) para controlar qual serviço/recurso os usuários podem acessar. 
Segue o **modelo de responsabilidade compartilhada** da AWS.

O IAM possui compatibilidade com o **PCI DSS Compliance** (*Payment Card Industry Data Security Standard*) que basicamente é um padrão de segurança da informação para empresas que lidam com cartões de crédito. Logo, todos os usuários estão nos conformes do PCI DSS então você tem a garantia de que por exemplo os dados do seu cliente não serão compartilhados.

- :open_book: [Documentação Oficial - O que é IAM](https://docs.aws.amazon.com/pt_br/IAM/latest/UserGuide/introduction.html)

<br />

## Características

- Usuários (*users*): Contas que se autenticam por meio de login (nome de usuário/email, senha e MFA caso habilitado)
- Grupos (*groups*): Quando existem muitas contas surge a necessidade de organizar essas contas e é aí que entram os grupos, **os usuários podem pertencer a um ou mais grupos**. Pode-se associar os grupos aos departamentos (Ex: financeiro, recursos humanos, tecnologia da informação, vendas, etc) existentes dentro da empresa ou a funções de trabalho (Ex: arquitetos, banco de dados, desenvolvedores, devops, etc) para segmentar os usuários por exemplo. 
- Funções (*roles*): Uma função permite de uma forma simples de adicionar grupos de permissões/regras para usuários específicos e grupos ou para serviços AWS.
- Políticas (*policies*): Você pode aplicar *policies* em usuários, grupos e funções. Ou seja a *policy* será vinculada/anexada a um usuário, grupo ou função.

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

---
Feito com ♥ by :man_astronaut: Guilherme Bezerra :wave: [Entrar em contato!](https://www.linkedin.com/in/gbdsantos/)
