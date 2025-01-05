## Roteiro completo e detalhado de fundamentos de JavaScript

## **1. Introdução ao JavaScript**
### **1.1 O que é JavaScript?**
- **Conceito**: JavaScript é uma linguagem de programação que permite criar interatividade em páginas da web. É executada no navegador e no servidor (Node.js).
- **Exemplo de Uso**: 
  - Adicionar interatividade a botões, validação de formulários, animações, etc.
- **Prática**: Crie um arquivo `.html` com um `<script>`:
  ```html
  <!DOCTYPE html>
  <html>
  <head><title>JS Básico</title></head>
  <body>
    <h1>Olá, Mundo!</h1>
    <script>
      console.log("Olá, Mundo!");
    </script>
  </body>
  </html>
  ```

---

## **2. Tipos de Dados e Operações Básicas**
### **2.1 Tipos Primitivos**
- **Conceito**: Tipos básicos em JavaScript.
  - `String`: Texto.
  - `Number`: Números inteiros ou decimais.
  - `Boolean`: Verdadeiro ou falso.
  - `Undefined`: Sem valor atribuído.
  - `Null`: Valor intencionalmente vazio.
  - `Symbol`: Identificador único.
  - `BigInt`: Números inteiros muito grandes.

- **Exemplo**:
  ```javascript
  const nome = "Lucas"; // String
  const idade = 30;     // Number
  const ativo = true;   // Boolean
  let valor;            // Undefined
  const nada = null;    // Null
  ```

### **2.2 Operadores Básicos**
- **Conceito**: Ferramentas para realizar cálculos ou comparações.
  - **Aritméticos**: `+`, `-`, `*`, `/`, `%`.
  - **Comparação**: `==`, `===`, `!=`, `!==`, `>`, `<`, `>=`, `<=`.
  - **Lógicos**: `&&`, `||`, `!`.

- **Exemplo**:
  ```javascript
  const soma = 5 + 3; // 8
  const ehMaior = 10 > 5; // true
  const condicao = ehMaior && ativo; // true
  ```

---

## **3. Declaração de Variáveis**
### **3.1 Usando `var`, `let` e `const`**
- **Conceito**:
  - `var`: Declarada globalmente ou no escopo da função.
  - `let`: Escopo de bloco e valor reatribuível.
  - `const`: Escopo de bloco e valor imutável.

- **Exemplo**:
  ```javascript
  var nomeVar = "Var";
  let nomeLet = "Let";
  const nomeConst = "Const";
  ```

### **3.2 Regras de Nomeação**
- **Conceito**: Deve começar com letra, `$`, ou `_`.
- **Prática**:
  ```javascript
  const $dolar = 10;
  let _underscore = 20;
  const idadePessoa = 25; // CamelCase recomendado
  ```

---

## **4. Estruturas de Controle**
### **4.1 Condicionais**
- **Conceito**: Permitem executar blocos de código baseados em condições.
- **Exemplo**:
  ```javascript
  const idade = 18;
  if (idade >= 18) {
    console.log("Maior de idade");
  } else {
    console.log("Menor de idade");
  }
  ```

### **4.2 Switch**
- **Conceito**: Verifica múltiplos casos.
- **Exemplo**:
  ```javascript
  const dia = "segunda";
  switch (dia) {
    case "segunda":
      console.log("Começo da semana");
      break;
    case "sexta":
      console.log("Fim da semana");
      break;
    default:
      console.log("Dia comum");
  }
  ```

---

## **5. Estruturas de Repetição**
### **5.1 Loops**
- **Conceito**: Repetem um bloco de código enquanto a condição for verdadeira.
- **Tipos**:
  - `for`: Loop com início, condição e incremento.
  - `while`: Executa enquanto a condição for verdadeira.
  - `do...while`: Sempre executa pelo menos uma vez.

- **Exemplo** (For):
  ```javascript
  for (let i = 0; i < 5; i++) {
    console.log(`Número: ${i}`);
  }
  ```

- **Exemplo** (While):
  ```javascript
  let i = 0;
  while (i < 3) {
    console.log(i);
    i++;
  }
  ```

---

## **6. Funções**
### **6.1 Declaração e Invocação**
- **Conceito**: Um bloco de código que pode ser reutilizado.
- **Exemplo**:
  ```javascript
  function saudacao(nome) {
    return `Olá, ${nome}!`;
  }
  console.log(saudacao("Lucas"));
  ```

### **6.2 Arrow Functions**
- **Conceito**: Sintaxe curta para funções.
- **Exemplo**:
  ```javascript
  const soma = (a, b) => a + b;
  console.log(soma(2, 3)); // 5
  ```

---

## **7. Objetos e Arrays**
### **7.1 Objetos**
- **Conceito**: Estruturas que armazenam pares chave-valor.
- **Exemplo**:
  ```javascript
  const pessoa = {
    nome: "Lucas",
    idade: 30,
    saudacao() {
      return `Olá, meu nome é ${this.nome}`;
    },
  };
  console.log(pessoa.saudacao());
  ```

### **7.2 Arrays**
- **Conceito**: Coleções ordenadas de elementos.
- **Exemplo**:
  ```javascript
  const frutas = ["Maçã", "Banana", "Laranja"];
  frutas.push("Manga");
  console.log(frutas); // ["Maçã", "Banana", "Laranja", "Manga"]
  ```

---

## **8. Manipulação do DOM**
### **8.1 Seleção de Elementos**
- **Conceito**: Acessar elementos HTML.
- **Exemplo**:
  ```javascript
  const titulo = document.getElementById("titulo");
  titulo.textContent = "Novo Título";
  ```

### **8.2 Eventos**
- **Conceito**: Adicionar interatividade.
- **Exemplo**:
  ```javascript
  const botao = document.getElementById("botao");
  botao.addEventListener("click", () => {
    alert("Botão clicado!");
  });
  ```

---

## **9. Operações com JSON**
### **Conceito**
- JSON (JavaScript Object Notation) é usado para representar dados.
- **Exemplo**:
  ```javascript
  const dados = '{"nome": "Lucas", "idade": 30}';
  const obj = JSON.parse(dados); // Converter JSON para Objeto
  console.log(obj.nome); // Lucas
  ```

---

## **10. Tratamento de Erros**
### **Conceito**
- Usar `try...catch` para lidar com erros.
- **Exemplo**:
  ```javascript
  try {
    const resultado = soma(2, 3); // Função inexistente
  } catch (erro) {
    console.log("Erro:", erro.message);
  }
  ```

---

Com esses fundamentos bem consolidados, você estará preparado para avançar para níveis intermediários e avançados. Recomendo que pratique cada tópico criando pequenos projetos, como calculadoras, listas de tarefas ou um contador interativo!