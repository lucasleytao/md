## Roteiro intermediário de estudo JavaScript

## **1. Manipulação Avançada de Arrays**
### **1.1 Métodos Funcionais**
- **Conceito**: Métodos que permitem transformar e manipular arrays de forma declarativa.
- **Principais Métodos**:
  - `map`: Transforma cada item do array.
  - `filter`: Filtra itens com base em uma condição.
  - `reduce`: Reduz o array a um único valor.
  - `forEach`: Itera sobre cada item sem retornar um novo array.
  - `find` e `findIndex`: Encontram itens no array.

- **Exemplo**:
  ```javascript
  const numeros = [1, 2, 3, 4, 5];

  const dobrados = numeros.map(num => num * 2); // [2, 4, 6, 8, 10]
  const pares = numeros.filter(num => num % 2 === 0); // [2, 4]
  const soma = numeros.reduce((acc, num) => acc + num, 0); // 15
  console.log(dobrados, pares, soma);
  ```

---

## **2. Programação Assíncrona**
### **2.1 Promises**
- **Conceito**: Maneira de lidar com operações assíncronas como requisições de dados.
- **Exemplo**:
  ```javascript
  const promessa = new Promise((resolve, reject) => {
    const sucesso = true;
    if (sucesso) resolve("Operação bem-sucedida!");
    else reject("Erro na operação.");
  });

  promessa
    .then(res => console.log(res)) // "Operação bem-sucedida!"
    .catch(err => console.error(err));
  ```

### **2.2 Async/Await**
- **Conceito**: Sintaxe simplificada para trabalhar com Promises.
- **Exemplo**:
  ```javascript
  const fetchDados = async () => {
    try {
      const res = await fetch("https://jsonplaceholder.typicode.com/posts");
      const dados = await res.json();
      console.log(dados);
    } catch (err) {
      console.error("Erro:", err);
    }
  };

  fetchDados();
  ```

---

## **3. Módulos**
### **3.1 Import e Export**
- **Conceito**: Permite dividir o código em diferentes arquivos.
- **Exemplo**:
  - **Arquivo `soma.js`**:
    ```javascript
    export const soma = (a, b) => a + b;
    ```

  - **Arquivo `app.js`**:
    ```javascript
    import { soma } from "./soma.js";
    console.log(soma(2, 3)); // 5
    ```

### **3.2 Módulos CommonJS (Node.js)**
- **Exemplo**:
  - **Arquivo `soma.js`**:
    ```javascript
    module.exports = (a, b) => a + b;
    ```

  - **Arquivo `app.js`**:
    ```javascript
    const soma = require("./soma");
    console.log(soma(2, 3)); // 5
    ```

---

## **4. Orientação a Objetos (OOP)**
### **4.1 Classes**
- **Conceito**: Estrutura para criar objetos com propriedades e métodos.
- **Exemplo**:
  ```javascript
  class Animal {
    constructor(nome, especie) {
      this.nome = nome;
      this.especie = especie;
    }

    fazerSom() {
      console.log(`${this.nome} faz um som!`);
    }
  }

  const cachorro = new Animal("Rex", "Cachorro");
  cachorro.fazerSom(); // "Rex faz um som!"
  ```

### **4.2 Herança**
- **Conceito**: Classes podem herdar de outras classes.
- **Exemplo**:
  ```javascript
  class Cachorro extends Animal {
    latir() {
      console.log("Au au!");
    }
  }

  const rex = new Cachorro("Rex", "Cachorro");
  rex.latir(); // "Au au!"
  ```

---

## **5. Trabalhando com JSON e APIs**
### **5.1 JSON (JavaScript Object Notation)**
- **Conceito**: Formato para transferência de dados.
- **Exemplo**:
  ```javascript
  const dados = '{"nome": "Lucas", "idade": 30}';
  const obj = JSON.parse(dados); // Converter para objeto
  console.log(obj.nome); // "Lucas"
  ```

### **5.2 Requisições HTTP**
- **Exemplo** (usando Fetch):
  ```javascript
  fetch("https://api.exemplo.com/usuarios")
    .then(res => res.json())
    .then(data => console.log(data))
    .catch(err => console.error(err));
  ```

---

## **6. Manipulação Avançada do DOM**
### **6.1 Criação Dinâmica de Elementos**
- **Conceito**: Criar e manipular elementos DOM via JavaScript.
- **Exemplo**:
  ```javascript
  const div = document.createElement("div");
  div.textContent = "Novo elemento";
  document.body.appendChild(div);
  ```

### **6.2 Eventos Complexos**
- **Conceito**: Trabalhar com eventos delegados e dinâmicos.
- **Exemplo**:
  ```javascript
  document.body.addEventListener("click", event => {
    if (event.target.tagName === "BUTTON") {
      console.log("Botão clicado:", event.target.textContent);
    }
  });
  ```

---

## **7. Trabalhando com LocalStorage e SessionStorage**
### **7.1 LocalStorage**
- **Conceito**: Armazena dados persistentes no navegador.
- **Exemplo**:
  ```javascript
  localStorage.setItem("usuario", "Lucas");
  console.log(localStorage.getItem("usuario")); // "Lucas"
  ```

### **7.2 SessionStorage**
- **Conceito**: Armazena dados durante a sessão atual.
- **Exemplo**:
  ```javascript
  sessionStorage.setItem("token", "abc123");
  console.log(sessionStorage.getItem("token")); // "abc123"
  ```

---

## **8. Tratamento Avançado de Erros**
### **8.1 Lançar Erros**
- **Conceito**: Usar `throw` para criar mensagens de erro personalizadas.
- **Exemplo**:
  ```javascript
  const dividir = (a, b) => {
    if (b === 0) throw new Error("Divisão por zero não é permitida");
    return a / b;
  };

  try {
    console.log(dividir(10, 0));
  } catch (erro) {
    console.error(erro.message);
  }
  ```

---

## **9. Expressões Regulares**
### **Conceito**: Usar padrões para buscar e manipular strings.
- **Exemplo**:
  ```javascript
  const regex = /\d+/; // Busca por números
  const texto = "A idade é 30 anos.";
  console.log(texto.match(regex)); // ["30"]
  ```

---

## **10. Ferramentas e Debugging**
### **10.1 Console do Navegador**
- **Conceito**: Inspecionar variáveis e rastrear erros.
- **Exemplo**:
  ```javascript
  console.log("Mensagem informativa");
  console.warn("Aviso");
  console.error("Erro");
  ```

### **10.2 Debugger**
- **Conceito**: Interrompe a execução para inspecionar código.
- **Exemplo**:
  ```javascript
  const soma = (a, b) => {
    debugger; // Interrompe aqui
    return a + b;
  };
  console.log(soma(2, 3));
  ```

---

Com esses tópicos intermediários, você estará preparado para desenvolver aplicações mais robustas e escaláveis, tanto no frontend quanto no backend!