<img src="./Asserts_Readme/spring.svg" align="right"  width="200" height="160" />

# Spring Boot - Poc
<br/><br/><br/>

## Índice
* Objetivo
* Como utilizar?
    - Passo a passo
    - Estrutura
* Dicas
* Dúvidas
* Contatos

## Objetivo <img src="./Asserts_Readme/goal.png" width="40" height="40" />
Bem-vindo! Esse projeto tem como objetivo fornecer um exemplo de solução e um passo a passo de como criar e utilizar do framework Sprint Boot para criar uma aplicação Restful dentro do ambiente banco, para isso é necessário a a personalização da ferramenta Eclipse Neon para permitir o importe de bibliotecas externas, execução e testes como requisição Http utilizando o Web-Browser, que possa contribuir para com o seu conhecimento.


## Como utilizar? <img src="./Asserts_Readme/technical-support.png" width="40" height="40" />

### Passo a passo <img src="./Asserts_Readme/step.png" width="25" height="25" />

1. Vá até a Central de Software e instale o **GitHub** e o **Eclipse Neon**, caso eles ainda não estejam instalados.

2. Now clone it:

    ```sh
    $ git clone git://github.com/braziljs/conf-boilerplate.git
    ```

3. Then go to the project's folder:

    ```sh
    $ cd conf-boilerplate
    ```

4. Install all dependencies:

    ```sh
    $ npm install
    ```

5. And finally run:

    ```sh
    $ npm run watch
    ```
   Now you can see the website running in `localhost:9778` :D

6. Once you're done editing and want to publish the site to GitHub Pages:

    ```sh
    $ npm run deploy



### Estrutura <img src="./Asserts_Readme/folder-management.png" width="25" height="25" />

A estrutura básica do projeto se dá na seguinte forma:
```
.
|-- out/
|-- src/
|   |-- documents
|   |-- layouts
|   |-- partials
|-- docpad.js
|-- package.json
```

### out/

É onde os arquivos gerados são armazenados, uma vez que o DocPad tenha sido rodado. Porém, esse diretório se torna desnecessário no versionamento, por isso está ignorado ([.gitignore](https://github.com/braziljs/conf-boilerplate/blob/master/.gitignore)).

### [src/documents](https://github.com/braziljs/conf-boilerplate/blob/master/src/documents)

Contém o arquivo responsável por importar todas as seções da aplicação. Além disso contém o tema com todos seus arquivos como imagens, arquivos CSS e JS.

### [src/layouts](https://github.com/braziljs/conf-boilerplate/tree/master/src/layouts)

Contém o template padrão da aplicação.

### [src/partials](https://github.com/braziljs/conf-boilerplate/tree/master/src/partials)

São blocos de código utilizados para gerar a página principal do site ([index.html](https://github.com/braziljs/conf-boilerplate/blob/master/src/documents/index.html.eco)).

### [docpad.js](https://github.com/braziljs/conf-boilerplate/blob/master/docpad.js)

Armazena de forma fácil a maior parte das configurações da aplicação.

### [package.json](https://github.com/braziljs/conf-boilerplate/blob/master/package.json)

Lista as dependências de módulos do NodeJS.



## Dicas <img src="./Asserts_Readme/tips.png" width="40" height="40" />

## Contatos