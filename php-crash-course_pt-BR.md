# PHP Crash Course (Curso Rápido)

A ideia inicial desse markdown é virar um roteiro para uma série de pequenos vídeos, então algumas coisas podem parecer muito superficiais porque são tópicos para recordação durante a gravação, mas prometo fazer o máximo para que também vire uma espécie de mega artigo sobre o PHP (como o [PHP: The Right Way](https://phptherightway.com/)), até porque pode ser um documento vivo que se atualiza conforme o PHP e seu ecossistema também se atualizam.

## Contribua

Issues e PR's são muito bem-vindas! Desde uma seção nova, uma ordenação diferente, uma corração ortográfica... sinta-se à vontade para contribuir ou interagir de alguma forma ;)

## Introdução

O PHP é uma linguagem multi-paradigma e de propósito geral, mas que se da muito bem na web, especificamente no lado do servidor (server-side), sendo responsável principalmente por backends e APIs que incluem: acesso a bancos de dados, servidores TCP, websockets, chats, comunicação em tempo-real, gerenciamento de filas, comunicação com outras APIs e por aí vai um mundão de coisa que acontece em um servidor. **A última versão estável é a 7.4** e é a que o curso vai usar para ensina-la.

## Ambiente

### Instalação

#### Windows
* [Chocolatey](https://chocolatey.org/)
* `choco install php`

#### Mac
* [Homebrew](https://brew.sh/)
* `brew install php`

#### Linux
* `apt install php`
* `yum install php`

### Editor
* [VSCode](https://code.visualstudio.com/)
* [Intelephense](https://marketplace.visualstudio.com/items?itemName=bmewburn.vscode-intelephense-client)

## Hello, World!

PHP tem, provavalmente, o "Hello World" mais fácil entre as linguagens. É só você escrever "Hello World" direto, sem aspas, nem comandos como `echo` ou `print`. É sério! Duvida?

Abre um novo arquivo e escreve:

```
Hello, World!
```

Salve como `hello.php`, por exemplo e execute:

```bash
php hello.php
```

Tá lá, não tá? `Hello, World!` na tela!

Só um "Hello World" já é um programa válido em PHP porque qualquer coisa fora das tags de inicialização (`<?php`) e encerramento (`?>`) será interpretado como um output (uma saída) pelo interpretador do PHP.

> Note que, exatamente por isso, existe na regras/recomendações/padrões de escrita de código da comunidade PHP a recomendação que diz pra você evitar colocar a tag de encerramento (`?>`) em arquivos que devem conter apenas PHP, pra te ajudar a evitar ter outout/saída de qualquer coisa extra que você não queira - https://www.php-fig.org/psr/psr-12/#22-files

### O jeito mais comum

Ok, só queria que você começasse com essa ideia em mente, mas um "Hello, World!" mais "comum", como em outras linguagens, usando comandos que instruam o interpretor a imprimir algo na tela, seria:

```php
<?php
echo "Hello, World!";
```

Agora sim, usando o comando `echo` a gente consegue dizer pro PHP imprimir essa **String** "Hello, World!" na tela e esse comando vem depois de informar-mos que haverá código PHP nas linhas abaixo usando a tag de abertura `<?php`. O ponto-e-vírgula finaliza uma instrução, um *statement*.

#### Experimente!

```php
Hello,
<?php
echo "World!";
```

Mas, hey, pera aí! **Str**... o quê que você falou?

## Tipos

**String** é um tipo no PHP. Você de repente até já ouviu por aí que PHP não tem tipo, não é bem assim, PHP é uma linguagem **dinâmicamente tipada** e com **tipagem fraca**, mas os tipos estão lá.

 `String`s são usadas para representar textos, como o `"Hello, World!"`. Você define qual é esse texto delimitando-o com aspas duplas ou simples.

Além das `String`s também tem: `int` para representar números inteiros como `1`, `2`, `3` etc; `float` pra representar números racionais usando um ponto flutuante, ou seja, ½ fica `0.5`; `bool` para representar valores *Booleanos* como `true` ou `false` e `array` para representar coleções/conjuntos.

## Operadores

Você pode performar operações nesses diferentes tipos de valores, os exemplos mais comuns são os operadores aritiméticos, como somar dois inteiros:

```php
<?php
echo 2 + 2;
```

E você pode "somar" (concatenar) duas strings com o ponto:

```php
<?php
echo "Hello," . "World!":
```

Incrementar e decrementar inteiros com `++` e `--` respectivamente:

```php
<?php
$n = 1;
$n++;
echo $n; // 2
```

```php
<?php
$n = 2;
$n--;
echo $n; // 1
```

Se quiser incrementar ou decrementar por um valor maior que 1, pode usar `+=` e `-=`:

```php
<?php
$n = 1;
$n += 2;
echo $n; // 3
```

## Variáveis

As variáveis servem para armazenar valores em memória e poder reaproveita-los durante o programa. Elas são definidas usando o símbolo de dólar `$` seguido de um identificador e uma atribuição representada pelo símbolo de igual (`=`), por exemplo, uma variável para armazenar um nome:

```php
<?php
$name = "Leo";
echo $n;
```

Esse programa vai imprimir `Leo` na tela, ou seja, o valor da variável passada para o comando `echo`.

Variáveis podem armazenar outros tipos além de `String`s, por exemplo, idade (*age*) como um número inteiro:

```php
<?php

$name = "Leo";
$age = 28;

echo $name;
echo $age;
```

O resultado desse programa não ficou muito legal, certo? Ficou `Leo28` tudo junto. Como a gente pode incluir uma quebra de linha entre o nome e a idade ou melhor, colocar as legendas "Nome:" e "Idade:" antes desses valores?

As `String`s tem uma propriedade especial, elas podem interpolar com as variáveis e usar o valor dessas variáveis:

```php
<?php

$name = "Leo";
$age = 28;

echo "Nome: $name Idade: $age";
```

Agora o `echo` é feito com uma nova `string` e essa nova `string` interpola os valores de `$name` (nome) e `$age` (idade).

Para incluir uma quebra de linha, você pode incluir o caractere especial `\n`:

```php
echo "Nome: $name\nIdade: $age";
```

## Estruturas para controle de fluxo de dados

Aqui entra a tal da "lógica de programação", as famosas estruturas `if..else`, `for`, `foreach`, `while`, `switch` etc.

A mais comum é a `if..else`, é quando você começa a criar condicionais e ganha poder de expressão para computações um pouco mais complexas usando as variáveis. Uma condição, por exemplo: *se a idade for maior ou igual a 18, então pode dirigir* ficaria:

```php
<?php

$name = "Leo";
$age = 28;

if ($age >= 18) {
  echo "$name pode dirigir";
} else {
  echo "$name não pode dirigir";
}
```

Como 28 é maior que 18, o código executado é o que está entre o primeiro bloco delimitado pelas chaves `{` `}`. Mude a idade para um valor menor que 18 e veja que o segundo bloco que será executado, o bloco do `else`.

Você também pode encadear sequências de condições na mesma estrutura, por exemplo:

```php
if ($age >= 18) {
  echo "Pode dirigir e votar";
} else if ($age >= 16) {
  echo "Pode apenas votar";
} else {
  echo "Não pode nem dirigir nem votar";
}
```

Outras condições mais comuns também podem ser `==` (igual), `<` (menor), `<=` (menor ou igual) e `!=` (diferente).

O `while` vai executar o código de um bloco **enquanto** a condição informada for verdadeira, for `true`:

```php
<?php
$n = 0;

while ($n < 3) {
  $n++;
}

echo $n; // 3
```

`$n` começou o programa com o valor `0` e nós falamos pro interpretador: *__enquanto__ (`while`) `$n` for menor (`<`) que o valor `3`*, no bloco do `while` nós incrementamos o valor de `$n`. Na primeira vez o `$n` é `0`, então a condição é verdadeira (`0` é menor que `3`) o bloco é executado e incrementa o valor de `$n` que agora é `1`, ainda é menor que `3`, então vai executaor o bloco de novo que por sua vez vai incrementar de novo e assim por diante até que `$n` seja `3`... `3` não é menor que `3`, `3` é **igual** a `3`, então o bloco ao invés de ser executado ele é pulado e chegamos no `echo $n` que vai imprimir o valor `3` de `$n`.

O `for` é uma estrutura de repetição como o `while`, mas um pouquinho mais poderosa. Nela a gente informa um inicializador, uma condição e uma expressão pra ser executação no fim de cada iteração/cada volta.

```php
<?php
for ($i = 0; $i < 3; $i++) {
    echo $i;
}
```

Para (`for`) `$i` igual a `0`, enquanto `$i` for menor que `3`, incremente (`++`) `$i`.

## Array

Os arrays são estruturas de dados para coleções e conjuntos. Se você precisar de uma lista de nomes, ao invés de um nome só, ficaria:

```php
<?php
$names = ["Leo", "Alice", "Bob"];
print_r($names);
```

Os arrays são delimitados por colchetes `[` `]` e os valores dentro dele são separados por vígula.

Note que no resultado desse programa:

```
Array
(
    [0] => Leo
    [1] => Alice
    [2] => Bob
)
```

Tem esses valores antes do símbolo `=>`, esses valores são as chaves do array, no caso de uma lista, essas chaves são os índices, uma lista é um *index-based array*, ou seja, um array baseado em índices numéricos.

A gente pode percorrer a estrutuda de dados da lista usando o `foreach`:

```php
<?php
$names = ["Leo", "Alice", "Bob"];

foreach ($names as $name) {
    echo $name;
}
```

Ou seja, **para cada** (`foreach`) um dos nomes (`$names`), pegue o valor **como** (`as`) nome (`$name`) e execute o bloco. No caso, o bloco invoca o comando `echo` passando a variável `$name` para imprimir os nomes na tela.

Arrays também pode ser associativos e ter strings ao invés de inteiros (`int`) como chave:

```php
<?php
$dev = [
  'name' => 'Leo',
  'age' => 18,
];

print_r($dev);
```

Note que agora definimos uma chave e um valor, ao invés de só um valor:

```
Array
(
    [name] => Leo
    [age] => 18
)
```

O no resultado do programa, vemos que ao invés de `0` e `1`, temos as chaves `name` e `age` que haviamos definido.

Para acessar o valor de uma chave diretamente, basta usar o nome da chave como string entre colchetes:

```php
echo $dev['name']; // Leo
```

ou

```php
echo $dev['age']; // 28
```

Você também pode ter arrays dentro de arrays misturando *index-based* (listas) com *key-based* associativo:

```php
$devs = [
  ['name' => 'Leo', 'age' => 28],
  ['name' => 'Alice', 'age' => 29],
  ['name' => 'Bob', 'age' => 30],
];
```

É possível acessar elementos de uma lista diretamente, como fizemos no array associativo, passando qual índice você quer acessar, mas nesse caso como inteiro, então sem as aspas:

```php
print_r($devs[0]);
```

As listas são *zero-based*, o primeiro índice é o `0`, não o 1.

## Funções

Por enquanto nós só fizemos programas lineares, começa na primeira linha, vai até o fim e maravilha. Já é possível fazer pequenos scripts dessa forma, mas e se precisarmos repetir trechos de códigos similares? Aí vem as funções e algumas noções de reaproveitamenteo de código, elas encapsulam o comportamento que você programou numa estrutura que pode ser chamada diversas vezes, como fizemos com o `print_r` anteriormente:

```php
<?php

function say_hello()
{
  echo "Hello, World!";
}

say_hello(); // Hello, World!
say_hello(); // Hello, World!
```

As funções podem receber parâmetros diferentes para reaproveitar um mesmo comportamento em dados diferentes:

```php
<?php

function say_hello($name)
{
  echo "Hello, $name!";
}

say_hello("Leo"); // Hello, Leo!
say_hello("Alice"); // Hello, Alice!
say_hello("Bob"); // Hello, Bob!
```

Lembrei que falei sobre PHP ter tipagem dinâmica? Bom, pras variáveis é verdade, mas para as funções (e outros que veremos mais pra frente) é possível sim definir **estaticamente** o tipo dos seus argumentos e o tipo do retorno da função.

```php
function say_hello(string $name): void
{
  echo "Hello, $name!";
}
```

Agora essa função está mais estrita sobre o tipo de parâmetro que ela pode receber, apenas `string`s vão funcionar, se você passar um `int` (inteiro) vai dar um erro e isso é muito legal porque trás mais garatias pro seu código e evita os temidos *bugs* que você só encontraria quando rodasse o projeto.

Para que esse PHP mais legal, fechadinho e estrito, funcione, você precisa habilitar em cada arquivo com `declare(strict_types=1)`. Só colocar logo depois do `<?php` (veremos a seguir).

`void` siginifica que a função não vai retornar nada, mas o que é esse retorno?

### Retorno

As funções podem receber parâmetros e também retornar um valor, isso trás mais utilidade e reaproveitamento para elas. Vamos para uma função de soma:

```php
<?php declare(strict_types=1); // Olha ele aqui

function sum(int $a, int $b): int
{
  return $a + $b;
}

echo sum(1, 1); // 2
```

Recebe dois inteiros (`int`) e retorna a soma deles. Agora pode não parecer muito útil, mas imagina que você pode ter uma equação ou algoritimo mais complexo dentro de uma função.

```php
<?php declare(strict_types=1); // Olha ele aqui

function average(int $a, int $b): int
{
  return ($a + $b) / 2;
}

echo average(2, 4); // 3
echo average(3, 7); // 5
```

## Closures

As Closures são funções anônimas (funções sem nome):

```php
<?php declare(strict_types=1);

$sum = function (int $a, int $b): int {
  return $a + b;
};

$mul = function (int $a, int $b): int {
  return $a * $b;
};
```

Duas Closures, uma para soma e uma para multiplicação e ambas atribuidas às variáveis `$sum` e `$mul` respectivamente. A atribuição às variáveis, permite que as funções anônimas sejam invocadas mesmo sem sabermos seu nome, usuamos então o nome da variável, com o sinal de dólar mesmo:

```php
echo $sum(2, 2); // 4
echo $mul(3, 3); // 9
```

As Closures tem propriedades como **First-class** (podem ser atribuídas a variáveis) e **High-order** (podem ser parâmetros ou retornos de outras funções), são atributos essênciais para **Programação Funcional**.

### First-class

É o que vimos anteriormente , uma função sendo atribuida à uma variável. Seguindo a linha de operações aritiméticas, uma função subtração ficaria:

```php
$sub = function (int $a, int $b): int {
    return $a - $b;
};
```

### High-order

Uma função recebendo ou retornando outra função parece coisa de louco no inicio, mas é algo extremamente poderoso para composição de novas funcionalidades a partir de funcionalidades já existentes.

```php
$double = function (int $val) use ($mul): int {
    return $mul($val, 2);
};

echo $double(2); // 4
```

As Closures não tem acesso ao scopo antecessor automaticamente, por isso a adição do `use ($mul)`, para a Closure saber que a outra Closure atribuida a variável `$mul` existe. Nesses casos simples, isso pode ser evitado com arrow-functions:

### Arrow functions

As arrow-functions são simplesmente formas reduzidas de escrever Closures:

```php
$double = fn(int $val): int => $mul($val, 2);
```

Note como a sintaxe do nosso programa fica muito mais simples e elegante.

## Classes

Os arrays associativos são mais interessantes quando precisamos de uma estrutura de dados conhecida como HashMap. Para o exemplo anterior o ideal é trazer mais semântica com mais tipos usando o recurso de classes e aqui daremos também nossa primeira espiada na famosa **Orientação a Objetos**.
