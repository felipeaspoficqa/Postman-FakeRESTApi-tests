# 🧪 Testes de API com Postman - FakeRestAPI

Projeto de portfólio focado em testes de API REST utilizando **Postman** e **JavaScript assertions**, com validação de cenários positivos, negativos, schema validation e documentação de bugs encontrados.

---

## 🚀 Objetivo

Demonstrar conhecimentos em testes de API, cobrindo:

- ✅ Happy path
- ⚠️ Testes negativos
- 📌 Validação de status code
- 📄 Validação de schema com AJV
- 🔁 Fluxos CRUD
- 🐞 Documentação de bugs encontrados

---

## 🛠️ Tecnologias utilizadas

- Postman
- JavaScript
- AJV (JSON Schema Validator)
- FakeRestAPI

---

## 📋 Cenários testados

### 📥 GET - Listar atividades
- Retorno 200
- Estrutura do array de objetos
- Validação de schema
- Método não suportado (405)

### ➕ POST - Criar atividade
- Criação com sucesso
- Validação do ID retornado
- Validação de schema
- Teste com body vazio

### 🔍 GET por ID
- Busca por ID válido
- ID inexistente (404)
- ID inválido (400)
- Método não suportado (405)

### ✏️ PUT - Atualizar atividade
- Atualização com sucesso
- Body inválido
- ID inexistente

### 🗑️ DELETE - Deletar atividade
- Exclusão com sucesso
- ID inexistente
- ID inválido

---

## 🐞 Bugs encontrados

### Bug 1
**API cria activity com body vazio sem retornar erro de validação nos endpoint POST, PUT ou DELETE /activities** 

**Passos para execução:**  
1. No Postman, selecionar um dos métodos citados na seguinte URL:  
   `https://fakerestapi.azurewebsites.net/api/v1/Activities`  
2. Enviar um body request vazio - `{}`  
3. Clicar em **Send** e verificar o resultado  

**Resultado esperado:**  
API deveria apresentar o status code **400 - Bad Request**  

**Resultado obtido:**  
API retorna status code **200** e salva registro com **id: 0, title: null e data inválida**

---

### Bug 2
**API retorna 200 ao tentar atualizar activity com ID inexistente no endpoint PUT /activities/{id}**  

**Passos para execução:**  
1. No Postman, selecionar o método **PUT** na seguinte URL:  
   `https://fakerestapi.azurewebsites.net/api/v1/Activities`  
2. No body, seguindo o modelo de payload descrito na documentação, colocar o número **99999** como valor do campo `id`  
3. Clicar em **Send** e verificar o resultado  

**Resultado esperado:**  
API deveria apresentar o status code **404 - Not Found**  

**Resultado obtido:**  
API retorna status code **200** e salva registro com **id: 99999** (que é inexistente)

---

### Bug 3
**API retorna 200 com body vazio ao tentar deletar activity com ID inexistente no endpoint DELETE /activities/{id}**

**Passos para execução:**  
1. No Postman, selecionar o método **DELETE** na seguinte URL:  
   `https://fakerestapi.azurewebsites.net/api/v1/Activities/99999`  
2. Clicar em **Send** e verificar o resultado  

**Resultado esperado:**  
API deveria apresentar o status code **404 - Not Found**  

**Resultado obtido:**  
API retorna status code **200**

---

## 💻 Como executar

1. Importar a collection no Postman
2. Configurar as variáveis
3. Executar os requests manualmente ou via Collection Runner

---

## 📌 Observação

Os bugs documentados foram identificados durante a execução dos testes negativos e demonstram capacidade de análise crítica, validação de regras de negócio e documentação de defeitos.
