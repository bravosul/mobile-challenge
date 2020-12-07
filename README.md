# Bravosul Mobile Challenge

O App consiste na necessidade de atender um pequeno comércio com um sistema simples de controle de produtos:

Criar um app com as seguintes telas:
 - Autenticação, pública;
 - Lista de produtos, com acesso restrito;
 - Criação de produtos, com acesso restrito;
 - Edição de produtos, com acesso restrito; 
 - Modal de exclusão, com acesso restrito;
 - Tela exibindo apenas produtos ativados, pública;
 - Tela descrevendo como como rodar sua aplicação (seja criativo), pública.

Qualquer funcionalidade extra é bem vinda para agregar na solução básica proposta.
O layout é por sua conta. A arquitetura é por sua conta, seja esperto.
Você será avaliado pela qualidade do código, pela modularidade, pela legibilidade, pela criatividade, pela quantidade de funcionalidades básicas e extra.

# Instruções:

- Não tenha pressa! Iremos avaliar a qualidade do seu código, mesmo incompleto e principalmente a sua semântica.

# Ganhe pontos extras por:
  - Testes unitários;
  - Código limpo e organização;
  - Documentação de código;
  - Documentação do projeto (readme);
  
# Prazo de entrega?
48 horas

# Como entregar?
O código deve ser entregue em um repositório Git Público,

# Endpoints
#### URL Base
```sh
https://bravosul-app.herokuapp.com/
```

#### API de autenticação
```sh
/auth/local
```
Request POST `https://bravosul-app.herokuapp.com/auth/local`
```sh
{
  "identifier": "dev@bravosul.com.br",
  "password": "Brvsl@2020"
}
```
Response
```sh
{
    "jwt": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6MSwiaWF0IjoxNTc2OTM4MTUwLCJleHAiOjE1Nzk1MzAxNTB9.UgsjjXkAZ-anD257BF7y1hbjuY3ogNceKfTAQtzDEsU",
    "user": {
        "id": 1,
        "username": "bravosul",
        ...
    }
}
```
#### API de produtos
| Method | Path | Description | Permission| 
| ------ | ------ | ------ | ------ |
| GET | `/products` | Get a list of products | Public |
| GET | `/products/:id` | Get a specific product | Authenticated |
| GET | `/products/count` | Count products | Authenticated |
| POST | `/products` | Create a product | Authenticated |
| DELETE | `/products/:id` | Delete a product | Authenticated |
| PUT | `/products/:id` | Update a product | Authenticated |

#### Create Product

Você deve usar o JWT na solicitação para dizer que pode criar um produto.

Request POST `https://bravosul-app.herokuapp.com/products`
```sh
{
  "name": "Nome do Produto",
  "description": "Mussum Ipsum, cacilds vidis litro abertis. Posuere libero varius. Nullam a nisl ut ante blandit hendrerit. Aenean sit amet nisi. Quem num gosta di mé, boa gentis num é.",
  "enabled": 1
}
```
Response
```sh
{
  "id": 3,
  "name": "Nome do Produto",
  "description": "Mussum Ipsum, cacilds vidis litro abertis. Posuere libero varius. Nullam a nisl ut ante blandit hendrerit. Aenean sit amet nisi. Quem num gosta di mé, boa gentis num é.",
  "enabled": true,
  "created_by": null,
  "updated_by": null,
  "created_at": "2020-07-31T05:11:54.993Z",
  "updated_at": "2020-07-31T05:11:54.993Z"
}
```
