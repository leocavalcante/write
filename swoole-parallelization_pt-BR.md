# Paralelizando processos no PHP com a Swoole

Esse pequeno script:

```php
for ($i = 0; $i < 3; $i++) {
    echo "Index $i\n";
}
```

Todo mundo já sabe o que faz, bem simples.

Só que imagine que ao invés de um simples `echo` a gente faça algo mais elaborado que envolva *I/O* ou *CPU* e demore mais.
Vamos simular isso com `sleep()`?

```php
for ($i = 0; $i < 3; $i++) {
    sleep(2);
    echo "Index $i\n";
}
```

Tenso, né? Nossa task leva só 2 segundos, mas se acumula entre as 3 e leva 6 segundos!

```
$ time php co.php
Index 0
Index 1
Index 2

real    0m6.034s        
user    0m0.030s        
sys     0m0.000s        
```

Por muito tempo (e ainda hoje) isso é resolvido com muita gambiarra, tasks em background que depois você não sabe como pegar o retorno, filas em Redis pra coisas simples, complicação etc.
Com a **Swoole** muda tudo!
É só você colocar sua task dentro de uma *corotina* e serão executadas em **paralelo!**

```php
Swoole\Runtime::enableCoroutine();

for ($i = 0; $i < 3; $i++) {
    go(function () use ($i) {
        sleep(2);
        echo "Index $i\n";
    });
}
```

E é exatamente assim, por enquanto você precisa explicitamente habilitar com `Swoole\Runtime::enableCoroutine()` (será removido em futuras versões) e depois criar uma co-rotina usando a função go(); (sim, emprestaram o da Go-lang!)

```
$ time php co.php
Index 0
Index 1
Index 2

real    0m2.039s        
user    0m0.000s        
sys     0m0.030s        
```

Resolvido! 3 tasks que levam 2 segundos vão levar 2 segundos mesmo no total porque rodarão em paralelo.
