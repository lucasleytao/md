Os **Hooks** são uma funcionalidade introduzida no React a partir da versão 16.8. Eles permitem que você use o estado e outras funcionalidades do React em componentes funcionais, algo que antes era exclusivo dos componentes baseados em classe.

Vamos explorar os **Hooks** de forma completa:

---

## **1. O que são Hooks?**

Hooks são funções especiais do React que permitem "enganchar" recursos como estado, ciclo de vida, contexto, etc., em componentes funcionais. Eles trazem simplicidade e flexibilidade para o código.

---

## **2. Regras dos Hooks**

Antes de usar Hooks, você precisa seguir algumas regras importantes:

1. **Somente em funções React**  
   Os Hooks só podem ser usados dentro de componentes funcionais ou seus próprios hooks personalizados.  
   ❌ Não use em funções normais ou fora de componentes.  
   ✅ Correto:  
   ```javascript
   function MeuComponente() {
     const [contador, setContador] = React.useState(0);
     return <button onClick={() => setContador(contador + 1)}>Clique: {contador}</button>;
   }
   ```

2. **Na ordem certa**  
   Nunca use Hooks dentro de loops, condições ou funções aninhadas. Eles devem estar no topo do componente.  
   ❌ Errado:  
   ```javascript
   if (condicao) {
     const [valor, setValor] = useState(0); // Proibido
   }
   ```

3. **Prefixo `use`**  
   Personalize Hooks com o prefixo `use` para que o React reconheça.

---

## **3. Hooks Principais**

Aqui estão os Hooks mais usados, divididos em categorias:

### **3.1. Estado: `useState`**
O `useState` é usado para gerenciar o estado em componentes funcionais. Ele retorna um par: o estado atual e uma função para atualizá-lo.

#### **Sintaxe:**
```javascript
const [estado, setEstado] = useState(valorInicial);
```

#### **Exemplo: Contador**
```javascript
function Contador() {
  const [contador, setContador] = useState(0);

  return (
    <div>
      <p>Você clicou {contador} vezes</p>
      <button onClick={() => setContador(contador + 1)}>Clique</button>
    </div>
  );
}
```

---

### **3.2. Efeitos Colaterais: `useEffect`**
O `useEffect` substitui os métodos de ciclo de vida como `componentDidMount`, `componentDidUpdate` e `componentWillUnmount`. Ele é usado para lidar com efeitos colaterais, como chamadas de API, timers ou interações com o DOM.

#### **Sintaxe:**
```javascript
useEffect(() => {
  // Código a ser executado
  return () => {
    // Limpeza opcional
  };
}, [dependencias]);
```

#### **Exemplo: Fetch de dados**
```javascript
function DadosAPI() {
  const [dados, setDados] = useState([]);

  useEffect(() => {
    fetch('https://api.exemplo.com/dados')
      .then((res) => res.json())
      .then((data) => setDados(data));
  }, []); // Executa apenas uma vez

  return <div>{JSON.stringify(dados)}</div>;
}
```

#### **Exemplo: Limpeza com `useEffect`**
```javascript
function Temporizador() {
  const [contador, setContador] = useState(0);

  useEffect(() => {
    const timer = setInterval(() => setContador((prev) => prev + 1), 1000);
    return () => clearInterval(timer); // Limpa o timer
  }, []);

  return <p>Contador: {contador}</p>;
}
```

---

### **3.3. Contexto: `useContext`**
O `useContext` permite acessar valores de um `Context` sem precisar de um `Consumer`.

#### **Exemplo: Tema**
```javascript
const TemaContext = React.createContext();

function ExibirTema() {
  const tema = useContext(TemaContext);
  return <p>O tema atual é {tema}</p>;
}

function App() {
  return (
    <TemaContext.Provider value="escuro">
      <ExibirTema />
    </TemaContext.Provider>
  );
}
```

---

### **3.4. Referências: `useRef`**
O `useRef` armazena uma referência mutável que não causa re-renderizações quando alterada. É útil para acessar elementos do DOM ou valores persistentes.

#### **Exemplo: Foco no input**
```javascript
function FocoInput() {
  const inputRef = useRef(null);

  const focar = () => {
    inputRef.current.focus();
  };

  return (
    <div>
      <input ref={inputRef} />
      <button onClick={focar}>Focar no input</button>
    </div>
  );
}
```

---

### **3.5. Memorização: `useMemo` e `useCallback`**

#### **`useMemo`**
Usado para memorizar valores computados que são caros de calcular.

```javascript
function SomaPesada({ numero }) {
  const resultado = useMemo(() => {
    return numero * 2; // Simula cálculo pesado
  }, [numero]);

  return <p>Resultado: {resultado}</p>;
}
```

#### **`useCallback`**
Usado para memorizar funções, evitando recriação desnecessária.

```javascript
const handleClick = useCallback(() => {
  console.log('Clicado!');
}, []);
```

---

### **4. Hooks Avançados**

#### **4.1. `useReducer`**
Alternativa ao `useState` para estados mais complexos.

```javascript
function reducer(estado, acao) {
  switch (acao.tipo) {
    case 'incrementar':
      return { contador: estado.contador + 1 };
    default:
      return estado;
  }
}

function ContadorComReducer() {
  const [estado, dispatch] = useReducer(reducer, { contador: 0 });

  return (
    <div>
      <p>{estado.contador}</p>
      <button onClick={() => dispatch({ tipo: 'incrementar' })}>Incrementar</button>
    </div>
  );
}
```

#### **4.2. `useImperativeHandle`**
Customiza instâncias de refs em componentes filhos.

```javascript
const FancyInput = React.forwardRef((props, ref) => {
  const inputRef = useRef();

  useImperativeHandle(ref, () => ({
    focar: () => inputRef.current.focus(),
  }));

  return <input ref={inputRef} />;
});
```

---

### **5. Hooks Personalizados**
Você pode criar seus próprios Hooks para reutilizar lógica.

```javascript
function useContador(inicial = 0) {
  const [contador, setContador] = useState(inicial);
  const incrementar = () => setContador(contador + 1);
  return [contador, incrementar];
}

function Componente() {
  const [contador, incrementar] = useContador(5);
  return <button onClick={incrementar}>Clique: {contador}</button>;
}
```

---

### **Conclusão**
Os Hooks modernizam o React, permitindo que você escreva código mais limpo e reutilizável. Comece pelos básicos como `useState` e `useEffect`, e depois explore Hooks avançados e personalizados à medida que sua aplicação cresce em complexidade.