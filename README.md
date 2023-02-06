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
<p>/comments - 500 comentários</p>
<p>/albums - 100 albuns</p>
<p>/photos - 5000 fotos</p>
<p>/todos - 200 todos</p>
<p>/users - 10 usuários</p>


## Organizando as suas requisições no Postman 💻🧑🏼‍🚀
Em termos de organização, gosto de seguir o seguinte "breadcrumb": Workspace > Coleção > Requisição

No nosso caso, criei o Workspace "API Testing - JSONPlaceholder":
![1](https://user-images.githubusercontent.com/40409188/217072038-bf427030-22f0-4be3-b399-c8d1381deada.gif)


## Como forma de organizar a visualização, criei coleções referentes à cada endpoint da API:

![2](https://user-images.githubusercontent.com/40409188/217072462-19c7908c-6b95-4f3c-849b-808d374d2879.gif)

Por fim, criei a requisição dentro da coleção referente ao endpoint que quero fazer a chamada.
![3](https://user-images.githubusercontent.com/40409188/217072486-52aee508-1c57-4664-993a-cf3cb705a9d2.gif)


#Criando suas primeiras requisições no Postman:
Neste tópico, realizaremos todas as mais comuns requisições no endpoint /posts e analisaremos as suas respostas.

# GET em /posts ✅
Para realizar uma requisição GET em /posts, basta inserir o link da API com o endpoint /posts e selecionar o método GET.
![4](https://user-images.githubusercontent.com/40409188/217072489-016fa3d9-9383-464b-9fe8-fc81f72434cd.gif)


Nesta requisição, conseguimos notar que o GET em /posts nos retorna uma estrutura com várias publicações, essas publicações contém em suas respectivas estruturas os seguintes atributos:

{
"userId" -> id do usuário que criou a publicação.
"id" -> id da publicação.
"title" -> título da publicação.
"body" -> corpo/texto da publicação.
} 
# POST em /posts ✅
Para realizar uma requisição POST em /posts, basta inserir o link da API com o endpoint /posts, selecionar o método POST e passar o corpo da requisição. Note que não foi passado o id da publicação, uma vez que neste caso, a API assimila a nova publicação ao próximo Id não cadastrado, entretanto, há a possibilidade de passar quaisquer "id" no corpo da requisição, desde que o mesmo já não tenha sido assimilado anteriormente.

![5](https://user-images.githubusercontent.com/40409188/217072492-1386b2c7-3b17-4355-a86b-9be91a03bfbf.gif)


### No corpo da resposta, é possível notar os dados da publicação que foram passados na requisição e o id da publicação que foi assimilado pela API.

# GET em /posts/{id} ✅
Muito parecido com o GET feito no endpoint_ /posts_, o GET em /posts/{id} deve nos retornar somente os dados da publicação referente ao id passado no endpoint.

![6](https://user-images.githubusercontent.com/40409188/217072494-87e21139-7a2b-4634-9d24-99252f61e6a0.gif)

## Nota-se que no corpo da resposta, temos apenas a estrutura da publicação referente ao id que foi passado.

# PUT em /posts/{id} ✅
Para realizar a requisição PUT no endpoint /post/{id}, deve-se passar no corpo da request todos os dados que farão o "update" do id referido. Esses dados irão sobrepor o que existe atualmente no endpoint.
![7](https://user-images.githubusercontent.com/40409188/217072497-a0451c30-33bf-4a02-baa0-ec03f564efe1.gif)

Note que levando em consideração o exemplo que fizemos de requisição GET em /posts/1 podemos notar a diferença do conteúdo do endpoint /posts/1 antes e depois do PUT.

Neste caso, nota-se que o corpo da resposta é preenchido somente com os dados passados no corpo da requisição do método PUT (além do "id" que é assimilado automaticamente pela api, isso porque a URL já está passando o "id" como um parâmetro).

# Antes

{
    "userId": 1,
    "id": 1,
    "title": "sunt aut facere repellat provident occaecati excepturi optio reprehenderit",
    "body": "quia et suscipit\nsuscipit recusandae consequuntur expedita et cum\nreprehenderit molestiae ut ut quas totam\nnostrum rerum est autem sunt rem eveniet architecto"
}
# Depois

{
    "title": "meu título",
    "id": 1,
}
# PATCH em /posts/{id} ✅
Para realizar a requisição PATCH no endpoint /post/{id}, deve-se passar no corpo somente os campos que serão alterados na estrutura do id referido. Esses dados irão sobrepor somente os campos que foram passados no corpo da requisição, diferente do PUT.

![8](https://user-images.githubusercontent.com/40409188/217072499-81b01051-2701-429c-b659-1a034a8de977.gif)

Também levando em consideração o exemplo que fizemos de requisição GET em /posts/1 podemos notar a diferença do conteúdo do endpoint /posts/1 antes e depois do PATCH: No nosso caso, como somente "title" foi passado no corpo da requisição, somente ele foi alterado na estrutura.

# Antes

{
    "userId": 1,
    "id": 1,
    "title": "sunt aut facere repellat provident occaecati excepturi optio reprehenderit",
    "body": "quia et suscipit\nsuscipit recusandae consequuntur expedita et cum\nreprehenderit molestiae ut ut quas totam\nnostrum rerum est autem sunt rem eveniet architecto"
}
# Depois

{
    "userId": 1,
    "id": 1,
    "title": "meu novo título",
    "body": "quia et suscipit\nsuscipit recusandae consequuntur expedita et cum\nreprehenderit molestiae ut ut quas totam\nnostrum rerum est autem sunt rem eveniet architecto"
}
# DELETE em /posts/{id} ✅
É simples realizar uma requisição de DELETE no Postman, basta selecionar o método e, neste caso, passar o parâmetro do "id" no endpoint. O corpo da resposta vazio

![9](https://user-images.githubusercontent.com/40409188/217072500-72adeac5-2de6-4b74-8c4b-42771462c713.gif)

Com o status de 200, é perceptível que a requisição de DELETE teve sucesso, desta forma, pode-se notar que não há corpo de resposta.

Para que servem as variáveis de ambiente no Postman e como criá-las
Agora que já sabemos como fazer requisições no Postman, vamos avançar mais um pouco e entender como as varíaveis de ambiente podem nos ajudar no que tange a automatização dos testes de API.

No nosso caso, as variáveis de ambientes serão de extrema importância para evitar a repetição e re-trabalho nos testes, além de claro, tornar a visualização menos complexa.
Criando nossa primeira variável de ambiente
Para isso, é necessário que seja criado o ambiente que comportará todas as variáveis criadas.

### PASSO A PASSO PARA CRIAR AMBIENTE E VARIÁVEL MANUALMENTE:

![10](https://user-images.githubusercontent.com/40409188/217072503-196a8e5d-55b3-4f38-bc6c-e1cc9a510546.gif)

# <p>Atualizando uma variável de ambiente com base na response de uma requisição 🌐</p>
Para atualizar uma variável de ambiente assimilando determinado conteúdo do corpo da resposta da requisição, é primeiro interessante saber que os testes no Postman, que podem ser feitos através do JavaScript embutido no software, só irão ser executados após a requisição ter sido concluída. Desta forma, vamos à prática!

Na aba "Tests" da requisição, deve ser passado o seguinte código:

var **variável declarada no teste que fará análise do JSON** = JSON.parse(responseBody)
pm.environment.set("variável de ambiente pré criada", **variavel que fará a análise do JSON**["variável que vem no corpo da requisição"]);
"var" -> irá declarar uma variável no teste da requisição.
"JSON.parse(responseBody)" -> fará a análise do JSON presente no response body da requisição.
"pm.environment.set" -> serve para setar o conteúdo da variável de ambiente dentro do ambiente atual selecionado.
Utilizando como exemplo a requisição de POST no endpoint /posts, gostaríamos de criar uma variável que assimilasse o "id" da publicação que será criada. Sendo assim, devo antes de tudo, criar uma variável de ambiente para assimilar o valor que será recebido no corpo da resposta. No nosso caso esta variável de ambiente será "id_da_publicacao".

Desta forma, nosso código na aba tests ficaria assim:

var jsonData = JSON.parse(responseBody)
pm.environment.set("id_da_publicacao", jsonData["id"]);

![11](https://user-images.githubusercontent.com/40409188/217072507-52b91bce-7487-4cc2-a499-ac86cc30089d.gif)

Isso pode ser utilizado para diversos fins, como: Associar um token de autorização de uma requisição de cadastro à outras requisições que necessitam dele, por exemplo. Em testes, pode ser feito um POST seguido de um DELETE /endpoint/{id} pelo "id" que foi pego na requisição do POST. São inúmeras formas de utilização, vai da sua necessidade e criatividade!

# <p>Com isso, como fazer testes de API com validações no Postman? 🤷🏼‍♂️</p>
O desenvolvimento de scripts de test no Postman são feitos de uma maneira bem simples, utilizando apenas a sintaxe de validações da Chai Assertion Library presente na estrutura dessa ferramenta, eles podem ir desde validações de status code até multiplas validações de cookies, response time, conteúdo de headers e entre outras.

Teste de validação de status code
O teste de validação pode ser feito utilizando a seguinte sintaxe:

 pm.test("nome do teste", function () {
 pm.response.to.have.status(status desejado);
});

![12](https://user-images.githubusercontent.com/40409188/217072512-3786753e-eec5-429f-89b6-7722709fa78d.png)


Repare que, tendo um status que valida o status code, se ele for igual o esperado o resultado é positivo para o teste. ✅

# Testes de resposta da requisição ✅
Não muito diferente, os testes do response body, validam todo conteúdo que é recebido no corpo da resposta, com diversos "asserts" que são contemplados pela "Chai Assertion Library", então quando se tratam de validações, o céu é o limite!
Vários testes realizados em uma única requisição e que ficarão salvos para sempre que a requisição for feita:

    //validações do status code
      //Teste de validação de status code
pm.test("Status code é 200", function () {
pm.response.to.have.status(200);
});

      //Teste de resposta em texto do status code
pm.test("O nome do status code tem o texto: OK", () => {
pm.response.to.have.status("OK");
});

  //validações dos cabeçalhos da requisição
      //Teste para verificar a existência de um cabeçalho.
pm.test("Content-type está presente nos cabeçalhos", () => {
pm.response.to.have.header("Content-Type");
});

  //Validação de desempenho
      //teste de tempo de resposta
pm.test("O tempo de resposta é menor que 150ms", () => {
pm.expect(pm.response.responseTime).to.be.below(150);
});



//validações do corpo da resposta
pm.test("O response da requisição foi validado.", () => {
//criação de constante para fazer o parse do JSON
  const respostaDoJson = pm.response.json();
//teste que valida o conteúdo de uma variável
  pm.expect(respostaDoJson.userId).to.eql(1);
//teste que valida o tipo de uma variável
  pm.expect(respostaDoJson.userId).to.be.a("number");
  pm.expect(respostaDoJson.id).to.eql(1);
  pm.expect(respostaDoJson.id).to.be.a("number");
  pm.expect(respostaDoJson.title).to.be.a("string");
  pm.expect(respostaDoJson.title).to.eql("sunt aut facere repellat provident occaecati excepturi optio reprehenderit");
//teste que valida a quantidade de caracteres no conteúdo de uma variável
  pm.expect(respostaDoJson.title).to.have.lengthOf(74);
});
O resultado destes testes utilizando o método GET no endpoint /posts/1 da API que estamos utilizando foi o seguinte:

![13](https://user-images.githubusercontent.com/40409188/217072513-f27bbb48-b513-4846-91a6-d50d9874bac5.png)
Repare aqui que, por ter um tempo de resposta maior que o esperado no nosso script, o teste não passou!

## Para finalizar, como rodamos todas as requisições e seus respectivos testes automaticamente?
Acessando a pasta principal da coleção, é possível notar o botão "run collection", que ao ser clicado começará a fazer as requisições na ordem de organização das pastas. Assim:

![14](https://user-images.githubusercontent.com/40409188/217072516-e0750d44-66b8-4c20-8613-313939a764e0.gif)


Como um extra, explico a funcionalidade de Monitores no Postman. 🖥️✅
Além de tudo que foi passado aqui, criar um monitor para a sua coleção torna possível:

Estabelecer um timer para rodar todas as requisições automaticamente de X em X horas/dias/semanas
Receber e-mails automaticamente a cada erro/falha nos testes.
Estabelecer delays entre requisições.
Escolher região dos servidores do Postman onde os testes serão feitos.
Retestar automáticamente X vezes se um teste falhar.
Criar um tempo máximo para timeout das requisições.

![15](https://user-images.githubusercontent.com/40409188/217072520-a3d4325a-1b74-483e-8879-984cb535db46.gif)



# <p>FIM!</p>
## Muito obrigado pessoal! 🙏🙏



