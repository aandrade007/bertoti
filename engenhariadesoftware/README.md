**1° Resumo do primeiro texto:**

O texto fala sobre o que é realmente engenharia de software e como ela é diferente de programação ou ciência da computação. Muitas vezes esses termos são usados como se fossem a mesma coisa, mas têm significados diferentes. Programar é basicamente escrever código, enquanto a engenharia de software envolve todo o processo de criação e manutenção desse código com mais organização, planejamento e qualidade a longo prazo.

A engenharia de software é comparada a outras engenharias, como a civil ou a mecânica, onde os profissionais usam teoria e prática para construir coisas reais e seguras. A diferença é que a engenharia de software é uma engenharia onde o produto é INTANGÍVEL.

O Google, por ter muita experiência desenvolvendo sistemas grandes e complexos, traz uma visão importante sobre como tornar a engenharia de software mais confiável e profissional. O objetivo do livro é ajudar desenvolvedores e empresas a adotarem práticas mais sérias e sustentáveis no desenvolvimento de software.



**2° Resumo do segundo texto:**

A ideia do texto é mostrar que engenharia de software não é **só** escrever código, mas também cuidar do código ao longo do tempo, desde quando ele nasce até quando é aposentado.
O Google aprendeu, com o tempo, que um bom sistema precisa ser feito pensando em três coisas:

1- Tempo e Mudança: O código vai precisar mudar com o tempo. Tem que ser fácil de manter e adaptar.

2- Escala e Crescimento: A equipe vai crescer, o sistema vai crescer, e o jeito de trabalhar também tem que evoluir.

3- Decisões e Custos: Nem tudo dá pra fazer perfeito. Cada escolha tem um custo, e a gente precisa saber equilibrar.

No fim, o que eles dizem é: programar bem não é só fazer funcionar hoje, mas fazer de um jeito que continue funcionando, sendo ESCALÁVEL e sendo útil por muito tempo.
Eles aprenderam isso na marra, pois, tiveram que evoluir e escalar seu projeto rapidamente. E, isso fez deles uma das maiores empresas do mundo.



**3° Exemplos de Tradeoffs:**

**1. Custo vs. Qualidade**

**Exemplo:** Quando você está desenvolvendo um aplicativo, você pode escolher entre usar bibliotecas e frameworks gratuitos ou pagar por uma ferramenta paga que oferece mais recursos e maior qualidade.
Não estou dizendo que as versões pagas são as melhores, portanto, muita das vezes elas oferecem mais desenmpenho.

**Explicação:** Se você optar por usar uma solução gratuita, o custo do projeto diminui, mas pode ter que lidar com limitações, como menos documentação, bugs ou menos suporte. 
Se você pagar por uma ferramenta premium, a qualidade do desenvolvimento tende a ser melhor, com mais funcionalidades e suporte, mas o custo aumenta, o que pode impactar o orçamento do projeto.

**2. Velocidade vs. Precisão**

**Exemplo:** Em um projeto de desenvolvimento de um sistema, você pode priorizar a velocidade de entrega, fazendo o código de forma mais rápida e com algumas soluções temporárias, ou pode dedicar mais tempo para refinar o código e garantir que tudo funcione de maneira ideal.

**Explicação:** Se você focar em rapidez, pode entregar o projeto no prazo, mas pode deixar "gambiarras" no código, o que pode comprometer a manutenção e a escalabilidade no futuro. Se focar em precisão, o código será mais bem estruturado e eficiente, mas a entrega será mais demorada e o projeto pode ultrapassar o cronograma. Assim o ideal seria equilibrar a rapidez com a qualidade e precisão.

**3. Windows vs. Linux**

**Exemplo:** Como estudante de ADS, você pode escolher usar o Windows ou o Linux como sistema operacional para desenvolver seus projetos e estudar. 
O Windows oferece uma interface mais amigável e compatibilidade com uma maior variedade de programas, enquanto o Linux é mais flexível, poderoso para desenvolvimento, mas pode ser menos intuitivo.

**Explicação:** Usar o Windows pode facilitar o uso de programas gráficos e softwares populares, como o Visual Studio, mas em contrapartida, você pode enfrentar dificuldades ao lidar com ambientes de desenvolvimento que exigem mais controle, como servidores ou ambientes de programação voltados para back-end. 
Já o Linux oferece maior controle e facilidade para trabalhar com ferramentas de programação, como Docker e servidores, e é muito usado em ambientes de desenvolvimento e produção, mas pode ser mais difícil de aprender e usar, principalmente para quem não está acostumado com a linha de comando.



**4° Diagrama de classes UML:**

<img width="1167" height="647" alt="image" src="https://github.com/user-attachments/assets/fc410466-9900-4290-9499-479ce6a5ba9e" />


**5° Código Java:**

```java 
public class Main {
    public static void main(String[] args) {
        Empresa empresa = getEmpresa();

        System.out.println("Funcionários cadastrados:");
        empresa.listarFuncionarios();

        empresa.promover("123.456.789-0", "Coordenador");

        empresa.aumentarSalario("098.765.432-1", 500);

        Funcionarios encontrado = empresa.buscarFuncionario("56.076.164-8");
        if(encontrado != null){
            System.out.println("Funcionário encontrado: " + encontrado);
        } else {
            System.out.println("Funcionário não encontrado!");
        }

        empresa.removerFuncionarios("123.456.789-0");

        System.out.println("\nFuncionários após remoção:");
        empresa.listarFuncionarios();
    }

    private static Empresa getEmpresa() {
        Empresa empresa = new Empresa();

        Funcionarios primeiro = new Funcionarios();
        primeiro.setNome("Davi Andrade");
        primeiro.setRg("56.076.164-8");
        primeiro.setCargo("Engenheiro");
        primeiro.setSalario(6500.00);

        Funcionarios segundo = new Funcionarios();
        segundo.setNome("Nicolas Anderson");
        segundo.setRg("123.456.789-0");
        segundo.setCargo("Professor");
        segundo.setSalario(2000.00);

        Funcionarios terceiro = new Funcionarios();
        terceiro.setNome("Gustavo Zago");
        terceiro.setRg("098.765.432-1");
        terceiro.setCargo("Faxineiro");
        terceiro.setSalario(1518.53);

        empresa.adicionarFuncionario(primeiro);
        empresa.adicionarFuncionario(segundo);
        empresa.adicionarFuncionario(terceiro);
        return empresa;
    }
}

```

```java
import java.util.LinkedList;
import java.util.List;

public class Empresa {
    private String nome;
    private String cnpj;
    private List<Funcionarios> funcionarios = new LinkedList<>();

    void adicionarFuncionario(Funcionarios funcionario){
        this.funcionarios.add(funcionario);
    }

    void removerFuncionarios(String rg){
        funcionarios.removeIf(funcionario -> funcionario.getRg().equals(rg));
    }

    void promover(String rg, String novoCargo){
        for(Funcionarios funcionario : funcionarios){
            if(funcionario.getRg().equals(rg)){
                funcionario.setCargo(novoCargo);
                System.out.println(funcionario.getNome() + " foi promovido para " + novoCargo);
            }
        }
    }

    void aumentarSalario(String rg, double aumento){
        for(Funcionarios funcionario : funcionarios){
            if(funcionario.getRg().equals(rg)){
                funcionario.setSalario(funcionario.getSalario() + aumento);
                System.out.println("Novo salário de " + funcionario.getNome() + ": " + funcionario.getSalario());
            }
        }
    }

    Funcionarios buscarFuncionario(String rg){
        for(Funcionarios funcionario : funcionarios){
            if(funcionario.getRg().equals(rg)){
                return funcionario;
            }
        }
        return null;
    }

    void listarFuncionarios(){
        for(Funcionarios funcionario : funcionarios){
            System.out.println(funcionario);
        }
    }
}

```

```java
public class Funcionarios {
    private String nome;
    private String rg;
    private String cargo;
    private double salario;

    public String getNome(){
        return nome;
    }

    public String getRg(){
        return rg;
    }

    public String getCargo(){
        return cargo;
    }

    public double getSalario(){
        return salario;
    }

    public void setNome(String nome){
        this.nome = nome;
    }

    public void setRg(String rg){
        this.rg = rg;
    }

    public void setCargo(String cargo) {
        this.cargo = cargo;
    }

    public void setSalario(double salario){
        this.salario = salario;
    }

    @Override
    public String toString() {
        return "Nome: " + nome + ", RG: " + rg + ", Cargo: " + cargo + ", Salário: " + salario;
    }

}

```


**6° Teste automatizados:**

```java

public class Teste {
    public static void teste(String[] args) {
        Empresa empresa = getEmpresa();

        System.out.println("Funcionários cadastrados:");
        empresa.listarFuncionarios();

        empresa.promover("123.456.789-0", "Coordenador");

        empresa.aumentarSalario("098.765.432-1", 500);

        Funcionarios encontrado = empresa.buscarFuncionario("56.076.164-8");
        if(encontrado != null){
            System.out.println("Funcionário encontrado: " + encontrado);
        } else {
            System.out.println("Funcionário não encontrado!");
        }

        empresa.removerFuncionarios("123.456.789-0");

        System.out.println("\nFuncionários após remoção:");
        empresa.listarFuncionarios();
    }

    private static Empresa getEmpresa() {
        Empresa empresa = new Empresa();

        Funcionarios primeiro = new Funcionarios();
        primeiro.setNome("Davi Andrade");
        primeiro.setRg("56.076.164-8");
        primeiro.setCargo("Engenheiro");
        primeiro.setSalario(6500.00);

        Funcionarios segundo = new Funcionarios();
        segundo.setNome("Nicolas Anderson");
        segundo.setRg("123.456.789-0");
        segundo.setCargo("Professor");
        segundo.setSalario(2000.00);

        Funcionarios terceiro = new Funcionarios();
        terceiro.setNome("Gustavo Zago");
        terceiro.setRg("098.765.432-1");
        terceiro.setCargo("Faxineiro");
        terceiro.setSalario(1518.53);

        empresa.adicionarFuncionario(primeiro);
        empresa.adicionarFuncionario(segundo);
        empresa.adicionarFuncionario(terceiro);
        return empresa;
    }
}
```














