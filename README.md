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

Este guia oferece uma base sólida para consultas durante os estudos de JavaScript. Boa prática!
