Relatório em README.md com:
1-explicação do padrão DAO (com exemplos)

O dao é responsável por organizar o código separando cada parte que acessa o banco de dados do resto do sistema, ou seja sem ele tudo iria ficar misturado em um unico arquivo, por exemplo em um restaurante o cliente faz o pedido pro garçom leva pra cozinha, o cliente não precisa saber como a comida foi feita pois ele recebe só o resultado.

arquitetura em camadas:
APP: é a parte que o usuario vê o menu no caso, e liga com as outras partes do sistema.

MODEL: Representa os objetos e cada um tem seus atributos.

DAO: é oque pode ser feito, funciona como um cardapio você pede mas não explica como é feito.

DAO.IMPL: É onde fica a parte sql e como fazer oque o dao falou.

DB: É a parte que fica a conexão com o banco e aqui tambem acontece o tratamento dos erros ConnectionFactory.java é a conexão e DbException.java é como o aviso de erro, aqui inves de mostrar confuso mostra de um jeito claro e mais organizado.


2-ciclo de vida da conexão JDBC

O ciclo de vida JDBC é os passos que ocorrem desde o momento em que o Java cria uma conexão com o banco de dados até o momento em que ela é fechada, por exemplo primeiro abrimos a conexão, depois preparamos o sql, executamos ele, lê o resultado e fechamos.

3-práticas de segurança (SQL injection, prepared statements)

O sql injection são tipos os hackers, é quando usuarios inserem comandos maliciosos no banco para alterar ou até excluir dados atravês de um texto por exemplo usuario: bia senha: 1313, ai simplesmente pegam isso e no campo da senha colocam or '1'='1' 1=1 é sempre verdadeiro então etram no sistema sem saber a senha, é ai que o preparedstatement entra ele resolve colocando ? ai inves de de ler o comando do hacker como verdadeiro ele lê como texto ai o banco entende que a senha é oque o hacker digitou e não encontra ninguem com essa senha.


conceitos:

DriveManager.getConnection(...)
é aonde abre a conexão com o banco ele pede 3 coisas, onde fica o banco, seu usuario e a senha.

PreparedStatement: o conceito ja tem la em cima mas relembrando, serve para preparar e executar comandos sql de forma segura.

executeUpdate() x executeQuery()
o executeUpdate() é pra quando precisa mudar algo no banco, INSERT, UPDATE E DELETE. Já o executeQuery() é pra quando queremos buscar algo no banco, SELECT por exemplo que traz os dados.

ResultSet é a resposta que o banco te dá depois de um select no caso é as informaçoes que aparecem, ai percorre as informaçõs linha por linha.

instantiateX(rs) é um método que pega uma linha do banco e transforma em um objeto java.




5.3
Não podemos concatenar por que fica mais fácil de pessoas invadirem o banco, podem entrar digitar algo malicioso e invadir o banco que é o sql injection

ja falamos do preparestatement e sql injection la em cima

O vazamento de conexão é quando abrimos uma e não fechamos isso pode deixar o sistema lento e com travamento, o try-with-resources evita que o banco vaze, antes dele tinhamos que fechar o sistema de forma manual que é mais trabalhoso, mais usando esse novo método a diferença é so onde declaramos a conexão e dentro dos parenteses do try avisa pro java: qando acabar esse bloco pode fechar tudo.




4-checklist de qualidade (fechamento de recursos, exceções)


mínimo 5 fontes (documentação, artigos, guias técnicos)
https://www.devmedia.com.br/introducao-ao-jdbc/43900

https://docs.oracle.com/javase/tutorial/jdbc/basics/connecting.html

https://www.devmedia.com.br/sql-injection/6102?utm_dev=google_ads_pmax&gad_source=1&gad_campaignid=22326280955&gbraid=0AAAAADrVyXE6rb1U9i-di4Bde4-l8y94N&gclid=Cj0KCQjwkrzPBhCqARIsAJN460nStYuzSgy3QbOIUlXa0-EApkWGkDLvaSv3atg7oNCC6h48mKxhw38aAswbEALw_wcB

https://docs.oracle.com/javase/8/docs/api/java/sql/PreparedStatement.html

https://www.devmedia.com.br/sql-injection-em-multiplas-plataformas/31389

https://www.devmedia.com.br/aprendendo-java-com-jdbc/29116

https://www.devmedia.com.br/jdbc-tutorial/6638

ttps://www.devmedia.com.br/aprendendo-java-com-jdbc/29116

https://www.devmedia.com.br/jdbc-tutorial/6638

https://www.devmedia.com.br/introducao-ao-jdbc/43900