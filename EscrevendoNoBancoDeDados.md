# Escrevendo no banco de dados 
---
__As importações no Java são essenciais para acessar recursos de bibliotecas externas escrever código mais limpo e legível, ao mesmo tempo em que aproveitamos as funcionalidades disponíveis em diferentes pacotes e bibliotecas, neste caso ultilizamos as bibliotecas.__

1. java.sql.Connection:
A classe Connection faz parte do pacote java.sql. Fundamental ao lidar com bancos de dados em Java. Ela representa uma conexão com um banco de dados específico. As operações de leitura, escrita e atualização são feitas por meio de objetos Connection.

2. java.sql.DriverManager:
A classe DriverManager é responsável por gerenciar os drivers de banco de dados em Java. Ela fornece métodos para registrar drivers.

3. java.sql.PreparedStatement:
A classe PreparedStatement é usada para representar uma declaração SQL pré-compilada. Ela permite que você execute consultas SQL estabelecendo parâmetro no banco de dados.

4. java.sql.SQLException:
SQLException é uma classe que representa exceções específicas relacionadas a operações com banco de dados. Ela é lançada quando ocorre algum erro durante a interação com o banco de dados, como problemas de conexão, consultas mal formadas ou indisponibilidade do banco de dados.

5. java.util.Scanner:
A classe Scanner, localizada no pacote java.util, é usada para ler entrada do usuário a partir do console ou de outros fluxos de entrada. Ela fornece métodos para ler diferentes tipos de dados.
```
import java.sql.Connection;  
import java.sql.DriverManager;
import java.sql.PreparedStatement;
import java.sql.SQLException;
import java.util.Scanner;

```
----
public static void main(String[] args) {: para executar nossa aplicação precisamos do método main, porém o Java só entende que é o método main na nossa aplicação se seguir essa assinatura: public static void main(String[] args).

Scanner sc = new Scanner(System.in);: aqui está sendo criado um objeto da classe Scanner chamado sc. O Scanner é utilizado para receber entrada do usuário. System.in está associado ao console ou à entrada de dados fornecida pelo teclado.

```
public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
```
---

__Neste trecho de código, o programa está solicitando ao usuário que insira informações por meio do console armazenando essas informações em variáveis específicas.__

```
        System.out.print("Nome: ");
        String nome = sc.nextLine();

        System.out.print("Telefone: ");
        String telefone = sc.nextLine();

         System.out.print("Email: ");
        String email = sc.nextLine();
```
---


__Já nesse trecho do código trata da inserção de dados em um banco de dados SQLite.por meio de bloco try-catch, primeiro começamos inserindo a url para a conexão com o banco de dados após isso ultilizamos o try. conn = DriverManager.getConnection(urlBanco); - Esta linha estabelece uma conexão com o banco de dados SQLite usando a URL fornecida (jdbc:sqlite:agenda.db).Após isso damos inicio as entradas de dados no banco com Nome , telefone e email. Por fim, as conexões com o PreparedStatement e com o banco de dados são fechadas para liberar os recursos.__


```
         String urlBanco = "jdbc:sqlite:agenda.db";
         Connection conn;
          try {
            conn = DriverManager.getConnection(urlBanco);
            String sql = "INSERT INTO contatos VALUES (?, ? ,?)";
            PreparedStatement pstatement = conn.prepareStatement(sql);
            pstatement.setString(1, nome);
            pstatement.setString(2, telefone);
            pstatement.setString(3, email);
            pstatement.executeUpdate();

          
            pstatement.close();
            conn.close();      
```
---

__O uso do bloco catch é feito para capturar e lidar com exceções. Isso permite que você capture o erro caso algo dê errado durante a conexão com o banco de dados ou durante a execução da instrução SQL. Está sendo utilizado o System.err.println(sqle.getMessage()); dentro do bloco catch. Isso imprimirá a mensagem de erro específica associada à exceção SQLException. É uma abordagem útil para identificar qual foi o problema caso ocorra uma exceção.
Além disso, o bloco finally está sendo usado para garantir que o recurso Scanner seja fechado independentemente de a exceção ter sido lançada ou não.
Isso assegura que, mesmo que ocorra um erro durante a execução do código, o recurso do Scanner será fechado no final, sem deixar vazamentos de recursos.__


 .__

```
        } catch (SQLException sqle) {
            System.err.println(sqle.getMessage());

        } finally {
            sc.close();
        }
```






