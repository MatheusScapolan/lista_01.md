# Instruções
- Faça uma cópia deste arquivo .md para um repositório próprio
- Resolva as 8 questões objetivas assinalando a alternativa correta e **justificando sua resposta.**
- Resolva as 2 questões dissertativas escrevendo no próprio arquivo .md
- Lembre-se de utilizar as estruturas de código como ``esta aqui com ` `` ou
```javascript
//esta aqui com ```
let a = "olá"
let b = 10
print(a)
```
- Resolva as questões com uso do Visual Studio Code ou ambiente similar.
- Teste seus códigos antes de trazer a resposta para cá.
- Cuidado com o uso de ChatGPT (e similares), pois entregar algo só para ganhar nota não fará você aprender. Não seja dependente da máquina!
- Ao final, publique seu arquivo lista_01.md com as respostas em seu repositório, e envie o link pela Adalove. 

# Questões objetivas
**1) Considerando a execução do código abaixo, indique a alternativa correta e justifique sua resposta.**
```javascript
console.log(x);
var x = 5;
console.log(y);
let y = 10;
```
**a) A saída será undefined seguido de erro** --> Alternativa Correta

b) A saída será 5 seguido de 10

c) A saída será undefined seguido de undefined

d) A saída será erro em ambas as linhas que utilizam console.log

Justificativa: 

A alternativa correta é: a ) A saída será undefined seguido de erro

No código anterior existem duas variáveis declaradas com var e let. 

Para a variável x declarada com var:

No Java Script, variáveis declaradas com var são "elevadas" para o topo do escopo, porém sem inicialização. Neste sentido, isso mostra que o código é interpretado como se tivesse uma declaração var x - no topo - só que o valor 5 só é definido posteriormente. Sendo assim, console.log(x) - imprime undefined, uma vez que x foi declarada, mas não recebeu um valor.

Para a variável y declarada com let:

Já as variáveis declaradas como let também são elevadas (hoisted), porém entram em um campo chamado de "Temporal Dead Zone" até a linha em que são inicializadas, o que significa que não podem ser usadas antes da sua declaração. Assim, console.log(y); causa um erro porque y ainda não foi inicializado.

Depois de eu executar o código é mostrado o seguinte resultado:

console.log(x); exibe undefined.

console.log(y); lança um erro (ReferenceError: Cannot access 'y' before initialization).

**2) O seguinte código JavaScript tem um erro que impede sua execução correta. Analise e indique a opção que melhor corrige o problema. Justifique sua resposta.**

```javascript
function soma(a, b) {
    if (a || b === 0) {
        return "Erro: número inválido";
    }
    return a + b;
}
console.log(soma(2, 0));
```

**a) Substituir if (a || b === 0) por if (a === 0 || b === 0)** --> Alternativa Correta

b) Substituir if (a || b === 0) por if (a === 0 && b === 0)

c) Substituir if (a || b === 0) por if (a && b === 0)

d) Remover completamente a verificação if (a || b === 0)

Justificativa:

A alternativa correta é: a) Substituir if (a || b === 0) por if (a === 0 || b === 0)

O problema no código acima está na forma como a condição if (a || b === 0) é definida. O operador || (OU) faz com que a verificação seja interpretada de forma incorreta: O JS interpreta isso errado porque ele lê b === 0 primeiro (o que está correto), mas depois entende a sozinho, e qualquer número diferente de 0 é considerado verdadeiro (true).

Sendo assim, mesmo quando a = 2, a condição é verdadeira.

Dessa forma, a solução é escrever corretamente a verificação de 0 para ambas as variáveis separadamente, assim: if (a === 0 || b === 0). Por fim, o código só retornará erro quando pelo menos um dos números for 0, do jeito que realmente é para ser feito.

______
**3) Ao executar esse código, qual será a saída no console? Indique a alternativa correta e justifique sua resposta.**
```javascript
function calcularPreco(tipo) {
    let preco;

    switch(tipo) {
        case "eletrônico":
            preco = 1000;
        case "vestuário":
            preco = 200;
            break;
        case "alimento":
            preco = 50;
            break;
        default:
            preco = 0;
    }

    return preco;
}

console.log(calcularPreco("eletrônico"));
```

a) O código imprime 1000.

**b) O código imprime 200.** --> Alternativa Correta

c) O código imprime 50.

d) O código gera um erro.

Justificativa: 

A alternativa correta é: b) O código imprime 200.

O erro do código acima está na ausência de um break após preco = 1000;. No switch, se não for colocado break, o JS continua executando os proximos "cases" até encontrar um break ou chegar ao fim do código.

No início, o código começa verificando tipo === "eletrônico" - o que está correto -  então preco = 1000;.

Só que como não há break, ele continua para o próximo case ("vestuário"), que muda o preco para 200 e só então encontra o break, parando a execução.

Sendo assim, o valor final retornado pela função é 200.

Por fim, para que isso seja corrigido tem que adicionar um break após preco = 1000. Asssim, garantindo que o código pare assim que encontrar a opção correta.

______
**4) Ao executar esse código, qual será a saída no console? Indique a alternativa correta e justifique sua resposta.**
```javascript
let numeros = [1, 2, 3, 4, 5];

let resultado = numeros.map(x => x * 2).filter(x => x > 5).reduce((a, b) => a + b, 0);

console.log(resultado);
```
a) 0

b) 6

c) 18

**d) 24** --> Alternativa Correta

Justificativa:

A alternativa correta é a d) 24

Vou explicar por linha os códigos:

O map(x => x * 2) multiplica cada número do array por 2, assim: 

[1, 2, 3, 4, 5] --> [2, 4, 6, 8, 10]

O filter(x => x > 5) mantém apenas os valores maiores que 5, assim:

[6, 8, 10]

O reduce((a, b) => a + b, 0) soma todos os números do array filtrado:

6 + 8 + 10 = 24

**5) Qual será o conteúdo do array lista após a execução do código? Indique a alternativa correta e justifique sua resposta.**

```javascript
let lista = ["banana", "maçã", "uva", "laranja"];
lista.splice(1, 2, "abacaxi", "manga");
console.log(lista);
```

a) ["banana", "maçã", "uva", "abacaxi", "manga", "laranja"]

b) ["banana", "abacaxi", "manga"]

**c) ["banana", "abacaxi", "manga", "laranja"]** --> Alternativa Correta

d) ["banana", "maçã", "uva", "abacaxi", "manga"]

Justificativa:

A alternativa correta é: c) ["banana", "abacaxi", "manga", "laranja"].

O método splice(1, 2, "abacaxi", "manga") tem a função de modificar a lista, assim, removendo e adicionando elementos. O primeiro parâmetro (1) indica que a alteração começa no índice 1, onde está "maçã". O segundo parâmetro (2) especifica que dois elementos serão removidos a partir desse índice, ou seja, "maçã" e "uva".

Posteriormente, os valores "abacaxi" e "manga" são inseridos no lugar dos removidos. Assim, a lista original ["banana", "maçã", "uva", "laranja"] se transforma em ["banana", "abacaxi", "manga", "laranja"].

______
**6) Abaixo há duas afirmações sobre herança em JavaScript. Indique a alternativa correta e justifique sua resposta**

I. A herança é utilizada para compartilhar métodos e propriedades entre classes em JavaScript, permitindo que uma classe herde os métodos de outra sem a necessidade de repetir código.  
II. Em JavaScript, a herança é implementada através da palavra-chave `extends`.


**a) As duas afirmações são verdadeiras, e a segunda justifica a primeira.** --> Alternativa Correta

b) As duas afirmações são verdadeiras, mas a segunda não justifica a primeira.

c) A primeira afirmação é verdadeira, e a segunda é falsa.

d) A primeira afirmação é falsa, e a segunda é verdadeira.

A alternativa correta é: a) As duas afirmações são verdadeiras, e a segunda justifica a primeira.

Justificativa:

A herança em JavaScript permite que uma classe reutilize métodos e propriedades de outra, evitando a repetição de código.

A palavra-chave extends é utilizada para implementar a herança, permitindo que uma classe filha herde comportamentos de uma classe pai. Dessa forma, uma subclasse pode acessar ou até sobrescrever métodos da superclasse.

______
**7) Dado o seguinte código. Indique a alternativa correta e justifique sua resposta.**

```javascript
class Pessoa {
  constructor(nome, idade) {
    this.nome = nome;
    this.idade = idade;
  }

  apresentar() {
    console.log(`Olá, meu nome é ${this.nome} e tenho ${this.idade} anos.`);
  }
}

class Funcionario extends Pessoa {
  constructor(nome, idade, salario) {
    super(nome, idade);
    this.salario = salario;
  }

  apresentar() {
    super.apresentar();
    console.log(`Meu salário é R$ ${this.salario}.`);
  }
}
```

I) A classe Funcionario herda de Pessoa e pode acessar os atributos nome e idade diretamente.  
II) O método `apresentar()` da classe Funcionario sobrepõe o método `apresentar()` da classe Pessoa, mas chama o método da classe pai usando `super`.  
III) O código não funciona corretamente, pois Funcionario não pode herdar de Pessoa como uma classe, já que o JavaScript não suporta herança de classes.

Quais das seguintes afirmações são verdadeiras sobre o código acima?

**a) I e II são verdadeiras.** --> Alternativa Correta

b) I, II e III são verdadeiras.

c) Apenas II é verdadeira.

d) Apenas I é verdadeira.

A alternativa correta é: a) I e II são verdadeiras.

Justificativa:

A classe Funcionario herda de Pessoa usando extends. Isso significa que os atributos nome e idade são herdados e podem ser acessados diretamente por meio de this.nome e this.idade.

A classe Funcionario sobrescreve o método apresentar() de Pessoa, mas dentro desse método, chama o método da superclasse usando super.apresentar(). Isso garante que a funcionalidade original seja preservada antes de adicionar a mensagem sobre o salário.
______

**8) Analise as afirmações a seguir. Indique a alternativa correta e justifique sua resposta.**

**Asserção:** O conceito de polimorfismo em Programação Orientada a Objetos permite que objetos de diferentes tipos respondam à mesma mensagem de maneiras diferentes.  
**Razão:** Em JavaScript, o polimorfismo pode ser implementado utilizando o método de sobrecarga de métodos em uma classe.

a) A asserção é falsa e a razão é verdadeira.

**b) A asserção é verdadeira e a razão é falsa.**

c) A asserção é verdadeira e a razão é verdadeira, mas a razão não explica a asserção.

d) A asserção é verdadeira e a razão é verdadeira, e a razão explica a asserção.

A alternativa correta é: b) A asserção é verdadeira e a razão é falsa.

Justificativa:

O polimorfismo permite que diferentes classes implementem métodos com o mesmo nome, mas com comportamentos distintos, o que torna a afirmativa I correta. 
No entanto, a razão está incorreta, pois JavaScript não suporta sobrecarga de métodos como em outras linguagens. Se um método for declarado mais de uma vez na mesma classe, apenas a última definição será utilizada.
______

# Questões dissertativas
9) O seguinte código deve retornar a soma do dobro dos números de um array, mas contém erros. Identifique os problema e corrija o código para que funcione corretamente. Adicione comentários ao código explicado sua solução para cada problema.

```javascript
function somaArray(numeros) {

    for (i = 0; i < numeros.size; i++) {
        soma = 2*numeros[i];
    }
    return soma;
}
console.log(somaArray([1, 2, 3, 4]));
```
Resposta:

```javascript
function somaArray(numeros) {
    let soma = 0; // inicializa a variável soma corretamente

    for (let i = 0; i < numeros.length; i++) { // corrigido "size" para "length"
        soma += 2 * numeros[i]; // corrigido para somar o dobro dos elementos ao invés de sobrescrever
    }

    return soma;
}

console.log(somaArray([1, 2, 3, 4])); // deve retornar 20
```
______
10) Crie um exemplo prático no qual você tenha duas classes:

- Uma classe `Produto` com atributos `nome` e `preco`, e um método `calcularDesconto()` que aplica um desconto fixo de 10% no preço do produto.
- Uma classe `Livro` que herda de `Produto` e modifica o método `calcularDesconto()`, aplicando um desconto de 20% no preço dos livros.

Explique como funciona a herança nesse contexto e como você implementaria a modificação do método na classe `Livro`.

Resposta:

```javascript
// classe base Produto
class Produto {
    constructor(nome, preco) {
        this.nome = nome;
        this.preco = preco;
    }

    calcularDesconto() {
        return this.preco * 0.9; // aplica um desconto de 10%
    }
}

// classe Livro que herda de Produto
class Livro extends Produto {
    constructor(nome, preco, autor) {
        super(nome, preco); // chama o construtor da classe pai
        this.autor = autor;
    }

    calcularDesconto() {
        return this.preco * 0.8; // aplica um desconto de 20% para livros
    }
}

// criando instâncias das classes
const produtoGeral = new Produto("Fone Gamer", 100);
const livro = new Livro("O Príncipe", 150);

// testando os descontos
console.log(`${produtoGeral.nome} com desconto: R$${produtoGeral.calcularDesconto()}`);
console.log(`${livro.nome} com desconto: R$${livro.calcularDesconto()}`);
```
Explicação do código:

O código demonstra o uso de herança em JavaScript com as classes Produto e Livro. A classe Produto define um construtor que recebe nome e preco, além do método calcularDesconto(), que aplica 10% de desconto. A classe Livro herda de Produto usando extends, chama o construtor da classe pai com super(nome, preco), adiciona o atributo autor e sobrescreve calcularDesconto(), aplicando um desconto maior de 20%.

Depois, são criadas as instâncias produtoGeral ("Fone Gamer", R$100) e livro ("O Príncipe", R$150). Ao chamar calcularDesconto(), o primeiro aplica 10%, reduzindo para R$90, e o segundo aplica 20%, reduzindo para R$120. Essa estrutura evita repetição de código e permite personalizar regras de desconto para diferentes tipos de produtos.