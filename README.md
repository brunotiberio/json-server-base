# Bem vindo ao TiberioHub!

Este é o backend da aplicação TiberioHub - Um hub de portfólios de cursos dos alunos do professor Bruno Tibério ! O objetivo dessa aplicação é permitir que o mercado de trabalho conheça os novos qualificados com os cursos.


# Endpoints

A API tem um total de 5 endpoints, sendo em volta principalmente do usuário (aluno) - podendo cadastrar seu perfil e cursos que estudou.  
O JSON para utilizar no Insomnia pode ser baixado aqui ->  [https://drive.google.com/file/d/1t2ESS5ZEtp_EU4nAViXQI3BAba-s9iet/view?usp=sharing](https://drive.google.com/file/d/1t2ESS5ZEtp_EU4nAViXQI3BAba-s9iet/view?usp=sharing)  Para importar o JSON no Insomnia é só clicar na palavra "Insomnia" no canto superior esquerdo. Nesse dropdown é só clicar em "Import / Export > Import Data > Import from File > e escolher o local onde foi salvo o arquivo"  ✌️

O url base da API é  [https://tiberiohub.herokuapp.com/](https://tiberiohub.herokuapp.com/)

## Rotas que não precisam de autenticação

**Criação de usuário**

POST -> baseURL/register

Os dados solicitados pela API são:

    {
    	"email": "email@asdf",
    	"password": "123",
    	"name": "Bruno",
    	"age": "32"
    }

Em caso de sucesso na criação de usuário, é retornado a seguinte resposta:

    {
    	"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6ImJydW5vQGVtYWlsLmNvbSIsImlhdCI6MTY1NjUyMTQ2MywiZXhwIjoxNjU2NTI1MDYzLCJzdWIiOiIyIn0.T1ZS5thoU91UJwbaW5rKGLmaaMuru6PAXqf6lGJNLaU",
    	"user": {
    		"email": "bruno@email.com",
    		"name": "Bruno",
    		"age": "32",
    		"id": 2
    	}
    }

Response da api não cadastrado com sucesso:

| Situação | Mensagem |
|--|--|
|Caso e-mail já exista na base de dados | "Email already exists" |
|Caso não digita um e-mail ou senha|"Email and password are required"|
|Caso a senha não tenha, no mínimo de 4 dígitos|"Password is too short"|


**Login de usuário**

POST -> baseURL/login

Os dados solicitados pela API são:

    {
    	"email": "tiberio@email.com",
    	"password": "123456"
    }

Em caso de sucesso na criação de usuário, é retornado a seguinte resposta:

    {
    	"accessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJlbWFpbCI6InRpYmVyaW9AZW1haWwuY29tIiwiaWF0IjoxNjU2NTI1NDU3LCJleHAiOjE2NTY1MjkwNTcsInN1YiI6IjMifQ.umkLEQGjZ_VLorxsZQte7qXiVdEGMkSOl1SzZSrlPPY",
    	"user": {
    		"email": "tiberio@email.com",
    		"name": "Bruno",
    		"age": "32",
    		"id": 3
    	}
    }

Caso haja necessidade, o "accessToken" pode ser usado para ser armazenado no localStorage.

Response da api caso login não seja efetuado com sucesso:

| Situação | Mensagem |
|--|--|
|Caso esteja faltando e-mail ou senha | "Email and password are required" |
|Caso e-mail errado ou inválido|"Cannot find user"|
|Caso senha errada|"Incorrect password"|
|Caso senha abaixo de 4 caracteres:|"Password is too short"|

**Listar todos os cursos cadastrados**

Nesse endpoint é possível ver todos os cursos cadastrados na api

GET-> baseURL/courses

    [
    	{
    		"type": "Programação",
    		"name": "FullStack Kenzie",
    		"userId": 3,
    		"id": 1
    	}
    ]

**Listar cursos por tipo**

Nesse endpoint é possível listar todos os cursos por meio do atributo "type" que é colocado ao cadastrar um curso na API.

GET-> baseURL/courses?type=Comunicação

    [
    	{
    		"type": "Comunicação",
    		"name": "Jornalismo",
    		"userId": 3,
    		"id": 3
    	},
    	{
    		"type": "Comunicação",
    		"name": "Narração Esportiva",
    		"userId": 3,
    		"id": 4
    	}
    ]
    
## Rotas precisam de autenticação

**Cadastrar novo curso para o usuário**

POST -> baseURL/courses

Os dados solicitados pela API são:

    {	
    	"type": "Comunicação",
    	"name": "Narração Esportiva 2",
    	"userId": 3
    }

*Type -> Categoria do curso
Name -> Nome do curso
UserId -> ID do usuário logado* 

Em caso de sucesso na criação de novo curso, é retornado a seguinte resposta:

    {
    	"type": "Comunicação",
    	"name": "Narração Esportiva 2",
    	"userId": 3,
    	"id": 5
    }

No futuro, ao aprender mais sobre API e sua criação, pretendo incrementar ainda mais essa fakeAPI.
Obrigado!

SIM, ISSO É UMA IMAGEM DO SHUTTERSTOCK COM PESSOAS FELIZES.
![enter image description here](https://media.discordapp.net/attachments/705535674434060360/991796704351371335/unknown.png?width=521&height=473)

BRINCADEIRA, HUMORISMO, VAMO RIR!! HAHAHAHAHAHA
