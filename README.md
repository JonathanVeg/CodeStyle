# Manual Técnico de Code Style

## VSCode - Extensões recomendadas

### ESLint + Prettier

Única extensão da lista **obrigatória** para garantir que teremos o código padronizado.

Juntas garantem que todos teremos os códigos usando as guidelines definidas.

ESLint: Serve para garantir que todos os desenvolvedores do projeto usarão o _mesmo padrão de código_.

Prettier: Automatiza a correção das regras do ESLint de maneira automática quando salvar o arquivo.

Após instalar as duas extensões no VSCode, adicionar isso nas configurações de usuários do VSCode para garantir que estarão funcionando:

```json
// parte dos lints
"editor.formatOnSave": true,
"prettier.printWidth": 160,
"prettier.tabWidth": 4,
"prettier.trailingComma": "all",
"prettier.jsxBracketSameLine": true,
"prettier.eslintIntegration": true,

// mostrará duas marcacoes verticais no editor. O ideal é que o código nunca passe da primeira (80 colunas), mas ele não deve passar mesmo nunca da segunda.
"editor.rulers": [
    80,
    120,
],
```

#### NodeJS

Em cada projeto, adicionar essas dependências como **devDependencies**

```bash
yarn add -D eslint eslint-config-airbnb-base eslint-config-prettier eslint-plugin-import eslint-plugin-prettier

# OU

npm install -D eslint eslint-config-airbnb-base eslint-config-prettier eslint-plugin-import eslint-plugin-prettier
```

Dentro de cada projeto **NodeJS**, adicionar o arquivo .eslintrc.js com o seguinte conteúdo:

```javascript
module.exports = {
  env: {
    es6: true,
    node: true
  },
  extends: ["airbnb-base"],
  globals: {
    Atomics: "readonly",
    SharedArrayBuffer: "readonly"
  },
  parserOptions: {
    ecmaVersion: 2018,
    sourceType: "module"
  },
  rules: {
    indent: ["error", 2],
    "no-multiple-empty-lines": [1, { max: 1 }],
    "class-methods-use-this": "off",
    "no-param-reassign": "off",
    "comma-dangle": [
      "error",
      {
        arrays: "never",
        objects: "always"
      }
    ],
    "no-unused-vars": [
      "error",
      {
        argsIgnorePattern: "next"
      }
    ]
  }
};
```

#### ReactJS

Em cada projeto, adicionar essas dependências no **devDependencies** do _package.json_ e rodar o _npm install_ ou _yarn_ em seguida

```json
yarn add -D eslint eslint-config-airbnb eslint-config-prettier eslint-plugin-import eslint-plugin-jsx-a11y eslint-plugin-prettier eslint-plugin-react eslint-plugin-react-hooks prettier

# ou

npm install -D eslint eslint-config-airbnb eslint-config-prettier eslint-plugin-import eslint-plugin-jsx-a11y eslint-plugin-prettier eslint-plugin-react eslint-plugin-react-hooks prettier
```

Dentro de cada projeto **ReactJS**, adicionar o arquivo .eslintrc.js com o seguinte conteúdo:

```javascript
module.exports = {
  env: {
    browser: true,
    es6: true
  },
  extends: ["airbnb", "prettier", "prettier/react"],
  globals: {
    Atomics: "readonly",
    SharedArrayBuffer: "readonly"
  },
  parser: "babel-eslint",
  parserOptions: {
    ecmaFeatures: {
      jsx: true
    },
    ecmaVersion: 2018,
    sourceType: "module"
  },
  plugins: ["react"],
  rules: {
    quotes: [2, "single"],
    indent: ["error", 2],
    "no-multiple-empty-lines": [1, { max: 1 }],
    "prettier/prettier": "error",
    "comma-dangle": [
      "error",
      {
        arrays: "never",
        objects: "always"
      }
    ],
    "react/jsx-filename-extension": [
      "warn",
      {
        extensions: ["js", "jsx"]
      }
    ],
    "import/prefer-default-export": "off"
  }
};
```

### GitLens

Integrada com o Git (não github) mostra informações úteis dentro do git dentro do projeto. Entre as funcionalidades, a principal é que ela ajuda a resolver conflitos de maneira visual e simples.

### Rocketseat React Native + Rocketseat ReactJS

Juntas, elas disponibilizam vários atalhos para programar em React Native e React JS respectivamente. Facilita muito a vida tê-las instaladas.

### Color Highlight

Ajuda a visualizar as cores dentro do VSCode. Ele identifica onde tem um hexadecimal, rgb, nome de cor, etc e mostra a cor ao lado.

### Settings Sync

Ao conectar ao github, com ela você consegue sincronizar suas configurações do VSCode direto num _gist_ do github. Bastante útil quando se tem muitas extensões e não quer o risco de perder suas configurações.

## GIT

Nunca esquecer de configurar o .gitignore adequadamente. Na pasta gitignores tem arquivos base para o gitignore de node, reactjs e reactnative.

Evitar commits com descrições poucos explicativas.

### Política de Branches

Sempre trabalharemos com pelo menos 3 branches:

- Master: somente coisas prontas para ir para produção.
- Homologação: branch de branch para o cliente.
- Dev: tudo que está em desenvolvimento, está pronto, mas ainda não foi para produção. Branch que irá para o servidor de testes adequado.
- Feature: cada feature precisa ter sua branch. Uma vez pronta (e testada!) é feito um pull request para a branch _dev_.

## TESTES

Teremos que ter, ainda será pensado e adicionado aqui.
