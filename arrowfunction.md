O símbolo ``=>`` é chamado de "arrow function" (função flecha) e foi introduzido no ES6 (ECMAScript 2015). É uma forma mais concisa de escrever funções em JavaScript.

Vou mostrar o mesmo código escrito de diferentes formas:

```javascript
// 1. Usando função tradicional
const dobrados = numeros.map(function(n) {
    return n * 2;
});

// 2. Usando arrow function (forma que você mostrou)
const dobrados = numeros.map(n => n * 2);

// 3. Arrow function com múltiplos parâmetros precisaria de parênteses
const soma = numeros.map((num, index) => num + index);

// 4. Arrow function com mais de uma linha precisa de chaves e return
const complexo = numeros.map(n => {
    const dobro = n * 2;
    return dobro + 1;
});
```

Algumas características importantes da arrow function:
1. Ela é mais curta que a função tradicional
2. Quando tem apenas uma linha, o `return` é implícito
3. Quando tem apenas um parâmetro, os parênteses são opcionais
4. Ela tem um comportamento diferente com o `this` comparado às funções tradicionais

No seu exemplo específico, `n => n * 2` é uma função que:
- Recebe um parâmetro `n`
- Retorna implicitamente o valor de `n` multiplicado por 2