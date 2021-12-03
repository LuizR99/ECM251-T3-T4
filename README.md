# ECM251-T3-T4

## Back-End 

A chamada de conexão com o banco de dados(BD) é feita pela classe ConnectionDAO e pega a url de conexão do BD pela classe SharedPaths, contendo as seguintes funções:

* executeQuery(sqlString : String) → executa uma query no banco de dados(BD).
* close() → fecha a conexão com o BD.
* getPreparedStatement(sqlString: String) → atualiza o banco de dados.

Utilizamos uma interface como base chamada "GenericDAO" para todas as classes que se comunicarão com o banco de dados, contendo as seguintes funções: 

* getOne(id:Int) → Recebe como parâmetro um id e executa uma query no BD procurando um filme/série/avaliação/usuário com o mesmo número e retornando todos os seus dados.

* getId(id:Int) → Teste que verifica se o id existe no BD, retornando true ou false.

* getAll() → Retorna todos os dados do BD.

* setOne(obj : Any) → Escreve uma linha no BD.

* setVar(list : List<Any>) → Recebe um lista e escreve linha por linha no BD.

* update(obj : Any) → Reescreve uma linha no BD.

* delete(id : Int) → Deleta uma linha no BD.
  


Também foram criados alguns models como data classes para separar os elementos de cada tabela:
  
- Element
  * elementID:Int → id da obra (filme/série).
  * name:String → nome da obra.
  * year:Int → ano de lançamento da obra.
  * category:String → categorias da obra.
  * duration:Int → duração da obra (minutos para filmes / temporadas para séries).
  * director:String → Diretores da obra.
  * type:String → tipo (filme ou série).
  * synopsis:String → sinópse da obra.

- Review
  * reviewID:Int → id da avaliação
  * text:String → texto da avaliação
  * rating:Double → nota da avaliação
  * userID:Int → id do usuário que fez a avaliação
  * elementID:Int → id do filme/série que foi avaliado

- User
  * userID:Int → id do usuário
  * login:String → nome de login do usuário
  * password:String → senha do usuário
  * email:String → email do usuário
  * name:String → nome do usuário

As rotas foram definidas separadamente seguindo a documentação do ktor (https://ktor.io/docs/creating-http-apis.html#defining-the-routing-for-customers):
  
- ElementRoutes
  
  /element → get que retorna um json com todos os elementos das obras armazenadas no BD.
  
  /element/{elementID} → get que retorna o json de uma obra com o id especificado.
  
  /element (POST) → armazena uma linha com os dados da obra no BD.
  
  /element/{elementID} (DELETE) → deleta uma linha com o id da obra informado.

- ReviewRoutes
  
  /review → get que retorna um json com todas as reviews das obras armazenadas no BD.
  
  /review/{reviewID} → get que retorna o json de uma review com o id especificado.
  
  /review (POST) → armazena uma linha com os dados da review no BD.
  
  /review/{reviewID} (DELETE) → deleta uma linha com o id da review informado.
  
  
- UserRoutes
  
  /user → get que retorna um json com todos os usuários armazenados no BD.
  
  /user/{userID} → get que retorna o json de um usuário com o id especificado.
  
  /user (POST) → armazena uma linha com os dados do usuário no BD.
  
  /user/{userID} (DELETE) → deleta uma linha com o id do usuário informado.

A Application.kt é onde a API executa as rotas e tem como porta definida: "http://localhost:8080/"


## FRONT-END
  
Algumas funções criadas em js para tratar os dados fornecidos pela API:
  
  * Get(url) → manda um GET para a API com a url fornecida como parâmetro
  * AVG(reviews, elementID) → faz a média das reviews de um filme selecionado através do elementID.
  * top6(element, reviews) → separa o top 6 ratings mais altos em ordem decrescente.
  * tipo(element, type) → separa os elementos de acordo com o tipo dele (filme/série).
  
A parte do front está incompleta, faltando algumas implementações como: Login, Avaliação (formulário), Botões "Avaliar agora",  preenchimento de algumas páginas, barra de busca, imagens, etc.



