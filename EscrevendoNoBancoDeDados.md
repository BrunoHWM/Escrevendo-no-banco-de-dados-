# Escrevendo no banco de dados 

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

A classe EscrevendoNoBanco possui uma variável chamada texto, que pode ser acessada e modificada usando os métodos getNome() (para obter o valor atual de texto) e setTexto(String texto) (para atualizar o valor de texto com um novo valor passado como argumento). 

Variável de Instância:
String texto = "";: Aqui é declarada uma variável de instância chamada texto do tipo String. Inicialmente, ela está vazia.

Método getNome():
public String getNome() { return texto; }: Este é um método público que não recebe argumentos. Ele retorna o valor da variável texto atualmente armazenado nela.

Método setTexto(String texto):
public void setTexto(String texto) { this.texto = texto; }: Este é um método público que aceita um argumento do tipo String chamado texto. Ele é usado para atualizar o valor da variável de instância texto com o valor passado como argumento.
```
public class EscrevendoNoBanco {
    String texto = "";

    public String getNome() {
        return texto;
    }

    public void setTexto(String texto) {
        this.texto = texto;
    }
```





