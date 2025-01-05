## Variáveis

### **1. `var`**  
`var` é a forma mais antiga de declarar variáveis em JavaScript. Tem escopo de função, não respeita o escopo de bloco, e pode ser redeclarada.

#### **Onde usar `var`:**
- Em código legado, onde outros desenvolvedores possam já estar usando `var`.
- Quando a variável precisa ser acessível em todo o escopo de uma função (mas não em bloco).

#### **Exemplo de uso de `var` em função:**
```javascript
function exemploVar() {
  var texto = "Dentro da função";
  if (true) {
    var texto = "Redeclarado no mesmo escopo de função";
    console.log(texto); // "Redeclarado no mesmo escopo de função"
  }
  console.log(texto); // "Redeclarado no mesmo escopo de função"
}
exemploVar();
```

#### **Onde não usar `var`:**
- Não é recomendado em código moderno, pois pode causar comportamento inesperado devido ao escopo estranho.
- **Erro comum:**
  ```javascript
  if (true) {
    var exemplo = "Var no bloco";
  }
  console.log(exemplo); // "Var no bloco" (mesmo fora do bloco!)
  ```

---

### **2. `let`**  
`let` é mais moderno e respeita o escopo de bloco, sendo preferido para variáveis que precisam ser reatribuídas.

#### **Onde usar `let`:**
- Quando você sabe que o valor da variável pode mudar ao longo do programa.
- Para declarar variáveis com escopo específico (blocos, laços ou funções).

#### **Exemplo de uso de `let`:**
```javascript
if (true) {
  let idade = 25;
  console.log(idade); // 25
}
// console.log(idade); // ReferenceError: idade is not defined
```

#### **Onde não usar `let`:**
- Não use `let` para valores que não mudam, pois isso vai contra sua semântica.
- **Erro comum:**
  ```javascript
  let numero = 5;
  numero = 10; // OK
  const numeroFixo = 5;
  numeroFixo = 10; // TypeError
  ```

---

### **3. `const`**  
`const` é usado para declarar valores constantes ou referências a objetos e arrays que não mudarão de referência (mas seus valores internos podem mudar).

#### **Onde usar `const`:**
- Para variáveis que nunca terão o valor reatribuído.
- Para objetos e arrays que você quer proteger contra reatribuição.

#### **Exemplo de uso de `const`:**
```javascript
const PI = 3.14;
const pessoa = { nome: "Lucas" };
pessoa.nome = "João"; // OK, você pode modificar a propriedade
console.log(pessoa); // { nome: "João" }
```

#### **Onde não usar `const`:**
- Quando você sabe que o valor precisa mudar durante a execução.
- **Erro comum:**
  ```javascript
  const contador = 0;
  contador = 1; // TypeError: Assignment to constant variable.
  ```

---

### **Resumo da Utilização:**
| Tipo       | Quando Usar                                                      | Quando Não Usar                                               |
|------------|------------------------------------------------------------------|--------------------------------------------------------------|
| `var`      | Em código legado ou para compatibilidade.                        | Em código moderno ou com escopo de bloco.                    |
| `let`      | Quando o valor pode mudar ou precisa de escopo de bloco.         | Para valores constantes.                                      |
| `const`    | Para valores que não serão reatribuídos.                         | Quando precisa reatribuir ou para compatibilidade com código antigo. |

Usar **`let`** e **`const`** é a prática mais recomendada no JavaScript moderno, sendo que `var` deve ser evitado em projetos novos.