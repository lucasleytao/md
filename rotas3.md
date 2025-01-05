``Completa``

```javascript
// Estrutura do projeto para os exemplos:
//
// projeto/
//   ├── src/
//   │   ├── components/
//   │   │   ├── Button/
//   │   │   │   ├── Button.js
//   │   │   │   └── styles.css
//   │   │   └── Card/
//   │   │       └── Card.js
//   │   ├── pages/
//   │   │   ├── Home/
//   │   │   │   └── index.js
//   │   │   └── About/
//   │   │       └── index.js
//   │   └── utils/
//   │       └── helpers.js
//   └── package.json

// 1. Exemplo usando ./ (diretório atual)
// Arquivo: src/components/Button/Button.js
import './styles.css';  // Importa CSS do mesmo diretório
const Button = () => {
    return <button className="button">Clique aqui</button>;
};

// 2. Exemplo usando / (diretório raiz)
// Arquivo: src/pages/Home/index.js
// Note: Em muitos frameworks modernos, '/' se refere à pasta src
import Button from '/components/Button/Button';  // Caminho absoluto desde a raiz
import helpers from '/utils/helpers';

const Home = () => {
    return (
        <div>
            <h1>Página Inicial</h1>
            <Button />
        </div>
    );
};

// 3. Exemplo usando ../ (voltar um nível)
// Arquivo: src/components/Card/Card.js
import Button from '../Button/Button';  // Volta um nível para acessar a pasta Button

const Card = () => {
    return (
        <div className="card">
            <h2>Título do Card</h2>
            <Button />
        </div>
    );
};

// 4. Exemplo usando ../../ (voltar dois níveis)
// Arquivo: src/pages/About/index.js
import helpers from '../../utils/helpers';  // Volta dois níveis: sai de About/ e pages/
import Button from '../../components/Button/Button';

const About = () => {
    const { formatDate } = helpers;
    
    return (
        <div>
            <h1>Sobre nós</h1>
            <p>Data atual: {formatDate(new Date())}</p>
            <Button />
        </div>
    );
};

// 5. Exemplo mais complexo com múltiplos níveis
// Arquivo: src/components/Button/SubComponent/SubButton.js
import helpers from '../../../utils/helpers';  // Volta três níveis
import Button from '../Button';  // Volta um nível
import Card from '../../Card/Card';  // Volta dois níveis e entra em Card

const SubButton = () => {
    return (
        <div>
            <Button />
            <Card />
        </div>
    );
};

```

Vamos analisar cada tipo de rota em detalhes:

1. `/` (Diretório Raiz):
   - Começa a busca desde a raiz do projeto
   - Em frameworks modernos, geralmente aponta para a pasta `src/`
   - Exemplo: `import Button from '/components/Button'`
   - É útil para evitar caminhos relativos complexos

2. `./` (Diretório Atual):
   - É como dizer "aqui mesmo onde estou"
   - Útil para importar arquivos que estão na mesma pasta
   - Exemplo: `import './styles.css'` busca um arquivo no mesmo diretório
   - Na maioria das vezes, você pode omitir o `./`

3. `../` (Voltar Um Nível):
   - Como "subir uma pasta"
   - Muito usado para acessar arquivos em pastas vizinhas
   - Exemplo: Se você está em `pages/Home`, usar `../` te leva para `pages/`

4. `../../` (Voltar Dois Níveis):
   - Como "subir duas pastas"
   - Útil quando você precisa acessar arquivos mais distantes
   - Exemplo: De `pages/About/index.js` para acessar `utils/helpers.js`

Algumas dicas práticas:

1. Visualize como uma árvore:
```
Você está aqui: src/pages/Home/index.js
./ → Você está em Home/
../ → Volta para pages/
../../ → Volta para src/
```

2. Use autocomplete do seu editor:
- Comece digitando o caminho e deixe o editor te ajudar
- Se o caminho não funcionar, verifique se você subiu níveis suficientes

3. Dica profissional:
```javascript
// Em vez de caminhos complexos como:
import Button from '../../../components/Button';

// Configure aliases no seu projeto:
import Button from '@/components/Button';
```

4. Regra prática:
- Conte as barras (`/`) entre seu arquivo atual e o arquivo alvo
- Para cada barra, você precisa de um `../`