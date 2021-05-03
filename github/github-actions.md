# GitHub Actions

Primeiro passo é criar um diretório `$ mkdir -p .github/workflows`

Dentro da diretório criado, crie o arquivo `$ touch build.yml`

```yml
name: build
on: [push]
jobs:
  build:
    runs-on: ubuntu-latest
    strategy:
      matrix:
        node-version: [14.x]
    steps:
      - uses: actions/checkout@v2
      - name: Use Node.js ${{ matrix.node-version }}
        uses: actions/setup-node@v1
        with:
          node-version: ${{ matrix.node-version }}
      - run: npm install
      - run: npm run lint
      - run: npm run build
      - run: npm test
      - name: Coveralls
        uses: coverallsapp/github-action@master
        with:
          github-token: ${{ secrets.GITHUB_TOKEN }}
```

## name

É o nome do fluxo de trabalho. É opcional.

## on

É o evento que aciona o workspace.

## jobs

São as tarefas que o workspace executa.

## runs-on

É o ambiente em que o workspace é executado.

## strategy.matrix

É a matriz de contrução, em nosso exemplo, estamos executando um work para uma versão de nó único.

## steps

São as tarefas que um work. Nesse exemplo, estamos usando as ações do GitHub:

- Checkout
- Setup Node.js
- Coveralls GitHub Action

### actions/checkout

Verifica o repositório e `actions/setup-node` configura o ambiente.

### coverallsapp/github-action

Envia o relatório de cobertura para o Coveralls

## Steps.run

Executa os comandos, esses comandos podem ser escrito tanto no NPM ou com comandos bash.

## env

Define as variáveis de ambiente para todo o fluxo de trabalho ou etapa individual.
