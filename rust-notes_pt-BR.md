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
