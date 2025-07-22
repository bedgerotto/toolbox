---
layout: post
title: Tratamento de arrays em PHP
date: 2017-05-23 22:30:50 -0300
categories: [PROGRAMMING]
tags: [PHP, CERTIFICATION] 
---

# Tratando arrays em PHP

No PHP existem diversas funções para se trabalhar com [arrays](https://secure.php.net/manual/pt_BR/ref.array.php). Neste post vou abordar 3 delas que conheci recentemente e que vêm me ajudando muito.

Como desenvolvedor web, me sinto obrigado a estar sempre atualizado e buscando conteúdos para aprender. Em meio a estes encontrei diversos posts falando sobre as mágicas que os métodos `.map()`, `.reduce()` e `.filter()` do JavaScript fazem. Confesso que fiquei bem empolgado e fui procurar algo parecido em PHP. E não é que encontrei?

```
array_reduce();
array_map();
array_filter();
```

Vou detalhar um a um logo abaixo:

---

## array_reduce

Conforme a descrição da documentação, esta função itera sobre os elementos de um array e executa uma função *callback* sobre cada um. Porém, retorna um único valor.

**Exemplo:**

```php
$toSum = [1, 2, 3, 4, 5];

$sum = array_reduce($toSum, function($carry, $num) {
    return ($carry + $num);
});
echo $sum;
// Neste caso será exibido na tela o número 15
```

---

## array_map

Também conforme a documentação do PHP, esta função executa uma função *callback* em cada elemento de um array passado por parâmetro. Essa função *callback* retorna o elemento modificado.

**Exemplo:**

```php
$clientes = [
    [ 'nome' => 'José', 'idade' => 30 ],
    [ 'nome' => 'Maria', 'idade' => 45 ],
    [ 'nome' => 'João', 'idade' => 35 ]
];

$newClientes = array_map(function ($arr) {
    $arr['nome'] = str_toupper($arr['nome']);
    $arr['idade'] = $arr['idade'] + 10;
    return $arr;
}, $clientes);

var_dump($newClientes);
/*
O resultado deve ser um array parecido com o seguinte:
[
    [ 'nome' => 'JOSÉ', 'idade' => 40 ],
    [ 'nome' => 'MARIA', 'idade' => 55 ],
    [ 'nome' => 'JOÃO', 'idade' => 45 ]
]
*/
```

---

## array_filter

Mais uma vez, baseado na própria documentação do PHP, podemos ver que o `array_filter` faz jus ao seu nome. Ele filtra um array passado por parâmetro, utilizando uma função *callback*. Cada elemento que deve estar no array é retornado pelo *callback*.

**Exemplo:**

```php
$clientes = [
    [ 'nome' => 'José', 'idade' => 30 ],
    [ 'nome' => 'Maria', 'idade' => 45 ],
    [ 'nome' => 'João', 'idade' => 35 ]
];

$newClientes = array_filter($clientes, function ($arr) {
    if ($arr['idade'] > 40) {
        return $arr;
    }
});

var_dump($newClientes);
/*
O resultado deve ser um array parecido com o seguinte:
[
    [ 'nome' => 'Maria', 'idade' => 45 ]
]
*/
```

---

São três exemplos bem simples, mas que demonstram um pouco do uso dessas funções poderosas. Existem diversas outras funções para se trabalhar com array no PHP que podem inclusive ser mescladas com as apresentadas aqui para gerar novos resultados. Com certeza as possibilidades são bem grandes.

**Espero ter ajudado e instigado no aprofundamento da linguagem.**

Até o próximo post.
