# Json-Server + Heroku + Github: deploy de uma fake API com banco de dados

- **Tecnologias utilizadas**
    - Node.js
    - Json-server
    - Heroku CLI
    - Github
- **Iniciando o projeto**
    
     
    
    ```bash
    mkdir project_name
    cd project_name
    yarn init -y
    touch server.js
    touch db.json
    ```
    
- **Instalação de dependências**
    
    `Json-server`
    
    ```bash
    yarn add json-server
    ```
    
    `Heroku CLI`
    
    ```bash
    sudo snap install --classic heroku
    ```
    
    Para outros SO, segue o link da documentação:
    
    → [https://devcenter.heroku.com/articles/heroku-cli](https://devcenter.heroku.com/articles/heroku-cli)
    
- **Arquivos de configuração**
    
    `package.json`
    
    ```json
    ...
    "scripts": {
        "start": "node server.js"
    },
    ...
    ```
    
    `server.js`
    
    ```jsx
    const jsonServer = require('json-server');
    
    const server = jsonServer.create();
    const router = jsonServer.router('db.json');
    const middlewares = jsonServer.defaults();
    const port = process.env.PORT || 3333;
    
    server.use(middlewares);
    server.use(router);
    
    server.listen(port);
    ```
    
    `db.json`
    
    ```json
    {
      "users": [
        {
          "id": 1,
          "first_name": "Justina",
          "last_name": "Ginglell",
          "email": "jginglell0@networkadvertising.org",
          "gender": "Female"
        },
        {
          "id": 2,
          "first_name": "Marion",
          "last_name": "Jenman",
          "email": "mjenman1@surveymonkey.com",
          "gender": "Male"
        },
        {
          "id": 3,
          "first_name": "Alfy",
          "last_name": "Begin",
          "email": "abegin2@list-manage.com",
          "gender": "Female"
        },
        {
          "id": 4,
          "first_name": "Karney",
          "last_name": "Zanussii",
          "email": "kzanussii3@hao123.com",
          "gender": "Male"
        },
        {
          "id": 5,
          "first_name": "Reid",
          "last_name": "Schapero",
          "email": "rschapero4@timesonline.co.uk",
          "gender": "Male"
        },
        {
          "id": 6,
          "first_name": "Dorine",
          "last_name": "Braybrookes",
          "email": "dbraybrookes5@gov.uk",
          "gender": "Female"
        },
        {
          "id": 7,
          "first_name": "Sarena",
          "last_name": "Frape",
          "email": "sfrape6@alexa.com",
          "gender": "Female"
        },
        {
          "id": 8,
          "first_name": "Malva",
          "last_name": "Pierse",
          "email": "mpierse7@usda.gov",
          "gender": "Female"
        },
        {
          "id": 9,
          "first_name": "Rania",
          "last_name": "Dablin",
          "email": "rdablin8@state.gov",
          "gender": "Female"
        },
        {
          "id": 10,
          "first_name": "Ingrim",
          "last_name": "Offen",
          "email": "ioffen9@slideshare.net",
          "gender": "Male"
        }
      ]
    }
    ```
    
    Site para gerar dados fictícos:
    
    -> [https://www.mockaroo.com/](https://www.mockaroo.com/)
    
- **Implementação do deploy**
    1. Subir pro Github
        
        ```bash
        git add .
        git commit -m "create server and add database"
        ```
        
    
    1. Login no Heroku
        
        ```bash
        heroku login
        ```
        
    2. Criar projeto no Heroku
        
        ```bash
        heroku create <project_name>
        ```
        
    3. Subir para o Heroku
        
        ```bash
        git push heroku master
        ```
        
- **Implementação do pipeline**
    1. Abra seu painel no Heroku e escolha seu aplicativo;
    2. Navegue para `deploy` e crie um pipeline;
    3. Conecte seu Github com o repositório do servidor;
    4. Configure a implantação automática e escolha a branch do pipeline;
    
    Agora, qualquer push ao repositório do servidor vai comunicar o Heroku, via pipeline, e fazer o deploy automaticamente.
