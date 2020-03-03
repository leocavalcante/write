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

Outras condições mais comuns também podem ser `==`, `<`, `<=` e `!=`.
