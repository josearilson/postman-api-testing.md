# Testes Automatizados de API Rest com Postman 🚀🧑🏼‍🚀
Aqui você vai encontrar além de uma introdução sobre requisições no Postman, como testá-las de maneira automatizada.


### O que são requisições HTTP, na prática? 🤓

Na prática, requisições HTTP são chamadas feitas pelo cliente ao servidor e que, dependendo do método, esperam uma resposta.

### Os métodos (ou verbos, como são comumente chamados) mais utilizados são:
- GET - O método GET deve retornar os dados do endpoint ao qual foi feito a requisição.
- PUT - O método PUT tem como objetivo alterar/editar, de maneira a sobrescrever os dados do endpoint da requisição.
- PATCH - Diferente do método PUT, o PATCH altera somente os campos especificados no corpo da requisição, sem sobrescrever totalmente o endpoint.
- POST - O método POST cria um novo recurso no servidor, nesse método, o corpo da requisição irá carregar os dados que serão transmitidos para o endpoint.
- DELETE - O método DELETE, como o próprio nome já diz, remove um recurso específico.
Com essas informações, já podemos começar nossa jornada na WEB por baixo dos panos!




### O que vamos usar? 😁💻
Para os nossos exemplos, estarei utilizando, além da ferramenta Postman, a fake API JSONPlaceholder.

## Essa API possui os seguintes endpoints:
<p>/posts - 100 publicaçöes</p>
/comments - 500 comentários
/albums - 100 albuns
/photos - 5000 fotos
/todos - 200 todos
/users - 10 usuários


## Organizando as suas requisições no Postman 💻🧑🏼‍🚀
Em termos de organização, gosto de seguir o seguinte "breadcrumb": Workspace > Coleção > Requisição

No nosso caso, criei o Workspace "API Testing - JSONPlaceholder":
