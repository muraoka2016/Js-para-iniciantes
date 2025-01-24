# Guia Conceitual de JavaScript

Este guia cobre os principais conceitos e sintaxes de JavaScript para referência futura, com exemplos práticos.

---

## 1. Sintaxe Básica

### Variáveis

As variáveis em JavaScript podem ser declaradas com `var`, `let` ou `const`.

```javascript
var nome = "João"; // Variável de escopo global ou de função
let idade = 25; // Variável de escopo limitado a blocos
const cidade = "Rio"; // Variável constante, valor não pode ser alterado
```

### Tipos de Dados

- **Primitivos:** `string`, `number`, `boolean`, `undefined`, `null`, `symbol`, `bigint`
- **Objetos:** `Object`, `Array`, `Function`

### Operadores

- **Aritméticos:** `+`, `-`, `*`, `/`, `%`
- **Comparativos:** `==`, `===`, `!=`, `!==`, `<`, `<=`, `>`, `>=`
- **Lógicos:** `&&`, `||`, `!`

Exemplo:

```javascript
let soma = 5 + 3; // 8
let ehMaior = 10 > 5; // true
let resultado = !(5 === "5"); // true (=== compara valor e tipo)
```

---

## 2. Funções

Funções são blocos de código reutilizáveis.

### Declaração

```javascript
function saudacao(nome) {
  return `Olá, ${nome}!`;
}
console.log(saudacao("Maria")); // "Olá, Maria!"
```

### Função Anônima

```javascript
const soma = function (a, b) {
  return a + b;
};
console.log(soma(2, 3)); // 5
```

### Arrow Functions

```javascript
const multiplicar = (a, b) => a * b;
console.log(multiplicar(4, 5)); // 20
```

---

## 3. Arrays e Objetos

### Arrays

Os arrays são listas ordenadas.

#### Métodos Comuns

- `push()`: Adiciona um elemento ao final.
- `pop()`: Remove o último elemento.
- `shift()`: Remove o primeiro elemento.
- `unshift()`: Adiciona um elemento no início.
- `map()`, `filter()`, `reduce()`: Métodos funcionais.

Exemplo:

```javascript
let frutas = ["maçã", "banana", "laranja"];
frutas.push("uva");
console.log(frutas); // ["maçã", "banana", "laranja", "uva"]
```

### Objetos

Objetos são coleções de pares chave-valor.

```javascript
let pessoa = {
  nome: "Ana",
  idade: 28,
  cidade: "Curitiba",
};
console.log(pessoa.nome); // "Ana"
```

---

## 4. DOM (Document Object Model)

O DOM permite interagir com elementos HTML.

### Selecionar Elementos

```javascript
let elemento = document.getElementById("meuId");
let elementos = document.querySelectorAll(".minhaClasse");
```

### Modificar Elementos

```javascript
let titulo = document.getElementById("titulo");
titulo.textContent = "Novo Título";
titulo.style.color = "blue";
```

### Eventos

```javascript
document.getElementById("botao").addEventListener("click", function () {
  alert("Botão clicado!");
});
```

---

## 5. Aplicações de DOM e JS em Formulários

### Manipular Inputs

```javascript
document
  .getElementById("formulario")
  .addEventListener("submit", function (event) {
    event.preventDefault();
    let nome = document.getElementById("nome").value;
    if (nome === "") {
      alert("Por favor, preencha o campo!");
    } else {
      alert(`Olá, ${nome}!`);
    }
  });
```

### Validação Simples

```javascript
let email = document.getElementById("email").value;
if (!email.includes("@")) {
  alert("Email inválido!");
}
```

---

## 6. JSON (JavaScript Object Notation)

JSON é um formato de troca de dados leve, baseado em texto.

### Conversão entre Objeto e JSON

- **Objeto para JSON:** `JSON.stringify(objeto)`
- **JSON para Objeto:** `JSON.parse(json)`

Exemplo:

```javascript
let pessoa = {
  nome: "João",
  idade: 30,
};
let json = JSON.stringify(pessoa); // Converte para JSON
console.log(json); // '{"nome":"João","idade":30}'

let objeto = JSON.parse(json); // Converte de volta para Objeto
console.log(objeto.nome); // "João"
```

---

# Seção 7: Callback, Promise, Async/Await e Fetch API

Nesta seção, exploraremos conceitos fundamentais para a programação assíncrona em JavaScript, como **Callback**, **Promise**, **Async/Await** e a **Fetch API**. Esses recursos são amplamente utilizados para lidar com operações assíncronas, como chamadas a APIs ou tarefas que demoram a ser concluídas.

## 1. Callback

Um **callback** é uma função passada como argumento para outra função e que será executada posteriormente. Esse conceito foi amplamente utilizado antes da introdução das Promises e do Async/Await.

### Exemplo:

```javascript
function obterDados(callback) {
  setTimeout(() => {
    const dados = { nome: "João", idade: 25 };
    callback(dados);
  }, 2000); // Simula uma operação assíncrona
}

function exibirDados(dados) {
  console.log("Dados recebidos:", dados);
}

obterDados(exibirDados);
```

### Limitações dos Callbacks:

- **Callback Hell**: Quando temos várias operações assíncronas aninhadas, o código pode se tornar difícil de ler e manter.

```javascript
buscarUsuario(1, (usuario) => {
  buscarPedidos(usuario.id, (pedidos) => {
    processarPedidos(pedidos, (resultado) => {
      console.log(resultado);
    });
  });
});
```

## 2. Promise

Uma **Promise** representa um valor que pode estar disponível agora, no futuro, ou nunca. Ela permite trabalhar com operações assíncronas de forma mais legível e menos propensa a erros.

### Exemplo:

```javascript
function obterDados() {
  return new Promise((resolve, reject) => {
    setTimeout(() => {
      const sucesso = true; // Simula sucesso ou erro
      if (sucesso) {
        resolve({ nome: "João", idade: 25 });
      } else {
        reject("Erro ao obter dados.");
      }
    }, 2000);
  });
}

obterDados()
  .then((dados) => {
    console.log("Dados recebidos:", dados);
  })
  .catch((erro) => {
    console.error(erro);
  });
```

### Vantagens:

- Evita o **callback hell**.
- Melhor controle sobre erros.

## 3. Async/Await

O **Async/Await** é uma sintaxe mais moderna para trabalhar com Promises. Ele torna o código assíncrono mais legível e semelhante ao código síncrono.

### Exemplo:

```javascript
async function exibirDados() {
  try {
    const dados = await obterDados();
    console.log("Dados recebidos:", dados);
  } catch (erro) {
    console.error(erro);
  }
}

exibirDados();
```

### Benefícios:

- Código mais limpo e fácil de entender.
- Fluxo mais linear e semelhante ao síncrono.

## 4. Fetch API

A **Fetch API** é usada para fazer requisições HTTP. Ela retorna uma Promise, sendo compatível com Async/Await.

### Exemplo com Fetch e Promises:

```javascript
fetch("https://jsonplaceholder.typicode.com/posts")
  .then((response) => {
    if (!response.ok) {
      throw new Error("Erro na requisição");
    }
    return response.json();
  })
  .then((dados) => {
    console.log("Posts:", dados);
  })
  .catch((erro) => {
    console.error(erro);
  });
```

### Exemplo com Fetch e Async/Await:

```javascript
async function obterPosts() {
  try {
    const response = await fetch("https://jsonplaceholder.typicode.com/posts");
    if (!response.ok) {
      throw new Error("Erro na requisição");
    }
    const dados = await response.json();
    console.log("Posts:", dados);
  } catch (erro) {
    console.error(erro);
  }
}

obterPosts();
```

### Principais Recursos da Fetch API:

- **GET**: Buscar dados.
- **POST**: Enviar dados.
- **PUT** e **DELETE**: Atualizar ou excluir dados.

### Exemplo de POST com Fetch:

```javascript
async function criarPost(post) {
  try {
    const response = await fetch("https://jsonplaceholder.typicode.com/posts", {
      method: "POST",
      headers: {
        "Content-Type": "application/json",
      },
      body: JSON.stringify(post),
    });

    if (!response.ok) {
      throw new Error("Erro ao criar post");
    }

    const dados = await response.json();
    console.log("Post criado:", dados);
  } catch (erro) {
    console.error(erro);
  }
}

criarPost({ title: "Novo Post", body: "Conteúdo do post", userId: 1 });
```

## Conclusão

Compreender **Callback**, **Promise**, **Async/Await** e **Fetch API** é essencial para lidar com a programação assíncrona em JavaScript. Cada abordagem tem suas vantagens e limitações, mas juntas, fornecem ferramentas poderosas para criar aplicações robustas e responsivas.

Este guia oferece uma base sólida para consultas durante os estudos de JavaScript. Boa prática!
