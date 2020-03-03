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

PHP tem, provavalmente, o "Hello World" mais fácil entre as linguagens. É só você escrever "Hello World" direto, sem aspas, nem comandos como `echo` ou `print`. É sério! Dúvida?

Abre um novo arquivo, escreve:

```
Hello, World!
```

Salve como `hello.php`, por exemplo e execute:

```bash
php hello.php
```

Tá lá, não tá? `Hello, World!` na tela!

Só um "Hello World" já é um programa válido em PHP porque qualquer coisa fora das tags de inicialização (`<?php`) e encerramento (`?>`) vai ser interpretado como um output (uma saída) pelo interpretador do PHP.

> Note que, exatamente por isso, existe na regras/recomendações/padrões de escrita de código da comunidade PHP a recomendação que diz pra você evitar colocar a tag de encerramento (`?>`) em arquivos que devem conter apenas PHP, pra te ajudar a evitar ter outout/saída de qualquer coisa extra que você não queia - https://www.php-fig.org/psr/psr-12/#22-files
