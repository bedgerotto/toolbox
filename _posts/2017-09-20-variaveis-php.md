---
layout: post
title: Declarando variáveis em PHP
date: 2017-09-20 22:30:50 -0300
categories: [PROGRAMMING]
tags: [PHP, CERTIFICATION] 
---

# Variáveis

As variáveis em PHP podem ser definidas com umas infinidade de nomes, porém, mesmo com toda a flexibilidade que a linguagem oferece existem algumas regrinhas e tipos para serem observados.

## Regra:

Toda variável em PHP deve iniciar com `$` (cifrão). Em seguida deve vir um caracter não numérico, isso inclui `_` e `-`.

A gama de definições possível para variáveis é representada pela seguinte expressão regular:
```
[a-zA-Z\x7f-\xff][a-zA-Z0-9\x7f-\xff]*
```

## Tipos

Apesar de não ser uma linguagem fortemente tipada, o PHP trabalha com alguns tipos primitivos, comuns entre outros lingagens, tipos compostos e especiais. Abaixo deixo uma tabela com os tipos que a própria documentação disponibiliza:

| Escalares | Compostos | Especial |
|-----------|-----------|----------|
| integer   | Array     | Resource |
| float     | Object    | Null     |
| string    | Callable  |          |
| boolean   |           |          |

Escalares: int, float, scalar, boolean

## Atribuição

Existem 2 tipos de atribuição de variáveis possíveis: **Por Valor** e **Por Referência**

### Atribuição por valor

Este tipo de atribuição é o mais comum e o mais utilizado. Na verdade, nem há muito o que se falar sobre ele pois o próprio conceito de variável o define.

Para utilizar este tipo basta declarar uma variável `$a` e atribuir um valor qualquer a ela. Depois podemos atribuir `$a` como valor de `$b`. Ao fazermos isto, `$a` e `$b` teriam o mesmo valor, porém ao mudar o valor de `$a`, `$b` manteria seu valor atribuído inicialmente. Exemplo:

```php
$a = 10; // Atribuição de $a
$b = $a; // Atribuição de $a em $b
$a = 20; // Trocando valor de $a

print $a; // 20
print $b; // 10
```

Simples, não? Pois então, vamos para o próximo.

### Atribuição por referência

Este modelo de atribuição de variáveis é menos utilizado por iniciantes, porém não menos importante. Neste caso vamos iniciar uma variável `$a` e atribuir o valor 10 a ela. Depois iniciamos a variável `$b` e atribuímos `$a` como referência utilizando o operador `&`. Neste ponto `$b` não tem um valor próprio, mas ele é uma referência para `$a`. Então se alteramos o valor de `$a`, logo, alteramos também o valor de `$b`. Exemplo:

```php
$a = 10; // Atribuição de $a
$b = &$a; // Atribuição de $a em $b
$a = 20; // Trocando valor de $a

print $a; // 20
print $b; // 20
```

> Obs: Objetos em PHP **SEMPRE** serão passados como referência

## Referências:

- [Documentação PHP](http://php.net/manual/pt_BR/language.variables.basics.php)
- [Livro Certificação PHP](https://www.casadocodigo.com.br/products/livro-certificacao-php)
