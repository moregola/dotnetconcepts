# dotnetconcepts
Question for Job Works
# 1. Orientação a Objetos:
### • Explique o conceito de herança múltipla e como C# aborda esse cenário.

> C# permite que uma classe pode implementar diversas classes, herdando propriedades e comportamentos de todas as classes que você estender a essa subclasse, se tornando uma sub classe de diversas interfaces.

> Um exemplo é a classe LIST que herda comportamentos de diversas outras interfaces, tendo outros comportamentos além da classe Array, como estender métodos do ICollection ou IEnumerable. Também permite a conversão do objeto para outras classes que ele pode ser instanciado através de métodos de conversão facilitando a manipulação de conjuntos de dados no backend.


### • Explique o polimorfismo em C# e forneça um exemplo prático de como ele 
### pode ser implementado.


>C# permite que uma classe pode implementar diversas classes, herdando propriedades e comportamentos de todas as classes que você >estender a essa subclasse, se tornando uma sub classe de diversas interfaces.
>Um exemplo é a classe LIST que herda comportamentos de diversas outras interfaces, tendo outros comportamentos além da classe Array, >como estender métodos do ICollection ou IEnumerable. Também permite a conversão do objeto para outras classes que ele pode ser >instanciado através de métodos de conversão facilitando a manipulação de conjuntos de dados no backend.

` string[] arrayA = new string[] { "text" }; `

` List<string> listB = new List<string>(); `

` listB.AddRange(arrayA); `

> O método AddRange adiciona o arrayA do tipo Array<string> sem precisar de uma conversão para o mesmo tipo, no caso lista.
> Existem várias vantagens de usar o polimorfismo. 
> Menos código, ganho de processamento, evitar conversões desnecessárias.
> Poder usar tipos mais simples como array para depois estruturar uma lista que é uma classe que exige mais processamento e ocupa mais
> espaço na memória.
> Podemos dar outros exemplos mais abstratos e metafóricos:

```
class Vehicle 
 {
            void Acelerate()
            {
                (lógica para mover o objeto)
           }
}
```

```
class Car : Vehicle 
{
   private readonly int Tire = 4;
}
```

```
class Bike : Vehicle 
{
   private readonly int Tire = 2;
}
```
> Quando você instância um objeto do tipo Car ou do Tipo Bike, ambos terão o método Acelerate();
> Em contrapartida, ainda são objetos diferentes e ambos tem suas propriedades pneu privadas e imutáveis.


# •2. SOLID:
### • Descreva o princípio da Responsabilidade Única (SRP) e como ele se aplica em 
### um contexto de desenvolvimento C#.

> Basicamente é levar em consideração na abstração de uma aplicação que suas classes , interfaces, ações devem ser quebradas em pequenas > classes e comportamentos simples para que tem apenas uma razão para mudar, ou seja, deve possuir uma única responsabilidade.
>
> Ao modelar um Domínio, isso é extremamente necessário para evitar complexidade, deixando a complexidade lógica para aplicação que > > > > utilizará o CORE.
> 
> Cada Model deverá ser criada pensando que ela existe para apenas 1 coisa e seus comportamentos sendo simples.
> 
> Ao modelar uma camada de Services, criamos uma service focada em manipular dados de uma Model apenas, sendo ela responsável por 
> manipular apenas aquela classe evitando que exista necessidade de alterar essas classes caso novas models sejam criadas ou alteradas, 
> resultando apenas na alteração de sua service correspondente.
> 
> Com isso existe que ela será fechada para alteração pois não haveria motivos para que ela mudasse de comportamento, levando a criação de outro classe.


### • Como o princípio da inversão de dependência (DIP) pode ser aplicado em um 
### projeto C# e como isso beneficia a manutenção do código?

> Esse princípio sugere que devemos depender de abstrações e não de classes concretas.
> Em C# fazemos através de interfaces na modelagem de camadas e também aplicando Injeção de Depêndencia.
> Com isso, a criação das classes concretas ficam mais claras e suas implementações mais coesas, clean e de fácil manutenção.
> Isso permite menos volatilidade , bugs , imprevistos, visto que cada classe concreta deve seguir seu “contrato” (interface)
> Com isso, permite que possamos também aplicar outro princípio que é a Inversão de Dependência, permitindo injetar classes concretas em memória para que sejam injetadas em outras classes ao invés de instanciar a classe concreta diretamente na classe que será usada como propriedade


# 3. Entity Framework (EF):
### • Como o Entity Framework gerencia o mapeamento de objetos para o banco de 
### dados e vice-versa?

> Através do context injetado em memória.
> A transação de baixo nível é feita através do ADO.net incorporada na biblioteca do Entity
> Sendo mais específico, ao iniciar o projeto o entity cria um objeto de mapeamento das entidades do banco, permitindo então que essa camada traduza a nossa lógica e comandos para lógica e comandos de seu banco de dados através do Provider.

### • Como otimizar consultas no Entity Framework para garantir um desempenho eficiente em grandes conjuntos de dados

> Podemos escrever e preparar queries diretamente com Entity Framework.
> Utilizar o IQueryable para manipular dados que serão acessados depois é importante para não chamar o banco várias vezes.

> Podemos usar o Linq to Entities ou fazer micro consultas usando Linq diretamente, retornando apenas as propriedades necessárias e colunas necessárias para retorno de lista.

> Podemos indexar colunas para acelerar buscas em tabelas muito grandes.

> Também podemos escrever diretamente uma query SQL pura para retornar conjuntos de dados mais específicos ou escrever 

# 4. WebSockets:
### • Explique o papel dos WebSockets em uma aplicação C# e como eles se 
### comparam às solicitações HTTP tradicionais.

> WebSockets utilizam chamadas CONNECT ao invés de gets.
> O uso deles permite uma “conexão” entre sistemas, trocando informações através do protocolo TCP.
> Comumente utilizados em chats, ou em qualquer aplicação que exija uma conexão sem necessidade de requests de troca para se obter a informação.

### • Quais são as principais considerações de segurança ao implementar uma 
### comunicação baseada em WebSockets em uma aplicação C#?

> Usar Comunicação Criptografada para comunicação entre aplicações.
> Configurar autenticação para iniciar a conexão.
> Configurar corretamente o webSocketOptions no start da aplicação.
> Abstrair e implementar tratamento de erros para que não possam ser utilizados para ataques.
> A documentação sobre isso é completa e aborda esses aspectos de segurança ao implementar WebSockets.


# 5. Arquitetura:
### •• Descreva a diferença entre arquitetura monolítica e arquitetura de 
### microsserviços. Qual seria sua escolha ao projetar uma aplicação C#?

> Arquitetura monolítica é quando uma aplicação contém todos os seus módulos em apenas uma solução.
> Essa solução será composta de módulos que podem variar como consoles applications, library class, web application e etc.
> Com isso, todo seu produto rodará apenas em 1 aplicação específica.
> Microsserviços é a concepção de criar diversas aplicações que se comuniquem (Ports and Adapters).
> Esse conceito permite que o produto cresça rapidamente, através de micro aplicações, micro front ends. Isso permite também flexibilidade de equipes para
> criarem diversas partes do produto/sistema/aplicação simultaneamente acelerando o desenvolvimento.
> Permite melhor balanceamento do sistema, pois consegue gerenciar cada aplicação e conforme a necessidade escalar ela através de Cloud, criando gateways para
> nivelar a comunicação da aplicação escalada.
> O controle de falhar também é melhorado pois cada aplicação terá seu monitoramento independente e as ações de correção serão mais focadas e rápidas.
>
> Em geral, Monolítos podem ser modificados a longo prazo para que sejam transformados em microsserviços reutilizando parte dos seus módulos.
>
> Já o contrário teria um custo muito alto, sendo a reversão para monolito de um projeto de Microsserviços praticamente impossível.

Para projetos C# considero que:
>   	Monolíto é bom para projetos pequenos, de baixo orçamento e baixa complexidade com equipes pequenas para trabalhar.

>   	Microsserviços é bom para projetos médios e grandes, para produtos complexos, com muita atividade, permitindo que cada atividade seja bem projetada e independente da outra.



### •• Como você escolheria entre a arquitetura de microsserviços e a arquitetura 
### monolítica ao projetar uma aplicação C# que precisa ser altamente escalável?

> Escolheria microsserviços em um primeiro momento num escopo aberto.

> Mas como citei na resposta anterior em resumo
> Monolitos podem virar microsserviços mas microsserviços tornam inviável a reversão para microsserviços.
>  E para justificar minha escolha, Monolitos seriam difíceis de modelar para alta escalabilidade,
> Mesmo que o MVP seja um monolito, para alta escalabilidade deverá ser projetado microsserviços.
>
> Monolíto é bom para projetos pequenos, de baixo orçamento e baixa complexidade com equipes pequenas para trabalhar sem necessidade de escalabilidade.
>
> Microsserviços é bom para projetos médios e grandes, para produtos complexos, com muita atividade, permitindo que cada atividade seja bem projetada e independente da outra.




