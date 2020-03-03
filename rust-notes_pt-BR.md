# Rust notes

Minhas "descobertas" me aventurando por Rust em 2020!
> ⚠️ As anotações aqui são de um leigo descobrindo a linguagem, se você já é experiênte e se encomodou com algo, por favor, abra uma issue ou envie uma PR ;)

## !

Assim que você começa e vê o famoso "Hello, world!", você já de cara com uma macro e sintaxe pra ela é como chamar uma função, mas com uma exclamação (**!**) no final.

```rust
fn main() {
    println!("Hello World!");
}
```

Você já fica se perguntando "o que é essa f*cking '!'?", "será que toda função usa?", mas não se preocupe agora.

## str, &str e String

Ter 3 tipos de strings é algo estranho de primeira, você vai mexer mais com `&str` e `String`.<br>
Basicamente (visão de um leigo): a `&str` é quando o compilador sabe o tamanho em tempo de compilação e `String` é quando você vai receber uma string que não da pra ter tamanho determinado em tempo de compilação, tipo uma variável de ambiente, um argumento da linha de comando, uma requisição HTTP, o retorno de um banco de dados etc.<br>
Um é estático/compile-time a outra é dinâmica/run-time.

## Ownership and borrowing

Bom, esse é **principal conceito da Rust**, aqui que faz a Rust ser a Rust então esse conceito te pega logo de cara, em coisas triviais como passar uma variável pra função e tentar usar essa variável depois.

```rust
fn say_hello(name: String) {
    println!("Hello, {}!", name);
}

fn main() {
    let name = "Leo".to_string();
    say_hello(name);
    say_hello(name);
}
```

Esse código inofensivo retorna um `error[E0382]: use of moved value: name`, aí você já começa a sacar que o Rust vai te dar canseira. Isso é porque o tipo `String` não implementa a trait `Copy` então quando uma `String` é passada pra uma função ela vai como **ownership**, você entrega ela pra função `say_hello` e não tem mais no scopo da `main`, você "resolve" isso com o **borrowing**, ou seja, ai você empresta ao invés de dar. Você diz que vai só emprestar ao invés de tomar, usando o `&` tanto na declaração do tipo do argumento quanto na váriavel como parâmetro:

```rust
fn say_hello(name: &String) {
    println!("Hello, {}!", name);
}

fn main() {
    let name = "Leo".to_string();
    say_hello(&name);
    say_hello(&name);
}
```

Aí você pensa "vou sair usando `&` em tudo então", mas não desista, não se entregue, uma hora essa ideia de ownership e borrowing entra na mente e você entende quando usar um ou outro.
