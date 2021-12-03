# ECM251-T3-T4

## Back-End 

Utilizamos uma interface como base chamada "GenericDAO" para todas as classes que se comunicarão com o banco de dados, contendo as seguintes funções: 
* getOne(id:Int) → Recebe como parâmetro um id e executa uma query no banco de dados(BD) procurando um filme/série/avaliação/usuário com o mesmo número e retornando todos os seus dados.

* getId(id:Int) → Teste que verifica se o id existe no BD, retornando true ou false.

* getAll() → Retorna todos os dados do BD.

* setOne(obj : Any) → Escreve uma linha no BD.

* setVar(list : List<Any>) → Recebe um lista e escreve linha por linha no BD.

* update(obj : Any) → Reescreve uma linha no BD.

* delete(id : Int) → Deleta uma linha no BD.








