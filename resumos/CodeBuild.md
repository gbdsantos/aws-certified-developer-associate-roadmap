# Amazon CodeBuild

## :pushpin: Índice

- [Introdução](#introdução)
- [Referências](#books-referências)

<br />

## Introdução

Amazon CodeBuild é um serviço de build na nuvem. Ele compila o seu código, executa testes de unidade e produz artefatos prontos para implantação.

No código do arquivo `buildspec.yml` deverá conter as instruções para realizar o *build*. Este arquivo deve estar no diretório raiz(*root directory*) do seu código.
 
- Exemplo de arquivo `buildspec.yml`

```YAML
version: 0.2

phases: 
    install:
        runtime-versions:
            nodejs: latest
        commands:
            - echo "installing something"
    pre_build:
        commands: 
            - echo "we are in the pre build phase"
    build:
        commands:
            - echo "we are in the build block"
            - echo "we will run some tests"
            - grep -Fq "Congratulations" index.html
    post_build:
        commands:
            - echo "we are in the post build phase"
```

<br />

## :books: Referências

Para uma compreensão mais profunda sobre o CodeBuild recomendo a leitura da documentação oficial, os links estão abaixo.

- [O que é o AWS CodeBuild?](https://docs.aws.amazon.com/pt_br/codebuild/latest/userguide/welcome.html)
