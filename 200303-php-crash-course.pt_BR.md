# PHP Crash Course (curso rápido)

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

As variáveis servem para armazenar valores em memória e poder reaproveita-los durante o programa. Elas são definidas usando o símbolo de dólar `$` seguido de algum identificado, por exemplo, uma variável para armazenar um nome:

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
