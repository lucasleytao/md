## Rotas

### **O que são rotas?**
Esses símbolos (`/`, `./`, `../`, `../../`) são usados para especificar caminhos relativos ou absolutos em um sistema de arquivos ou em rotas de um site. Eles indicam a **localização de um arquivo ou recurso** em relação a onde você está atualmente no projeto ou na URL.

---

### **Explicando cada um**

1. **`/` — Caminho absoluto a partir da raiz do sistema ou site**  
   - Para **arquivos locais**: Começa da **raiz do sistema de arquivos**.  
     Exemplo: `/home/lucas/projeto/src/index.js`.  
   - Para **URLs em navegadores**: É a **raiz do domínio ou site**.  
     Exemplo: Se o site é `https://lucasleitao.com` e você acessa `/about`, ele vai para `https://lucasleitao.com/about`.

---

2. **`./` — Caminho relativo ao diretório atual**  
   - Significa **"no mesmo diretório em que estou agora"**.
   - Exemplo:  
     Se você está na pasta `src` e quer acessar um arquivo chamado `App.js`, você usaria:  
     ```javascript
     import App from './App';
     ```
     Aqui, `./` diz: "Olhe no **diretório atual (src)** por algo chamado App.js".

---

3. **`../` — Suba um nível no diretório atual**  
   - Significa **"volte um diretório para trás"**.  
     Exemplo:  
     Se você está em `src/components` e quer acessar algo na pasta `src`, use:  
     ```javascript
     import utils from '../utils';
     ```
     Aqui, `../` diz: "Saia da pasta `components` e vá para a pasta `src`".

---

4. **`../../` — Suba dois níveis no diretório atual**  
   - Significa **"volte dois diretórios para trás"**.  
     Exemplo:  
     Se você está em `src/components/shared` e quer acessar algo na pasta `src`, use:  
     ```javascript
     import config from '../../config';
     ```
     Aqui, `../../` diz: "Saia de `shared`, saia de `components`, e entre na pasta `src`".

---

### **Exemplo prático em um projeto**

#### Estrutura de arquivos:
```
projeto/
│
├── src/
│   ├── App.js
│   ├── components/
│   │   ├── Header.js
│   │   └── shared/
│   │       └── Footer.js
│   ├── utils/
│   │   └── helpers.js
│   └── config.js
```

#### Como usar:

1. **Dentro de `Header.js`, importar `Footer.js` (mesma pasta):**
   ```javascript
   import Footer from './shared/Footer';
   ```

2. **Dentro de `Footer.js`, importar `helpers.js` (fora de `shared`):**
   ```javascript
   import helpers from '../../utils/helpers';
   ```

3. **De qualquer arquivo, importar `config.js` (diretório raiz do `src`):**
   ```javascript
   import config from '../config';
   ```

---

### **No navegador: Rotas de URL**

- **`./`:**  
  É o caminho relativo à página atual.  
  Exemplo: Se você está em `https://lucasleitao.com/blog`, acessar `./post` leva você para:  
  `https://lucasleitao.com/blog/post`.

- **`/`:**  
  É a raiz do site.  
  Exemplo: Acessar `/about` em `https://lucasleitao.com/blog` leva para:  
  `https://lucasleitao.com/about`.

- **`../`:**  
  Volta uma pasta na estrutura de URL.  
  Exemplo: Se você está em `https://lucasleitao.com/blog/post`, acessar `../` leva para:  
  `https://lucasleitao.com/blog`.

- **`../../`:**  
  Volta duas pastas na estrutura de URL.  
  Exemplo: De `https://lucasleitao.com/blog/post/comments`, acessar `../../` leva para:  
  `https://lucasleitao.com/blog`.

---

### **Resumo simplificado (para guardar na mente)**

- **`/`**: Comece da raiz (Pasta raiz). 
- **`./`**: Aqui mesmo (Onde estou).  
- **`../`**: Suba um nível (Volte um diretório atrás).  
- **`../../`**: Suba dois níveis (Volte dois diretórios atrás).